---
title: "Xubuntu Core 16.04 installer"
date: 2016-03-25
forum: Ubuntu Development Version
---

### Post by egeezer on 2016-03-25
I'm trying to find a workaround for the installer bug in the Xubuntu Core 16.04 ISO that didn't permit creating a swap partition in the alpha version.  I took a chance and downloaded the beta 2 ISO of it, hoping the bug was fixed, but apparently it is still there.
 


 Some weeks ago I did find a thread that answered this question, but somehow I can't seem to find a search filter that brings up that specific thread, or any that address exactly what I'm after.
 

 Any help will be welcomed with great appreciation!

  	 	 	 	   Edited to add: just looked at Launchpad, and the workaround there (delete swap partition, recreate it) doesn't work either.  Do I recall that the Nvidia driver might have been related to it (or is that evidence of another Senior Moment for me?)

---

### Post by mörgæs on 2016-03-26
> **egeezer said:**
> just looked at Launchpad, and the workaround there ... 

Please post the link.

---

### Post by egeezer on 2016-03-26
Sorry, I should have done that.  Here it is:

                        [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1552539](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1552539)
  
There is also an earlier report of what appears to be the same bug in earlier versions of the installer:

                        [https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/990744](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/990744)
 
  I'm attempting to install Xubuntu Core 16.04 as a dual boot with 14.04.  I did install Xubuntu Core 15.10 successfully that way.  Both the ISOs were from Unit193, so I don't know what changed in the installer portion.

I'm reluctant to use the full version, since Core lets me install only what I really use.  Not to mention the fact that my slow connection is maddening to use for gigabyte-plus ISOs!

---

### Post by kansasnoob on 2016-03-26
I have not found a reliable work around for that bug.

---

### Post by Bucky Ball on 2016-03-26
If you have other installs you don't need to create a /swap. Choose 'something else' at install and mark the existing 14.04 /swap to use, doesn't matter if it's ticked to format. 

That's a workaround. I installed 16.04 LTS without issue this way as I already had 15.04 installed and just used that /swap so wasn't aware of this bug til now. :)

---

### Post by egeezer on 2016-03-26
> **Bucky Ball said:**
> If you have other installs you don't need to create a /swap. Choose 'something else' at install and mark the existing 14.04 /swap to use, doesn't matter if it's ticked to format. 


I did exactly that on one of the three tries I made. It went as far as setting up signin credentials, but just as the installation began I got the "Something went wrong, automatically supply a bug report" announcement.

Tries so far: two with "something else", one with "beside each other" and a clean partition available.

I'm not experienced enough to cook up a new scheme, so I might just be patient and wait until it gets fixed.  Also note that according to the latest full beta 2 release the installer problem persists throughout the Ubuntu family.

---

### Post by kansasnoob on 2016-03-26
I have a dumb question that I hadn't thought of until now :redface:

If this is an Xubuntu core install are you using the netboot images:

[http://cdimage.ubuntu.com/netboot/xenial/](http://cdimage.ubuntu.com/netboot/xenial/)

Or have I misunderstood?

If you're using the netboot images  then this bug affects the debian-installer (aka; d-i) as well as ubiquity.

---

### Post by egeezer on 2016-03-26
Not netboot - I'm using the Xubuntu Core ISO from Unit193's site

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

The ones for 15.04 and 15.10 installed well (15.10 in both 64- and 32-bit)

---

### Post by kansasnoob on 2016-03-26
Those are not official Xubuntu images and according to the package manifest don't even use ubiquity:

[https://unit193.net/xubuntu/core/pending/xubuntu-16.04-core-i386.iso.manifest](https://unit193.net/xubuntu/core/pending/xubuntu-16.04-core-i386.iso.manifest)

So you should contact them about the issue with their installer. It certainly may be our upstream bug affecting their installer but we have no way of knowing.

---

### Post by kansasnoob on 2016-03-26
I see they do have instructions for installing Xubuntu core the official way using the aforementioned netboot iso:

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

---

### Post by egeezer on 2016-03-26
> **kansasnoob said:**
> I see they do have instructions for installing Xubuntu core the official way using the aforementioned netboot iso:

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

I used that with 15.04 when it came out. I think I won't pester Mr or Ms Unit193 about it - it certainly appears that the Ubiquity installer is what is used, so I'll wait for big news from upstream.

Thanks to both of you for the assistance, and thanks kansasnoob for a pleasant chat!:D

---

### Post by Bucky Ball on 2016-03-26
You could also install 14.04 LTS by installing the minimal install and choosing Xubuntu-core from the tasksel screen when you get to it. There's a link to how to do that on the Xubuntu-core intro page (not the Unit193 page). Worth a shot with 16.04? Try the 16.04 LTS minimal ISO and choose Xubuntu-core from tasksel? Maybe have the same bug, though. :-k

---

