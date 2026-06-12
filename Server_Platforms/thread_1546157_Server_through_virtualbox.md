---
title: "Server through virtualbox"
date: 2010-08-04
forum: Server Platforms
---

### Post by NertSkull on 2010-08-04
So I was curious if this was a bad idea.  I've been building websites for a bit, but always hosted somewhere else and never really understood the webserver side of things.  But now I want to.

So I was going to have a small website put up just for me and a few family members.  I was going to host it local on one of my machines that I don't do much with.  Its just running Ubuntu 9.10 as a mythtv server for me.

I was thinking of setting up a virtual box and installing the LAMP server type of setup on that.  Then forward the ports from the desktop (ubuntu 9.10) to it.  And then forward appropriate ports from the router as needed (and set up a dyndns thing).

Is this a really bad idea with some security issues I'm not aware of?  Or is it just like running a regular server.

I know its probably not needed at all.  I kind of just want to try it.  Partly so I can just turn off the website when I want.  Also so I can wipe all traces of it in the future when I'm done.  I didn't really want to install a bunch of extra stuff on my old desktop though.

So is it a bad idea?  Mainly I'm just worried if there is some serious security issue that would compromise my network more than just regular hosting.

Also, along that line, anyone have good tutorials they'd be willing to point me to for making sure you have a super secure webserver?

Thanks all.  Its been fun learning apache and the associated stuff.  But pretty complicated also.

---

### Post by YesWeCan on 2010-08-05
I've just discovered Virtual Box and it is pretty impressive. I would try it just for the experience if nothing else. I suspect using VB for a LAMP is unecessary but has some advantages: VB makes a single image file for your guest OS's virtual hard disk and so it is very easy to back it up, restore it and delete all traces of it. The instant restore is particularly useful.

From what I understand, VB creates a virtual router between the guest OS and the host. So this virtual router can be your firewall and you can configure it for port forwarding. The VB manual is quite good: [http://www.virtualbox.org/wiki/Documentation](http://www.virtualbox.org/wiki/Documentation)

Be aware of some guest limitations. You may not be able to use a 64-bit OS as a guest. I am hosting Win7 32-bit on Ubuntu 10.04 64-bit and I have some serious problems with USB support - crashes. I have not tried hosting Ubuntu on Ubuntu. Aside from USB and not being able to get sound from an audio CD my Win7 virtual machine is awesome.

---

### Post by lukeiamyourfather on 2010-08-05
I would not recommend this. Not because of VirtualBox (because VirtualBox is awesome!) but because most or all consumer internet service providers prohibit hosting servers on their connection. If a server is compromised then anything that it does with your connection you're liable for.

Hosting providers like Go Daddy and others rent dedicated and virtual dedicated servers which would be a good way to get some experience with hosting sites on Linux without as much liability and sneaking around.

Alternatively use VirtualBox and run the server just local to experiment with. If you use VirtualBox you'll need to forward the HTTP port to the guest (or use bridged networking). More information about guest networking is in their documentation.

[http://www.virtualbox.org/manual/ch06.html#natforward](http://www.virtualbox.org/manual/ch06.html#natforward)

Good luck with whatever server route you take. :popcorn:

---

### Post by NertSkull on 2010-08-05
Where are you getting your information on ISP's blocking webservers?  I've actually read the acceptable use policies on many of the major ISP's and the only rules that relate to webserver are the non-profit ones.  You are not allowed to host a website as part of a business for money endeavor (unless, of course, you sign up for the business class accounts).

As far as the compromised server, well thats a concern with anything you do on the internet.  If I let anyone control my computer, whatever they do on it I could be liable for.  

Which, brings me back to the initial question, is there something less safe doing it through the virtualbox route vs just a dedicated machine.

In the end, I suspect I'll tinker with this for a month or two, wipe off my virtual box and be done - I get bored easily :)   But it from what I read I can't find anything more or less security problematic through a virtual box than the normal problems associated with a server on a dedicated machine.

Thanks all for the input.  I did try doing it just locally for now.  And it works pretty well.

---

### Post by lukeiamyourfather on 2010-08-05
> **NertSkull said:**
> 
Which, brings me back to the initial question, is there something less safe doing it through the virtualbox route vs just a dedicated machine.

No, a virtual machine is equally secure if setup properly (close unnecessary ports, security fixes up to date, confirm and edit all default configurations, etc.).

The reason I say hosting your own server is a liability is because you have to open ports on your firewall and expose the system to the internet. There are many bots and tools which can scan IP ranges for servers with unpatched or zero-day vulnerabilities and then exploit them. If running a desktop behind a firewall you wouldn't have the same issues because the firewall would block the incoming requests rather than forwarding them to the server.

If using a third party hosting service, they will take care of most of the security patches and vulnerabilities for you. Or if they don't its their butt on the line not your's for whatever the compromised system gets used for. Sometimes it doesn't matter if a system gets compromised, other times it does like when the system gets used for mirroring child pornography. Honestly judge, its not mine! The provider is protected by law in most places, but the end user is ultimately responsible for what happens on that connection. 

Its not a guarantee you'll have issues but be aware of the possibility. I've seen servers go online and within 24 hours have issues or become completely compromised (strangers with root access) because they were either configured improperly or not up to date. I guess just make sure you've done your homework first. ;)

Terms about hosting servers on a connection varies between providers, but most I've had prohibit hosting file severs and websites on the connection. Unless of course its a business connection like a T1 meant for hosting with equal up and down. You might be lucky and have a provider with flexible terms regarding hosting a server on the connection, in which case I'm a little jealous! Again, good luck with whatever you decide to do with a server.

---

### Post by NertSkull on 2010-08-06
Sounds good, thanks for the advice.  I think I'll look around at some of those companies and see what it would cost me to go with one of them.  Hopefully one that doesn't require a year long contract so I can get rid of it. 

Thanks again.

---

