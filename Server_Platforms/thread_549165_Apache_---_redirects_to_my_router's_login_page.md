---
title: "Apache --- redirects to my router's login page"
date: 2007-09-12
forum: Server Platforms
---

### Post by andytof47 on 2007-09-12
Hi I have Apache up and running and it seems fine but when I go to test it on a diferent computer on the same subnet on the same router I type in the name of the website i'm hosting and 

BAM! I end up on my routers login screen...


Is this because I need to actually test it from the outside world e.g a different network?

thanks Oh yes I have port forwarding enabled etc, it is really just that I want my hunch confirmed --- A nice why this is so would be nice to (just a link is ok or you can write on this post)


Cheers all

many many thanks

---

### Post by wirelessmonkey on 2007-09-12
It sounds like you may want to recheck the port forwarding configuration on your router.

---

### Post by andytof47 on 2007-09-13
Thanks for the reply,

But I have checked my routers Port forwarding setup and it is definently set to hand the requests over to the machine and the machine is set listening to port 80

I had a similar problem once setting up an FTP server ---- basically I couldn't get a login to test it from the same network but external access was possible...

I wasn't sure if the case was the same for a web server or at very least with my setup, A dynamic public IP with dyndns daemon, resolving to [www.blahblah.cc](www.blahblah.cc)  

I think I can access but only externally because I have found a web server tester which retreives the page and displays some stats about it, however I'm not 100% sure because when I try to access it via a web proxy such as [www.hidebehind.org](www.hidebehind.org) or some other proxy it just times out.....

Again any links or info is much appreciated


Cheers

---

### Post by tribble222 on 2007-09-14
This happens to me.  If I'm in my lan I have to access my website by typing 192.168.x.x (wherever it is) but if I'm outside my lan I can access it normally [www.mysite.com](www.mysite.com) (or just my wan ip).  I'm afraid I don't know how to fix it.  If you need someone to check if your site is working externally you could pm me the address and I'll let you know.

---

