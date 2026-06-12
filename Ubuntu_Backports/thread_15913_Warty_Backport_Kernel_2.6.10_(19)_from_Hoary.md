---
title: "Warty Backport: Kernel 2.6.10 (19) from Hoary"
date: 2005-02-17
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-17
**Synopsis**
This resolves a lot of bugs found in the previously backported kernel.

**Backporting Process**
The source archive directly came from Hoary. I was able to meet all dependencies, with the kernel-wedge / dpatch from the previous backport.

**Packaging Status:**
i386 -- Staging rev 51 & 52
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
1. This backport will be in the **bleeding** section, as kernel upgrades may not be taken so  warmly by everyone.

2. This kernel may have known security issues, as does the current Hoary kernel. Snipping from changelog:

```

rev 18:   * TEMPORARY revert SECURITY fix and inotify update from -17 since they
    break the kernel ABI.

rev 17:  * [SECURITY] fix some sign comparison problems in the filesystem layer.
    - Add patch stolen-from-head_fix-sign.dpatch

```
Doesn't look like anything TOO big, but be advised!!

3. Restricted modules aren't built yet. I have to upload these then pull the headers back from the APT tree first! Patience, my friends.

4. This upload may take an hour or two -- it's a good 200MB of stuff @ 30KB/s! Patience.....

5. Known by the state of California to cause birth defects.

---

### Post by faqpete on 2005-02-18
[QUOTE=jdong]

**Beta tester notes:**
1. This backport will be in the **bleeding** section, as kernel upgrades may not be taken so  warmly by everyone.
[/QUOTE]
 Hi jdong!
When I'm adding the bleeding line to my sources via synaptic and click on the reload-button in synaptic, i get the following error:

