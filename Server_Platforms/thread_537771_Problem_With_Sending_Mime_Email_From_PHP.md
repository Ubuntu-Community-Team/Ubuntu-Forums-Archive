---
title: "Problem With Sending Mime Email From PHP"
date: 2007-08-29
forum: Server Platforms
---

### Post by jlacroix on 2007-08-29
Note: I edited my initial post because I found the main issue, but I have a different issue now.

When I am using php mail to send an email through a website I created, the email seems corrupted and/or it has garbage text on the very bottom. I want to get rid of this garbage text. I traced the problem to be my headers in my code. If I leave out the headers it will show up perfect. I need the headers to be in there though, so hopefully I can get help finding the error in my header:

I appreciate any help I can get, this is one of those annoying things that work fine but have that one thing happening that you can't seem to get rid of, and in my case its garbage data. :(

```

function htmlmail($to, $subject, $message){
	//add From: header 
	$headers = "From: workorder@landaal.com\n";

	//specify MIME version 1.0 
	$headers .= "MIME-Version: 1.0\n"; 

	//unique boundary 
	$boundary = uniqid("WORKORDER"); 

	//tell e-mail client this e-mail contains//alternate versions 
	$headers .= "Content-Type: multipart/alternative" . 
			"; boundary = $boundary\n"; 

	//message to people with clients who don't 
	//understand MIME 
	$headers .= "This is a MIME encoded message.\n"; 

	//plain text version of message 
	$headers .= "--$boundary\n" . "Content-Type: text/plain; charset=ISO-8859-1\n" . "Content-Transfer-Encoding: //base64\n"; 
	$headers .= chunk_split(base64_encode("This is the plain text version!")); 

	//HTML version of message 
	$headers .= "--$boundary\n" . "Content-Type: text/html; charset=ISO-8859-1\n" . "Content-Transfer-Encoding: base64\n\n"; 
	$headers .= chunk_split(base64_encode($message)); 

	//send message 
	//mail($to, $subject, "", $headers); 
	//$body = $message;
	// THIS ONE ALMOST WORKED: mail($to, $subject, "", $body);
	//mail($to, $subject, $body, $headers);


	$body = $message;
	mail($to, $subject, $body, $headers);

```

---

