---
title: "Daily iso's"
date: 2024-03-31
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2024-03-31
Why are there no more dailies. the last current is from March 23rd and pending is still from March 25th., yet both current and pending are dated March 28th.

Henry

---

### Post by dajonaga on 2024-03-31
Maybe because of the xz-utils debacle

[https://arstechnica.com/security/2024/03/backdoor-found-in-widely-used-linux-utility-breaks-encrypted-ssh-connections/](https://arstechnica.com/security/2024/03/backdoor-found-in-widely-used-linux-utility-breaks-encrypted-ssh-connections/)

[https://openssf.org/blog/2024/03/30/xz-backdoor-cve-2024-3094/](https://openssf.org/blog/2024/03/30/xz-backdoor-cve-2024-3094/)

[https://www.cisa.gov/news-events/alerts/2024/03/29/reported-supply-chain-compromise-affecting-xz-utils-data-compression-library-cve-2024-3094](https://www.cisa.gov/news-events/alerts/2024/03/29/reported-supply-chain-compromise-affecting-xz-utils-data-compression-library-cve-2024-3094)

---

### Post by Hewjr100 on 2024-03-31
What a mess, I hope it gets sorted out soon.

Gort

---

### Post by zebra2 on 2024-03-31
> **Hewjr100 said:**
> What a mess, I hope it gets sorted out soon.

Gort

Since Noble 24.04 is a development release "soon" is defined as April 27th.  Canonical can't supply a daily without a working installer minimum.   Everything is being upgraded right now.  If you per chance don't have the patience for this I suggest you install Ubuntu Mantic until Noble releases.  Mantic is an outstanding release and will easily upgrade to Noble when it releases. Also, it is possible the 24.04  release could miss it's release date.  This has happened in the past when there are problems.

---

### Post by corradoventu on 2024-03-31
Build of ISO has been failing for a few days: [https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/noble/ubuntu](https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/noble/ubuntu)

---

### Post by guiverc on 2024-03-31
I did note (*mentioned on IRC if I recall correctly; #ubuntu-release*) the focus was on xz effects this weekend, and not any build failures for *noble*.

I noted yesterday my *mate-desktop* still has issues on this box, no doubt that package issue (*time_t64*) would prevent a Ubuntu-MATE build, so the focus on xz no doubt will help the time_t64 builds anyway.

(*note: locally today (1 April 2024) is a public holiday, and thus may qualify, at least to me, as part of the 'weekend' reference on #ubuntu-release*)

---

### Post by Hewjr100 on 2024-04-06
From what I see it looks like Noble is going to be delayed again.  I see nothing showing any progress with this xz situation.

Henry

---

### Post by corradoventu on 2024-04-06
I'm running Noble on my PC and many updated packages arrive every day. About 300 packages in 2 days.

---

### Post by #&amp;thj^% on 2024-04-06
> **corradoventu said:**
> I'm running Noble on my PC and many updated packages arrive every day. About 300 packages in 2 days.

Same here lots coming in to play now.

The Daily Iso's have been stuck on this date 2024-03-28 03:56, they will  in due time push a newer one when ready.

---

### Post by Irihapeti on 2024-04-06
I would far rather they took their time over the xz cleanup than rush things and get us all into trouble. At least, it doesn't look like being a two-month delay as per 6.06 :)

I do see that there are some ARM images coming through, so if you have a RPi or ARM VM, that's always an option.

---

### Post by ajgreeny on 2024-04-06
I remember well that delay of 6.04 which when it finally appeared as 6.06 was a major step and certainly provided us with an excellent version of the default gnome-2 Ubuntu; one of the best at that time if my memory serves me correctly.

I didn't use Xubuntu at that time as I do now, and did once unity appeared, but I assume that was also delivered late?

 Incidentally I updated/upgraded the one KVM system I still have installed today and got a huge number of packages back, many of them ones that I couldn't reinstall a week ago so things are definitely moving in the right direction.

---

### Post by corradoventu on 2024-04-07
New daily ISO arrived!!! 	noble-desktop-amd64.iso	2024-04-07 09:19 	5.0G
installed OK.

---

### Post by zebra2 on 2024-04-07
What I get is that /daily-live/current  is identical to my March 23 ISO.  Daily-live/pending is 64.4% complete. I'm downloading the Pending ISO now. Will let you know if it installs.  I have three laptops that finally crashed and I brought back up with Mantic.  I have a fourth system that is still running on a non-updated Noble. Might take a while to get this all installed and updated.

---

### Post by oldfred on 2024-04-07
I use Kubuntu and just noticed new ISOs
[http://cdimage.ubuntu.com/kubuntu/daily-live/current](http://cdimage.ubuntu.com/kubuntu/daily-live/current)
2024-04-07 08:28

So now running this to update my ISO in /ISO folder
```
[FONT=monospace][COLOR=#000000]zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/current/noble-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/current/noble-desktop-amd64.iso.zsync)[/COLOR]
[/FONT]
```

Kubuntu change from March 28th ISO.
> [FONT=monospace][COLOR=#000000]Read noble-desktop-amd64.iso. Target 54.2% complete.[/COLOR]
[/FONT]

I wish flavors would not use same name for development ISO, makes it difficult to rename & track which is which if downloading more than one.

---

### Post by Claus7 on 2024-04-07
Hello,

just tried it, installing it using virtualbox. It has also gnome shell 46.

Regards!

---

### Post by #&amp;thj^% on 2024-04-07
Xubuntu as well new today>>>	2024-04-07 08:31 haven't tried installing it just yet.

I think I'm just going to set this one out, and wait for the next release.....

---

### Post by #&amp;thj^% on 2024-04-07
1st bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/2060398](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/2060398)

More to come...:P

And Login Loop again in play>>> I used ctrl+alt+F2 logged in and and ran startx

Bugs seem to be plenty 4 more coming...

---

### Post by zebra2 on 2024-04-07
I installed the pending ISO on my most difficult to install Laptop. It failed install for both efi and legacy.  I then reinstalled my Mantic ISO that was successful (again).  Then decided to upgrade my newly installed Mantic to Noble by changeing to Noble repositories.  The Noble install had 576 Packages to download and about 525 held back. The upgrade attempt ended with a failed system grub error.  I have a bunch of Laptops so no big deal for me but I'm on hold for now.

---

### Post by #&amp;thj^% on 2024-04-07
> **zebra2 said:**
> The upgrade attempt ended with a failed system grub error.  

Two other 24.04 installs and the same as you "failed to install Grub" but I have refind so no problems there.

I'm getting called away for a day or two so I'll file a grub-bug then....unless you file first then I'll just add myself to it.

---

### Post by oldfred on 2024-04-07
Kubuntu install worked without issue, to my HDD sda drive where main 22.04 install is on NVMe drive.
Too used to NVMe and tuning that 22.04 boots very quick. Noble took over 40 sec from HDD to boot.

First time I have used Calamares installer & it installed grub to ESP on HDD, did not overwrite ubuntu entry on NVMe's ESP like Ubiquity installer that was still in all versions of Kubuntu until 24.04.

---

### Post by zebra2 on 2024-04-07
> **1fallen said:**
> Two other 24.04 installs and the same as you "failed to install Grub" but I have refind so no problems there.

I'm getting called away for a day or two so I'll file a grub-bug then....unless you file first then I'll just add myself to it.


Considering your undeniable superior experience I will take a pass on the bug report.  No question in my mind that you can explain it better. I only know enough to be dangerous.

---

### Post by #&amp;thj^% on 2024-04-07
Ah come on now, don't sell yourself short....:) I've seen you in action and nothing wrong with your skill set. ;)

I think your smart enough....but I will file it when I can....along with oldfred's comment "did not overwrite ubuntu entry on NVMe's ESP like Ubiquity installer"

---

### Post by ajgreeny on 2024-04-07
Just installed the pending ISO **Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240407.2)** using KVM and so far all seems good.
No crashes at all so far.

Minor point, but grub is still not set with **quiet splash** options as default meaning the text scrolling at boot; not a problem but it really doesn't look good!

---

### Post by oldfred on 2024-04-07
One of the first things I change is to remove quiet splash & replace with noplymouth.
Seems to boot faster, or just may be seeing something happening is better than staring at logo screen.

---

### Post by zebra2 on 2024-04-08
Updated pending iso for April 8th which had 2% change.  Performed a simple default efi install. Install failed. Went back to bed. zzzzzzzzzzzzzz   Will check my bios in the morning to make sure it hasn't changed it' self and try one more time.

Edit:  zsynced pending with daily and they are the same.

---

### Post by #&amp;thj^% on 2024-04-08
This is just personal notes from todays attempt for a bare metal install:
```
Apr 08 08:40:50 xubuntu subiquity_log.6435[59507]: Starting unattended upgrades script
Apr 08 08:40:50 xubuntu subiquity_log.6435[59507]: Allowed origins are: o=Ubuntu,a=noble, o=Ubuntu,a=noble-security, o=UbuntuESMApps,a=noble-apps-security, o=UbuntuESM,a=noble-infra-security, o=Ubuntu,a=noble, o=Ubuntu,a=noble-security, o=UbuntuESMApps,a=noble-apps-security, o=UbuntuESM,a=noble-infra-security
Apr 08 08:40:50 xubuntu subiquity_log.6435[59507]: Initial blacklist:
Apr 08 08:40:50 xubuntu subiquity_log.6435[59507]: Initial whitelist (not strict):
Apr 08 08:40:51 xubuntu subiquity_event.6435[6435]:   curtin command in-target
Apr 08 08:41:15 xubuntu subiquity_log.6435[59507]: package cpdb-backend-cups upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)
Apr 08 08:41:15 xubuntu subiquity_log.6435[59507]: package cpdb-backend-cups upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)
Apr 08 08:42:16 xubuntu subiquity_log.6435[59507]: package gimp upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)
Apr 08 08:42:16 xubuntu subiquity_log.6435[59507]: package gimp upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)
```

And the installer will crash and burn from there.....lol

---

### Post by zebra2 on 2024-04-08
I did another upgrade from Mantic to Noble. It aborted with a failed efi shim install. 

Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1

---

### Post by #&amp;thj^% on 2024-04-08
> **zebra2 said:**
> I did another upgrade from Mantic to Noble. It aborted with a failed efi shim install. 

Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1

Yep same on this upgrade from Mantic to Noble

They wanted me to hold off on the bug-report for a day so I will.
One day only and not another minute more.....LOL

I was able to fix mine though, I really don't want to post how though, I'm known for Big and Bigger hammers...:P
```
apt policy shim-signed
shim-signed:
  Installed: 1.58+15.8-0ubuntu1
  Candidate: 1.58+15.8-0ubuntu1
  Version table:
 *** 1.58+15.8-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

``` 
```
aptitude why shim-signed
i   xubuntu-desktop             Recommends indicator-messages                   
i A indicator-messages          Recommends indicator-applet | indicator-renderer
p   ubiquity-frontend-gtk-panel Provides   indicator-renderer                   
p   ubiquity-frontend-gtk-panel Depends    ubiquity-frontend-gtk (= 24.04.3)    
p   ubiquity-frontend-gtk       Depends    ubiquity (= 24.04.3)                 
p   ubiquity                    Depends    shim-signed          
```
```
apt policy xz-utils
xz-utils:
  Installed: 5.6.1+really5.4.5-1
  Candidate: 5.6.1+really5.4.5-1
  Version table:
 *** 5.6.1+really5.4.5-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Hewjr100 on 2024-04-08
I was able to install to do a fresh install of Noble with April 7th iso, xz version is 5.4.5

Henry

PS I am using BIOS, UEFI is disabled.

---

### Post by zebra2 on 2024-04-08
I didn't get mine fixed but I did however do a "apt upgrade --download -only" and copied off the /var/cache/archives so I wouldn't have to repeat the download.  Just to save a little time.

---

### Post by zebra2 on 2024-04-08
> **Hewjr100 said:**
> I was able to install to do a fresh install of Noble with April 7th iso, xz version is 5.4.5

Henry

PS I am using BIOS, UEFI is disabled.

Thanks for the info. I'll give it a try.  May take a while but will report back.

Edit: OTOH, Think I will wait for the next daily current.

---

### Post by zebra2 on 2024-04-09
April 9th. Failed to install boot for both EFI and Legacy.  I also tried enabling wifi network and allowing the install to update the install disk and still nothing. The installer is properly formatting the boot partition for both efi and legacy but not setting up the boot. 
Note: zsync reported the April 9th ISO to be 98% complete.  Current and Pending were the same. 

Will try again tomorrow. Great to be retired!

---

### Post by ajgreeny on 2024-04-09
I have just installed the April 9 Xubuntu pending iso with no problems in KVM as I did two days ago with the April 7 version, again using Xubuntu.
Everything worked as it should using UEFI (didn't try MBR) and I managed to add packages that I always add to my installs without any glitch of any sort.

---

### Post by guiverc on 2024-04-09
I'd expect most have seen this, but there is a *status* page for Ubuntu *noble beta*.

[https://discourse.ubuntu.com/t/noble-numbat-24-04-beta-release-status-tracking/44043](https://discourse.ubuntu.com/t/noble-numbat-24-04-beta-release-status-tracking/44043)

It currently includes

> 
[LIST]
[*]Ubuntu Budgie and the x13s image require a rebuild with livecd-rootfs/24.04.60 (migrated to release)
[*]Xubuntu needs a rebuild with casper/1.496 (in -proposed)
[*]Ubuntu-unity needs a rebuild with gnome-session/46.0-1ubuntu3 (in -proposed)
[*]Kubuntu needs a rebuild with kubuntu-meta/1.449 (migrated to release)
[*]Ubuntu needs a rebuild with gnome-initial-setup/46.0-1ubuntu5 (in -proposed)
[*]Lubuntu needs a rebuild with calamares-settings-ubuntu/1:20.04.25 (in -proposed)
[/LIST]


though I've noted Ubuntu Studio on IRC will also be rebuilt...

---

### Post by zebra2 on 2024-04-10
April 10th cdi current iso is identical to April 9th.

April 10th cdi pending iso is 77%.

I will try an install of the pending iso as soon as I get one of those round things.

---

### Post by zebra2 on 2024-04-10
Success!  Installed April 10 pending EFI boot .  Ran update "all packages up to date".  
FYI

[code]
zebra0@zebra0:~$ inxi1
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Noble Numbat (development branch)
Release:	24.04
Codename:	noble
inxi -Sxx
System:
Host: zebra0 Kernel: 6.8.0-22-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
Desktop: GNOME v: 46.0 tk: GTK v: 3.24.41 wm: gnome-shell dm: GDM3
Distro: Ubuntu 24.04 LTS (Noble Numbat)
$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 46.0
Version: 46.0-0ubuntu4
loginctl type
Type=wayland
BIOS UEFI
zebra0@zebra0:~$ 
/[code]

---

### Post by #&amp;thj^% on 2024-04-11
> **1fallen said:**
> Yep same on this upgrade from Mantic to Noble

They wanted me to hold off on the bug-report for a day so I will.
One day only and not another minute more.....LOL

I was able to fix mine though, I really don't want to post how though, I'm known for Big and Bigger hammers...:P
```
apt policy shim-signed
shim-signed:
  Installed: 1.58+15.8-0ubuntu1
  Candidate: 1.58+15.8-0ubuntu1
  Version table:
 *** 1.58+15.8-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

``` 
```
aptitude why shim-signed
i   xubuntu-desktop             Recommends indicator-messages                   
i A indicator-messages          Recommends indicator-applet | indicator-renderer
p   ubiquity-frontend-gtk-panel Provides   indicator-renderer                   
p   ubiquity-frontend-gtk-panel Depends    ubiquity-frontend-gtk (= 24.04.3)    
p   ubiquity-frontend-gtk       Depends    ubiquity (= 24.04.3)                 
p   ubiquity                    Depends    shim-signed          
```
```
apt policy xz-utils
xz-utils:
  Installed: 5.6.1+really5.4.5-1
  Candidate: 5.6.1+really5.4.5-1
  Version table:
 *** 5.6.1+really5.4.5-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

All Fixed now.....:)
New Install from yesterdays .iso 4-10-2024....

---

### Post by corradoventu on 2024-04-11
Ubuntu 24.04 LTS "Noble Numbat" - Beta amd64 (20240410)

---

