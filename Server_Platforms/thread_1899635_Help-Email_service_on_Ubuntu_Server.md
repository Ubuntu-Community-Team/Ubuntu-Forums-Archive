---
title: "Help-Email service on Ubuntu Server"
date: 2011-12-24
forum: Server Platforms
---

### Post by Hobbiest on 2011-12-24
Hi @ all
this is my first post here, if i am on the wrong section, i request Ubuntu Forum Leaders, kindly move my Thread/Post to the correct section. I hope you can understand as i am newbe here :)

Oki- now lets come quick to the point :- i have already installed Ubuntu server on Dedicated server along with phpmyadmin+webmin etc. I wish to install and run a service like other mail service providers like gmail+yahoo etc.

i want that new user can register on my this service as a mailuser with [email]hisname@mymailservice.com[/email] from there he/she can send outgoing mails to other mail services like gmail+yahoo  also my user can get mails form other email users from gamil+yahoo etc, along with all standered features like attachments+contactbook etc.

to be totally honest with all you great guys , i have no idea what i need to install to get this thing working , i am looking for Free Open Source as my service will also be Free for all users also i can tweak few things as per my requirement. first i want to start with dedicated hosting and maybe later on i may shift to Cloud hosting as and when required.

Kindly suggest me How Can I Do It.

regards
Hobbiest
ashwanigaur.india at gmail dot com

---

### Post by HermanAB on 2011-12-24
Howdy,

The easiest mail server to install is Citadel.  Go to citadel.org and run the Easy Install script.  It takes about 20 minutes and results in a full featured and working system (using Citadel and Apache) and you can always change things later as well.

---

### Post by Lars Noodén on 2011-12-24
In addition to Citadel there is also [Kolab](http://kolab.org/).  Both are significantly more than just basic e-mail.  They include also calendars and other groupware functions.  If you want just e-mail and nothing more, then you can look to exim, postfix, qmail, sendmail, or simta.

---

### Post by tommihl on 2011-12-24
Btw in some countries ISP's restrict ports used to send mail..

---

### Post by Lars Noodén on 2011-12-24
> **tommihl said:**
> Btw in some countries ISP's restrict ports used to send mail..

That varies from ISP to ISP.  In some cases, contacting the ISP to have them unblock the port works.  

In any case, you can test if port 25 is blocked with various services on the net like canyouseeme:
[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by Hobbiest on 2011-12-24
Heartly Thanks to all of you so wounderfull helpfull guys.
i will go through as you advised and hopefully i will get full working new mail service like GMAIL/YAHOO etc and i promise i will provide much more than simple email. so lets keep fingers crossed.

regards to all
hobbiest

---

### Post by oldos2er on 2011-12-24
Moved to Server Platforms.

---

### Post by Hobbiest on 2011-12-25
Thanks for moving the thread to correct section.
regards

---

### Post by dirtrider1 on 2011-12-25
Honestly no offense but if your asking here what to do regarding your initial mail setup you may want to watch out, mail servers are one of the most frequently abused services on the net be careful.

---

### Post by Hobbiest on 2011-12-25
Thanks for the Warning.
i am new, if you can tell me more in details, hopefully i can take prevention action in starting.

another issue is that if i use any thing like Citadel or Kolab or Roundcube as these are under GPL, i tried to read all about GPL but its so complex to understand, Can some one only tell me does GPL allow use for Commercial use like if i get some money via adsense or something like that or if i provide paid options for some extra functions like maybe Big size of attachments allowed in mail service or something like that.

regards

---

### Post by Lars Noodén on 2011-12-25
> **Hobbiest said:**
> Thanks for the Warning.
i am new, if you can tell me more in details, hopefully i can take prevention action in starting.

another issue is that if i use any thing like Citadel or Kolab or Roundcube as these are under GPL, i tried to read all about GPL but its so complex to understand, Can some one only tell me does GPL allow use for Commercial use like if i get some money via adsense or something like that or if i provide paid options for some extra functions like maybe Big size of attachments allowed in mail service or something like that.

regards

It's not that complex if you think about it.  You are free to use GPL licensed software for both commercial and non-commercial activities.  The main point of the GPL is that if you start to re-distribute the software you must also distribute the source code so that the end-users have the same freedom and options that you had.  It's the single most widely used software license currently.

---

### Post by Hobbiest on 2011-12-25
thanks Lars for making things little more clear, lets say i install citadel and tweak it to remove some functions and add some extra functions and start a new mail service which may be partly free or commercial does it means that i am bound to provide my tweaked(modified) citadel to everyone whoever asks for the same????

regards

---

### Post by Lars Noodén on 2011-12-25
Both Google and Volkswagen use GPL software but only VW distributes the software (as part of the car). 

You are bound to give the source code out **only** if you give away or sell the software.  

If you are not distributing it then there is no license obligation.  So if you are just running your service and people use it either free of charge or for a fee, but you are not distributing the actual software, then there is no need to give away the source code either modified or unmodified.  Again if you are just using the software and not handing it out (either free of charge or for a fee) then there is no obligation to give it out.

However, back in the early days of the Web it was a common practice to link to the software that was in use so that others could do the same thing or learn.

---

### Post by Hobbiest on 2011-12-25
Kindly provide Ubuntu forum user a Thanks Button so that i can also say Thanks by Clicking.
regards

---

### Post by Dry Lips on 2011-12-25
If you want to set up a complete email server without using the solutions outlined above (citadel, kolab) I would recommend this tutorial: 
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
(Ubuntu + Postfix + Courier IMAP + MySQL  		+ Amavisd-new + SpamAssassin + ClamAV  		+ SASL + TLS + SquirrelMail/Roundcube + Postgrey)

---

### Post by Hobbiest on 2011-12-25
thanks Dry Lips for the suggestion.
btw i already tried to install citadel but always gets something wrong, which i cant understand. if i can attach log file here(as i will be doing it here for the first time so no idea if i can attach files) kindly some Guru can have a look and guide me how to install citadel correctly. 
regards

---

### Post by Hobbiest on 2011-12-25
hummm i dont know why file not uploaded to the forum, let me try again.
thanks

aha txt file was big, just remove .doc and save it as .txt

---

### Post by lisati on 2011-12-25
> **Hobbiest said:**
> Kindly provide Ubuntu forum user a Thanks Button so that i can also say Thanks by Clicking.
regards

We used to have a "thanks" button but it ended up being disabled due to a combination of database issues (the plugin didn't scale well to a forum our size) and abuse.

Good luck with the email server.

---

