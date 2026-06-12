---
title: "LTSP - Is this even possible?"
date: 2007-05-30
forum: Server Platforms
---

### Post by Yakboy on 2007-05-30
A large part of my day job is Citrix running on Server 2003 as such I'm familiar with that sort of Terminal Services  but I was wondering if the following is possible:

-I'd like a Terminal Server to serve Firefox as something resembling a Published Application as they are on M$ TS with Citrix tech.

-I'd like a web front end to this so I can access from anywhere in the world, and pref using 443.

-I'd like any required client to work under Windows and have a zero footprint install.

Is this possible using LTSP under Ubuntu? I am happy to start trying to put this together but I'd like to know that it is possible before getting cracking. So far as I can tell LTSP is geared fairly specfically towards offering a complete desktop (full screen) to clients sat on the same LAN. Tell me I'm wrong and give me a good reason to push to make this possible!!

Thanks in advance.

---

### Post by craigp84 on 2007-05-31
I'll add to this list.

I'd like a ferrari, and a couple of pairs of those trainers with the wheels in.

I really fancy a smart watch with a *brown* leather strap, to go with my new jacket (it's cracking).

Yakboy,

What you're looking for is "Citrix running on Server 2003", not LTSP, ubuntu or any other linux technology.

If you're able to take some of the preconceived solutions out of the problem description, you have quite a lot of options, LTSP, NX, VNC, X11 forwarding yada yada but none of them are citrix on server 2003 - they will function differently and will require a suitably different approach.

Might be worth phoning your local Linux consultant and having a chat too.

But i suspect what you're needing is Citrix on Server 2003, so go phone Citrix & Microsoft for a quote.

-c

---

### Post by bmathis on 2007-05-31
If you use NX, you can setup the connection client to automatically run a program in kiosk mode, but no web interface as far as i know.

---

### Post by Alterax on 2007-06-29
You've got a couple of options, but they'll work differently depending on the circumstances.

You'll need to find a program that lets you run X11 programs in Windows on the client side and a way of establishing a link with ssh -X serverIPaddress.  Then you can run the application on the server, but have the display put on the client.

Another option would be to do something like web-based apps (on Tomcat's httpd server) or java applets.  Will take some work but I do think it can be done.

Possible to do these things?  With enough background, information, and work, I'd say yes.  Can I myself do it?  No, but if the need arises I am sure I could work up something.

--Alterax

---

