---
title: "Run perl script from web form"
date: 2006-05-22
forum: Server Platforms
---

### Post by balloons on 2006-05-22
I've setup my own webserver with apache, and setup a simple web page with a contact form. How do I grab the input from the web form and pass it to my perl script? The perl script simply sends them an email, after scraping a webpage. What I want to have happen is:

1) someone inputs their email address on my website via a form
2) The form calls the perl script on my server, passing their email address, which performs the operations, and sends back a success page.

Anyone do anything like this?

---

### Post by vayde on 2006-05-22
You are talking about creating a CGI program.  Many books have been written on the subject.

Check out CGI.pm  It's a perl module written to do exactly what you are talking about, and much much more.

Apart from the books, (possibly the best being 'Official Guide to Programming with CGI.pm' by Lincoln Stein, the module's author) you will find tons of stuff on the web.

---

### Post by geek_Man on 2006-11-14
To send form data to a Perl script you'll have to put make the action of the form point the the script```
<form name="myform" action="/cgi-bin/foo.pl" method="post">
``` if you change that to whatever the script name is it should work (hopefully... it's sorta been a while since I've done HTML). Your Perl script should look something like this```
#!/usr/bin/perl

use CGI;
CGI::ReadParse();

$foo = $in{name-of-whatever-the-text-field-is};
```Uh, I don't really know how you would send the mail, but that's sort of a start. What the bit of script does is puts the e-mail address into the scalar $foo. That's about all I can tell you.

---

### Post by tturrisi on 2006-11-15
Just as easy to use php:

A script I slapped together that I modify & style for different sites:
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">

<html>

<head>

<title>TITLE</title>

<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">

<meta name="keywords" content=" ">

<meta name="description" content=" ">

<meta name="author" content=" ">

<meta name="copyright" content=" ">

<link rel="shortcut icon" href=" ">

</head>

<body>

<table cellspacing="0" cellpadding="0" border="0">

<tr>



<?php

if ($_POST['submit'] == TRUE) { //if submit button pressed process email



$emailto	= "YOUR_EMAIL_ADDRESS";

$email		= stripslashes(strip_tags($_POST['email']));

$subject	= stripslashes(strip_tags($_POST['subject']));	

$name		= stripslashes(strip_tags($_POST['name']));
$phone		= stripslashes(strip_tags($_POST['phone']));

$msg		= stripslashes(strip_tags($_POST['msg']));

$msgformat	= "From: $name\nEmail: $email\nPhone: $phone\n\n$msg";



if(empty($email) || empty($subject) || empty($name) || empty($phone) || empty($msg)) {

?>

<td>

<p>Error!</p>

<p>Fill in all sections of the e-mail form.</p>

<form name="email" method="post" action="">

<table cellspacing="0">

<tr><td>Your E-Mail:</td><td><input type="text" name="email" size="26" value="<?php echo $email?>"></td></tr>

<tr><td>Subject:</td><td><input type="text" name="subject" size="26" value="<?php echo $subject?>"></td></tr>

<tr><td>Your Name:</td><td><input type="text" name="name" size="26" value="<?php echo $name?>"></td></tr>
<tr><td>Phone:</td><td><input type="text" name="phone" size="14" value="<?php echo $phone?>"></td></tr>

<tr><td colspan="2"><pre><textarea name="msg" rows="8" cols="50"><?php echo $msg?></textarea></pre></td></tr>

<tr><td colspan="2"><input type="submit" name="submit" value="Send"></td></tr>

</table>

</form></td></tr></table>

</body>

</html>


<?php

} //closes if empty fields
// validate email address

elseif(!ereg("^[_a-z0-9-]+(\.[_a-z0-9-]+)*@[a-z0-9-]+(\.[a-z0-9-]+)*(\.[a-z]{2,3})$", $email)) {

?>

<td>

<p>Error!</p>

<p>Invalid e-mail address. Tip: Don't use UPPERCASE letters, use lowercase only.</p></p>

<form name="email" method="post" action="">

<table cellspacing="0">

<tr><td>Your E-Mail:</td><td><input type="text" name="email" size="26" value="<?php echo $email?>"></td></tr>

<tr><td>Subject:</td><td><input type="text" name="subject" size="26" value="<?php echo $subject?>"></td></tr>

<tr><td>Your Name:</td><td><input type="text" name="name" size="26" value="<?php echo $name?>"></td></tr>
<tr><td>Phone:</td><td><input type="text" name="phone" size="14" value="<?php echo $phone?>"></td></tr>

<tr><td colspan="2"><pre><textarea name="msg" rows="8" cols="50"><?php echo $msg?></textarea></pre></td></tr>

<tr><td colspan="2"><input type="submit" name="submit" value="Send"></td></tr>

</table>

</form></td></tr></table>

</body>

</html>

<?php

}//closes elseif bad email address

// send the message

elseif(mail($emailto, $subject, $msgformat, "From: $name <$email>")) {

?>

<td>

<p>Success!</p>

<p>Your message has been sent. Thank you.</p>

<p>You will receive a response as soon as possible.</p>

</body>

</html>


<?php

} //closes elseif send the message


else { //Oops! if problem with the mail server

?>

<td>

<p>Oops!</p>

<p>For technical reasons, the mail server could not send your message.</p>

<p>Please try again later or use an alternate method of contacting us.</p>

<p>Address/Phone/Fax</p>

</html>


<?php

} //closes oops

} //closes if submit



else { //display the contact form if submit button not pressed

?>



<p>Email Contact Form</p>

<form name="email" method="post" action="">

<table cellspacing='0'>

<tr><td>Your E-Mail:</td><td><input type="text" name="email" size="26" value=""></td></tr>

<tr><td>Subject:</td><td><input type="text" name="subject" size="26" value=""></td></tr>

<tr><td>Your Name:</td><td><input type="text" name="name" size="26" value=""></td></tr>
<tr><td>Phone:</td><td><input type="text" name="phone" size="14" value=""></td></tr>

<tr><td colspan="2"><pre><textarea name="msg" rows="8" cols="50"></textarea></pre></td></tr>

<tr><td colspan="2"><input type="submit" name="submit" value="Send"></td></tr>

</table>

</form></td></tr></table>

</body>

</html>



<?php 

} //closes if submit else statement

?>


```

---

### Post by skymt on 2006-11-15
The Apache project has [a good CGI tutorial](http://httpd.apache.org/docs/2.2/howto/cgi.html) that should get you started.

---

