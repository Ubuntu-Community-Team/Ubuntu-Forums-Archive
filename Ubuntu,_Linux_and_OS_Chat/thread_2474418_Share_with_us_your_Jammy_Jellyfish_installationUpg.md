---
title: "Share with us your Jammy Jellyfish installation/Upgrade Experience"
date: 2022-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by wildmanne39 on 2022-04-28
Jammy Jellyfish was released April 21st, 2021, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Jammy Jellyfish.

This thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2468660](https://ubuntuforums.org/showthread.php?t=2468660)

---

### Post by TheFu on 2022-04-29
Always read the release notes, RN, BEFORE installing a new Ubuntu.  It will save time, usually.
[https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)

Things in the release notes that I didn't expect or though are specifically important:

[LIST]
[*]iptables is deprecated. nftables replaces it. Choose which you want and then setup the system to use one or the other.
[*]RSA for ssh is disabled.  This can impact RSA-only clients trying to connect to 22.04 ssh-servers.  That's scp, sftp, rsync, and many backup tools too. **ssh-keygen -t ed25519** to create ed25519 keys.
[*]NFS v4 disables UDP. That shouldn't be an issue, since NFS v4 has used TCP by default for some years, but in corporate environments, it could force firewall changes between subnets.  There are other NFS changes, but I tested 22.04 NFS client connections to older NFSv4 servers and didn't have any issues. Read the RN if you have issues.
[*]Ruby v3 is the default now. They've left v2.x behind. Expect to make code changes. Rubyists are used to this.
[*]OpenSSL v3.0. That can have API impacts whenever a new major release change happens. libssl1.x is impacted. See the RN for more. 
[*]Firefox is a snap package now.  To avoid that, switch to the ESR version. There's a PPA: sudo add-apt-repository ppa:mozillateam/ppa [https://ubuntuhandbook.org/index.php/2022/03/install-firefox-esr-ubuntu/](https://ubuntuhandbook.org/index.php/2022/03/install-firefox-esr-ubuntu/)
[*]Php 8.2.  If you are migrating from a Php v7.x environment, be prepared for mandatory code changes.
[*]Samba.  Some minor version support has been removed and will not be recognized. Read the RN for more links and details.
[*]Virtualization - new major versions of both virt-manager and libvirt mean big new capabilities. TPM is enabled by default if UEFI bios is enabled for a VM. 
[*]virtio-gpu video used for most modern distros should provide a performance improvement for desktop-on-desktop VMs.
[*]Wireguard is not in the main package repo.
[*]LXD v5.0 included. Live migrations, clustering, and VM support on parity with container support. Sadly, it is still a snap only package.
[*] MS-AD support improved, but no love for using Linux-only LDAP servers for user-management.
[/LIST]

Of course, those are my major takeaways. Yours will be different.

---

### Post by makitso on 2022-04-29
I have an older Thinkpad T510 circa 2011 that ran into the iommu problem.  The liveCD hung until I added the intel_iommu=off to the grub line and once installed to grub in etc/default.

---

### Post by Claus7 on 2022-04-30
Hello,

upgrade since alpha version from lts to lts worked smoothly. Upgrading from impish though, things resulted with errors: the error popped up was about firefox, which did not end up installing as snap. Trying to report the issue it mentioned something like it was difficult to access the servers or something similar. That resulted in not clearing the system when installation finished, which I had to do manually. Time will tell how the system will behave, yet, up to now things are working. Last time it was with chromium, this time it was with firefox. I'm waiting for the next browser that will become snap to distract an upgrade! 

Regards!

---

### Post by mathipu on 2022-05-08
This has been the worst upgrade (from 21.10) for me in as long as I can remember; maybe ever.  I think I started with Hoary Hedgehog, originally.

I have a Thinkpad X1 Extreme Gen 2.  Not too old.  i7-8750H, Nvidia 1050Ti

- kernel 5.15 won't boot because it doesn't recognize my nvme drive, thankfully 5.13 boots
- my usb speakers are recognized as a keyboard, or something - anyway they don't work and the only audio output I have is dummy, not even internal speakers work
- usb camera doesn't work
- bluetooth doesn't work
- I just tried a usb headphone/mike.  doesn't work.  not sure what this snap-device-helper nonsense is, but it's suspicious to me
- the firefox snap is a disaster
    --- it's slow to startup and since I use multiple profiles, each profile is slow to startup... 15 - 20 seconds.  something like that.  unusable.
    --- gnome browser integration doesn't work
    --- keepassxc browser integration doesn't work
    --- pdf file downloads (so far) silently fail
- the skype snap was broken.  It wouldn't start. I had to reinstall; though lot of good it does me since I don't have any working audio/video    
- of course, a number of gnome extensions don't work, but I'm used to that on upgrades

So this is all, so far.  I guess I'll spend the next few hours tackling these things. :-/

Incidentally, I love deb packages and apt.  It's always been one of the joys of Ubuntu.  It's something that was never broken (well, maybe sometimes) for me.  These snaps have been troublesome.  Upgrades have had issues.  Multiple instances of the same packages, some that work, better or worse than others, some that are broken; have been a problem.  Permissions have been a problem.  I think there was an issue with snaps accessing my encrypted volumes... hmm... maybe the issue with FF.  

Of the two practical OS choices in the world: OSX and Linux; I can't stand OSX, though I'm forced to endure it for work.  The gnome UI is much more power-user friendly, as is practically every aspect if Gnome/Ubuntu/Linux... including, thankfully nothing that resembles Homebrew (until Snap).  Efforts to emulate OSX in any way are not my favorite.

A while ago, I switched to Arch and then went back to Debian again; but at the end of the day, what I like is a computer that works with the least amount of pain and Ubuntu has gratefully delivered on that more reliably than any other system.  This is a downer.

---

### Post by poorguy on 2022-05-09
Where I had to install from a dvd the loading to get to the install menu took 20 minutes to 30 minutes and the install took from 15 minutes to 20 minutes and when installing from a USB flash drive not much better.

It would have been nice to have some warning that the decompressing of the files would take a bit of time.

I'm also using old outdated desktops created from other old outdated desktop parts and memory is only 4.0GB t0 6.0GB.

Once the install was finished everything works as it should so in the end all is well.

What I find wrong with Firefox is having to remove all of the languages which in my case is not needed.

Ubuntu 22.04 Ubuntu 22.04 official flavors ain't the same as the previous versions and has taken some getting used to but it's okay.

Snaps don't seem to be as bad as what is written about them and I believe that some of the complainers about Snaps are armchair users and have never installed any Snaps or used any Snaps.

AppImages, Flatpaks, Snaps five and a half one way six another.

---

### Post by mathipu on 2022-05-16
Well, I was about ready to do a full reinstall, because the live CD worked.  By the way, as some have mentioned elsewhere, the pain of a reinstall isn't "I have too many apps installed," it's reconfiguring everything.  Browser extensions.  Yubikey auth.  All of the apps (e.g. Moneydance, Sweethome3d, etc...).  Getting all of the browser profiles back into place and working... reconfiguring the browser.  It's a pain.  

So anyway, I did a last-ditch apt update and got a 5.15 kernel update which, lo and behold, installed all of the missing kernel modules.  The other option I considered was to just compile my own kernel, but I haven't done that in a while and going through all of the options isn't something I looked forward to.

The last thing left is that the base grub ubuntu menu item still doesn't find the hard drive, but that should be easy to remedy.

Oh, and I deleted the FF snap and went back to a PPA version of FF, which makes life so much better and faster.

Even if I "get out of the armchair" and get into the field with Snaps (something which I don't see the need for) it still won't make FF snap any faster OR make the keepassxc integration suddenly work.  No thanks.  Why would I want this?

---

### Post by him610 on 2022-05-17
I completed one fresh install of Xubuntu 22.04; as well as, one upgrade to Xubuntu 22.04 on the same laptop - a seven year old Acer Aspire V3-572G.
As I recall, the fresh install completed without any issues.
The upgrade completed without any noticeable issues also.
After installation, I ran a script to install all of my normal manual installs.
They both feel like (oldshoe) home now.
My survey response is part of the blue bar - Install - worked flawlessly.
My upgrade experience was not captured in the survey.

---

### Post by tomendry on 2022-08-08
Hello I am new here

---

### Post by Erik1984 on 2022-08-16
Did the upgrade recently when 22.04.1 became available. Didn't want to wait for the graphical upgrade notification as it's very uncertain you'll receive it on Kubuntu (ymmv). Used the command from the following guide to start the upgrade: [https://help.ubuntu.com/community/JammyUpgrades/Kubuntu](https://help.ubuntu.com/community/JammyUpgrades/Kubuntu)

After the upgrade these are my findings:
The shortcut to Firefox on the panel didn't work anymore after upgrade to the snap version (don't know if that's the reason). Also plasma browser integration is not able to find / connect to the background process it needs. So far everything seems OK :) Good enough score so I'm happy

---

### Post by QIII on 2022-08-16
I don't usually upgrade between LTS releases, preferring to do a fresh installation.  But I thought I'd try it just to see how it went (after doing a thorough backup of both important data and some configs).

I had only two very minor issues:  The arrangement of my three monitors changed (easy enough to fix) and one script that I run for my conky (giving the status of virtual machines) is not running properly.  Haven't had time to fiddle with it just yet.

As I am using Kubuntu, I'm going to assume the two issues related to KDE and not vanilla Ubuntu.

As far as the process itself, I think that do-release-upgrade is somewhat slower than a fresh installation.  So I'll go back to fresh installs again.

---

### Post by Claus7 on 2022-08-17
Hello,

> **QIII said:**
> ...
As far as the process itself, I think that do-release-upgrade is somewhat slower than a fresh installation.  So I'll go back to fresh installs again.

out of curiosity: have you counted the time required in order to install everything back to your (as close as possible) original setup and do the necessary configurations?

Regards!

---

### Post by QIII on 2022-08-17
> **Claus7 said:**
> Hello,



out of curiosity: have you counted the time required in order to install everything back to your (as close as possible) original setup and do the necessary configurations?

Regards!

Yes.  Still faster.  But then again I have had years to perfect what I save and how I go about restoring.

Additional note I hadn't noticed before, and probably a good reason to do a fresh installation next time:

I had to purge the amdgpu module and re-install it specifically for 22.04.  That was not difficult using Synaptic to be sure I got all the right pieces to re-install, but it is something that was not done well by using do-release-upgrade.

---

### Post by StuartCarter on 2022-08-18
After upgrade I have a notification from snapd-desktop-integration that some required theme snaps are missing, want to install them now? But clicking on the notification does nothing. Kinda annoying.

---

