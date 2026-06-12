---
title: "Borked Fresh install of Precise A1 on Dell OptiGX270"
date: 2012-01-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-07
Any ideas??

```

ventrical@ventrical1ME051:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-8-generic (3.2.0-8.14) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-8-generic /boot/vmlinuz-3.2.0-8-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-8-generic
Segmentation fault (core dumped)
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-8-generic /boot/vmlinuz-3.2.0-8-generic
Segmentation fault (core dumped)
run-parts: /etc/kernel/postinst.d/pm-utils exited with return code 139
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-8-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python3.2-minimal (3.2.2-3) ...
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: error processing python3.2-minimal (--configure):
 subprocess installed post-installation script returned error exit status 134
dpkg: dependency problems prevent configuration of python3.2:
 python3.2 depends on python3.2-minimal (= 3.2.2-3); however:
  Package python3.2-minimal is not configured yet.
dpkg: error processing python3.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-minimal:
 python3-minimal depends on python3.2-minimal (>= 3.2.2); however:
  Package python3.2-minimal is not configured yet.
dpkg: error processing python3-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3.2 (>= 3.2.2); however:
  Package python3.2 is not configured yet.
 python3 depends on python3-minimal (= 3.2.2-0ubuntu2); however:
  Package python3-minimal is not configured yet.
dpkg: error processing python3 (--configure):
 dependNo apport report written because the error message indicates its a followup error from a previous failure.
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             ency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3 (>= 3.1.3-13~); however:
  Package python3 is not configured yet.
dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error procNo apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      essing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 10.0~b3+build2-0ubuntu1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of launchpad-integration:
 launchpad-integration depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing launchpad-integration (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-8-generic; however:
  Package linux-image-3.2.0-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.8.8); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.155.2); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on launchpad-integration; however:
  Package launchpad-integration is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-8-generic
 python3.2-minimal
 python3.2
 python3-minimal
 python3
 lsb-release
 ubuntu-minimal
 command-not-found
 update-manager-core
 firefox
 firefox-globalmenu
 firefox-gnome-support
 launchpad-integration
 linux-image-generic
 linux-generic
 update-manager
 ubuntu-desktop
 unattended-upgrades
Error org

```

---

### Post by ventrical on 2012-01-07
and whats this with the Debian settings in the repos ?

---

### Post by teh603 on 2012-01-07
Download the daily image and try again? At least that way you'll be sorta guaranteed a working install. It looks like you were trying to upgrade over an existing install and borked your system to hell and back.

---

### Post by ventrical on 2012-01-07
Actually I did a re-install !! But at first - yes .. i wanted to test the overwrite installer.

  It works great but I can't get the kernel upgrade and other programs.

and  how would I install the daily again .. ?


thanks..

---

### Post by ventrical on 2012-01-07
Ok.. I got the kernel to install. I just re-booted and chose <recovery mode> at GRUB. I was then able to use sudo apt-get upgrade to install kernel but other files will not install.

dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3.2-minimal
 python3.2
 python3-minimal
 python3
 lsb-release
 ubuntu-minimal
 command-not-found
 update-manager-core
 firefox
 firefox-globalmenu
 firefox-gnome-support
 launchpad-integration
 update-manager
 ubuntu-desktop
 unattended-upgrades
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by paul_in_london on 2012-01-07
Have you tried using **aptitude** instead of **apt-get**?

---

### Post by ventrical on 2012-01-07
> **paul_in_london said:**
> Have you tried using **aptitude** instead of **apt-get**?

  Yes Paul.. I have and to no avail. What I proceeded to do was to remove those files individually using

sudo apt-get remove .. and it worked at first but the lsb-release, python3 and unattedned-upgrades all have these weird dependencies with firefox. Just weird. Anyways I succeded in completley loosing firefox .. and I have been going all day so I shut that station off for the night and will get back at er in the morning.

---

### Post by paul_in_london on 2012-01-07
There does seem to be something weird going on with your software sources.

EDIT: Here's my **/etc/apt/sources.list**:

```
deb http://archive.ubuntu.com/ubuntu precise main restricted

deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu precise-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main
deb-src http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main
deb http://repository.spotify.com stable non-free
```

