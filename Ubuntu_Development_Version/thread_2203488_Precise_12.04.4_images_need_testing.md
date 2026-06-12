---
title: "Precise 12.04.4 images need testing"
date: 2014-02-03
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-02-03
This is for those who just love to test :guitar:

The 12.04.4 images are now available for testing:

[http://iso.qa.ubuntu.com/qatracker/milestones/311/builds](http://iso.qa.ubuntu.com/qatracker/milestones/311/builds)

These images include the Saucy Hardware Enablement Stack as well as a couple of 'ubiquity' bug fixes.

So, if you're inclined, please test and report :D

---

### Post by ventrical on 2014-02-04
Thnx noob ! :)

---

### Post by kansasnoob on 2014-02-04
Rebuilt just hours ago:

```
lance@lance-desktop:~/Downloads/Ubuntu$ zsync http://cdimage.ubuntu.com/precise/daily-live/20140204/precise-desktop-i386.iso.zsync
#################### 100.0% 380.1 kBps DONE     

reading seed file precise-desktop-i386.iso: ************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read precise-desktop-i386.iso. Target 94.0% complete.      
downloading from http://cdimage.ubuntu.com/precise/daily-live/20140204/precise-desktop-i386.iso:
#################### 100.0% 632.0 kBps DONE      

verifying download...checksum matches OK
used 720433152 local, fetched 46664462

```

---

### Post by ventrical on 2014-02-04
> **kansasnoob said:**
> Rebuilt just hours ago:

```
lance@lance-desktop:~/Downloads/Ubuntu$ zsync http://cdimage.ubuntu.com/precise/daily-live/20140204/precise-desktop-i386.iso.zsync
#################### 100.0% 380.1 kBps DONE     

reading seed file precise-desktop-i386.iso: ************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read precise-desktop-i386.iso. Target 94.0% complete.      
downloading from http://cdimage.ubuntu.com/precise/daily-live/20140204/precise-desktop-i386.iso:
#################### 100.0% 632.0 kBps DONE      

verifying download...checksum matches OK
used 720433152 local, fetched 46664462

```

  I used /current/ instead of /20140204/.

 Anyways .. I have a few new convert/noobs and they are just amazed by some of the precise Unity2D features and I have been able to encourage some of these to try the testing branch. :)

---

### Post by ventrical on 2014-02-06
Just upgraded an existing copy of Precise. I used Update Manager and it failed ;)lol

  I then went to terminal and sudo upgraded there . Al went well.

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by oldfred on 2014-02-06
I still have 12.04.0, but with updates not distribution update. So still 3.2-xx kernels.
But it says I have 12.04.4.

I have notice that for several weeks all the BootInfo reports show 12.04.4 for all 12.04 versions.

```
fred@A105-Precise:~$ uname -a
Linux A105-Precise 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
fred@A105-Precise:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

So to really know what version a user is running you have to see which kernel it still has.

---

### Post by ventrical on 2014-02-06
> **oldfred said:**
> I still have 12.04.0, but with updates not distribution update. So still 3.2-xx kernels.
But it says I have 12.04.4.

I have notice that for several weeks all the BootInfo reports show 12.04.4 for all 12.04 versions.

```
fred@A105-Precise:~$ uname -a
Linux A105-Precise 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
fred@A105-Precise:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

So to really know what version a user is running you have to see which kernel it still has.

Ahhh .. yes .. I'll check that now.

 Also have the .iso and plan to test that tommorrow.

Regards..

---

### Post by ventrical on 2014-02-06
Here...  but November ??

```

ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:20:03 UTC 2013 i686 i686 i386 GNU/Linux
ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
ventrical@ventrical-MS-7798:~$ 


```

---

### Post by ventrical on 2014-02-06
I used synaptic to install the latest kernel and it was strange because it downloaded two sets of kernels. One mentioning somthing about generic-lts-quantal.

```

ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 3.5.0-45-generic #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 i686 i686 i386 GNU/Linux
ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
ventrical@ventrical-MS-7798:~$ 



```


So this is still not it ?

perhaps I'll run the live image that kansasnoob is refering to.

---

### Post by cariboo on 2014-02-06
I'm running the 3.2.0-58 kernel on my server, I haven't done a dist-upgrade since the last point release, but it shows 12.04.4 on the mtod when logging into the server:

