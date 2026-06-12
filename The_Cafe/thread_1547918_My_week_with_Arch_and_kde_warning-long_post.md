---
title: "My week with Arch and kde: warning-long post"
date: 2010-08-07
forum: The Cafe
---

### Post by TVAbuntu on 2010-08-07
I was inspired to write this post after having a slow week and deciding to do something different with my OS for a while.

I started thinking I'd try PC-BSD as something totally different, but then when I realized that the PBI's and ports had to be run in "jails" to play nicely, I thougt I'd just try free-BSD. Slapped it on a free partition (has to be primary though). Did the install. Note this is on a computer with only rt2870usb wireless. Well, it wasn't autodetected. Tried iwconfig, found it's not a freeBSD command, and promptly decided that since I struggle at the CLI enough, I'd go back to linux, rather than learn new shell commands.

Thought I'd try sidux, but before doing the install realized it was probably too similar to Ubuntu to be worth it, and after browsing the forums decided it wasn't my style. A little to formal and a flavor of being autocratic.

So I thought about Gentoo, but decided that even with a light week I didn't have *that* much time.

Now I had installed Arch a few times before, but never on my main box and never without a wired connection. I had also never really tried to make it my main box. I figured I might as well give kde 4.4 a good try also. My prior Arch installs were with openbox and LXDE. I wanted to try a rolling release as well, as I have quite a few backports running on Ubuntu, and figured a rolling release, more 'bleeding edge' might be nice.

Well, the install went reasonably well. I had prepared in advance with the source tarball of the rt2870 driver and firmware from ralink just in case, but after modprobing the native rt2x00 drivers as per the wiki, no problem. 

Dropped kde got into into a vanilla kde desktop. Does take a bit: overall about 4-5 hours for the complete install, what with refreshing my memory about the modules, rc.conf, etc.

Then had to learn how to use kde 4.4.

Found the K-launcher awful, but launcelot was a good replacement. Problem is the you can't add apps to the panel via launcelot, so would have to re-add the klauncer widget, then drop an app to the panel, which sometimes would just refuse to add a plasmoid for unclear reasons. 
Dolphin was slow as molasses and sometimes needed to be killed an restarted to launch. Konqueror was a slow at both browsing and file management. The cool thing about 4.4 is that the apps are modular (how I wish that were true of gnome) and so I just removed Konqueror.

I prefer chromium to firefox, but try as I might, I could never get it to render fonts properly. I did discover rekonq which wasn't bad, and vimperator in the process, which was an interesting find. Note I was trying to stick with QT apps and stay away from GTK.

In that light, I couldn't stand Amarok2--buggy and unintuitive, and couldn't manage podcasts properly.

Back to Arch: the forums are great. A little more "technical", but in my opinion a linux distro is in part made or broken by the community, and that is one of Arch's strongest selling points.

That said, the community contributes quite a bit of the applications via the AUR. This is very cool, but pacman doesn't natively support checking for updates. So I explored "AUR helpers" and settled on clyde as a pacman replacement. Remarkable piece of work. However I ultimately decided that the AUR made me a little nervous as there was too much potential for malicious or buggy software to be introduced without checks and I am not technically inclined enough to review the code to ensure it is "safe." Admittedly reading the comments is reassuring, but on updates, I can't be bothered to go read all the new comments, so that introduces a vulnerability.

Then I had a few .pacnew files to reconcile. It wasn't bad, but not something I want to do all the time, and I felt I was "guessing" at what to merge or overwrite.

So as the week comes to a close, I have moved back to Ubuntu. I realize that quite a few of my issues are kde4.4 related, but I'm just more of a gnome type of person. Makes me glad Gnome-shell has been pushed back. I also realized that while Arch is very satisfying in some ways, in normal life I just don't have the time for it, and I prefer the extensive repositories to the AUR.

Good experience though.

---

### Post by Dustin2128 on 2010-08-07
don't stop looking; there's a distro for everyone. and that distro is slackware ;)

---

### Post by Shining Arcanine on 2010-08-07
> **TVAbuntu said:**
> So I thought about Gentoo, but decided that even with a light week I didn't have *that* much time.

Gentoo Linux does not require much more time than Arch Linux. The compilation process requires no input from you once it starts. You can have it compile over night, go to bed and come back to it the next day. As long as you have a recent processor, it should finish overnight.

---

### Post by smellyman on 2010-08-07
Arch has been great for me, openbox, lxde, gnome.....but like you, KDE is always a buggy nightmare for me.

---

### Post by KdotJ on 2010-08-07
I had a stab at Arch, I must say I really liked it. I installed xfce4 for it whici I like anyway. Maybe one day when I have a bigger machine with more hard drives I will install it natively rather than in a VM. I was also impressed with Arch's documentation

---

### Post by TVAbuntu on 2010-08-07
Slackware and Gentoo are the two remaining "biggies" I have not tried (Zenwalk and Sabayon don't count, right?) I have always been scared off by the compile times of Gentoo, and chasing dependencies on Slackware.
I'm sure at some point I will do an install, and spend some time on them, but it's hard to see them replacing big brown for everday use. And I still haven't trashed my LXDE Arch install. Just don't use it much.

I'm done with kde for now though.

---

### Post by Ctrl-Alt-F1 on 2010-08-07
I've tried Arch before.  My system was FAST!  However I missed some of the gnome specific programs that come with Ubuntu (whose names I didn't know, so I couldn't install them in arch.

> **KdotJ said:**
> I was also impressed with Arch's documentation

^^This.

---

### Post by Dustin2128 on 2010-08-07
> **TVAbuntu said:**
> Slackware and Gentoo are the two remaining "biggies" I have not tried (Zenwalk and Sabayon don't count, right?) I have always been scared off by the compile times of Gentoo, and chasing dependencies on Slackware.
I'm sure at some point I will do an install, and spend some time on them, but it's hard to see them replacing big brown for everday use. And I still haven't trashed my LXDE Arch install. Just don't use it much.

I'm done with kde for now though.
test slackware out, its a solid system.

---

### Post by NightwishFan on 2010-08-08
I like the choice of distributions because nearly all of them are great and you can have something new with a new focus if what you have gets old.

---

### Post by wolfmaniac on 2010-08-08
Right now I have Slackware 13.1 (That means KDE, as I am a Gnome hater) on my two laptops(one is my research workstation and other is my personal laptop) and Slack is rock solid as always. I have used Arch for quite a while as main system,the only problem I had was the breaking of applications with each update. The same problem exist with Ubuntu (I do not use it bec of Gnome and bugs) and Kubuntu (Its a nightmare...). That's why I love slackware...you will update only with the new release...and Patrick Volkerding and team make sure that nothing will be broken.
 I have tried a few other distros with kde 4.4 and I found that they do a lot of patching in the original code and make kde unusable.

If u really want to try KDE vanilla install Slack 13.1. 

Long live SLACKWARE and KDE

---

### Post by papangul on 2010-08-08
> **TVAbuntu said:**
> .. but I'm just more of a gnome type of person.
You could try PCLinuxOS based *Gnome ZenMini Desktop*:
[http://www.pclinuxos.com/?page_id=186](http://www.pclinuxos.com/?page_id=186)

Rolling release goodness + Synaptic(apt-rpm backend) + Nautilus Elementary.

The package versions are similar to what we get from ppas in ubuntu. I have only run it from livecd(plan to install it since I'm impressed :)) so I can't comment on it further but obviously it lacks the fast boot of ubuntu.

---

