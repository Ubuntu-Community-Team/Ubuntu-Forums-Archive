---
title: "How good is Kubuntu 9.10?"
date: 2009-11-04
forum: The Cafe
---

### Post by Unanimated on 2009-11-04
I changed my filesystem from ext3 to ext4 while it was mounted (silly me.. ^_^) and it caused many annoying damages, so I'm just moving my home folder to my other hard drive and reinstall Ubuntu (I also want the benefits of a clean install). The problem I'm having is choosing between reinstalling Ubuntu or installing Kubuntu 9.10. Is it really that great? Is the performance up to par with GNOME? How system-intensive is the new K desktop? I used Kubuntu 8.10 or 9.04 (I think 8.10) and I wasn't terribly impressed. It ran fine, though. But also, games like Unreal Tournament 2004 and Tremulous run fine (again) on GNOME, and I'm wondering if they'll still run smoothly in K. I have an NVIDIA GeForce 6200, 1GB RAM, and an Intel Pentium 4 2.8 GHz processor. What I'm really wondering is this - is Kubuntu 9.10 really that great? And does it run as well (or better) as GNOME in Ubuntu 9.10?

---

### Post by edin9 on 2009-11-04
It still has some stability issues as of 4.3.3.

---

### Post by bovender on 2009-11-04
When I planned to migrate from WinXP to (k)Ubuntu recently, I performed full installs of both variants. Kubuntu surprised me with constant crashes, even while the desktop environment was loading I was confronted with tons of cryptic error messages. This crashed, that failed, and so on. So I went for Ubuntu, which overall seemed cleaner and much more stable.

Ideally you would try them both on a long, rainy weekend...

---

### Post by SunnyRabbiera on 2009-11-04
Well as far as KDE is concerned I feel 4.3 is the best in the series so far, but i would try a non buntu for a better KDE experience, say Mandriva or openSUSE.

---

### Post by edin9 on 2009-11-04
> **SunnyRabbiera said:**
> Well as far as KDE is concerned I feel 4.3 is the best in the series so far, but i would try a non buntu for a better KDE experience, say Mandriva or openSUSE.

+1 
    openSUSE 11.2 KDE is pretty good.

---

### Post by Unanimated on 2009-11-04
> **SunnyRabbiera said:**
> Well as far as KDE is concerned I feel 4.3 is the best in the series so far, but i would try a non buntu for a better KDE experience, say Mandriva or openSUSE.
I've tried Mandriva and openSUSE. Mandriva broke (literally... wouldn't load, the OS itself forgot my password and I couldn't log in, many other annoying issues...) and SUSE didn't detect hardware right, even in Qemu. I'm using Ubuntu now, and I think I'll just reinstall it and maybe someday dual-boot or virtualize with Kubuntu. Is Arch Linux any good?

---

### Post by hoppipolla on 2009-11-04
> **edin9 said:**
> It still has some stability issues as of 4.3.3.

thanks for the heads up! Upgrading! hehe :)

---

### Post by dragos240 on 2009-11-04
> **SunnyRabbiera said:**
> Well as far as KDE is concerned I feel 4.3 is the best in the series so far, but i would try a non buntu for a better KDE experience, say Mandriva or openSUSE.

What about arch & kdemod?

---

### Post by hoppipolla on 2009-11-04
> **SunnyRabbiera said:**
> Well as far as KDE is concerned I feel 4.3 is the best in the series so far, but i would try a non buntu for a better KDE experience, say Mandriva or openSUSE.

I'm not sure if I agree, I mean with Kubuntu you get the wicked Ubuntu base.

What I do is install Ubuntu and then stick kubuntu-desktop on top of it :)

---

### Post by adalal on 2009-11-04
Well, the easiest option, is to install both desktops, compare them side by side... and then remove the other desktop...

---

