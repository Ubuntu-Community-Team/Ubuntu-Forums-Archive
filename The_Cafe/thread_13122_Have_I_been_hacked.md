---
title: "Have I been hacked?"
date: 2005-01-28
forum: The Cafe
---

### Post by cacofonix on 2005-01-28
I don't know if this is the right place as I'm using debian so if you guys could be nice and help me out I would really appreciate it :D.
I'm really worried about something that has happened recently. I have had menus and programs dissapear from the start menu, the shutdown option logs me out and doesn't shut down even though I have told it to shutdown in the kde options and now today I get this on my console. I have tried both rkhunter and chkrootkit and the output doesn't suggest anything is out of the ordinary I have a firewall up the only thing I have listening is dhcp and I have what I think are hard passwords to crack. am I worried about nothing or what?


cacofonix

---

### Post by mark on 2005-01-28
It doesn't look real good...that PROMPT string is kinda scary.  What kind of firewall are you running, hardware or software?

Mark

---

### Post by cacofonix on 2005-01-28
The prompt is what worries me the most :-( I have a router that has a built in firewall and I'm using guarddog as well.


cacofonix

---

### Post by mark on 2005-01-28
Hmm - I have a similar setup, except Firestarter instead of guarddog and I've not had anything at all like this.  Then again, I have NO outward-facing ports exposed.

Not sure what to suggest.  You might want to go to *[http://www.grc.com](http://www.grc.com)* and navigate to the *Shields Up!* page to test for blatant vulnerabilities.

---

### Post by Quest-Master on 2005-01-29
That is sort of scary 0_0

I think I should download a firewall too. I'm behind two routers though, it's almost impossible for anything to get through this connection XD

---

### Post by Yukonjack on 2005-01-29
[QUOTE=cacofonix]I don't know if this is the right place as I'm using debian so if you guys could be nice and help me out I would really appreciate it :D.
I'm really worried about something that has happened recently. I have had menus and programs dissapear from the start menu, the shutdown option logs me out and doesn't shut down even though I have told it to shutdown in the kde options and now today I get this on my console. I have tried both rkhunter and chkrootkit and the output doesn't suggest anything is out of the ordinary I have a firewall up the only thing I have listening is dhcp and I have what I think are hard passwords to crack. am I worried about nothing or what?
cacofonix[/QUOTE]

Go to [Gibson Research](http://www.grc.com)  and use ShieldsUp see if he can get in.

---

### Post by jdodson on 2005-01-29
[QUOTE=cacofonix]I don't know if this is the right place as I'm using debian so if you guys could be nice and help me out I would really appreciate it :D.
I'm really worried about something that has happened recently. I have had menus and programs dissapear from the start menu, the shutdown option logs me out and doesn't shut down even though I have told it to shutdown in the kde options and now today I get this on my console. I have tried both rkhunter and chkrootkit and the output doesn't suggest anything is out of the ordinary I have a firewall up the only thing I have listening is dhcp and I have what I think are hard passwords to crack. am I worried about nothing or what?


cacofonix[/QUOTE]

do you have any friends that can access your machine?  perhaps it is a friend playing a joke on you.  if not, backup your files and unplug the box.  check your system access logs and see whats up.  my guess if you have been compromised then they might have covered thier tracks.  however, they might not have.

---

### Post by cacofonix on 2005-01-29
[QUOTE=Yuckonjack] Go to Gibson Research and use ShieldsUp see if he can get in[/QUOTE]

I went there and got scanned I had some stealthed ports but most of them were closed (I think its scanning the router and not me) 


[QUOTE=jdodson]do you have any friends that can access your machine?  perhaps it is a friend playing a joke on you.  if not, backup your files and unplug the box.  check your system access logs and see whats up.  my guess if you have been compromised then they might have covered thier tracks.  however, they might not have.[/QUOTE]

I don't think its a friend playing tricks on me, they all use windows and I don't think they know anything about running linux. 


cacofonix

---

### Post by Jad on 2005-01-29
Salam, 
Try Sygate Tech online scan 
[http://scan.sygatetech.com/](http://scan.sygatetech.com/)

---