```
uname -a
Linux willy 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

---

### Post by kansasnoob on 2014-02-06
I'm just sticking with the Precise kernel and X-stack on my production machines because of the convoluted LTS Hardware Enablement Stack process:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by kansasnoob on 2014-02-06
Release announcement is here:

[https://lists.ubuntu.com/archives/ubuntu-announce/2014-February/000180.html](https://lists.ubuntu.com/archives/ubuntu-announce/2014-February/000180.html)

Release Notes are here:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by ventrical on 2014-02-07
Here is the  new live .iso that kansasnoob originally refered to in his first post requesting testing.

```

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ 


```

So it is now using  3.11.0-15 kernel. Works like a breeze! Never saw a USB load so fast. Just beautiful work. Also you will notice where the .iso will show  Precise 12.04.4 LTS when using SDC where the other .isos will not.

Regards..

---

### Post by ventrical on 2014-02-07
> **cariboo907 said:**
> I'm running the 3.2.0-58 kernel on my server, I haven't done a dist-upgrade since the last point release, but it shows 12.04.4 on the mtod when logging into the server:

```
uname -a
Linux willy 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

The kernel is now 3.11.0-15 but it will not upgrade using standard terminal methods (that I have tried). It will only upgrade to that kernel if you use the release .iso.

---

### Post by kansasnoob on 2014-02-07
> **ventrical said:**
> The kernel is now 3.11.0-15 but it will not upgrade using standard terminal methods (that I have tried). It will only upgrade to that kernel if you use the release .iso.

Right, same as Saucy:

```
lance@lance-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"
lance@lance-desktop:~$ uname -a
Linux lance-desktop 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686 i686 i686 GNU/Linux

```

What behavior are you expecting?

Did you read this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

As I understand it the Saucy stack in Precise will be supported until 14.04.1 is released in August, of course many Ubuntu users will have already upgraded to 14.04 by then :)

---

### Post by kansasnoob on 2014-02-07
I just thought to add that the change from an 18 month support cycle to a 9 month support cycle for interim releases was not a knee-jerk process. While that was still being discussed Canonical decided to increase LTS desktop support to 5 years just as it has been for servers. Precise was the first release to employ this process.

So there are now two ongoing dev cycles, the interim cycle and the LTS point release cycle :)

This should be the last we hear of Precise in Ubuntu +1 because 12.04.4 was the last point release for Precise.

---

### Post by kansasnoob on 2014-02-07
> **cariboo907 said:**
> I'm running the 3.2.0-58 kernel on my server, I haven't done a dist-upgrade since the last point release, but it shows 12.04.4 on the mtod when logging into the server:

```
uname -a
Linux willy 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

Since there seems to some confusion between interim release dev and LTS dev maybe we need to cook up something like an "always on top" sticky :confused:

I have concerns because I know that the original LTS kernel and X-stack will be supported for the full five years, but my postings may actually lead someone to upgrade to unusable kernels or X-stacks :(

---

### Post by ventrical on 2014-02-07
> **kansasnoob said:**
> Since there seems to some confusion between interim release dev and LTS dev maybe we need to cook up something like an "always on top" sticky :confused:

I have concerns because I know that the original LTS kernel and X-stack will be supported for the full five years, but my postings may actually lead someone to upgrade to unusable kernels or X-stacks :(


  The new .iso still has an extreme prejudice for ATi Radeon Xpress1250 and Broadcomm Wireless. Even with 'nomodeset'  the PC reports a verbose fail and then locks up on my Acer Extensa 4420.(that means it locks up and you can't do anything. no Ctrl+Alt+F1, reboot .. nada. You have to hard shutdown and restart so you cannot report what the screen is spewing out). Haven't tried it yet on other boxes but I am confident it works just beautifully with Dell  nVidia and Intel sets.

Anyways .. I installed  Lubuntu Trusty Alpha but there is still these probs with the ATi graphics adapter.

What was that  that Ronac used to say; 'If it ain't broke, don't fix it!. :)
  

Regards..

---

### Post by zika on 2014-02-07
Did You try```
radeon.dpm=0
```as kernel-boot switch...?

---

### Post by ventrical on 2014-02-07
> **kansasnoob said:**
> Right, same as Saucy:

```
lance@lance-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"
lance@lance-desktop:~$ uname -a
Linux lance-desktop 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686 i686 i686 GNU/Linux

```

What behavior are you expecting?

Did you read this:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

As I understand it the Saucy stack in Precise will be supported until 14.04.1 is released in August, of course many Ubuntu users will have already upgraded to 14.04 by then :)


 I had assumed that a currently maintained hard install of Precise would  be upgraded through terminal using the sudo command process:

```

sudo apt-get update
sudo apt-get upgrade

