---
title: "Adobe seems to have fixed the flash installer..."
date: 2009-12-09
forum: The Cafe
---

### Post by sandyd on 2009-12-09
as part of an update
[http://www.pcworld.com/article/184109/adobe_updates_flash_air_with_critical_fixes.html](http://www.pcworld.com/article/184109/adobe_updates_flash_air_with_critical_fixes.html)

today, adobe has finally fixed the adobe flash installation/reinstallation problems (dependencies, and non-uninstallable flash)
theirs now a seperate deb version for 9.04+ avalible on their site.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

new alpha refresh of x64 flash was also released yesterday
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Improvements/additions to the x64 bit edition include
> **3D Effects** - Easily transform and animate any display object through 3D space while retaining full interactivity.  Fast, lightweight, and native 3D effects make motion that was previously reserved for expert users available to everyone.  Complex effects are simple with APIs that extend what you already know.
         [B]
Custom Filters and Effects[/B] - Create and [share your own]("http://www.adobe.com/go/pixelbender") portable filters, blend modes, and fills using  [Adobe Pixel Bender&#8482;]("http://www.adobe.com/go/pixelbender_toolkit"), the same technology used for many After Effects CS3 filters. Shaders in Flash Player are about 1KB and can be scripted and animated at runtime.
        [B]
Advanced Text Layout[/B] - A new, highly flexible text layout engine, co-existing with TextField, enables innovation in creating new text controls by providing low-level access to text offering right-to-left and vertical text layout, plus support for typographic elements like ligatures. 

**Enhanced Drawing API** - Runtime drawing is easier and more powerful with re-styleable properties, 3D APIs, and a new way of drawing sophisticated shapes without having to code them line by line.
       [B]
Visual Performance Improvements[/B] &#8211; Applications and videos will run smoother and faster with expanded use of hardware acceleration.  By moving several visual processing tasks to the video card, the CPU is free to do more.
       [B]
Enhanced Sound APIs[/B] &#8211; Work with loaded MP3 audio at a lower level in Flash Player 10.  The new APIs will let you do application-level audio mixing through ActionScript and even audio filtering with Adobe Pixel Bender.

Adobe air also got an update, but i cant seem to find the changelog.....
thankyou adobe. just what i wanted for my early christmas present!! ;)

---

### Post by hoppipolla on 2009-12-09
wow that's really cool :)

I mean the version in the repos has always seemed ok, but this is certainly a step up!

Well done Adobe! :)

---

### Post by sudoer541 on 2009-12-09
I just got an update from adobe flash 32bits and it seems faster then before

---

### Post by ZankerH on 2009-12-09
It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!

---

### Post by wojox on 2009-12-09
Thanks for the heads up carlee. Just purged the old and installed the new. :D

---

### Post by schauerlich on 2009-12-09
> **ZankerH said:**
> It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!

UF uses vBulletin, which is proprietary.

Bye.

---

### Post by Giant Speck on 2009-12-09
> **ZankerH said:**
> It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!

The irony is hilarious.

---

### Post by Crunchy the Headcrab on 2009-12-09
> **ZankerH said:**
> It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!
No.  I'm going to use the hell out of it.  :D

---

### Post by pwnst*r on 2009-12-09
> **Giant Speck said:**
> The irony is hilarious.

hahaha

---

### Post by lovinglinux on 2009-12-09
Thanks for the info.

The separate version is installed via partner repository now, instead of manual deb installation. Cool. You can install with the link below:

[apt:adobe-flashplugin?channel=$distro-partner](apt:adobe-flashplugin?channel=$distro-partner)

Ubuntu Update Manager will also provide it if you have the partner repo enabled and flashplugin-nonfree installed.

---

### Post by Psumi on 2009-12-09
x64 version is MUCH more stable than it ever was now, and much faster, thank you adobe!

---

### Post by speedwell68 on 2009-12-09
> **ZankerH said:**
> It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!

Oh please, are you seriously suggesting that you don't use any sites that use flash?  

I noticed that an updated version in the update manager earlier and I have to say that things seem a lot smoother, like the iPlayer and Youtube videos that have been embedded in forum posts.

