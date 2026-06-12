---
title: "Empathy and Google Talk"
date: 2008-07-10
forum: The Cafe
---

### Post by pravinbravi on 2008-07-10
You guys should try multi-protocol new jabber client empathy (empathy-megaphone-applet). Its there in Hardy Heron. We can do voice chat too with gtalk users.

Good luck guys.

--
Pravin

---

### Post by zmjjmz on 2008-07-10
There is a GSoC project to get VOIP over Googletalk integrated into Pidgin.

---

### Post by Polygon on 2008-07-10
> **zmjjmz said:**
> There is a GSoC project to get VOIP over Googletalk integrated into Pidgin.

ive been hearing about voip/video finally getting into pidgin, i wonder if this is a part of it?

---

### Post by voteforpedro36 on 2008-07-10
> **pravinbravi said:**
> You guys should try multi-protocol new jabber client empathy (empathy-megaphone-applet). Its there in Hardy Heron. We can do voice chat too with gtalk users.

Good luck guys.

--
Pravin

That was one hell of a bump, sir.

---

### Post by bruce89 on 2008-07-10
> **voteforpedro36 said:**
> That was one hell of a bump, sir.

Empathy is **that** good though.

---

### Post by jpeddicord on 2008-07-10
> **voteforpedro36 said:**
> That was one hell of a bump, sir.

Indeed it was. Split.

---

### Post by bruce89 on 2008-07-10
By the way, Empathy is proposed at the official GNOME IM client again. It was proposed for 2.22, but there were some licence issues.

Empathy is more than a Jabber client, if you install *telepathy-haze*, it can use almost all the protocols that Pidgin can use (it makes use of libpurple).

*telepathy-butterfly* -- MSN
*telepathy-gabble* -- Jabber/XMPP
*telepathy-haze* -- libpurple (AIM, ICQ, MSN, Yahoo)
*telepathy-idle* -- IRC
*telepathy-salut* -- link-local XMPP (Bonjoureque)
*telepathy-sofiasip* -- SIP

---

### Post by ssam on 2008-07-10
telepathy (the frame work behind empathy) can do all sorts of very clever stuff.
[http://www.robot101.net/2008/07/10/guadec-telepathy-boat-part/](http://www.robot101.net/2008/07/10/guadec-telepathy-boat-part/)

hopefully some more desktop apps will start picking this stuff up soon.

---

### Post by mrgnash on 2008-07-10
Empathy has been the only IM client to compete with Pidgin for my heart :P I'm expecting big things in the future :)

---

### Post by sergiom99 on 2008-07-12
> **pravinbravi said:**
>  We can do voice chat too with gtalk users.

I cannot get the voice call to work in Kubuntu HH. How'd you do it??
[http://ubuntuforums.org/showthread.php?t=819046&page=3](http://ubuntuforums.org/showthread.php?t=819046&page=3)
Tired of dual booting :(

---

### Post by FuturePilot on 2008-07-12
Empathy looks like it holds a lot of promise. I'm really looking forward to seeing this get into Gnome. From what I can tell, it can do a lot of things Pidgin can't. Hopefully we will see it in Gnome 2.24. :)

---

### Post by pravinbravi on 2008-07-30
[I]I cannot get the voice call to work in Kubuntu HH. How'd you do it??
[http://ubuntuforums.org/showthread.php?t=819046&page=3](http://ubuntuforums.org/showthread.php?t=819046&page=3)
Tired of dual booting [/I]

Hi,

Writing after a long absence, my apologies.

Well Kubuntu requires you to install the empathy and the telepathy packages from the hardy-backports. I tried this on a friend's (Kubuntu) laptop, but i was unsuccessful in installing the telepathy compatible with the new empathy 0.23 package.

The voice feature works only with the new telepathy files (empathy 0.23 depends on corresponding telepathy) installed.

Looks like we have to make a deb file from the source package, but it can get messy building from a source package.

See if you have any luck mr. sergiom99.

Alternatively, I have installed google talk in my winxp virtual machine under ubuntu 8.04. had little trouble with the pulse audio and ESD setting for the VMware 6.5 beta, but its all configured fine now and works beautifully.

--
Pravin

---

### Post by pravinbravi on 2008-07-30
> **zmjjmz said:**
> There is a GSoC project to get VOIP over Googletalk integrated into Pidgin.

read
[http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo](http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo)

will need farsight2, but had dep problem. we can install the following so that farsight2 can be built from source.

[http://sourcedeps.debian.net/pool/main/f/farsight2/farsight2-build-depends_0.0.2-1_all.deb](http://sourcedeps.debian.net/pool/main/f/farsight2/farsight2-build-depends_0.0.2-1_all.deb)
[http://sourcedeps.debian.net/pool/main/f/farsight2/farsight2-build-depends_0.0.3-1_all.deb](http://sourcedeps.debian.net/pool/main/f/farsight2/farsight2-build-depends_0.0.3-1_all.deb)

farsight2 source

[http://farsight.freedesktop.org/releases/farsight2/farsight2-0.0.1.tar.gz](http://farsight.freedesktop.org/releases/farsight2/farsight2-0.0.1.tar.gz)
[http://farsight.freedesktop.org/releases/farsight2/farsight2-0.0.3.tar.gz](http://farsight.freedesktop.org/releases/farsight2/farsight2-0.0.3.tar.gz)

but when u try to build farsight2, on make install or checkinstall the following error shows up
```
chmod: changing permissions of `/usr/local/lib/libgstfarsight-0.10.a': No such file or directory
make[5]: *** [install-libLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/pravin/Desktop/farsight2-0.0.1/gst-libs/gst/farsight'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/pravin/Desktop/farsight2-0.0.1/gst-libs/gst/farsight'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/home/pravin/Desktop/farsight2-0.0.1/gst-libs/gst/farsight'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/pravin/Desktop/farsight2-0.0.1/gst-libs/gst'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/pravin/Desktop/farsight2-0.0.1/gst-libs'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

```surprisingly make install works fine. huh! :)

---

### Post by pravinbravi on 2008-08-19
Also helpful would be a reading of the following 

[http://ubuntuforums.org/showthread.php?t=819046](http://ubuntuforums.org/showthread.php?t=819046)

add the following line to your apt sources

```
sudo gedit /etc/apt/sources.list
```
[FONT=monospace]
add the following line to the end of the page

## packages for telepathy
[/FONT]deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

```
sudo apt-get update;sudo apt-get upgrade;sudo apt-get install telepathy-gabble telepathy-mission-control telepathy-stream-engine empathy;sudo apt-get autoremove

```
Hope this thing helps you guys. Enjoy!

---

