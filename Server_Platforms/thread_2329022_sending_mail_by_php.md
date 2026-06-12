---
title: "sending mail by php"
date: 2016-06-27
forum: Server Platforms
---

### Post by pedro_rodriguez2 on 2016-06-27
Hi,
I have made a simple web page. I have a contact form using a send_mail.php I got from the net.

After a bit of a struggle, I got apache2 and php working on this little laptop. When I have it all working well, I will upload it to the space we bought.

I do not get any errors now, but I also do not get any mail. This is the first bit of the php file:

> #!/usr/bin/php
<?php 
/* 
This first bit sets the email address that you want the form to be submitted to. 
You will need to change this value to a valid email address that you can access. 
*/ 
$webmaster_email = "mymail@foxmail.com";

Near the end of the php file/script it has:

> // If we passed all previous tests, send the email then redirect to the thank you page. 
else { 
mail( "$webmaster_email", "Feedback Form Results", 
  $comments, "From: $email_address" ); 
header( "Location: $thankyou_page" ); 
} 
?>

Just that, I don't get any mail! Of course, that's not my actual email, but in the php file my email is correct.

So I suppose this is a permissions thing. Apache or php can't send mail. How to make that happen??

Any tips out there??

---

### Post by howefield on 2016-06-27
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by pedro_rodriguez2 on 2016-06-27
I read some more and changed /etc/php5/php.ini

I inserted this

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; [http://php.net/sendmail-path](http://php.net/sendmail-path)
;changed by me
sendmail_path = /usr/sbin/sendmail -t -i
;sendmail_path =

On the other hand, maybe it should have quotes "" like this. I've tried both, still no mail!

I do not know what /usr/sbin/sendmail should look like, but mine has only this!

> #!/bin/sh
echo "Please install an MTA on this system if you want to use sendmail!" >&2
exit 255

sendmail_path = "/usr/sbin/sendmail -t -i -f [EMAIL="fromMe@blah.com"]fromMe@blah.com[/EMAIL]"

---

### Post by nerdtron on 2016-06-27
I don't think sendmail is installed on your system? Also, sendmail is an outdated MTA. You'll better off using postfix. Have a look at here: [http://askubuntu.com/questions/47609/how-to-have-my-php-send-mail](http://askubuntu.com/questions/47609/how-to-have-my-php-send-mail)

Do you have your own domain name? Because I don't think you'll be able to send emails to the public internet if you do not own a domain.

---

### Post by pedro_rodriguez2 on 2016-06-27
sendmail was present in /usr/sbin but it was a dummy package. Almost empty.

I installed sendmail and ran sendmailconfig

That is complex. I do not know what settings I might need.

We do have our own domain [www.rapidresults.wang](www.rapidresults.wang) but it may not be open yet. In China you have to get an ICP (Internet Content Provider) license to open a web page. We have that now, but yesterday the page was still blocked as 'domain expired'.

The point is, I think I should be able to make sendmail work here on my laptop. The settings for sendmail are not easy, too many config files, I don't know what to put where. If you know a good tutorial, please send me the link.

Maybe you are right and this cannot work from home!

I'll try from the web too!

---

### Post by pedro_rodriguez2 on 2016-06-27
Getting close now!

I installed ssmtp. Still can't send a mail from my web page, but that may be a problem with  the authorization. Here is a bit of my /var/log/mail.log from just now

> Jun 28 10:00:02 pedro-schule sSMTP[2182]: Server didn't like our AUTH LOGIN (530 Must issue a STARTTLS command first.)
Jun 28 10:06:14 pedro-schule sSMTP[2841]: Server didn't like our AUTH LOGIN (530 Must issue a STARTTLS command first.)
Jun 28 10:09:02 pedro-schule sSMTP[2916]: Server didn't like our AUTH LOGIN (530 Must issue a STARTTLS command first.)

So I changed ssmtp.conf, tried again

> Jun 28 10:19:54 pedro-schule sSMTP[3093]: Creating SSL connection to host
Jun 28 10:19:55 pedro-schule sSMTP[3093]: SSL connection using RSA_ARCFOUR_SHA1
Jun 28 10:19:55 pedro-schule sSMTP[3093]: Authorization failed (535  Error: \C7\EB&#697;\D3\C3\CA\DA&#552;\C2\EB\B5\C7¼\A1\A3\CF\EA\C7\E9\C7&#49140;: [http://service.mail.qq.com/cgi-bin/h...28&&no=1001256]("http://service.mail.qq.com/cgi-bin/help?subtype=1&&id=28&&no=1001256"))
Jun 28 10:20:01 pedro-schule sSMTP[3114]: Creating SSL connection to host
Jun 28 10:20:01 pedro-schule sSMTP[3114]: SSL connection using RSA_ARCFOUR_SHA1
Jun 28 10:20:02 pedro-schule sSMTP[3114]: Authorization failed (535  Error: \C7\EB&#697;\D3\C3\CA\DA&#552;\C2\EB\B5\C7¼\A1\A3\CF\EA\C7\E9\C7&#49140;: [http://service.mail.qq.com/cgi-bin/h...28&&no=1001256]("http://service.mail.qq.com/cgi-bin/help?subtype=1&&id=28&&no=1001256"))

Any ideas??

---

