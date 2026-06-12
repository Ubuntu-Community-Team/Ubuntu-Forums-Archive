---
title: "driver support"
date: 2009-04-09
forum: System76 Support
---

### Post by eyecreate on 2009-04-09
I wanted to know, if I decide to change my distro to something else besides Ubuntu, will the system76 driver still supply anything useful? Also, what things could it possible still provide?

---

### Post by Lee_Machine on 2009-04-10
I asked the same question a while ago and the answer was the S76 driver is built to run for Ubuntu, but that it should work on distros based on Ubuntu such as Linux Mint. The new one just came out too :)


I have not tried that though. 

What distro? Plus what S76 computer do you have?

The best thing to do is to used gparted and set aside 10GBs and install it on that.

---

### Post by eyecreate on 2009-04-10
I wanted to run a KDE based distro without problems, but I couldn't get Kubuntu to be as good as Chakra project(so far) but it's is based on arch. I almost tried what you said, I booted off a USB drive to test and it seems most things works fine(except touchpad scrolling). I'd use Kubuntu if it worked better on my serp4 and if some packages weren't broken.(aka, the button to set up plasmoids on screensaver lock doesn't do anything in Kubuntu sadly, when it should.) I guess I just want to play with a nice working copy of KDE4, and another non-Ubuntu distro piqued my interest.(I might try Mandriva too) If it's too complicated, I'd just stay with Ubuntu.

---

### Post by Lee_Machine on 2009-04-10
I say you wait for Kubuntu 9.04, it has KDE 4.2, among many other  KDE improvements.

If you just want to install and mess around with Distros then run them virtually with Virtualbox OSE.

If you need help with that let me know, right now I am using VB OSE to mess around with Slackware, and Backtrack3.

Plus I run WindowsXP SP3 for homework reasons.

---

### Post by eyecreate on 2009-04-10
I do already run VirtualBox on my laptop to test machines out and it has been how I've tested some of my options. I guess to make it fair I'll wait till Kubuntu 9.04 is officially released, but it was the beta that I was talking about when I was looking at Kubuntu. I even had made a backup my hard drive a week ago and had erased my drive and put Kubuntu on only to have it die when I tried upgraing packages.(let alone the other problems I mentioned) Kubuntu has alot to fix before it becomes "smooth" on my laptop, so I'm kinda skeptic about how "ready" it'll be at release. idk, maybe I'm just judging it too hard, as I used to use Kubuntu over Ubuntu back in it's 7.04 days. I wish making decisions were alot easier.

---

### Post by Lee_Machine on 2009-04-12
I went ahead and installed Kubuntu 9.04 beta on my Pangoline and all seemed well until I updated the software. It broke many things (as you mentioned it did in your post)

I didn't catch on to what you were saying. Not sure how familiar you are with running ubuntu in text mode, dpkg will fix most things. 

So run 

dpkg --configure -a

That will fix any dependencies it can and then spit out which ones need to be reinstalled. For me it was kubuntu-window-manager

After that and a few more updates, plus installing the nvidia driver it ran pretty smoothly.  

I tried KDE 4.2 when it first came out and my feelings are the same now. It's WAY better that when 4.0 cam out, but no where as good a GNOME. 

That is pretty much an opinion. I know there are some more "advanced" features in KDE, but for me navigation just seems off...I wont start yet another KDE vs GNOME thread :lolflag:

Anyways I was running Kubuntu 9.04 32bit beta, and I couldn't find anything that didn't work. (hardware wise)

---

