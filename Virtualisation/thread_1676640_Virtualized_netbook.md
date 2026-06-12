---
title: "Virtualized netbook"
date: 2011-01-27
forum: Virtualisation
---

### Post by Chareos on 2011-01-27
Hi guys,

today a strange idea took me.
I'm an accustomed linux user, driven by simple passion.

Actually I'm sick, SICK of my slow netbook. But no butget / real need for a full powered laptop, so...

I asked myself
*Is there a way to put an Ubuntu installation in an istance, running from a good-powered desktop, and have my laptop merely bootup to it via home network ?*

Would it be... faster than remote desktop control ? (also consider that my desktop has to stay available for other use, so a simple remote desktop solution would not be good)


If so, anyone knows a good text on the web to start from ?
I'm not even sure about tech terms at this point, so my googling is quite uneffective.


Thanks a lot for any hint !!

---

### Post by gordintoronto on 2011-01-27
If you don't want to use remote desktop, that means the programs will actually run on your slow, slow netbook. Booting from the other computer won't be an advantage.

---

### Post by mazato on 2011-01-27
Chareos, I don know if this might really help you on the direction you want to go, but it might give ideas on what you can do.

My setup:
I have a 600 Mhz Thinkpad X20, 320 RAM, about 20 GB HD with a wireless card and I have Lubuntu installed in it!. In case you don't know, Lubuntu is based on Ubuntu but runs on LXDE (LXDE is a much, much lighter desktop enviroment than GNOME).
A 3.00 Ghz desktop with 2 gigs on RAM running Ubuntu 10.04.
These hosts are connected to the same LAN.

As you, I got tired of my slow old laptop, but found a workaround to recycle my trusty and oldie Thinkpad X20.

I installed NX ([http://www.nomachine.com/](http://www.nomachine.com/)) on my Ubuntu desktop and enabled WakeOnLan in the Bios (you can google this for HowTos).
Then I installed the NX client on my laptop. 
Now I can log on to my desktop using NX (after waking it up and automatic login) and I can also go to the desktop and run another session while still running the other NX session.You can even terminate your NX session or save it. This is a poor man's solution that really worked for me, so it might for you too.

take care!

---

### Post by Chareos on 2011-01-27
Thanks both :-)

@Mazato: sounds like my scenario !
How NX feels ? Is it smoother - more similar to a local machine - than the average vnc client ?

If the nVidia closed (sic) driver allows it, a double session on desktop may be a very quick solution...

---

### Post by mazato on 2011-01-27
Chareos, for me it is a great advantage running NX on my laptop because of the heavy apps that I want to run in it, but run too slow. When running cpu intensive apps, it feels much better than VNC, try it first so you can really feel it for yourself and decide upon this. What really made me use this solution, was the fact that i can run another session at the same time on the same desktop and save them too.!
good luck!

---

### Post by SlugSlug on 2011-01-28
If your laptop supports Network boot (PXE) then LTSP would be a place to good start.

Run LTSP on your desktop & you could boot your laptop from pxe so it will use Desktops resources..

---

### Post by HermanAB on 2011-01-29
Howdy,

You should re-install your netbook with Xubuntu, Lubuntu or Puppy.

---