### Post by Unanimated on 2009-11-04
Well, I found out about 5 minutes ago that I actually have a 64-bit processor. (About 2 weeks ago, I got a new one from my uncle and I didn't realize his was 64-bit.) So, right now I'm downloading the Ubuntu 64-bit ISO. Before I install it, what's the 64-bit support in Ubuntu like? I heard it was pretty terrible in Windows XP, and I also heard that Flash is rather difficult to install. But that information is also from over a year and a half ago, so that's probably pretty unreliable at this point. But still, how good is the support in Ubuntu?

---

### Post by edin9 on 2009-11-04
> **hoppipolla said:**
> thanks for the heads up! Upgrading! hehe :)

lol.

---

### Post by SunnyRabbiera on 2009-11-04
> **Unanimated said:**
> Well, I found out about 5 minutes ago that I actually have a 64-bit processor. (About 2 weeks ago, I got a new one from my uncle and I didn't realize his was 64-bit.) So, right now I'm downloading the Ubuntu 64-bit ISO. Before I install it, what's the 64-bit support in Ubuntu like? I heard it was pretty terrible in Windows XP, and I also heard that Flash is rather difficult to install. But that information is also from over a year and a half ago, so that's probably pretty unreliable at this point. But still, how good is the support in Ubuntu?

I weould say flash is still rough around the edges, its why i dont use 64bit.
But linux support of 64bit has always been better then windows overall.

---

### Post by edin9 on 2009-11-04
> **SunnyRabbiera said:**
> I weould say flash is still rough around the edges, its why i dont use 64bit.
But linux support of 64bit has always been better then windows overall.

I use 64bit Flash with Konqueror and have 0 problems.

---

### Post by Slug71 on 2009-11-04
> **Unanimated said:**
> Well, I found out about 5 minutes ago that I actually have a 64-bit processor. (About 2 weeks ago, I got a new one from my uncle and I didn't realize his was 64-bit.) So, right now I'm downloading the Ubuntu 64-bit ISO. Before I install it, what's the 64-bit support in Ubuntu like? I heard it was pretty terrible in Windows XP, and I also heard that Flash is rather difficult to install. But that information is also from over a year and a half ago, so that's probably pretty unreliable at this point. But still, how good is the support in Ubuntu?

Ive been using 64bit since Jaunty development and i wouldnt go back to 32bit. Not because theres anything wrong with 32bit but everything works for me on 64bit. Acroread i installed from Jaunty's repo because it wasnt in Karmic's partner and i have the linux 64bit flash installed.

I downloaded it to my desktop and then

```
sudo mv /Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```

done.

I do have the ia32libs installed too though.

I have Java installed and Skype too. and Hulu Desktop.

---

### Post by qazwsx on 2009-11-04
> **edin9 said:**
> I use 64bit Flash with Konqueror and have 0 problems.

But nspluginviewer makes me crazy. Constantly eating CPU resources while flash is not even active. I hate writing that killall nspluginviewer command over and over again. That problem was already present in KDE 3. Maybe I am just a control freak :). But constantly using even 5 % of CPU cycles for that viewer is way too much.

---

### Post by Sugz on 2009-11-04
Just did a fresh install of Karmic today (at last) and i am really enjoying the experience so far.
A few bugs here and there and one that has not been repaired since Gutsy :( but overall extremely impressed. :popcorn:

---

### Post by edin9 on 2009-11-04
> **qazwsx said:**
> But nspluginviewer makes me crazy. Constantly eating CPU resources while flash is not even active. I hate writing that killall nspluginviewer command over and over again. That problem was already present in KDE 3. Maybe I am just a control freak :). But constantly using even 5 % of CPU cycles for that viewer is way too much.

So don't use nsplugin? It sucks.

---

### Post by xuCGC002 on 2009-11-04
My advice? Grab the mini.iso of 8.04, install that, and install xfce4 and xfce4-goodies. XFCE by itself doesn't use nearly as much RAM as Xubuntu does, as Xubuntu includes a ton of GNOME apps installed by default.

---

### Post by Ms_Angel_D on 2009-11-04
I've been running Kubuntu 9.10 Since the RC was released and I haven't had any issues. My system hums and everything is simply put beautiful.

---

### Post by stuart.reinke on 2009-11-04
> **hoppipolla said:**
> i'm not sure if i agree, i mean with kubuntu you get the wicked ubuntu base.

What i do is install ubuntu and then stick kubuntu-desktop on top of it :)

+1

---

