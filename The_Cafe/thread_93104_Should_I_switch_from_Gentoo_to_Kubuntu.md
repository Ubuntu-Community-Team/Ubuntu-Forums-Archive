---
title: "Should I switch from Gentoo to Kubuntu?"
date: 2005-11-21
forum: The Cafe
---

### Post by fourhead on 2005-11-21
Hello,

I'm a long-year (2 or 3) and actually very happy Gentoo user (you've probably heart about it ;-)). I've heart a lot of rumors about (K)ubuntu lately and I already tried a LiveCD of it and installed it within a QEMU VM to test it - and I really like it. It's clean, fast, and it's just "sympathic" in some way. To sum it up, I'm seriously considering a switch to Kubuntu on my AMD64 desktop and on an iBook G4. As I've said I'm not new to Linux, but I'm new (absolutely new) to Debian, so I have a few questions ...

1. One thing I loved about Gentoo was that virtually any program you could ever think of was available by a simple "emerge foo". While testing Kubuntu I found out that many programs I'd like to install where not available in the "Adept" package manager. Is there a way to add more programs to this repository? Would those package then be "official" packages? I hate nothing more than to have to google after each single package I want to install, so a really big package database is very important to me.

2. If there's a new (K)ubuntu release, can I do a complete update online or do I have to download and re-install it from CD/DVD? What about new major package releases, say KDE 3.5, if this comes out, could I just run an update trough this Adept utility and I have KDE 3.5 or would I have to wait for a new major Kubuntu release to get KDE 3.5? (I'm asking because I'm already on KDE-3.5_rc1 here, and I wouldn't want to wait until 2006/04 for the next Kubuntu release)

3. How well does Kubuntu work on an iBook G4? My heavily-customized Gentoo works pretty well now, including suspend-to-disk, automatic display standby & harddisk standby after a certain time, depending on AC/battery etc. I wouldn't want to miss such features. Do the iBook special buttons work fine with Kubuntu? Can I put the iBook to sleep if I close the lid or press the power button?

4. How about kernel releases. Are new kernels only shipped with a new Kubuntu release, or will there be a new kernel from time to time. I'm asking because on Gentoo I've often seen enourmous improvements with new kernels, and it would be nice to not have to wait too long for a new kernel.

5. Is there anything you would say to a Gentoo user switching to Kubuntu? Any downfalls, any advantages, your own experience, would you recommend this switch or not? I have to say, I loved to really tweak every single aspect of my system, to have everything run like I want it, but on the other side, I'm getting older (26, uh), and I have work to do, and now I think I'd prefer a system that is leightweight, just runs and works, but that still allows me to do some tweaking IF I ever want it. Kubuntu seems to have a good balance between "just works", "tweakable" (thanks to Debian) and "leightweight" (I don't like SuSE because of this, but still it's a good distro if course, it's just not for me)

Well, that was it. I'd really appreciate any comments & tips & tricks from you, and you might welcome me as a new Kubuntu user! (If ex-Gentoo users are welcome ;-) )


Tom

---

### Post by fourhead on 2005-11-21
Hmm, a little addition. I just searched for some apps that I'm currently using on my desktop, and I can't find them in "Adept":

Codeine
EasyTag
Skype
LimeWire
digikam
showimg
QEMU
Tellico
rsnapshot
Gimp

Is a default Kubuntu 5.10 install missing something or do I have to add a repository to Adept? Or would I have to manually search & install those apps?


Tom

---

### Post by adwait on 2005-11-21
1)That's because a lot of programs are in the different repositories which are not enabled by default. Once you enable them (check my signature for how to do that), you will have all the programs available.
2)you can update online, you just have to change a file (/etc/apt/sources.list) and then run apt-get dist-upgrade. You are done!
3)no idea.....
4)Kernel updates are there from time to time, and also there's a separate bleeding edge version of the next release (Dapper) that you can install if you want very recent copies of softwares, including kernels.
5(no idea.......never used gentoo, but damn happy with kubuntu.

---

### Post by GeneralZod on 2005-11-21
1. The default repository for (K)Ubuntu is "main", and it contains a fairly comprehensive  range of software.  You will definitely want to add [other repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto), though.  I can't quite remember the policy on these, but I think they are "official" but not guaranteed to be supported by security updates etc.

2. You can do a "dist-upgrade" when the next version comes out; I won't explain the procedure here as there is always a flurry of HOWTO's whenever a new version comes out :)

3. Don't know about this; sorry!

