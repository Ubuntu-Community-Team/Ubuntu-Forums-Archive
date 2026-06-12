---
title: "Looken for the proper tutorial on mail server setup"
date: 2010-11-14
forum: Server Platforms
---

### Post by cid420 on 2010-11-14
Ok i have seen alot of great tutorials on getting a mail server up an running. but what i been seeing is no information on how to Obtain DNS, MX, SMTP encryption, if there are errors how to remedy them. all i see is how to install it. i am looken for the proper settings on getting a Free DNS or How to get a NS free or on how you accually send an Inbound and Outbound mail without errors. Really looken the proper step by step installation with the correct tutorials from the beginners perspective situation. Like for an exampled, if i want to control my own Mail server - can i usethe Google free DNS to put in the Bind9 and setup the Mail Server MX correctly to send the mail out and when i pull from there SMTP with no issues. i want to know this from the beginning - reason i am spatting off here is that I cannot get my mail server working at all after the fact that i use the Howtoforge and flurdy.com. 
 
if you dont quite understand what i am getting too i'll more on the lamens terms.. 
 
PS. i have asked my cable company if i could use the NS from them and they said i have to be into a business to do it. so whats the alternatives. where can i get a MX if i need to buy a domain then try to get a MX hosting site I would like to know that.. thanks. maybe its a wrong place to put this. i am still new at this an still learning. please be patient with me.. thanks.
 
Cid420

---

### Post by howefield on 2010-11-14
Moved to Server Platforms.

---

### Post by SeijiSensei on 2010-11-14
> **cid420 said:**
> where can i get a MX if i need to buy a domain then try to get a MX hosting site I would like to know that.

I'm not going to try and answer all the other questions, but the answer to this one is pretty straight-forward.  Once you register a domain you'll be able to create the required A and MX records to point to your server.  I use [DirectNIC](http://www.directnic.com/), but there are many [other good options]("http://ubuntuforums.org/showthread.php?t=1548399") as well.  I'd avoid GoDaddy, though.

---