---

### Post by sandyd on 2009-12-10
bump as a reminder.

---

### Post by tashirosgt on 2009-12-10
Is the flash installer fixed for Ubuntu 9.x and not for Ubuntu 8? 

I tried their installation for Ubuntu 8.04 on my machine and when I visit a site that uses Flash, the site redirects me to the "Get Adobe Flash" page.   Was there some manual configuration to work-around the problem in Ubuntu 8 ?

---

### Post by Psumi on 2009-12-10
Now that I'm back on GNOME, the flash plugin isn't as stable anymore. :(

---

### Post by Anuovis on 2009-12-26
I was hoping this would fix **_[flickering flash]("http://ubuntuforums.org/showthread.php?t=1347087")_** issues but at least on my system it did not.

---

### Post by Exodist on 2009-12-26
> **Anuovis said:**
> I was hoping this would fix **_[flickering flash]("http://ubuntuforums.org/showthread.php?t=1347087")_** issues but at least on my system it did not.
May be VSunc not enabled. If not its a hidden performance issue.

---

### Post by DustWolf on 2010-02-04
> **lovinglinux said:**
> [apt:adobe-flashplugin?channel=$distro-partner](apt:adobe-flashplugin?channel=$distro-partner)

Say how the heck does one use that link? I just get an invalid protocol message from my browser. Also, I can't seem to be able to add the link as a synaptic source either.

---

### Post by arnab_das on 2010-02-04
flickering issue very much there. just tested flash after updating. adobe needs to do a lot more.

---

### Post by Psumi on 2010-02-04
> **lovinglinux said:**
> Thanks for the info.

The separate version is installed via partner repository now, instead of manual deb installation. Cool. You can install with the link below:

[apt:adobe-flashplugin?channel=$distro-partner](apt:adobe-flashplugin?channel=$distro-partner)

Ubuntu Update Manager will also provide it if you have the partner repo enabled and flashplugin-nonfree installed.

How do we do this without software sources, synaptic, apturl or the update manager? (IE: If we hate gnome?)

---

### Post by Tibuda on 2010-02-04
> **DustWolf said:**
> Say how the heck does one use that link? I just get an invalid protocol message from my browser. Also, I can't seem to be able to add the link as a synaptic source either.
[https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)

> **Psumi said:**
> How do we do this without software sources, synaptic, apturl or the update manager? (IE: If we hate gnome?)
edit sources.list, and then use apt-get or aptitude

---

### Post by blur xc on 2010-02-04
I'm confused again.  This post is from two months ago.  Doens't flash just get updated automatically along with the rest of the standard updates?  Shouldn't sudo aptitude update && sudo aptitude safe-upgrade get you the latest flash anyway?  

I just tried installing, and apparently I already have that same version 10.0.42.34 installed...

BM

---

### Post by Psumi on 2010-02-04
> **danielrmt said:**
> [https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)


edit sources.list, and then use apt-get or aptitude

And what repo do we add?

---

### Post by Tibuda on 2010-02-04
> **Psumi said:**
> And what repo do we add?

Partner. I think it is already in the default sources.list, but commented. I can't check, as I don't use Ubuntu anymore.

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories)

---

### Post by cariboo on 2010-02-04
Apturl only pulls packages from the repositories and ppa's you have enabled. I you want the latest flash version you will have to get it from Adobe.

---

### Post by chriswyatt on 2010-02-04
> I you want the latest flash version you will have to get it from Adobe.

I assume you mean directly?  I got the latest Flash version from the Canonical repository.

---

### Post by jrusso2 on 2010-02-04
> **ZankerH said:**
> It's still proprietary software. Not what I'd call "fixed".

Do not use this restrictive software, and do not support websites that insist on you using it!

Hopefully if HTML 5 comes along we won't need flash.

---

### Post by cariboo on 2010-02-04
I've been using the 64-bit alpha version directly from Adobe for several months, and have had zero problems. Using the 64-bit version from the repositories caused my media center pc to lock up when running "HD" flash full screen.

---

