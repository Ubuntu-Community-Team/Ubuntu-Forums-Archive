---
title: "Postfix Setup Using External SMTP Server"
date: 2010-04-05
forum: Server Platforms
---

### Post by DenisonChapin on 2010-04-05
Hi everyone.

Thanks in advance for reading this thread and thank you so much for helpful replies. 

I'm a sys admin trying to set up Postfix to be able to use my company's external SMTP servers that are hosted at Rackspace.  The SMTP URL is owa.mailseat.com::2525

I've tried to setup the relayhost parameter in /etc/postfix/main.cf

Beyond that I'm stuck.  I've used a separate file, which I've postmaped, to specify the SMTP server URL and login info:

############
owa.mailseat.com [email]myemail@example.com[/email]:myPassExample
############

I need help.  Happy to start from scratch.

Is there any major things I'm missing here?  I have a php mail system setup that lets me send mail through my SMTP server just fine.

My goal is to be able to use PHP to send mail through our SMTP server on a contact form completion.  I want to be able to send mail from a different domain name (the one that our SMTP server is running exchange servers on), so for example, they hit [http://www.myexamplesite01.com](http://www.myexamplesite01.com) and fill out a form, which then sends that form-submitter an email from [http://www.ihavesmtpserversonthisdomain.com](http://www.ihavesmtpserversonthisdomain.com)

Thanks for the help!

Thanks
-Denny

---

### Post by Bachstelze on 2010-04-05
If you only want to send (and not receive) mail, you don't need something as big as Postfix. Install sSMTP instead:

```
sudo apt-get install ssmtp
```

Its configuration is pretty straightforward, and it will give you what you want.

---

### Post by DenisonChapin on 2010-04-05
Many thanks Bachstelze,

I've installed sSMTP and have set my config file as follows:

[INDENT]
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=owa.mailseat.com

# Where will the mail seem to come from?
rewriteDomain=alltreatment.com

# The full hostname
hostname=localhost

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

AuthUser=EMAIL@ADDRES.COM
AuthPass=PASSWORD
UseTLS=YES
UseSTARTTLS=YES


[/INDENT]

Here is the very basic php mail script I'm using:

[INDENT]
<?php
		$headers  = 'MIME-Version: 1.0' . "\r\n";
		$headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";
		$headers .= 'From: denny <dennys@example.com>' . "\r\n";

	mail('dennytest@testing.com', 'Test' , 'test email', $headers);
?>
[/INDENT]

No dice.

At least now the PHP script doesn't run automatically, but took a few seconds to load.  That's a sign of something (although what, I'm unsure of).

Any advice?  Did I screw up the sSMTP settings?  Do I need to add  extra headers/info to my php script?

Thanks!

---

### Post by Bachstelze on 2010-04-05
You said you need to connect to the mail server on port 2525, so you ned:

```
mailhub=owa.mailseat.com:2525
```

If that still doesn't solve it, look in /var/log/mail.*.

---

### Post by DenisonChapin on 2010-04-06
Thanks Bachstelze!

I had to use the built in send-mail function to figure out that it was actually working.

I still cannot figure out how to configure PHP to use ssmtp to send mail.  That's my biggest issue right now.  Anyone have any suggestions?

Thanks!!

---

### Post by Bachstelze on 2010-04-06
> **DenisonChapin said:**
> 
I still cannot figure out how to configure PHP to use ssmtp to send mail.  That's my biggest issue right now.  Anyone have any suggestions?


It doesn't need any configuration. It just uses the system's sendmail, which in your case is provided by ssmtp.

---

### Post by KB1JWQ on 2010-04-07
Right, just ensure your system is using the sendmail binary rather than attempting to have its own SMTP conversation and you should be set.

---

