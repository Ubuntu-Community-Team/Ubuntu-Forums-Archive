---
title: "Problems with Ubuntu, Apache, and No-IP"
date: 2009-01-22
forum: Server Platforms
---

### Post by nocturnalnights@gmail.com on 2009-01-22
Lord I am having terrible problems. I am running a pest control website for Merlin's Pest Control. I use Apache2 for my webserver, Noip2 for my DUC, and my server (x86) is running Ubuntu Ibex.

No-ip DUC is running, Apache is running, and Intrepid is running, but I can't view the website anywhere but locally. It worked until a few days ago, then POOF, the website can't be accessed remotely.

I have already lost money because of whatever is happening. Maybe it's the OS, the programs, the router, or the ISP? I can VNC in the server, so it aparently accepts some incoming traffic. Outgoing traffic is okay.

Does anyone have any ideas? I was having problems with the network using Apache on my PowerMac G4 in the same network for a failsafe. Could it be my network, or my router?

Ugh, I'm sorry to bother everyone with this, but I have been working on this all day and don't know anymore now then I did this morning. I guess exterminators don't make very good systems admins...

Dave
[http://www.merlinspestcontrol.net](http://www.merlinspestcontrol.net)

---

### Post by timvoet on 2009-01-23
Have you tried running your apache on another port.  Many ISP's are now blocking standard ports to prevent people running web servers on their home machines.  This is to force clients to pay for "business rate plan"

---

### Post by aaron.d on 2009-01-23
the url you provided seems fine. Do I understand that you use no-ip for dns services with your dynamic IP provided by ISP?

If you are making money off this you might want to get an unrestricted business line with you provider of choice, and a proper static IP, as well as a proper routing solution with reliable uptime.

Basically if the website works locally, its either a DNS issue, or an issue with your routing/port forwarding.

---

### Post by Coreigh on 2009-01-23
I agree. The URL is working now, you've established that this is a viable opportunity (income) get a dedicated IP (static address). You may not be making a lot of money, and you may be enjoying the server administration but at the point you have a live web site for someone who is paying you you should get some reliable services. Use a dedicated host for serving the "live" web-site and use your setup for development and testing. You'll save yourself lots of headaches and lost revenue, and you'll look better too.

---

### Post by sam1948 on 2009-01-23
are you behind router?
if so then you will have to forward the ports from the router to your computer check on which port apachi is listening and forward it through the router

---

### Post by jack8888 on 2009-07-13
I was very new to the ubuntu and i was always afraid of using linux commands but after reading your steps to install LAMP on ubuntu, i tried installing it and i did it successfully.  [plus size lingerie](http://www.pamperedpassions.com/plus_size_lingerie_55_ctg.html) [guitar lesson dvd review](http://www.bestguitardvds.com) I can say that i cannnot find any thing better then the steps you have given to install LAMP on ubuntu. Thanks for such Precise and clean steps.

---