4. Pretty much every app, library and kernel provided at release time is "frozen", and only security updates and major bug-fixes are provided.  If you want nice, up-to-date apps, it's probably best to stick with Gentoo.  The [backports](http://ubuntuforums.org/forumdisplay.php?f=47) project aims to provide for those that want more bleeding-edge stuff, but not every app is a candidate for backporting; in particular, kernels tend not to be backported.

5. I switched from Gentoo, and have mixed feelings - on the one hand, I like the great out-of-the-box experience you get with Kubuntu (after installing things like w32codecs, etc) and not having to compile everything, but miss the huge centralised repository of continually updated apps that you get with Gentoo.  Also, installing this like w32codecs is not as easy under (K)Ubuntu as it is under Gentoo.    I don't think you have the fine-grained control over things that get installed with (K)Ubuntu, either, but  this is unimportant to me as I generally tend to install everything but the kitchen sink, no matter which distro I use :).  On the whole, though, I'll probably stick with Kubuntu for the long haul.

Any further questions, just ask :)

---

### Post by kakashi on 2005-11-21
you can add the debain unstable repository to your /etc/sources.list. 
also search for your package here [http://www.apt-get.org/](http://www.apt-get.org/)
then add the repos to sources.list
then you'll have all the debian packages. wheter yopu should switch is based on what your priorities are. if you want a plethora of software availabe and a computer that always bleeding edge then use gentoo (nothing better) 
debain and ubuntu are for stability and ease of use. i have trashed my ubuntu installation about 20 times in less then 4 months. it takes around 45 mins to reinstall and since i maintain a local ubuntu repository it takes around 2 hours more to get my system perfect again.  and with programs like automatix its even easier. 
but gentoo is different. i installed it from stage 3 and it still took about a day to even get gnome running. i even tried to install it using the live cd installer (4 times) and something always went wrong and i screwed something up so i stick with ubuntu. it seems you are perfecly happy with gentoo so i think you should consider what you like about ubuntu and weigh it against gentoo. 

ubunut will offer.
1 . a clean fast system up and running in 45 min or less.
2. easy to use no fuss.
3. stability.

gentoo offers
1. larger (maybe larger the debian stable) repository of software.
2. a computer that is always bleeding edge.
3. i suppose soucrce compiling must increase speed a bit so that.
----bad is that it takes hours to install a program if its large cuz compiling takes that long.

its really up to you. nobody can decide for you. 
needless to say that both offer a large friendly useer base. (gentoo user even stuck with my noobish question when i asked on their forum)'

ps. does portage have xen 2 or xen 3 in its software repos.

---

### Post by fourhead on 2005-11-21
Thanks so much for your answers, they definitely helped me a lot. Well the one thing I really like about Gentoo is that it is so bleeding edge, and as i said I've often seen real advantages of having a bleeding-edge kernel (support for S-ATA DVD drivers for example), but on the other hand, I want to more concentrate on my work and my studies, and you indeed have a lot of work with Gentoo itself. It's not hard to get it up and running (at least not if you've done that 10+ times), but it's hard to make it really work as you want, because YOU have to install/configure everything. So this would be my main reason to switch to a more "just works" distro like Kubuntu, and I think I'll just try it on one of my machines and when I'm satisfied I'll also install it on the iBook.

So, I think you convienced me, and I'll have a look at those different repositories (didn't know about that, on Gentoo you have just one central repository).


Thanks a lot guys!


Tom


P.S. There's xen-3.0.0_pre20051027 and xen-sources-2.6.12.5-r2 in Portage.

---

### Post by otake-tux on 2005-11-21
I'm going through the same thing.  Just like you ,I WANT TO CONCENTRATE MORE ON MY WORK.  With gentoo you get the leatest stuff but you need to hack for too much time.  For example, kernel 2.6.14 came out.  Gentoo users have it however the ndiswrapper tool does not work right with the new kernel. So a lot of people , like me who went through the trouble of configuring and compiling the new kernel had to switch back to the old one because now we cant get wireless.

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=kakashi]you can add the debain unstable repository to your /etc/sources.list. 
also search for your package here [http://www.apt-get.org/](http://www.apt-get.org/)
then add the repos to sources.list
then you'll have all the debian packages. [/QUOTE]

NO NO NO NO NO NO NO

DO NOT MIX DEBIAN SOURCES WITH UBUNTU! THIS IS THE FASTEST WAY TO GET A BROKEN UBUNTU BOX! THEY ARE NOT COMPATIBLE!

Do this instead:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Do NOT tell people to add the Debian unstable to their sources.list. You might like a broken, mutant Ubuntu install but lets not advise such a course of action ANYONE on the forum please.

---

