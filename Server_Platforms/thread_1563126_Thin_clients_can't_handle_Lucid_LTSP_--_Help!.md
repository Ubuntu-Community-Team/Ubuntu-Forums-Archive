---
title: "Thin clients can't handle Lucid LTSP -- Help!"
date: 2010-08-28
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-08-28
Well, as doubtful I am of anyone being able to help me with this, I at least want to share this experience; maybe someone with more knowledge can share some advice.

I had an LTSP 4.1 system.  The server was an old workstation.  There are about 15 clients.  All they do is serve up an web-based library catalog search in Firefox for library patrons.

The "server" hardware was dying, and the OS was dapper drake, so I recommended they buy a good server with a warranty and I'd rebuild the system on Lucid (the idea being that it would be able to last until at least 2015).

All seemed well on the workbench; the thin clients seemed slow but usable.  Then I deployed it.

The results have been frustrating and disastrous.  The thin clients are slow, the keyboard sometimes takes 4-5 seconds to respond and using any kind of HTML control (drop-down, check box, text input) is extremely slow and painful.  Patrons just don't want to use them, and the staff is getting frustrated.

My thin clients are Affirmative Yesstations, various 22xx models.  They have 200 MHz processors, 64 MB of RAM, and SiS video using shared RAM.  Sure, low-spec, but they ran the old system fine.  What's more, I'm stuck with them for at least another year.

So here's what I've tried to fix the delays:
 - LDM_DIRECTX: well, they won't even boot without this.
 - Upgrading RAM to 256 MB.  Sped up boot-times, but didn't fix the responsiveness issue.
 - Multiple browsers -- firefox, opera, my own custom webkit browser, netsurf, maybe a few others.
 - Running firefox 2 from Hardy.  Fixed my problem on the test system, but not in the real system.  Not sure why yet.
 - Network compression, no network compression.  No difference.
 - Jettisoning all the baggage from the chroot image that I didn't need: pulseaudio, alsa, cups, etc.
 - Shutting off as much as I could through lts.conf
 - lowering the screen resolution and color depth.  At first I thought this worked, but after further testing it seems I was mistaken.

I probably tried a few more things.  I keep hoping there's some hidden setting that will magically fix it all, but I haven't found it yet.  

Anyone have any advice?

---

### Post by lykwydchykyn on 2010-08-29
bump...

---

### Post by scorp123 on 2010-08-29
Try a different distro maybe? Debian may have less eye-candy but then again it enjoys an excellent reputation for being a reliable server OS.
[http://wiki.debian.org/LTSP/Howto](http://wiki.debian.org/LTSP/Howto)

Or try a different product altogether?
[http://www.ulteo.com](http://www.ulteo.com)

Ulteo is open source too. And you can set it to deliver single applications (in Sun Ray lingo we'd call that a "kiosk application") to those remote screens ... 

If this had been a project my employer had tasked me with, then I'd have used Sun/Oracle Sun Ray Software and Sun Ray ultra-thin clients. It works tip top for such purposes ... but that stuff ain't free and it's closed source. So I suppose that using commercial solutions like this one is not possible for you?

---

### Post by lykwydchykyn on 2010-08-30
> **scorp123 said:**
> Try a different distro maybe? Debian may have less eye-candy but then again it enjoys an excellent reputation for being a reliable server OS.
[http://wiki.debian.org/LTSP/Howto](http://wiki.debian.org/LTSP/Howto)

I was going to try debian on the test server at work; I normally use debian on the server, but I was hoping to set up something that could run and be supported for at least 3 years.  Squeeze is due out later this year, and lenny would be out 12 months later.
> 
Or try a different product altogether?
[http://www.ulteo.com](http://www.ulteo.com)

Ulteo is open source too. And you can set it to deliver single applications (in Sun Ray lingo we'd call that a "kiosk application") to those remote screens ... 

I'm not sure what Ulteo gets me here.  All I need is to deliver a browser with a web page.  Would it be less demanding on the remote processor?  All I'm delivering now is the NBD volume and the X11 data.

> 
If this had been a project my employer had tasked me with, then I'd have used Sun/Oracle Sun Ray Software and Sun Ray ultra-thin clients. It works tip top for such purposes ... but that stuff ain't free and it's closed source. So I suppose that using commercial solutions like this one is not possible for you?
Well, if there were money to be spent I'd just have them replace the thin clients and be done with it.  From all the testing I've done, processor speed of the thin clients is the root of the problem.  

I wonder if I can build the client image with Debian and have it talk to the Ubuntu LTS server.  For some reason when I tried Debian initially the client image is 220 MB, whereas Ubuntu's is around 600 MB.  

I *REALLY* don't want to have to slick the server and start over at this point, but if nothing else works, I guess I may have to.

---

### Post by lykwydchykyn on 2010-08-30
Well, after a full day of experimentation, I had an epiphany.  Literally: I switched to epiphany.

I think I tried about every browser I could think of.  Well, at least the ones that made pretenses of being lightweight.

It still runs slowly, and I can't customize the interface as much as I'd like,  but it's "good enough for government work", which is good because, well, we're in government.

Still hunting for more ways to optimize this thing.

---

### Post by uberlinuxnerd on 2010-08-31
I'd be interested to see what your ping responses are when its lagging, I would put my finger on that bandwidth is your problem

---

### Post by lykwydchykyn on 2010-08-31
Ping responses are all pretty much under half a millisecond.  Bandwidth isn't the problem; the server has four NICs, so I bonded the extra two together and routed all the NBD swap traffic to the bonded IP.  

When I hook a "real" computer up (even an old 500MHz laptop) it runs just fine, so I'm pretty sure processor is the culprit.  I guess it could be that the NIC on the thinclient is having a bottleneck, but either way it amounts to the thinclient being too thin.

---

### Post by theller on 2010-09-01
I am using jaunty jack and I have one desktop running 30 thin clients with 260 users the only time I notice it's running slow is when we try to use google earth. I am using no machine nx on the thin clients. I am amazed at how good it works. I tried updating and I could not even get Lucid to even connect to the thin clients.

---

### Post by lykwydchykyn on 2010-09-01
What are the specs on your clients?

---

