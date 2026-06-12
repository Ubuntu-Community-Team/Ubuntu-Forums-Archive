---
title: "Wooh Mama!"
date: 2007-01-27
forum: Testimonials &amp; Experiences
---

### Post by laredo7mm on 2007-01-27
Hey all, first of all I have to say; Fantastic Distro!

I have been using Linux for a bit now, about 6 months.  I dropped the dual boot with Microsoft last September.  

I have been primarily using SuSe in various forms.  Either SLED 10, OpenSuSe 10.0, OpenSuse 10.1, and OpenSuSe 10.2.  All with KDE as my desktop environment.  For some reason, I could never quite get used to Gnome.

Recently, I decided to build a new box, and upgrade from my Socket A AMD, to an AM2 dual core with DDR2 ram, so I also decided it might be time to try out some different distros.  I had tried to dual boot with SuSe and Kubuntu in the past, but I had problems with the file system since I was using ReiserFS in SuSe and Kunbutu was ext3.  But since SuSe 10.2 has abandoned ReiserFS and defaulted to ext3, I did a fresh install of 10.2 from 10.1, so naturally that jogged my memory of Kubuntu using ext3....Might be time to try Kubuntu again.

Now, even though I am an Engineer, and all I want is data, data, data..., I like my "stuff" to look pretty.  So Gnome was never very appealing to me.  But, and a very but BUT, after installing Kunbuntu and using it for a few days I saw no major improvement over SuSe 10.2 with KDE, with the exception of the package manager and the "light" install (no more 3+ GB install).  WOW!!, I was sold on Ubuntu at that point!  I have never liked YAST as a package manager, so while running my various SuSe distros, I primarily used SMART as my package manager.  YAST is just way to slow.  Not to mention the first thing I did in SuSe 10.2 was disable ZMD, RUG, and YOU.

But, still being a novice Linux user, I managed to screw up my Boot Loader when I was trying to make it look pretty after installing Kunbuntu.  I went back and forth with YAST trying to rewrite my MBR.  Either I could get the Boot Screen to look pretty and have SuSe be the only option available, or it would look "ugly" and only Kunbutu was available.  So, once I got it back to pretty and SuSe, I decided the only way to get both back was to reinstall Kunbuntu.

Then, of course, with my over analytical Engineering brain, I worked Gnome into the equation (based on a bunch of ribbing I got from the guys at work bad mouthing KDE when I first started running Linux).  Now don't get me wrong, I love my KDE, but I was under the impression that my favorite programs that I run were only available in KDE.  Programs such as K3B and Klibido.  But contrary to my paradigms, I downloaded the Ubuntu 6.10 DVD Live "CD" to try it out.  To my surprise, I found both K3B and Klibido in the repositories when I was browsing Synaptic.  PLUS, Par2 and Unrar were readily available packages, not typically easy to find for SuSe 10.2, not to mention FFMPEG being broke for me in SuSe 10.2, but all is good in Ubuntu 6.10.

Anyway, I have abandoned SuSE, and accepted Ubuntu with the Gnome Environment.  I don't know what it is, but this is the first time I have used Gnome and it looks great!  Pretty enough for me, plus it seems to be faster (I don't mean to start any debates).  In a few days I will have all my parts in so I can build my dual core AMD Box, I can't wait to install the AMD64 version after seeing how well the i386 version is performing.

Plus, the computer I am typing on now (the Socket A) dual booted with SuSe 10.2 and Ubuntu 6.10 is going to be my 9 year old Daughter's computer.  Might as well start them on Linux young!

Anyway, great distro, I am loving it.

---

### Post by bward1 on 2007-01-28
I have always wondered why Kubuntu and ubuntu and the like are distributed seperately.  It leads to the common misconception that you can only have one.  This coupled with the fact that in windows you don't get a choice at all, and people think just that, they dont have a choice.  If you like kde but want to learn about gnome, then go ahead and install both of them.  When you go to login, there will be a session button somewhere and you click on that and choose your session.  You should be able to do this: ```
sudo apt-get install kde
``` and that should install all of the other packages that kde needs.  If you want you can also go into synaptic and and select other packages relating to kde as well.  KDE and Gnome aren't your only options though, some people like XFCE, fluxbox, fvvw, or enlightenment (all of which can be install through synaptic, or by running apt-get install).  Each of these has it's different advantages and disadvantages so it is really just a matter or personal preference.  Have fun with ubuntu!

---

### Post by seijuro on 2007-01-28
I think the biggest reason to have KDE as a seperate distro is for the KDE users who do not want GNOME installed. Speaking from my own persective I only have 2 gnome applications installed in my Kubuntu system and I would much rather have just a couple gtk librares required to run the apps installed than all of GNOME.

---

### Post by TheMono on 2007-01-30
If you're using par2, have a look into pypar2, a little python script to use par2 in GUI. Nice and easy.

There is a package for it floating round somewhere for Edgy...

---

### Post by laredo7mm on 2007-02-02
> **TheMono said:**
> If you're using par2, have a look into pypar2, a little python script to use par2 in GUI. Nice and easy.

There is a package for it floating round somewhere for Edgy...

Sweet, I will have to look for that.  Do they make a similar script for unrar?

I have my new box up and running the X64 version of Ubuntu 6.10.  It is rolling along very well, I am going to install my Quadro FX 1300 video card tonight.

All is still good on the Ubuntu front.

---

### Post by laredo7mm on 2007-02-14
Still lovin' it.  I just updateded to Fiesty Fawn Herd 3 last night, all went well.  I used the update manager process and then synatic to install the low latency kernel.

The only hick-up I had was broken X upon reboot.  But that was expected due to running the Nvidia binary driver for my Quadro FX1300 pcie card.  No big deal, just a quick edit of xorg.conf to get up and running with out 3D, just to check things out, then I reinstalled my Nvidia drivers.

7.04 seems faster than 6.10 even before the low latency kernel, now it really moves with the low latency kernel. 

The biggest benefit for me was the update to the 2.6.20 kernel.  Now I can have my K8temp module reporting my core temps through GKrellm.  Very nice indeed.  Especially since my endevours into compiling my own custom kernel had limited success. 

Anyway, another big thumbs up for Ubuntu!

---

### Post by jvc26 on 2007-02-15
Im still running happily on edgy at the moment (though on a personally compiled 2.6.20 kernel) seems to have a fair bit more speed than it used to, though I have never had a problem with Ubuntu's speed, it always seems to run briskly.
Il

---

