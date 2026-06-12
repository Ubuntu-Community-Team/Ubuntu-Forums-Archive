---
title: "can vbox run games?"
date: 2009-03-21
forum: The Cafe
---

### Post by SonnHalter on 2009-03-21
Haven't been on linux in a while. but my winblows machine has been botted and viruses. 

I only need windows for photoshop (knows it works in vbox) and games.

My computer is a gaming machine and I just want to know if vbox can handle it.

---

### Post by wolfen69 on 2009-03-21
it will choke on the newer games, but older games should be no problem. just make sure to allocate the full 128mb video ram for xp. and make sure to enable 3D support in vbox settings.

---

### Post by binbash on 2009-03-21
I got success at some old games

---

### Post by MasterNetra on 2009-03-21
Worst case scenario you could dual-boot.

---

### Post by compgeek83 on 2009-03-21
> **SonnHalter said:**
> Haven't been on linux in a while. but my winblows machine has been botted and viruses. 

I only need windows for photoshop (knows it works in vbox) and games.

My computer is a gaming machine and I just want to know if vbox can handle it.

i would love to see vbox with better gaming support, I gave up windows a few months back as my main os, and I refuse to do a dual boot.  Seems to me that wine does a pretty good job of making windows games run under linux, why cant vbox be made to "translate" between the games in their native linux...

---

### Post by speedwell68 on 2009-03-22
So far I have only tried two games in vbox, Quake 3 Arena and The Sims, both worked well.  I don't really play them I just did it to see if I could.

---

### Post by Ozor Mox on 2009-03-22
> **SonnHalter said:**
> Haven't been on linux in a while. but my winblows machine has been botted and viruses. 

I only need windows for photoshop (knows it works in vbox) and games.

My computer is a gaming machine and I just want to know if vbox can handle it.

VirtualBox will only be suitable for playing games that don't require 3D hardware acceleration.

---

### Post by jpeddicord on 2009-03-22
> **wolfen69 said:**
> it will choke on the newer games, but older games should be no problem. just make sure to allocate the full 128mb video ram for xp. and make sure to enable 3D support in vbox settings.

> **Ozor Mox said:**
> VirtualBox will only be suitable for playing games that don't require 3D hardware acceleration.

VirtualBox has 3D support now? I knew they were working on it, but I didn't know it was finished. Will have to give that a try.

---

### Post by Bölvaður on 2009-03-22
I tried out quake live because of this thread in the virtual box from their website. Armed with 128 mb for video + 3d acceleration and 600 mb ram... still lags like an anorexic chimp in an eating contest for hippos.

---

### Post by Ozor Mox on 2009-03-22
> **jacobmp92 said:**
> VirtualBox has 3D support now? I knew they were working on it, but I didn't know it was finished. Will have to give that a try.

I think you misread my post!

As far as I know, VirtualBox does not have 3D support yet. VMWare has experimental 3D support. The technology is on the way I think.

---

### Post by Glucklich on 2009-03-22
> **compgeek83 said:**
> i would love to see vbox with better gaming support, I gave up windows a few months back as my main os, and I refuse to do a dual boot.  Seems to me that wine does a pretty good job of making windows games run under linux, why cant vbox be made to "translate" between the games in their native linux...

I think what they want it's irrelevant. It's a question of computer resources. Basically vbox allows you to have a machine inside the machine. As usual, that secondary machine has to be controlled, otherwise it will steal all the resources of the original machine and consequently crashing it. Now, games are by far the most resource consumption program you can have. Recent games, take all the resources of the original machine without having to run it along with a secondary machine on. So, it's impossible to have the two machines plus a recent game. Dual boot or play Linux and Wine games.

---

### Post by jpeddicord on 2009-03-22
> **Ozor Mox said:**
> I think you misread my post!

As far as I know, VirtualBox does not have 3D support yet. VMWare has experimental 3D support. The technology is on the way I think.

I was referring to the post above it really, I just quoted yours as well as it was related. Anyway, I did find this in the VBox manual:

> 4.8 Hardware 3D acceleration (OpenGL)
Starting with version 2.1, the VirtualBox Guest Additions for Windows contain exper-
imental hardware 3D support.
   With this new feature, if an application inside your Windows guest uses 3D features
through the OpenGL programming interfaces, these will not be emulated in software
(which is slow), but instead VirtualBox will attempt to use your host&#8217;s 3D hardware.
This works for all supported host platforms (Windows, Mac, Linux, Solaris), provided
that your host operating system can make use of your accelerated 3D hardware in the
first place.

   The 3D acceleration currently has the following limitations:
    1. It is only available in Windows XP and 32-bit Vista guests with the Windows
       Guest Additions installed.
    2. Only OpenGL acceleration is presently available in those guests; Direct3D is not
       yet supported and will be added in a future release.
    3. Because the feature is experimental at this time, it is disabled by default and must
       be manually enabled in the VM settings (see chapter 3.7.1, General settings, page
       45).
   Please see chapter 13, Known issues, page 189 also.
   Technically, VirtualBox implements this by installing an additional hardware 3D
driver inside your Windows guest when the Guest Additions are installed. This driver
acts as an OpenGL hardware driver and reports to Windows that the (virtual) hardware
is capable of 3D hardware acceleration. When an application in the Windows guest re-
quests hardware acceleration through the OpenGL programming interfaces, these are
sent to the host through a special communication tunnel implemented by VirtualBox,
and then the host performs the requested 3D operation via the host&#8217;s OpenGL programming interfaces.

Wonder how well it works.

---