```

 It currently  downloads generic-lts-quantal and updates it to that  3.5.x-45 kernel using the above process. The behaviour I had expected was that it would install the 3.11.0-15 kernel during the upgrade over the existing install.

Regards..

---

### Post by ventrical on 2014-02-07
> **zika said:**
> Did You try```
radeon.dpm=0
```as kernel-boot switch...?

No. Not out of the box. It will not work with nomodeset so I'll reinstall a side by side. Where do I edit that in?

Thanks in advance.

Regards..

btw ... using
```

 lshw 

```
does report that it is using the radeon driver.

---

### Post by zika on 2014-02-07
> **ventrical said:**
> No. Not out of the box. It will not work with nomodeset so I'll reinstall a side by side. Where do I edit that in?
Thanks in advance.
Regards..In kernel-boot-line in Grub (where You've put &#8222;nomodeset&#8220; and where most people find &#8222;quiet splash&#8220;)...

> **ventrical said:**
> 
btw ... using
```

 lshw 

```
does report that it is using the radeon driver.Yes, as it should... I guess, did not look for card You've mentioned. Since it is ATI, I presume, that is OK. I would not suggest any switch for radeon if I did not presume that radeon driver is in use...

---

### Post by ventrical on 2014-02-07
> **zika said:**
> In kernel-boot-line in Grub (where You've put „nomodeset“ and where most people find „quiet splash“)...

Yes, as it should... I guess, did not look for card You've mentioned. Since it is ATI, I presume, that is OK. I would not suggest any switch for radeon if I did not presume that radeon driver is in use...

Thanks very much.  I am going to try it anyways. I'll also take a second look at BIOS settings .

Regards..

---

### Post by kansasnoob on 2014-02-07
> **ventrical said:**
> I had assumed that a currently maintained hard install of Precise would  be upgraded through terminal using the sudo command process:

```

sudo apt-get update
sudo apt-get upgrade

```

 It currently  downloads generic-lts-quantal and updates it to that  3.5.x-45 kernel using the above process. The behaviour I had expected was that it would install the 3.11.0-15 kernel during the upgrade over the existing install.

Regards..

So you apparently installed using 12.04.2 media which shipped with the Quantal Hardware Enablement Stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

12.04.3 shipped with the Raring HWE Stack, and 12.04.4 shipped with the Saucy HWE Stack. It's all explained in that link :)

**[COLOR="#FF0000"]One warning though[/COLOR]**, I have NOT found a method for properly downgrading the HWE stacks! All attempts resulted in borkage so I'm just leaving my production machines on the original Precise kernel and X-stack.

---

### Post by ventrical on 2014-02-07
> **kansasnoob said:**
> So you apparently installed using 12.04.2 media which shipped with the Quantal Hardware Enablement Stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

12.04.3 shipped with the Raring HWE Stack, and 12.04.4 shipped with the Saucy HWE Stack. It's all explained in that link :)

**[COLOR=#FF0000]One warning though[/COLOR]**, I have NOT found a method for properly downgrading the HWE stacks! All attempts resulted in borkage so I'm just leaving my production machines on the original Precise kernel and X-stack.


  I disabled Boot on Lan and D2D in BIOS but I think that was not the problem. What I did was a trick we used during Precise dev iso ... Install from Live Unity  Session.  That set the video driver correctly with the latest iso release 12.04.4 LTS. There is still a problem installing Broadcom wireless drivers using the jockey but I know how to search the fix out for that and install them from terminal.  Bottom line .. nothing has changed in Ubiquity, it appears, for touchy machines although not all laptops or desktops behave this way.

---

### Post by joncochran on 2014-02-07
> **kansasnoob said:**
> 
**[COLOR=#FF0000]One warning though[/COLOR]**, I have NOT found a method for properly downgrading the HWE stacks! All attempts resulted in borkage so I'm just leaving my production machines on the original Precise kernel and X-stack.

I'd be happy with a method of properly upgrading the HWE stacks.  When I try to upgrade my 12.04.2 setup with the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy 
```

I get tons of unmet dependency errors, all of which revolve around the xserver packages.   For example (and this is just a snippet):

```
 xserver-xorg-lts-saucy : Depends: xserver-xorg-core-lts-saucy (>= 2:1.11) but it is not going to be installed
```

When I try to add those packages by adding them to my apt-get install command, I get to the heart of the matter.  Namely, those new packages conflict with the quantal packages which are currently installed.  For example:

```
libgl1-mesa-dri-lts-raring : Conflicts: xorg-renamed-package-lts-quantal:i386
```

