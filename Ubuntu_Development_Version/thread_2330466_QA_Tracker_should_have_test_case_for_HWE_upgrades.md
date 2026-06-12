---
title: "QA Tracker should have test case for HWE upgrades"
date: 2016-07-11
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2016-07-11
As the title says:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1602066](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1602066)

If you agree jump on the bandwagon :guitar:

---

### Post by kansasnoob on 2016-07-22
Just thinking out loud here so be kind :)

Judging from how this was handled in Precise:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

I'm guessing the reasonable thing to do since no clear test procedure exists for this is to install your chosen flavor of Trusty daily which will have trusty-proposed enabled by default. Then watch for the lts-xenial bits of linux kernel and xserver to land as well as watching the changelog for updates to update-manager-core and as soon as we see hwe-support-status land we could see what happens with fresh installs of 14.04.2, 14.04.3, and 14.04.4 after they're fully updated and proposed is enabled.

So what I plan on trying is:

Step #1: Install Ubuntu Trusty daily (I figure it's best to start with Ubuntu itself, then I can repeat on my chosen flavor if it works).

Step #2: Update daily watching for the lts-xenial HWE to land and importantly watching the changelogs for 'update-manager-core' or anything remotely related to updates watching for hwe-support-status to land.

Step #3: When the lts-xenial HWE bits and hwe-support-status lands in 'update-manager-core' I'll boot into a fully updated 14.04.2, 14.04.3, or 14.04.4, enable proposed, and upgrade 'update-manager-core'. Then I'll see if the HWE upgrade is offered. 

Alternative to step #3: If all the lts-xenial HWE bits seem to have fallen in my Trusty daily install I might try what was suggested in Precise:

```
sudo apt-get install bzr -y
cd ~
bzr co --lightweight  lp:~mvo/update-manager/hwe-support-status
cd hwe-support-status
./hwe-support-status --verbose
```

I've never used bzr before but what's the worst that could happen?

---

### Post by kansasnoob on 2016-07-27
Does anyone understand this complaint:

```
lance@lance-desktop:~$ bzr co --lightweight  lp:~mvo/update-manager/hwe-support-status
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".

```

I have my dunce cap on and don't quite understand:

```
lance@lance-desktop:~$ bzr help launchpad-login
Purpose: Show or set the Launchpad user ID.
Usage:   bzr launchpad-login [NAME]

Options:
  --usage        Show usage message and options.
  --no-check     Don't check that the user name is valid.
  -q, --quiet    Only display errors and warnings.
  -v, --verbose  Display more information.
  -h, --help     Show help message.

Description:
  When communicating with Launchpad, some commands need to know your
  Launchpad user ID.  This command can be used to set or show the
  user ID that Bazaar will use for such communication.

Examples:
  Show the Launchpad ID of the current user:

      bzr launchpad-login

  Set the Launchpad ID of the current user to 'bob':

      bzr launchpad-login bob

Aliases:  lp-login
From:     plugin "launchpad"

```

---

### Post by kansasnoob on 2016-07-27
Regardless that does work:

```
lance@lance-desktop:~/hwe-support-status$ ./hwe-support-status --verbose
Your Hardware Enablement Stack (HWE) is supported until April 2017.

```

But I'm in hopes the GUI tool will show up with an updated update-manager-core in trusty-proposed.

---

### Post by kansasnoob on 2016-07-27
I was reading the man page for do-release-upgrade and I think adding the -p suffix may work (haven't tested yet) but I'm not sure how to do the same with the update-manager UI ............................ maybe as simple as 'update-manager -p'????????

---

### Post by ventrical on 2016-07-27
> **kansasnoob said:**
> Just thinking out loud here so be kind :)

Judging from how this was handled in Precise:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

I'm guessing the reasonable thing to do since no clear test procedure exists for this is to install your chosen flavor of Trusty daily which will have trusty-proposed enabled by default. Then watch for the lts-xenial bits of linux kernel and xserver to land as well as watching the changelog for updates to update-manager-core and as soon as we see hwe-support-status land we could see what happens with fresh installs of 14.04.2, 14.04.3, and 14.04.4 after they're fully updated and proposed is enabled.

So what I plan on trying is:

Step #1: Install Ubuntu Trusty daily (I figure it's best to start with Ubuntu itself, then I can repeat on my chosen flavor if it works).