[http://backports.ubuntuforums.org/backports/dists/warty/bleeding/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/bleeding/binary-i386/Packages.gz:) 404 Not Found

---

### Post by jdong on 2005-02-18
[QUOTE=faqpete]Hi jdong!
When I'm adding the bleeding line to my sources via synaptic and click on the reload-button in synaptic, i get the following error:

[http://backports.ubuntuforums.org/backports/dists/warty/bleeding/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/bleeding/binary-i386/Packages.gz:) 404 Not Found[/QUOTE]
That should be warty-backports[-staging], not just warty.

---

### Post by faqpete on 2005-02-18
Hi jdong!
Thx for your quick reply. After changing the entries in my sources.list (the right way??) the errormessage is gone. But I'm not able to find the new kernel-backport 2.6.10 :-(
Here's my sources.list:


[COLOR=SlateGray][I]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://www.grawert.net/ubuntu/](http://www.grawert.net/ubuntu/) warty universe 


##############Ubuntu Warty Backports################
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main restricted 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras universe multiverse 

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports universe multiverse 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main restricted 

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports bleeding 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports-staging bleeding  
[/I][/COLOR]
thanks for your help
faqpete

---

### Post by faqpete on 2005-02-18
Got it!
Now testing ;-)

---

### Post by faqpete on 2005-02-18
**My results of testing:**
ACPI improvements but *ndiswrappe*r (which works under 2.6.8 perfectly) still *doesnt work* - with the same errormessage: operation not permitted :-(
thanks nevertheless for backporting jdong!

---

### Post by om007 on 2005-02-18
Dear Ubuntu Gurus

just installed Ubuntu yesterday on my Compaq EVO n610c and getting in trouble with the fan not working ... one guy said he resolved this issue by installing 2.6.10 kernel ..


So i tried installing the backport but Synaptic fails with 

linux-image-2.6.10-3-686:
  Depends: initrd-tools but 0.1.70ubuntu9 is to be installed

but when i check for initrd-tools it says this version is already installed !!!

any help would be welcome !!!

OM007

---

### Post by jdong on 2005-02-18
OM007: Can someone else confirm/help with this problem? I can't reproduce it in my two plain Warty chroots.


Restricted modules are currently uploading.

---

### Post by neville_lobo on 2005-02-19
om007

Add this to your sources and update initrs-tools.

deb [http://www.backports.org/debian](http://www.backports.org/debian) stable initrd-tools
deb-src [http://www.backports.org/debian](http://www.backports.org/debian) stable initrd-tools

It worked for me.

Neville

---

### Post by jdong on 2005-02-19
You shouldn't need to -- that IS the Warty version of initrd-tools...


Does anyone else have this issue?

---

### Post by dcstar on 2005-02-28
One pleasing "side effect" of the 2.6.10 Kernel I have noticed is that I used to require "ACPI=OFF" in my kernel boot string to allow my PC to be powered off with the 2.6.8 kernel.

I no longer need that string to have my PC power off.

---

### Post by jdong on 2005-02-28
Naturally, each kernel version has numerous bugfixes and improvements over previous ones -- ACPI is one of the biggies.

---

### Post by fackamato on 2005-03-08
Has anyone encountered any issues using this kernel on Warty? No issues with 3d acceleration, sound, tv cards, xorg/xfree, gnome, whatever? :P  :wink:

---

### Post by fackamato on 2005-03-08
[QUOTE=jdong]You shouldn't need to -- that IS the Warty version of initrd-tools...


Does anyone else have this issue?[/QUOTE]

Got the same "error" message, going to try with the sources he said now...

And yup, that solved it.

---

### Post by dcstar on 2005-03-09
[QUOTE=fackamato]Has anyone encountered any issues using this kernel on Warty? No issues with 3d acceleration, sound, tv cards, xorg/xfree, gnome, whatever? :P  :wink:[/QUOTE]
For me, more things work (ACPI, IPv6 network utilities) than with the old kernels, nothing noticed on the downside yet.

---

### Post by fackamato on 2005-03-09
[QUOTE=dcstar]For me, more things work (ACPI, IPv6 network utilities) than with the old kernels, nothing noticed on the downside yet.[/QUOTE]

I'm using this kernel now, and I've only got good things to say about it, for example it fixed my tv card. :)

---

### Post by jdong on 2005-03-09
Ok, I'll mark this kernel stable under the **bleeding** section.

---

### Post by marguz on 2005-03-09
[QUOTE=jdong]You shouldn't need to -- that IS the Warty version of initrd-tools...


Does anyone else have this issue?[/QUOTE]


Yes, I as well just got that message. The only thing to do was to add the backports from debian

---

### Post by linux-nOOb on 2005-03-10
Hi all....first of all I would like to thank jdong and everyone else that is involved with BP's, it is incredible to watch you guys work.
 Today I upgraded my machine to the Kernel 2.6.10.19....the install went great.:)
Then I rebooted and logged in....low and behold I found my computer speaking to me in a language that I'm not familiar with.(German or Chekz? Buro for Office). Anyway I'm new to Linux and I can't find the config file to change back to Eng.
I checked the gdm.conf but can't find any language settings. When I log in I've 
tried the language settings, setting it to POSIX/Eng. No joy! 
 Any help would be greatly appreciated.
Thnx,
linux-nOOb

---

### Post by jdong on 2005-03-12
Ok, initrd tools -- the "~" version suffix messes up the dependencies... I'll most likely have to rebuild the package with a bumped down initrd-tools dependency.

As far as the language problem, add "lang=us" to your boot parameters, and see if the problem persists. I have no explanation for this problem!

---

### Post by jdong on 2005-03-12
Wow, Hoary's up to revision 27 now. I'll investigate the changelog, but most likely this will warrant a new backport!

---

### Post by popeye on 2005-03-15
[QUOTE=om007]Dear Ubuntu Gurus

just installed Ubuntu yesterday on my Compaq EVO n610c and getting in trouble with the fan not working ... one guy said he resolved this issue by installing 2.6.10 kernel ..


So i tried installing the backport but Synaptic fails with 

linux-image-2.6.10-3-686:
  Depends: initrd-tools but 0.1.70ubuntu9 is to be installed

but when i check for initrd-tools it says this version is already installed !!!
[/QUOTE]

I encountered the same problem it lies in the repositories you have dedicated and in the difference between the screenreport and the actual depends i think it's a bug in the kernel deb package.:

You need to have initrd-tools (>=0.175ubuntu2) which is in the repository:

[http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)  warty-backports-staging main

So include :
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports bleeding 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)  warty-backports-staging main

in your /etc/apt/sources.list and rerun the whole thing. That should do it.

---

### Post by Miggy on 2005-03-15
Hi,

after having installed 2.6.10-3-686 I have the problem, that my usb-stick isn't mounted automatically any longer. udev still creates the dev nodes for the usb-stick but than nothing else happens.

When I plug in my CF-memory-Card in my card reader then no event is triggered any longer notifying that the card is plugged in and so no dev nodes are created by udev.

Both things had worked with 2.6.8.
I'm still kind of a linux newbie, so suggestions would be appreciated  8-[ 

Now I had to realize that my usb printer also doesn't work any longer, also it is listed with lsusb  :neutral: 

Thanks in advance
Miggy

---

### Post by om007 on 2005-03-24
Thanks to the help in this forum ,i added the two lines proposed by popeye and others and  i finally upgraded my n610c to the last backport version and the upgrade went smoothly ..

regards

Om007

---