---

### Post by teh603 on 2012-01-07
As a general rule, the distribution upgrader isn't a good thing to try until very late in the release cycle. I almost never use it and prefer to do a clean install whenever possible.

---

### Post by ventrical on 2012-01-08
> **teh603 said:**
> As a general rule, the distribution upgrader isn't a good thing to try until very late in the release cycle. I almost never use it and prefer to do a clean install whenever possible.


  I used the alpha release ISO on my USB to upgrade. It gave me the option to  uninstall the old installation and  install the new. I think it is a new feature and I wanted to try it.  I'm just not sure how the debian option got in there.  If I can't fix it I'll just try another reinstall.

@Paul_in_London..

  I'll check out that sources.list.

---

### Post by ventrical on 2012-01-08
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by paul_in_london on 2012-01-08
> **ventrical said:**
> ```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

@ventrical,

I can't see any Debian repos in there (contrary to the screenshot in your earlier post).

Or are you using this one now instead?

---

### Post by ventrical on 2012-01-08
> **paul_in_london said:**
> @ventrical,

I can't see any Debian repos in there (contrary to the screenshot in your earlier post).

Or are you using this one now instead?


  No I am not. The  partition in question is an old  Lucid 10.04 LTS. When I first tried to install Precise alpha 1 from the oversized  .ISO on a uSB stick it gave me the option of upgrading from Lucid 10.04 to Precise 12.04.  but I did this while  hooked up to my KVM network and the install locked up and I lost mouse and keyboard control so I had to reboot. So I shut down , disconnected the KVM and then proceeded to try another install. This time I chose to re-install over the partially installed Precise 12.04 and the installer crashed! at which point it gave me the option to file a bug report (which I did under user Dale B.)

  After that  I then tried again to install using the option  to erase the previous installation and start anew. The installation completed successfully and then  I proceeded to download synaptic and then do the omnibus update.  That updated failed halfway through and so I re-booted and tried to recover using:

sudo dpkg --configure -a

and

sudo apt-get -f install

 and , then , as which up unto this point I get the errors as  which I have been posting.

  so I am going to keep trying to bring this install back or perhaps do a clean install unless somebody else chimes in with another way to recover from this.

BTW .. it is not an important install to recover. I basically am just trying to test the installer capabilities.

Thanks Paul..

 regards ,

ventrical

---

### Post by paul_in_london on 2012-01-08
> **ventrical said:**
> No I am not. The  partition in question is an old  Lucid 10.04 LTS. When I first tried to install Precise alpha 1 from the oversized  .ISO on a uSB stick it gave me the option of upgrading from Lucid 10.04 to Precise 12.04.  but I did this while  hooked up to my KVM network and the install locked up and I lost mouse and keyboard control so I had to reboot. So I shut down , disconnected the KVM and then proceeded to try another install. This time I chose to re-install over the partially installed Precise 12.04 and the installer crashed! at which point it gave me the option to file a bug report (which I did under user Dale B.)

  After that  I then tried again to install using the option  to erase the previous installation and start anew. The installation completed successfully and then  I proceeded to download synaptic and then do the omnibus update.  That updated failed halfway through and so I re-booted and tried to recover using:

sudo dpkg --configure -a

and

sudo apt-get -f install

 and , then , as which up unto this point I get the errors as  which I have been posting.

  so I am going to keep trying to bring this install back or perhaps do a clean install unless somebody else chimes in with another way to recover from this.

BTW .. it is not an important install to recover. I basically am just trying to test the installer capabilities.

Thanks Paul..

 regards ,

ventrical

No problem. I just had a quick look at this thread:

[http://ubuntuforums.org/showthread.php?t=1036024](http://ubuntuforums.org/showthread.php?t=1036024)

What happens if you do:

```
sudo update-apt-xapian-index
```

EDIT: Sorry, the other thing I meant to say was what about trying the sources list you posted in post #11 instead of your current one?

---

### Post by paul_in_london on 2012-01-08
Another thing that could be worth checking is whether you have a dpkg status file which predates the latest crash which occurred during the upgrade? For example **/var/backups/dpkg.status.0**. If you do, you could revert to the earlier status file and then try and repeat the upgrade.

---

### Post by ventrical on 2012-01-08
> **paul_in_london said:**
> No problem. I just had a quick look at this thread:

[http://ubuntuforums.org/showthread.php?t=1036024](http://ubuntuforums.org/showthread.php?t=1036024)

What happens if you do:

```
sudo update-apt-xapian-index
```EDIT: Sorry, the other thing I meant to say was what about trying the sources list you posted in post #11 instead of your current one?


 As for the :

sudo update-apt-xapian-index

 I had tried this sometime back with an issue that effenberg had posted and seemed to work well on one install - however.. I have already resolved the problem for now.

  I decided to (upgrade) to Oneiric using my Oneiric CD. I was presented with the same options to <erase Precise install and re-install> which was Oneiric (which I will upgrade using the transitional method for now.

  However, the upgrade to Oneiric  was not without fault as I had a 'libpam' issue which was eventually solved by using:

sudo apt-get upgrade

  Then I was able to install the 3.n.n-14 kernel on this install using synpatic.

  My conclusion so far is that the Ubiquity installer is severly impeded when trying to to upgrade to exisitings partions or installing over older paritions of previous versions of Ubuntu.

  Precise and company *will* install if it is a side X side or a fresh install on a <something else> modified partition - so I am not faulting Ubiquity totally here . But I can see the goal of devs in that they are trying to streamline and perfect the *upgrade* process - (just as the Update Manager also) but there are serious bugs still all around - (Update Manager included) then if Update Manager is still impaired in Oneiric then what benefit will their be with Ubiquity Installer and the state that it is in - being that  UM is sometimes on - sometimes off?

  Ok .. I'm off to transition this install to Precise. I'll get back on this.

Thanks for your replies Paul.

---

### Post by ventrical on 2012-01-08
> **paul_in_london said:**
> Another thing that could be worth checking is whether you have a dpkg status file which predates the latest crash which occurred during the upgrade? For example **/var/backups/dpkg.status.0**. If you do, you could revert to the earlier status file and then try and repeat the upgrade.

As previous I backgraded to Oneiric and will transition to Precise.

---

### Post by paul_in_london on 2012-01-08
Hi ventrical,

If it still fails, maybe you could try an alternate CD - although there's no guarantee that you won't run into the same potential underlying bugs.

Cheers,

Paul

---

### Post by teh603 on 2012-01-08
See, this is why I always backup my visible /home folders, do a "guided-use entire disk" clean install, and then restore my data from the backups. I'll be honest, I didn't even know the whole "this disk contains packages, do you want to install them?" thing was still around; I haven't seen it since I switched to Kubuntu and thought it dead. IMO the only two ways you should try to upgrade a system is doing a clean install, or using the update mangler's automatic distribution upgrade system.

---

### Post by ventrical on 2012-01-08
> **paul_in_london said:**
> Hi ventrical,

If it still fails, maybe you could try an alternate CD - although there's no guarantee that you won't run into the same potential underlying bugs.

Cheers,

Paul

  Thanks Paul.

BTW .. I had a successful transition using the manual method.


sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get update
sudo apt-get upgrade

Precise  works smoother now than ever.

Thanks

---

### Post by ventrical on 2012-01-08
Voila'

---

### Post by paul_in_london on 2012-01-08
> **ventrical said:**
> Thanks Paul.

BTW .. I had a successful transition using the manual method.


sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get update
sudo apt-get upgrade

Precise  works smoother now than ever.

Thanks

Glad you got it working mate. :)

Btw, I still prefer aptitude!

---

### Post by ventrical on 2012-01-08
> **teh603 said:**
> See, this is why I always backup my visible /home folders, do a "guided-use entire disk" clean install, and then restore my data from the backups. I'll be honest, I didn't even know the whole "this disk contains packages, do you want to install them?" thing was still around; I haven't seen it since I switched to Kubuntu and thought it dead. IMO the only two ways you should try to upgrade a system is doing a clean install, or using the update mangler's automatic distribution upgrade system.


Hi teh603,

 Oh yeah .. for sure I got my stuff backed up. I'm not sweating it. I'm just experimenting.. trying different scenarios with Ubiquity installer.  The Precise alpha and Oneiric installer now offer these new  install methods to upgrade from older versions or backgrade to an older version.  Of course the Precise alpha does not work but the Oneiric  did work and I downgraded to Oneiric and then manually upgraded to Precise (that which I am typing from right now !.)

  The Update Manager is still really having some probs with these latest releases - no doubt .. and .. yeah ..  I actually did do a Kubuntu Precise transition and it is the weirdest, funniest thing I ever seen :) hehehe .. I have it working on an older Nvidia graphics card and  it perplexes me that Kubunut will  use all the plamsa screens and graphics and yet will not allow Unity 3D to work with Ubuntu Precise...either way .. I'm not complaining ... it's just more fun for me :)

thanks  for you comments and help..

---

### Post by teh603 on 2012-01-08
> **ventrical said:**
> 
  The Update Manager is still really having some probs with these latest releases - no doubt .. and .. yeah ..  I actually did do a Kubuntu Precise transition and it is the weirdest, funniest thing I ever seen :) hehehe .. I have it working on an older Nvidia graphics card and  it perplexes me that Kubunut will  use all the plamsa screens and graphics and yet will not allow Unity 3D to work with Ubuntu Precise...either way .. I'm not complaining ... it's just more fun for me :)

thanks  for you comments and help..Dunno, it looked pretty similar to one I did going from Jaunty to Karmic (also the stupidest thing I ever did; I was back on Jaunty after a few hours because Karmic was *that* buggy) a couple of years ago. But the Unity interface is probably different enough to make a difference.

No idea on what's up with Unity 3D vs. Kubuntu. All I know is that Kubuntu always seems to run at maximum possible graphics accelleration after a fresh install, while the old Gnome interface was a lot more conservative. Since I tend to keep Desktop Effects turned off no matter which version I'm using, it doesn't affect me too much.

---

### Post by paul_in_london on 2012-01-08
> **ventrical said:**
> Voila'

Not much disk space left there mate! Do you use bleachbit?

---

### Post by ventrical on 2012-01-09
> **paul_in_london said:**
> Not much disk space left there mate! Do you use bleachbit?


 Heard of it but do not use it. It's a 10 GB partition.

 Should I use bleachbit? and what are the how tos?

thanks

---

### Post by paul_in_london on 2012-01-09
> **ventrical said:**
> Heard of it but do not use it. It's a 10 GB partition.

 Should I use bleachbit? and what are the how tos?

thanks

Ah, that would explain it. If you have the universe repo enabled, you you should just be able to install it straight off:

[http://www.ubuntuupdates.org/packages/show/389032](http://www.ubuntuupdates.org/packages/show/389032)

It's very simple to use and runs in 2 modes (with and without sudo basically).

Bit of info:

[http://www.linuxinsider.com/story/73218.html](http://www.linuxinsider.com/story/73218.html)

HTH.

---

### Post by ventrical on 2012-01-09
> **paul_in_london said:**
> Not much disk space left there mate! Do you use bleachbit?


Ok .. there is of course a bug here. Diskusage Analyzer says 3.4 GBs and System Monitor says 2.8GB but , still it is using a lot of space.

  Just making a note.

---

### Post by ventrical on 2012-01-09
That didn't work very well :)

---

### Post by cariboo on 2012-01-09
You have to run bleachbit as root, in order to remove archived packages. I always use:

```
sudo apt-get clean
```

to remove them.

---

### Post by ventrical on 2012-01-10
Thanks Cariboo907 ... I'll give that a try  again. I tired that during Oneiric beta testing but it only cleaned up a few MBs.

& also Lubuntu now has bleachbit/bleachbit as root as default in the menu .

---

### Post by ventrical on 2012-01-10
> **cariboo907 said:**
> You have to run bleachbit as root, in order to remove archived packages. I always use:

```
sudo apt-get clean
```to remove them.

Thanks again..

 That gave me almost 2 GBs  extra on a tight install ! :)

---

### Post by ventrical on 2012-01-10
extra-

---

