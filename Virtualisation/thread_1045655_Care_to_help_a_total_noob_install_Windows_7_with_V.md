---
title: "Care to help a total noob install Windows 7 with VirtualBox OSE?"
date: 2009-01-20
forum: Virtualisation
---

### Post by chazdraves on 2009-01-20
Greetings, all!

I'm having the darndest time! I've been trying for about 2 hours now to get Windows 7 installed via VirtualBox, but it just isn't happening. Every time it gets to the little flying colors (just before the installer officially starts) and freezes solid...

Can someone help me understand? I have all the boxes checked under the "General" settings tab...

- Chaz

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Can someone help me understand? I have all the boxes checked under the "General" settings tab...I'm not sure I know what you mean by this.  Does your system support all the features you have checked off.  Have you set the Base Memory and Video Memory to an appropriate amount based on your system specs?

I have not tried to install Windows 7 (nor do I intend to).  But HERE is a step-by-step guide to installing it in VirtualBox.  I cannot vouch for it, but it looks like a reasonable guide to me.

---

### Post by chazdraves on 2009-01-20
Well, I set the RAM to 3000 (I have 4GB) and video to 128 (I have 512, but it comes up with a max of 128). I belive my CPU supports all the features (C2D E8400).

I don't see a link in your post, just a capital "HERE". :)

Thanks!
- Chaz

---

### Post by Therion on 2009-01-20
This is the guide I use to get my virtual machines working.  It's written for Hardy Heron-host/XP guest but the directions are pretty much the same regardless, especially since you're using the OSE version of VirtualBox:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Well, I set the RAM to 3000 (I have 4GB) and video to 128 (I have 512, but it comes up with a max of 128). I belive my CPU supports all the features (C2D E8400).Video RAM is fine at 128.  Change Base Memory to 1536 (you can increase it to 2048 later if you really want to)

[HERE]("http://www.raymond.cc/blog/archives/2009/01/14/step-by-step-on-how-to-download-install-and-activate-windows-7-beta-without-messing-currently-installed-os-and-dual-boot/") is the missing link. :)  Sorry about that.  (It is based on using VirtualBox for Windows, but that shouldn't make any difference.  The method described in the [Community Documentation]("https://help.ubuntu.com/community/VirtualBox") is somewhat out of date... but it might give you some ideas.  Just don't use the part about setting up USB... it will more than likely mess up your system)

EDIT:  Don't worry about the USB thing.  VirtualBox-OSE doesn't support it anyway. :)

---

### Post by chazdraves on 2009-01-20
Everyone of those guides says to set it to "Windows" and then "Other". I don't have anything that just says "Windows", they all include a prefix".

Either way, this is as far as I get EVERY time!

[IMG]http://i31.photobucket.com/albums/c378/chazdraves/Windows7.png[/IMG]

I don't care to switch to Windows, I'm just curious to try the latest version as long as it's offered free...

- Chaz

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Everyone of those guides says to set it to "Windows" and then "Other". I don't have anything that just says "Windows", they all include a prefix".With "Operating System" set to "Microsoft Windows," I have the option of "Other Windows" under "Version."  If you do not have that, set it to Windows Vista.

---

### Post by chazdraves on 2009-01-20
Could this be a problem with the 64-bit version of Win7?

- Chaz

---

### Post by chazdraves on 2009-01-20
Hmm... My version of VirtualBox is only 2.0.4... I got it from the repos... is that the problem? I'm also downloading the 32-bit .iso as we speak as I understand there were problems with the 64-bit .iso not installing under Mac OSX...

- Chaz

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Could this be a problem with the 64-bit version of Win7?It could be.  Try the 32 bit version and see if you have better luck.

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Hmm... My version of VirtualBox is only 2.0.4... I got it from the repos... is that the problem?VirtualBox-2.1 has better 64 bit support.  If you'd like to try it, see [http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)  -- it is primarily about getting USB support in VirtualBox, but it also gives detailed instructions on getting and installing VirtualBox 2.1 (PUEL edition).

---

### Post by chazdraves on 2009-01-20
Yup, I downloaded 2.10 from the VirtualBox website just now and it's finally installing properly... We'll see what problems I run into once it's installed, but at least it's working...

Why isn't 2.10 in the repository? VB has a precompiled package available right at the site...?

- Chaz

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Why isn't 2.10 in the repository? VB has a precompiled package available right at the site...?It's a licensing issue.  You can add a repository for Sun's binaries quite easily by following the instructions I linked you to.  By doing this, you will receive important updates through the Synaptic Package Manager rather than having to check and update manually.

---

### Post by chazdraves on 2009-01-20
I see. Well, I added them to my list per the instructions.

Once in Win 7 I went to install the Guest Devices and had to restart, now I find it doesn't care to run anymore.. This could be far more trouble than it's worth. Especially since I don't care much in the first place...

- Chaz

---

### Post by chazdraves on 2009-01-20
Okay.. next noob question - how do I get my internet working now?

- Chaz

---

### Post by HotShotDJ on 2009-01-20
> **chazdraves said:**
> Okay.. next noob question - how do I get my internet working now?Post that in a new thread in the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum.  Although you'll probably find the answer by using the search box near the top of the Ubuntuforums window

---

### Post by chazdraves on 2009-01-20
Done and done!

- Chaz

---

