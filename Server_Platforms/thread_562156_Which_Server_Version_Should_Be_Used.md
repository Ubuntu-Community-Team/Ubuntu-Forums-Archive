---
title: "Which Server Version Should Be Used"
date: 2007-09-28
forum: Server Platforms
---

### Post by wxman on 2007-09-28
Hi

I know this has sort of been asked before, but I'm still confused.
I'm going to be setting up a server to host a few web sites. I have a new HP computer running a dual core 64 bit Pentium. I'm a bit confused which version of Ubuntu server to try on it, 6.06 or 7.04? I see people saying to use 6.06 all the time, but I still don't see the difference between the two?

Also, since I gave a 64 bit, should I get the 64 bit version? I know there were problems before with 32 bit apps not working on it.

 I do have the desktop version of 7.04 running on another computer here, and I love it. My kids agree it's better than Windows most of the time.

Thanks

---

### Post by Brazen on 2007-09-28
Use 6.06.  Canonical puts more work into making the LTS releases stable and reliable which is what you want for a server.  I always use 6.06 on servers, but I just use whatever is the latest version for my laptop.

Plus you don't want to have to go through a major version upgrade on your server every 6 months.  The LTS release are going to be about 2 or 3 years apart and Canonical has said it will be possible to upgrade from one LTS release directly to the next LTS release.  So in other words, you can go a lot longer without having to mess with your server, but still get security updates.

---

### Post by wxman on 2007-09-28
Thanks. That's kind of the impression I was getting.

Any opinion on the 64/32 bit version?

---

### Post by HermanAB on 2007-09-28
With a server, you won't have the usual hardware driver issues, so you can use the 64bit version.  

Note that the server edition is really meant for 'headless' operation and if the server is going to have a screen and keyboard attached to it, then you should rather install Xubuntu.

Cheers,

Herman

---

### Post by wxman on 2007-09-28
I haven't had a chance to do the install yet, but I gathered that there was no desktop. 
I think the way I need to run it, a "user friendly" desktop would be a help. I guess I could network the other desktop running Ubuntu, and use it, but I would rather use the server itself to work on.
I still install the server version don't I, then install the desktop, somehow, to do that?

---

### Post by wxman on 2007-09-28
I also just noticed that the downloads say 64 bit AMD. Will they not work on a dual core 64 bit pentium?

---

### Post by adamjs on 2007-09-28
Is there no desktop in the server version?

---

### Post by HermanAB on 2007-09-28
No desktop - a headless machine doesn't have anything to display it on...

Use Xubuntu if you are going to have a screen and keyboard.

---

### Post by Brazen on 2007-09-28
the 64 bit version will work fine on a 64-bit Pentium.  They just call it AMD64 because AMD came up with the specification and that is the name AMD gave it.  Intel just copied the spec and calls it a different name.

There is no desktop gui installed on the server version by default, but you can install it afterward.  Just do "sudo aptitude -y install ubuntu-desktop".  I would highly suggest that when you set up a production server that you do it without installing a gui desktop.  Try using Webmin instead.

---

### Post by wxman on 2007-09-28
I'll have to look up Webmin. I hadn't heard of that one before.

From what I read, there really is no big benefit to using the 64bit version. Some postings suggest that the 32bit one runs just as fast, and with fewer problems.

---

