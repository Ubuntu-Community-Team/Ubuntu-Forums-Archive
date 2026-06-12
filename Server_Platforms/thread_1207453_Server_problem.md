---
title: "Server problem"
date: 2009-07-08
forum: Server Platforms
---

### Post by Eric_D on 2009-07-08
Hi all, 

I made the jump about two months ago and made the jump form Windows to Ubuntu, so still quite a newbie. I have everything running quite smoothly except a problem with sending emails through my website or forum running on my own server at home. 

I had Wamp running on my server before the change over and had no probs.  It took me a little while to find out how to create a database and get the HTTP working but managed to get it working in the end but have this send email problem with both PHP and SMTP. I have tried everything I know and checked and double checked all the SMTP settings but have had no luck. Using "localhost" doesn't work either.

Below is one of the error messages I keep getting when I try to send "mass e-mail".

**E-mail error**
» **EMAIL/SMTP**
*/forum/adm/index.php*

Could not get mail server response codes.**Backtrace**

Connecting to smtp.gmail.com:465


Any help very much appreciated. 

Thanks in advance. 

Eric

---

### Post by windependence on 2009-07-08
Your SMTP server probably doesn't allow sending that many e-mails at once to prevent spam. Just a guess.

-Tim

---

### Post by Eric_D on 2009-07-08
Hi Tim, thanks for the reply.

I have only just set up the forum and there are only 3 registered users on there. Sorry should have mentioned that before. 

Email on new registration does not work either so have had to turn that off. It's supposed to be friends & family members only just to keep in touch but would be good if I can get the email working so that we can be notified if anyone leaves a message.

Do I have to setup an Email server on my server or should the SMTP work without one? 

Thanks

Eric

---

### Post by Eric_D on 2009-07-08
Resolved my problem, was trying to send through gmail account but seems it didn't like it. Sending through ISP now and it works.

Thanks again.

Eric

---

