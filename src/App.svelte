<script>
import emailjs from '@emailjs/browser';

export let message = "Email sent to Yash Khatavakar successfully!";
  let visible = false;

  // Automatically hide the toaster after 3 seconds
//   setTimeout(() => {
//     visible = false;
//   }, 3000);
let formDetails = {
  name: '',
  email: '',
  subject:"",
  message:""
};
function handleSubmit(e){
	e.preventDefault();
	const {name,message,subject} = formDetails ?? {};
	const payload = {
		from_name:name,
		to_name:"Yash Khatavakar",
		message,
		subject
	}
	
	emailjs
	.send('service_ueneul6', 'template_g882k4a', payload, {
		publicKey: 'sv7Ilq-Z6CCc8O-j0',
	})
	.then(
		(response) => {
		console.log('SUCCESS!', response.status, response.text);
		formDetails = {  
			name: '',
			email: '',
			subject:"",
			message:""
		}
		visible = true;
			setTimeout(() => {
			visible = false;
		}, 3000);
		},
		(err) => {
		console.log('FAILED...', err);
		
		},
	);
}
console.log("app.sveteee")

</script>

<main>
	<div class="vg-page page-contact" id="contact">
		<div class="container-fluid">
		  <div class="text-center wow fadeInUp">
			<div class="badge badge-subhead">Contact</div>
		  </div>
		  <h1 class="text-center fw-normal wow fadeInUp">Get in touch</h1>
		  <div class="row py-3">
			<div class="col-lg-12">
			  <form class="vg-contact-form" on:submit|preventDefault={handleSubmit}>
				<div class="form-row">
				  <div class="col-12 mt-3 wow fadeInUp">
					<input
					  class="form-control"
					  type="text"
					  name="name"
					  placeholder="Your Name"
					  bind:value={formDetails.name}
					  required
					/>
				  </div>
				  <div class="col-6 mt-3 wow fadeInUp">
					<input
					  class="form-control"
					  type="text"
					  name="email"
					  placeholder="Email Address"
					  bind:value={formDetails.email}
					  required
					/>
				  </div>
				  <div class="col-6 mt-3 wow fadeInUp">
					<input
					  class="form-control"
					  type="text"
					  name="subject"
					  placeholder="Subject"
					  bind:value={formDetails.subject}
					  required
					/>
				  </div>
				  <div class="col-12 mt-3 wow fadeInUp">
					<textarea
					  class="form-control"
					  name="message"
					  rows="6"
					  placeholder="Enter message here.."
					  bind:value={formDetails.message}
					  required
					/>
				  </div>
				  <button
					type="submit"
					class="btn btn-theme mt-3 wow fadeInUp ml-1"
				  >
					Send Message
				  </button>
				</div>
			  </form>
			</div>
		  </div>
		</div>
	  </div>
	
</main>
<div class="toaster {visible ? '' : 'hidden'}">
	{message}
  </div>
<style>

.toaster {
    position: fixed;
    bottom: 20px;
	left: 50%;
    transform: translateX(-50%);
    background-color: #4caf50; /* Green for success */
    color: white;
    padding: 15px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
  }

  .toaster.hidden {
    transform: translateY(100%);
    opacity: 0;
  }
</style>