Anyone have any insight to this...?

---

### Post by kansasnoob on 2014-02-07
> **joncochran said:**
> I'd be happy with a method of properly upgrading the HWE stacks.  When I try to upgrade my 12.04.2 setup with the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy 
```

I get tons of unmet dependency errors, all of which revolve around the xserver packages.   For example (and this is just a snippet):

```
 xserver-xorg-lts-saucy : Depends: xserver-xorg-core-lts-saucy (>= 2:1.11) but it is not going to be installed
```

When I try to add those packages by adding them to my apt-get install command, I get to the heart of the matter.  Namely, those new packages conflict with the quantal packages which are currently installed.  For example:

```
libgl1-mesa-dri-lts-raring : Conflicts: xorg-renamed-package-lts-quantal:i386
```

Anyone have any insight to this...?

How many times do I have to post the same link:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

You'll find the answer there ](*,)

'libgl1-mesa-glx-lts-*" packages MUST also be upgraded!

---

### Post by kansasnoob on 2014-02-07
This thread needs to be closed because 12.04.4 has been released and there will be no new images built.

General discussion of, or questions about Precise should be posted here:

[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

And, of course, bugs should be reported on Launchpad.

---

### Post by joncochran on 2014-02-07
> **kansasnoob said:**
> How many times do I have to post the same link:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

You'll find the answer there ](*,)

'libgl1-mesa-glx-lts-*" packages MUST also be upgraded!

Those *also* conflict with the quantal packages when I try to upgrade them.   Believe me, I've tried.  At one point I got up to:

```
 sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring xserver-xorg-core-lts-raring libgl1-mesa-dri-lts-raring libglapi-mesa-lts-raring libgl1-mesa-glx-lts-raring xserver-xorg-video-all-lts-raring
```

Which gave me this:

```
  libgl1-mesa-dri-lts-raring : Conflicts: xorg-renamed-package-lts-quantal:i386 libgl1-mesa-glx-lts-quantal:i386 : Recommends: libgl1-mesa-dri-lts-quantal:i386 (>= 7.2) but it is not going to be installed
```

I've got both libgl1-mesa-glx and libgl1-mesa-dri set to be installed, but they still conflict.


FWIW: The command on the wiki also fails with the same conflicts:

```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]

So, the trick was to do this and make sure I got both x86_64 and x86 libraries:

[/FONT][/COLOR]```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring [/FONT][/COLOR][COLOR=#333333][FONT=monospace]libgl1-mesa-glx-lts-raring:i386[/FONT][/COLOR]
```

---

### Post by kansasnoob on 2014-02-07
The first paragraph of the wiki says:

> In an effort to support a wider variety of hardware on an existing LTS release, the 12.04.2 and newer point releases will ship with an updated kernel and X stack by default. These newer hardware enablement stacks will be comprised of the newer kernel and X stacks from 12.10 (Quantal), 13.04 (Raring), 13.10 (Saucy), and 14.04 (Trusty). **[COLOR="#FF0000"]These enablement stacks are only intended for use on x86 hardware at this time.[/COLOR]** Those running virtual or cloud images should not need these newer enablement stacks and are thus recommended to remain on the original Precise stack. To remain on the original Precise stack there are a few options: 

---

### Post by joncochran on 2014-02-07
Eh...   isn't x86_64 technically x86?   If I were to install the latest 12.04.4 via CD, wouldn't I get the latest HWE?

It's OK... you can say yes.  :)

---

### Post by kansasnoob on 2014-02-08
> **joncochran said:**
> Eh...   isn't x86_64 technically x86?   If I were to install the latest 12.04.4 via CD, wouldn't I get the latest HWE?

It's OK... you can say yes.  :)

OK, yes, I guess. But 12.04.4 has now been released so support questions should be asked here:

[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

If a bug is encountered it should be filed at Launchpad.

The purpose of this thread was to let people know that QA testing of the 12.04.4 candidates was underway, but it's now been released so any further discussion of 12.04.4 is inappropriate in Ubuntu +1 ;)

In other news it now appears likely that there will be a 12.04.5 which will ship with the Trusty HWE stack:

[https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038042.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038042.html)

Seems sensible to me.

---

### Post by Bucky Ball on 2014-02-08
> **kansasnoob said:**
> 

The purpose of this thread was to let people know that QA testing of the 12.04.4 candidates was underway, but it's now been released so any further discussion of 12.04.4 is inappropriate in Ubuntu +1 ;)

*Thread closed.*

---

