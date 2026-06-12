---
title: "PHP5 Email contact form"
date: 2010-11-24
forum: Server Platforms
---

### Post by gypsumwolf on 2010-11-24
I am running Ubuntu 10.04LTS on a server.

I am trying to make an e-mail contact form. When I hit submit, it says the message was sent. I check my e-mail and I don't see it. Does it not work with gmail? or do I need to use a system [email]username@mydomain.net[/email]?

This is the PHP mailer.
```
<?php
if(isset($_POST['submit'])) {

$to = "myemail@mydomain"; #This is set to my gmail.com e-mail.
$subject = "Unserv Form";
$name_field = $_POST['name'];
$email_field = $_POST['email'];
$message = $_POST['message'];
 
$body = "From: $name_field\n E-Mail: $email_field\n Message:\n $message";
 
echo "Message was sent!";
mail($to, $subject, $body);

} else {

echo "Error, it did not work! Please mention this to admin@unserv.net!";

}
?>
```

This is a snip of HTML from the contact site:
```
	<form method="POST" action="sndmsg.php">
   	Name: <input type="text" name="name" size="19"><br>
   	<br>
   	E-Mail: <input type="text" name="email" size="19"><br>
   	<br>
   	Message:<br><textarea rows="20" name="message" cols="50"></textarea>
   	<br>
   	<br>
   	<input type="submit" value="Submit" name="submit">
		</form>
```

---

### Post by James78 on 2010-11-24
Your code looks fine to me, maybe the place where you are using the form doesn't have a properly setup email system? Where are you emailing from? See if emailing to another place works..

---

### Post by SeijiSensei on 2010-11-24
Look in /var/log/mail.log for some hints.  Also does your ISP allow outbound port 25 traffic?

One other issue concerns the form itself.  Since you allow both a From and a To field, your form is susceptible to being exploited by spammers.  Contact forms should use a predefined To address that is stored only in the script itself for security.

One other thing is that the SMTP sender address (not the From, but the address used in the exchange between servers) will be something like "apache@server.example.com" unless you've done some fancy footwork in Postfix or sendmail.

---

### Post by RTrev on 2010-11-24
Well, you tell them the message was sent, and then you actually try to send it.  There should be a boolean return code from the mail() function that would let you evaluate the success or failure of the send.  From that you can perhaps figure out why it's failing.

[http://php.net/manual/en/function.mail.php](http://php.net/manual/en/function.mail.php)

---

### Post by gypsumwolf on 2010-11-24
Its probably my e-mail system. Do I need to use postfix or libphp-phpmailer?

---

### Post by RTrev on 2010-11-24
I'd just look at the return code first.  I've used mail() quite a bit, and never had a problem.  Of course, as the manual notes, you might succeed in sending but the mail doesn't reach the destination for some other reason.

Only way to know is check the return code and then base your success or failure message on that.  Once you know if the mail is being sent successfully or not, it should be easier to debug.

You might want to include test code which would print out the entire list of arguments being handed to mail() so you can see if they look reasonable.  If someone puts in an invalid address, for example, you'd expect it to fail with a success message the way it's written now.

---

### Post by SeijiSensei on 2010-11-24
PHP function to check for valid e-mail addresses per RFC2821:

```

	function check_email($address) {
		
		# return code indicates result
		# 0 = email ok
		# 1 = bad address form
		# 2 = no mx record for domain and host doesn't accept smtp
		
                $bademail=0;
		
		# no @ or comma instead of period
		if (!strstr($address,"@") || (strstr($address,",")) { 
			$bademail=1;
			
		} else {
			$emailchk=explode("@",$address);
			$mailname=trim($emailchk[0]);
			$maildom=trim($emailchk[1]);
			
			# check domain part for invalid characters
			if (ereg("[^a-zA-Z0-9\.\-]",$maildom)) {
				$bademail=1;
			}
			
			# check domain part has a valid mx record
			if (!$bademail) {
				# note: host returns a null string to sysout if no record found
				# and it reports "host not found" to syserr
				$mxchk=`host -t mx $maildom`;
				if (empty($mxchk) || strstr($mxchk,"NXDOMAIN")) {
					$bademail=2;
					
					# check if host itself receives mail per RFC2821
					$nmapchk=`nmap -P0 -PT25 -sT -p 25 $maildom | grep smtp | grep open`;
					
					if (!empty($nmapchk)) {
						$bademail=0;
					}
				}
			}
			
		}
		
		return $bademail;
		
	}


```

The last check requires you to install "nmap" on the server.  Also the newest versions of PHP deprecate ereg() in favor or preg(); I haven't gotten around to changing that in my script yet.

---

