---
title: "Anyone get Haiku up and running? Have any Screenshots?"
date: 2009-09-27
forum: The Cafe
---

### Post by HappinessNow on 2009-09-27
Anyone get Haiku up and running? Have any Screenshots?

If you got it up, what are your thoughts?

---

### Post by BackwardsDown on 2009-09-28
I think its amazing! Installed it on my laptop a few days ago. After hours of browsing in firefox2.0 it hasn't crashed a single time. The ui is prettey intuitive, and it is very clever designed.

Give it a try in Virtualbox! Do select the Intel Pro/1000 MT Desktop (NAT) as Network device or else it won't connect trough the internet.

For screenshots you can check here:
[http://www.haiku-os.org/slideshows/haiku-tour](http://www.haiku-os.org/slideshows/haiku-tour)

I'm currently learning the Haiku API to write apps for Haiku myself, its pretty easy :P

---

### Post by Ichtyandr on 2009-09-28
I am also interested in probing Haiku. 
Do I have to get the latest virtualbox (have one from Jaunty universe)?
Also is it important which OS type in the virtualbox you put, was it "Other OS" eg?
thanks

---

### Post by BackwardsDown on 2009-09-28
Yes, the one from Jaunty is good. Its the opensource version though, so USB won't work. (not that many USB-devices are supported in haiku :))

And selecting other-os is fine. When it asks you to create a new harddisk for Haiku, don't, select the one provided on the site:
[http://www.haiku-os.org/get-haiku](http://www.haiku-os.org/get-haiku) (The VM-version).

---

### Post by Firestem4 on 2009-09-28
I used their prepackaged VMWare edition in VirtualBox. It runs great. I havne't had a chance to get it connected to the internet yet but I find its speed and stability quite astounding. I'll definitely be paying attention to this project in the future and see what comes of it.

---

### Post by Ichtyandr on 2009-09-28
Thanks people, 
I'll definitely give it a shot. 
its got a funky name!

---

### Post by chriskin on 2009-09-28
> **BackwardsDown said:**
> [COLOR="Red"]After hours of browsing in [COLOR="DarkOrange"]firefox2.0[/COLOR] it hasn't crashed a single time.[/COLOR]

!!
is firefox 2 still around? and why is it a miracle that it hasn't crashed? it wouldn't crash on linux, or windows , either, would it?

---

### Post by Firestem4 on 2009-09-28
> **Ichtyandr said:**
> Thanks people, 
I'll definitely give it a shot. 
its got a funky name!

I think its quite symbolic, as I am sure the developers thought so too. but also no less funky than naming a distro after a weird hat (Fedora)lol =)

---

### Post by BeRReGoN on 2009-09-28
The name comes from NetPositive (the BeOS browser) and is haiku error messages.

If you want to read some of them:
[http://8325.org/haiku/](http://8325.org/haiku/)

On my sony vaio laptop Haiku is running fine, only the wifi since ipw2200 is not supported yet by the new wifi stack (only atheros yet is supported) but more will be supported soon. I bough an old p3 to put haiku on it. It's working fine too but the cdrom doesn't work fine, some ata problems but i didn't test with the new sources, only with the alpha1.

---

### Post by Firestem4 on 2009-09-28
> **BeRReGoN said:**
> The name comes from NetPositive (the BeOS browser) and is haiku error messages.

If you want to read some of them:
[http://8325.org/haiku/](http://8325.org/haiku/)

:lolflag:Thats awesome. I love developers with a sense of humor =)

---

### Post by Skripka on 2009-09-28
> **chriskin said:**
> !!
is firefox 2 still around? and why is it a miracle that it hasn't crashed? it wouldn't crash on linux, or windows , either, would it?

Maybe because folks are USED to an "Alpha" OS meaning:

[quote=]
No warranties, either express or implied, are hereby given for anything provided by the ____________ ("Software"). All software is supplied as is, without any guarantee. The user assumes all responsibility for damages resulting from the use of the software, including, but not limited to, frustration, disgust, system abends, disk head-crashes, general malfeasance, floods, fires, shark attack, locust infestation, cyclones, hurricanes, tsunamis, local electromagnetic disruptions, hydraulic brake system failure, invasion, hashing collisions, normal wear and tear of friction surfaces, cosmic radiation, inadvertent destruction of sensitive electronic components, windstorms, the riders of nazgul, infuriated chickens, premature activation of a distant early warning system, peasant uprisings, halitosis, artillery bombardment, explosions, cave-ins, borg-assimilation, america bringing democracy to your country and/or frogs falling from the sky.
[/quote]

---

### Post by chriskin on 2009-09-29
> **Skripka said:**
> Maybe because folks are USED to an "Alpha" OS meaning:

i use alpha versions of ubuntu since 7.04, none has caused any serious problem to the whole experience

---

### Post by moster on 2009-09-29
> **chriskin said:**
> i use alpha versions of ubuntu since 7.04, none has caused any serious problem to the whole experience

Ubuntu alpha and haiku is different alpha.

That Ubuntu alpha is not from ground up but everything upgraded from previous versions. Same thing is with windows. they do not invent something from begining.

Haiku is well, from ground up filesystem, kernel, everything. It will certainly pass whole year to become beta.

---

### Post by chriskin on 2009-09-29
> **moster said:**
> Ubuntu alpha and haiku is different alpha.

That Ubuntu alpha is not from ground up but everything upgraded from previous versions. Same thing is with windows. they do not invent something from begining.

Haiku is well, from ground up filesystem, kernel, everything. It will certainly pass whole year to become beta.

good point :)

---

### Post by free10 on 2009-10-01
> **BackwardsDown said:**
> I think its amazing! Installed it on my laptop a few days ago. After hours of browsing in firefox2.0 it hasn't crashed a single time. The ui is prettey intuitive, and it is very clever designed.

Give it a try in Virtualbox! Do select the Intel Pro/1000 MT Desktop (NAT) as Network device or else it won't connect trough the internet.

For screenshots you can check here:
[http://www.haiku-os.org/slideshows/haiku-tour](http://www.haiku-os.org/slideshows/haiku-tour)

I'm currently learning the Haiku API to write apps for Haiku myself, its pretty easy :P

I ran almost exclusively BeOS 5 Pro from about 1999 to 2006 and it was almost totally stable and I virtually never shutdown except when a thunderstorm knocked out power. My rig during those years was an abit board and Celeron 2 566mhz overclocked to around one gig with 128-512mb of ram and an 8mb-64mb of video cards plus a 10gig-80 gig Western digital hard drive and it was much faster than other peoples computers in operations (close to real time) and totally more stable.

Now to get people to understand this I did install Ubuntu 6.04 on a second drive in it and it was so so so slow at everything in comparison to the 90s BeOS but a lot nicer than other Linux distros I had tried over the years.

I decided to upgrade my hardware in the middle of last year but I knew the drivers for BeOS were not their but also knew Haiku was soon be out and bought an F1 Samsung terabyte  sata 2 drive, a Q6000 Intel quad CPU, Gigabyte GA-EP35-DS3P mother board and 4 gigs of OZ DD2 ram plus a GT7600 video card with 256 of ram and now running 9.04, and it still is not near as fast as BeOS on my old hardware setup or easy to use but the new hardware did help its speed a lot. When alpha Haiku came out I burned it onto a CD-R and doing nothing more than rebooting off the live CD I was amazed it booted and worked. Got some kind of problem off the network chip set on connecting though, but I could use another older network card and cure that I would imagine. Now off a super slow CD live ISO it still was much faster than 9.04 though I did crash it twice playing with it LOL It may have been the CD is not meant to work that fast but then again it is alpha  LOL 

The first crash was using the Teapot demo just for fun and I had Pulse running too and showing all 4 of my cpus. Well Teapot with all effects on was hitting 2200 FPS (amazing) but maxing out only one CPU with little usage seen on the other 3, and that sure was not right. On anything else the CPU usage is all well balanced that I have tried with it. BeOS required two threads per app and recommended 8.

There is a lot of drag and drop in the system not seen in other systems and a number of somewhat hidden very cool features to some of the apps. Like in video player there is simple drag and drop for taking frames out of a video and creating a choice of image types of it. In sound recorder you can do some pretty wild stuff real easily.

On the browser end BeOS had a number of browsers like Opera 3 something and a number of Mozilla/Firefox versions including Sea Monkey. They are working on much more native and advanced browsers right now and if say Firefox 3.5 is so hot then you might see a version of it within a few months of it coming out for other systems. It just depends.

This should be a lot more fun than BeOS was. Ubuntu and other systems should pick up a lot of speed too in future years as using SSD drives in groups or raid systems become cheaper. Even windoz can be fast with enough SSDs and CPUs and having a tech set it up LOL

[http://www.youtube.com/watch?v=96dWOEa4Djs](http://www.youtube.com/watch?v=96dWOEa4Djs)

---