@kanasanoob

Does this mean any flavour or specifically ubuntu-desktop?

Regards..

---

### Post by kansasnoob on 2016-07-27
> **ventrical said:**
> @kanasanoob

Does this mean any flavour or specifically ubuntu-desktop?

Regards..

I'm not sure if all flavors participated in the LTS HWE thing. I see that Lubuntu did:

[http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/)

[http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/trusty-desktop-amd64.manifest](http://cdimage.ubuntu.com/lubuntu/trusty/daily-live/current/trusty-desktop-amd64.manifest)

I can tell by linux-generic-lts-xenial and xserver-xorg-core-lts-xenial. There are other lts-xenial parts to the HWE stack but that tells me they did opt in.

Installs performed with 14.04 and 14.04.1 media won't be affected. Only installs performed with 14.04.2, 14.04.3, and 14.04.4 will have to deal with HWE EOL.

---

### Post by ventrical on 2016-07-27
I downloaded an image today.

---

### Post by kansasnoob on 2016-08-04
Since ubuntu-release just announced the release of 14.04.5 I booted into a fully updated 14.04.2 (Trusty with Utopic HWE) and I notice the awaited update for update-manager*:

> update-manager (1:0.196.15) trusty-proposed; urgency=medium

  * Include HWE support tools and information. (LP: #1498059)

 -- Brian Murray <email address hidden> Mon, 18 Jul 2016 10:03:22 -0700

Appears that 3 packages need upgrading but just enabling proposed and then running apt-get install update-manager should get us the needed tools:

```
lance@lance-desktop:~$ sudo apt-get install update-manager -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python3-update-manager update-manager-core
The following packages will be upgraded:
  python3-update-manager update-manager update-manager-core
3 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Inst python3-update-manager [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all]) [update-manager-core:i386 ]
Inst update-manager-core [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all]) [update-manager:i386 ]
Inst update-manager [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf python3-update-manager (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf update-manager-core (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf update-manager (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])

```

So I'm guessing I'll try:

Step #1: Install and fully update 14.04.2, 14.04.3, or 14.04.4. (a reboot will be needed)

Step #2: Enable proposed, run apt-get update, and run apt-get install update-manager.

Step #3: Disable proposed and run apt-get update.

Step #4: See what happens if I run either update-manager -p or update-manager -d -c.

Does that even remotely make sense?

---

### Post by kansasnoob on 2016-08-04
Nope, tried with and without proposed enabled but no HWE EOL upgrade is offered, only the Trusty -> Xenial upgrade. I think I'll try and stir up some trouble on ubuntu-release. I get the impression that most of the devs I work with over there already think I'm a huge pain in the nether regions so what do I have to lose :redface:

---

### Post by ventrical on 2016-08-05
> **kansasnoob said:**
> Since ubuntu-release just announced the release of 14.04.5 I booted into a fully updated 14.04.2 (Trusty with Utopic HWE) and I notice the awaited update for update-manager*:



Appears that 3 packages need upgrading but just enabling proposed and then running apt-get install update-manager should get us the needed tools:

```
lance@lance-desktop:~$ sudo apt-get install update-manager -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python3-update-manager update-manager-core
The following packages will be upgraded:
  python3-update-manager update-manager update-manager-core
3 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Inst python3-update-manager [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all]) [update-manager-core:i386 ]
Inst update-manager-core [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all]) [update-manager:i386 ]
Inst update-manager [1:0.196.14] (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf python3-update-manager (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf update-manager-core (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])
Conf update-manager (1:0.196.15 Ubuntu:14.04/trusty-proposed [all])

```

So I'm guessing I'll try:

Step #1: Install and fully update 14.04.2, 14.04.3, or 14.04.4. (a reboot will be needed)

Step #2: Enable proposed, run apt-get update, and run apt-get install update-manager.

Does that even remotely make sense?


 [s]I have to ask .. who is the intended audience? I don't get it. These are things that only a migration assistant or other slightly more experienced noob would know. So my followup question is: Will this process be eventually automated without having to enable proposed ? or am I really missing somthing here ?[/s]

Regards..

---

### Post by ventrical on 2016-08-05
> **kansasnoob said:**
> Nope, tried with and without proposed enabled but no HWE EOL upgrade is offered, only the Trusty -> Xenial upgrade. I think I'll try and stir up some trouble on ubuntu-release. I get the impression that most of the devs I work with over there already think I'm a huge pain in the nether regions so what do I have to lose :redface:

OK.. gottchya. Same here .

Regards..

---

### Post by kansasnoob on 2016-08-05
I done it:

[https://lists.ubuntu.com/archives/ubuntu-release/2016-August/003843.html](https://lists.ubuntu.com/archives/ubuntu-release/2016-August/003843.html)

That elicited a number of responses at my bug report and I tried an HWE upgrade today (I was notified by update-notifier automatically since I'd updated update-manager from trusty-proposed yesterday). So i was able to perform my first test which failed spectacularly:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1610434](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1610434)

This exemplifies one of my greatest frustrations - the devs assuming that automated testing is enough. Sorry to say, it's NOT!

Hopefully with that one early bug report the bleeding will be minimal :(

---

### Post by ventrical on 2016-08-05
I received a regular update on a production install of Trusty Ubuntu-Desktop (which was previously 1.4.04.4) 

 I did not receive any notification of  an HWE upgrade but there was an <ubuntu-base> upgrade package that came along with all the other upgrades and now:

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-MS-7798:~$ 


```

so I assume the automated updates are working as I did not have any problems on reboot and I did not have to enable proposed.

Regards..

---

### Post by mc4man on 2016-08-05
Seems to me the whole ecosystem of lts is a bit broken. For example users of nvidia drivers thru nvidia-prime should be warned that a HWE upgrade, (mesa 11.x) will cause them to boot to a black screen (normal boot but display is disabled.
 A lot of head in the sand behaviour as the fact that this would happen has been known for 10 months.

Another is that while users are provided a newer kernel there is no lts version of linux-firmware so some advantages of that kernel are not available to those that might benefit.

I'd recommend that in most cases for 14.04 that users with hardware prior to 14.04 release stick with 14.04.1 
(- unless there was deficient support for their hardware in the 14.04.1 kernel

---

### Post by ventrical on 2016-08-05
> **mc4man said:**
> Seems to me the whole ecosystem of lts is a bit broken. 

+1

---

### Post by mc4man on 2016-08-05
Started a new bug on this (with a little sleigh of hand already confirmed, ect...
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1610476](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1610476)

---

### Post by kansasnoob on 2016-08-05
> I'd recommend that in most cases for 14.04 that users with hardware prior to 14.04 release stick with 14.04.1
(- unless there was deficient support for their hardware in the 14.04.1 kernel 

Absolutely right! 

That's why I said this [here]("https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066"):

> I began saving a list of web links of problems encountered when Precise users were notified of HWE EOL in anticipation of recommending that we amend our download page to recommend users always try the first point release. I chose not to do that because the 14.04.1 images were affected by [bug #1265192]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") which could result in data loss. (That may be worth pursuing prior to 16.04.2 but that's a whole different issue).

Before 16.04.2 is released I'll file a bug report. The download page would only have to add a few lines of text and an additional download link or two. It would be extremely easy to just prominently say:

Many users may prefer using the archived 16.04.1 images to avoid HWE EOL. For more info see - insert pertinent link(s) here.

---

### Post by kansasnoob on 2016-08-05
> **ventrical said:**
> I received a regular update on a production install of Trusty Ubuntu-Desktop (which was previously 1.4.04.4) 

 I did not receive any notification of  an HWE upgrade but there was an <ubuntu-base> upgrade package that came along with all the other upgrades and now:

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-MS-7798:~$ 


```

so I assume the automated updates are working as I did not have any problems on reboot and I did not have to enable proposed.

Regards..

Right, because it rolled to 14.04.5 as soon as 14.04.5 was released but the OS remains on the same HWE stack that existed during installation. I'm doing another test now with bog standard Ubuntu to see if my one bad experience may have been limited to Ubuntu GNOME. I'll let you know exactly what I have to do to trigger the HWE EOL prompt and upgrade.

---

### Post by ventrical on 2016-08-06
> **kansasnoob said:**
> Right, because it rolled to 14.04.5 as soon as 14.04.5 was released but the OS remains on the same HWE stack that existed during installation. I'm doing another test now with bog standard Ubuntu to see if my one bad experience may have been limited to Ubuntu GNOME. I'll let you know exactly what I have to do to trigger the HWE EOL prompt and upgrade.

To be perfectly honest I too have an 14.04.4 install of gnome-desktop but I tried your method, I downloaded the update-manager file from proposed and then I chickened out. Also , the upgrades were there and now they are not there... so I will just go ahead and see what happens.  Your experience on these upgrade issues is a little more advanced than most , including me, so I am trying to improvise .. so my apologies if I am off topic.

regards..

---

### Post by mc4man on 2016-08-06
I got the notice but clicking on install caused a crash for no really clear reason..
This install is 14.04.3

---

### Post by ventrical on 2016-08-06
Got this after upgrade of gnome-desktop.

```

ventrical@ventrical-amd642x6000:~$ hwe-support-status --verbose
You are not running a system with a Hardware Enablement Stack. Your system is supported until April 2019.
ventrical@ventrical-amd642x6000:~$ 


```


```

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-amd642x6000:~$ 


```

---

### Post by kansasnoob on 2016-08-06
> **ventrical said:**
> Got this after upgrade of gnome-desktop.

```

ventrical@ventrical-amd642x6000:~$ hwe-support-status --verbose
You are not running a system with a Hardware Enablement Stack. Your system is supported until April 2019.
ventrical@ventrical-amd642x6000:~$ 


```


```

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-amd642x6000:~$ 


```

Please post the output of:

```
cat /var/log/installer/media-info
```

And:

```
ls /boot
```

---

### Post by kansasnoob on 2016-08-06
> **mc4man said:**
> I got the notice but clicking on install caused a crash for no really clear reason..
This install is 14.04.3

Wonderful, eh?

Who would have thought such upgrades didn't need an actual test procedure to help ensure a somewhat painless experience?

Something that irks me is that the lts-xenial HWE is failing on hardware that run Xenial and fresh installs of 14.04.5 just fine. So maybe when people start reporting HWE upgrade failures they could just do-release-upgrade and see if Xenial works before backing everything up and going for a fresh install of 14.04.1??????

Regardless, it's "here we go again" time.

---

### Post by ventrical on 2016-08-07
> **kansasnoob said:**
> Please post the output of:

```
cat /var/log/installer/media-info
```

And:

```
ls /boot
```

```

ventrical@ventrical-amd642x6000:~$ cat /var/log/installer/media-info
Ubuntu-GNOME 14.04 LTS "Trusty Tahr" - Release amd64 (20140416.2)ventrical@ventrical-amd642x6000:~$ 


```

```
 ls /boot
abi-3.13.0-24-generic         initrd.img-3.13.0-93-generic
abi-3.13.0-63-generic         memtest86+.bin
abi-3.13.0-85-generic         memtest86+.elf
abi-3.13.0-91-generic         memtest86+_multiboot.bin
abi-3.13.0-93-generic         System.map-3.13.0-24-generic
config-3.13.0-24-generic      System.map-3.13.0-63-generic
config-3.13.0-63-generic      System.map-3.13.0-85-generic
config-3.13.0-85-generic      System.map-3.13.0-91-generic
config-3.13.0-91-generic      System.map-3.13.0-93-generic
config-3.13.0-93-generic      vmlinuz-3.13.0-24-generic
grub                          vmlinuz-3.13.0-63-generic
initrd.img-3.13.0-24-generic  vmlinuz-3.13.0-85-generic
initrd.img-3.13.0-63-generic  vmlinuz-3.13.0-91-generic
initrd.img-3.13.0-85-generic  vmlinuz-3.13.0-93-generic
initrd.img-3.13.0-91-generic
ventrical@ventrical-amd642x6000:~$ 


```

---

### Post by kansasnoob on 2016-08-07
> **ventrical said:**
> ```

ventrical@ventrical-amd642x6000:~$ cat /var/log/installer/media-info
Ubuntu-GNOME 14.04 LTS "Trusty Tahr" - Release amd64 (20140416.2)ventrical@ventrical-amd642x6000:~$ 


```

```
 ls /boot
abi-3.13.0-24-generic         initrd.img-3.13.0-93-generic
abi-3.13.0-63-generic         memtest86+.bin
abi-3.13.0-85-generic         memtest86+.elf
abi-3.13.0-91-generic         memtest86+_multiboot.bin
abi-3.13.0-93-generic         System.map-3.13.0-24-generic
config-3.13.0-24-generic      System.map-3.13.0-63-generic
config-3.13.0-63-generic      System.map-3.13.0-85-generic
config-3.13.0-85-generic      System.map-3.13.0-91-generic
config-3.13.0-91-generic      System.map-3.13.0-93-generic
config-3.13.0-93-generic      vmlinuz-3.13.0-24-generic
grub                          vmlinuz-3.13.0-63-generic
initrd.img-3.13.0-24-generic  vmlinuz-3.13.0-85-generic
initrd.img-3.13.0-63-generic  vmlinuz-3.13.0-91-generic
initrd.img-3.13.0-85-generic  vmlinuz-3.13.0-93-generic
initrd.img-3.13.0-91-generic
ventrical@ventrical-amd642x6000:~$ 


```

Right, see the iso date:

```
Ubuntu-GNOME 14.04 LTS "Trusty Tahr" - Release amd64 (**[COLOR="#FF0000"]20140416.2[/COLOR]**)
```

That's April 2014, so the installation media was original 14.04 which shipped with the 3.13 series kernel and it's supported all the way thru until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Only those who installed using the 14.04.2, 14.04.3, and 14.04.4 media will be effected by HWE EOL.

---

### Post by ventrical on 2016-08-07
> **kansasnoob said:**
> Right, see the iso date:

```
Ubuntu-GNOME 14.04 LTS "Trusty Tahr" - Release amd64 (**[COLOR=#FF0000]20140416.2[/COLOR]**)
```

That's April 2014, so the installation media was original 14.04 which shipped with the 3.13 series kernel and it's supported all the way thru until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Only those who installed using the 14.04.2, 14.04.3, and 14.04.4 media will be effected by HWE EOL.

Ok.. now I remember. Thanks for clearing that up.

regards..

---

### Post by kansasnoob on 2016-08-08
Just thinking out loud here about suggesting to users that they may wish to use the first point release images when the 2nd, 3rd, and 4th point releases are released to avoid HWE EOL. I'd originally thought about editing the download page but if you start here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Then click hover on Download you get a number of options including a link to flavors. If you click on Desktop you get here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

For server here:

[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

In either of those cases adding such a suggestion just doesn't seem to fit in well :(

But we do prominently point to the Release Notes. So I think that info would be best added to the Release Notes for the 2nd, 3rd, and 4th point releases. As an example look at the 14.04.4 Release Notes:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.4](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.4)

HWE is mentioned but it's quite a ways down in the Release notes so maybe right at the beginning this should be edited:

> **Introduction**

These release notes for Ubuntu 14.04.4 (Trusty Tahr) provide an overview of the release and document the known issues with Ubuntu 14.04.4 and its flavors. For details of the changes applied since 14.04.3, please see the 14.04.4 change summary. The release notes for 14.04, 14.04.1, 14.04.2, and 14.04.3 are available as well. 

Just adding a small bit (using 16.04.2 as an example):

> **Introduction**

These release notes for Ubuntu 16.04.2 (Xenial Xerus) provide an overview of the release and document the known issues with Ubuntu 16.04.2 and its flavors. For details of the changes applied since 16.04.1, please see the 16.04.2 change summary. The release notes for 16.04, and 16.04.1 are available as well. 

[COLOR="#0000FF"]Since Ubuntu 16.04.2 employs a LTS Hardware Enablement Stack some users may wish to use the 14.04.1 installation media to avoid HWE EOL in August 2018. Please read the section on LTS Hardware Enablement below.[/COLOR]

And I think that section should more thoroughly explain HWE EOL. As [Steve Langasek pointed out here]("https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066/comments/5") (more than once) "It is not guaranteed that all hardware will be supported after switching HWE stacks". So we should be sure users know that when installing an LTS, and then finding out later that they're screwed :(

---

### Post by kansasnoob on 2016-08-15
I see that Ubuntu server 16.04 is going to offer the HWE downloads only as an option:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus)

> **Ubuntu 16.04 LTS - Xenial Xerus**

The 16.04.2 and newer point releases will ship with an updated kernel and X stack by default for the desktop. Server installations will default to the GA kernel and provide the enablement kernel as optional.



I think desktop versions (and flavors) should do the same. Basically use the HWE versions only if the OEM kernel and X-stack don't work on your hardware.

---

