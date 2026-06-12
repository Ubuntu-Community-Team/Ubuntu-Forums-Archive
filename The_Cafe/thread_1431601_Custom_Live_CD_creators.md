---
title: "Custom Live CD creators"
date: 2010-03-16
forum: The Cafe
---

### Post by PacSci on 2010-03-16
Recently, I made a Fedora spin for my dad so he wouldn't have to borrow my Live CDs when he needed to check why someone's computer isn't working. I wanted to make him an Xubuntu-based CD, since he's been using it for about half a year and is quite comfortable with it, but I didn't really like any of the options for creating Ubuntu-based Live CDs.

In Fedora, the primary method for creating Live CDs is with livecd-creator - you create a Kickstart file for your Live CD (the spin-kickstarts package contains the kickstarts that are used to make the official discs, I took fedora-livecd-xfce.ks and edited that), and then just run 'livecd-creator -c your-kickstart-file' and BAM! After about an hour, a nice fresh ISO! And if you don't want to edit the Kickstart manually, you can use system-config-kickstart or Revisor.

On the other hand, as far as I can tell, my options in Ubuntu are:

[LIST]
[*] Building it manually, which is time-consuming and complicated
[*] Creating it with UCK, which is easy, but you can't choose the name of the ISO or the directory it's created in, and you can't save the profile and rebuild it later
[*] Creating it with Reconstructor 2, which is stock-Ubuntu-centric, I don't think it works with Karmic, and you can't see what packages **are** on the disc in the first place so you can remove them.
[*] Creating it with Reconstructor 3, which requires you to do it on the Web, makes you wait for them to build it or download the engine manually yourself, and has some of the problems of 2.
[*] Creating it with Remastersys, which appears to be limited to making a copy of your current system.
[/LIST]

I was actually considering Slax, but the only supported environment appears to be KDE and it's got kind of an old release. Still, I like the approach it takes of selecting "modules" like Slax Core, Slax X11, Slax KDE, Slax Apps, and Firefox, and having them built onto a CD for you. The actual architecture (i.e. the Linux-Live scripts and the LZM module system) probably wouldn't work for Ubuntu, but being able to go onto a Live CD editor and selecting "Ubuntu Core", "X11 Common", "XFCE Core", "XFCE Applications", "Abiword", "Gnumeric", "Firefox", and "GNOME Games" modules would be pretty cool for Ubuntu.

Anyway, this has been a long, rambling post, but the gist of it is this: Does anyone know of a better way to make a Live CD? And if not, how can we make one?

---

### Post by lisati on 2010-03-16
One option to look into might be [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by Kenny_Strawn on 2010-03-16
Try Ubuntu Customization Kit, which is in the repos... Just search for it in the Software Center.

---

### Post by PacSci on 2010-03-16
Thanks for the recommendations, guys, but the reason I made the post is because none of the existing options that I knew about were working for me. (I have actually used UCK and Reconstructor 2 before, but not Remastersys.)

---

### Post by perspectoff on 2010-05-25
> **PacSci said:**
> Thanks for the recommendations, guys, but the reason I made the post is because none of the existing options that I knew about were working for me. (I have actually used UCK and Reconstructor 2 before, but not Remastersys.)

Remastersys works well for me for simple systems. If you have a complex system, make sure you install it to a USB flashdrive with persistence, not a CD. 

Remastersys runs everything in your OS (it does not have the capability to be selective) and since everything must run in RAM, if you have a lot of computing requirements, it can't handle this using a LiveCD. Thus the advice for a USB drive (where a swap partition can exist).

---

### Post by MC_Sketch on 2010-05-25
i used Slax and Nimblex and they both worked very well, so you might wanna check them out :)

---

