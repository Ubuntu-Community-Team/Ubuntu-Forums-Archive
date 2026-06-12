---
title: "help setting up network printer"
date: 2008-10-18
forum: Server Platforms
---

### Post by inadaze on 2008-10-18
Hello,
I have been trying in vain for a week to set up a network printer on Hardy.  I have followed tutorials, google searched errors from logs - now I need help.  I tried with samba and cups but got completely lost in configuration because of Authentication problems with cups.  In a fit of frustration I uninstalled cups to start from scratch.  Can someone help me or point me to a good tutorial...?

My setup is a Hardy server connected to a Belkin wireless router via ethernet.  I have a MacBook Pro (10.4) connected to the belkin router wirelessly.  I have an Epson CX7450 Stylus printer connected by usb to the Hardy server.  I would like to setup all of this so that I can print from my MacBook wirelessly. 

Please help me..
thanks 
Jason

---

### Post by lykwydchykyn on 2008-10-18
Ok, first off you don't need samba.  It will only confuse things.

Set up your printer at the url [https://localhost:631](https://localhost:631), then on the administration tab check "share published printers connected to this system". 

since OS X also uses CUPS for printing, it should connect automatically.  If not, double check that port 631 is open on your Ubuntu machine's firewall.

---

### Post by inadaze on 2008-10-18
Thank you for your reply.
Ok, So I re-installed cupsys and cupsys-driver-gutenprint (because that is where the driver for my printer is said to be).

When I set up a new printer it asks me to choose device.  Which do I choose? Http, Ipp, Gutenprint stylus, Epson Stylus...

Also, the problem that eventually led me to remove cups was because it kept asking me for a use and password and everything I try doesn't work (users on my server and root).  I saw that I was suppose to adduser cupsys shadow, but I get the error : no user cupsys?  How can I authenticate things that I do in cups?

Cheers,
Jason

---

### Post by lykwydchykyn on 2008-10-18
You want http.  I believe you need to add a user to the lpadmin group, then you can login with that user's name and pw.

---

### Post by cariboo on 2008-10-18
Before you start sharing your printer make sure it works on your server, then share it.

Jim

---

### Post by inadaze on 2008-10-19
It works!!!!
I don't know what it was that I did different, but I followed your instructions and it worked.  Maybe it was the sharing printer option (but I am sure I had that on my last install too) or maybe it was samba that was messing me up.  

Either way I am a very happy geek today!

Thanks
Jay

---

