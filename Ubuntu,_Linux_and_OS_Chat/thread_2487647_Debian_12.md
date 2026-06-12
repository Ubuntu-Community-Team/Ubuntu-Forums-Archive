---
title: "Debian 12"
date: 2023-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by exploder on 2023-06-11
Installed Debian 12 Gnome on a laptop I had sitting around for a while. I was absolutely blown away by the quality! Everything works beautifully right out of the box! Even the fonts look great! This is by far my best experience with Gnome Shell! The Debian Developer's really did some impressive work on the new release!

---

### Post by TheFu on 2023-06-11
I only 2 questions.

[LIST]
[*]Server-only install available?
[*]Is lxd available as a deb package, not a snap?
[/LIST]

---

### Post by exploder on 2023-06-11
lxd is a deb.

---

### Post by #&amp;thj^% on 2023-06-11
> **TheFu said:**
> I only 2 questions.

[LIST]
[*]Server-only install available?
[/LIST]
Not the way your used to: [https://ostechnix.com/install-debian-12-bookworm/](https://ostechnix.com/install-debian-12-bookworm/)
The lxd.deb was already said by exploder.

---

### Post by TheFu on 2023-06-12
Yep.  

```
# apt install lxd
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  apparmor attr ca-certificates dns-root-data dnsmasq-base libdqlite0 libfuse3-3 libjansson4 liblxc-common
  liblxc1 liblzo2-2 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 libpopt0 libraft2
  libsqlite3-0 libsubid4 libuv1 lxcfs lxd-agent lxd-client openssl rsync squashfs-tools uidmap xz-utils
Suggested packages:
  apparmor-profiles-extra apparmor-utils fuse3 btrfs-progs ceph-common lvm2 zfsutils-linux lxd-tools gdisk
  openssh-server python3 python3-braceexpand
The following NEW packages will be installed:
  apparmor attr ca-certificates dns-root-data dnsmasq-base libdqlite0 libfuse3-3 libjansson4 liblxc-common
  liblxc1 liblzo2-2 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 libpopt0 libraft2
  libsqlite3-0 libsubid4 libuv1 lxcfs lxd lxd-agent lxd-client openssl rsync squashfs-tools uidmap
  xz-utils
0 upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.6 MB of archives.
After this operation, 97.0 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Will be interesting to see it in action.  The snap version mostly works. I just don't like snaps not providing any local control over updates and storage access by default. Switching to debian will be the result now that lxd is available.  Found some people saying their lxd/lxc instances over the last 6 months in "Debian Testing" had some failures.  Hopefully, those are handled.

Crap. Running into some name resolution failures, just like on Ubuntu.  Guess I need to fix that in my normal way - by masking all the systemd-resolved stuff and actually pointing /etc/resolv.conf at my LAN DNS ... 

....   off discovering that network setups in debian 12 container version isn't what I expected.  Got no networking and the Debian 12 manual doesn't exist at this point.  I have a NIC, but the systemd network config method and the old interfaces file method don't work. I'm surprised. Guess it is time to create manual init.d/ scripts to start and stop the NIC directly.  Hummmm.  Let me check the Debian Testing manual. Might be something inside that.  Nope.  Something is odd with their lxd container image.  Maybe I need a full VM.

---

### Post by #&amp;thj^% on 2023-06-12
Just a heads up if your fighting this like I did at first (with a vpn) then stop the VPN first.
This is where I got hung, Perhaps the network on the VM is not communicating with the default network created by docker during the build (bridge), so try "host" network :
```

docker build --network host -t [image_name]

for docker-compose:

service_name:
    container_name: name
    build: 
      context: .
      network: host


```
It's not as straight forward as Ubuntu but.....we knew that going in.

---

### Post by TheFu on 2023-06-12
I suspect you were posting in the wrong thread?
No VPN.
No docker.

I did an
```
$ lxc launch images:debian/12 deb12
```
That created an lxc container and launched it for use.
Then I logged in as root with 
```
$ lxc exec deb12 -- sudo --login
```
From there, I see no interfaces are up. No standard networking base files.
```
$ lxc info deb12                                                         
Name: deb12                                                                                     
Status: RUNNING
Type: container
Architecture: x86_64
PID: 619363
Created: 2023/06/11 11:44 EDT
Last Used: 2023/06/11 12:04 EDT

Resources:                                                                         l
  Processes: 6
  Disk usage:
    root: 46.86MiB
  CPU usage:                                                                       o
    CPU usage (in seconds): 1
  Memory usage:
    Memory (current): 27.32MiB
    Memory (peak): 79.82MiB
  Network usage:                                                                   o
    eth0:
      Type: broadcast
      State: UP
      Host interface: vethb433a23a
      MAC address: 00:16:3e:4f:66:a3
      MTU: 1500
      Bytes received: 7.34MB
      Bytes sent: 0B
      Packets received: 100068
      Packets sent: 0
      IP addresses:
    lo:
      Type: loopback                                                               l
      State: UP
      MTU: 65536
      Bytes received: 0B
      Bytes sent: 0B                                                               o
      Packets received: 0
      Packets sent: 0
      IP addresses:
        inet:  127.0.0.1/8 (local)

```
Anyway, it has a NIC, at least as far as the host system is concerned.
Probably need to stop hijacking this thread.  And I have some more research.  Probably need to load it into a full VM first.  I ran debian 10 for a few years as my email gateway. When it was time to upgrade the OS, I moved to an Ubuntu container, which has been working, mostly, except I had to move firewall stuff upstream. Containers can't run firewalls root-less.

---

### Post by #&amp;thj^% on 2023-06-12
No not the wrong thread, just did not have a clear picture of what you were doing. (Now I have a very foggy idea of what your doing currently)
BTW This is A Chat Area not support, maybe that's what you meant? IJDK. 
But I'll happily leave you be now>

---

### Post by exploder on 2023-06-25
I have never had the pleasure of participating in Debian development but they sure do nice work! I have Debian 12 running on three systems, not a single problem in my daily use. Memory use is higher than I am used to but it's not by any means a problem. Some are saying that memory use is more accurate in this release, that could be I guess. Multimedia playback worked out of the box. I hardly know what to do, so used to having stuff to fix or work around and there is nothing that needs fixed.

For all the complaining about the Debian installer being old and dated, it's actually perfect just the way it is! It's not pretty or fancy but it gives you choice. You can install any DE you like and all your packages are current! I guess they could pretty it up but it works perfectly and for all the more time spent using it, if it's not broke why fix it?

The vanilla Gnome Debian provides is excellent! Gnome Shell actually looks nice these days. I do use Dash To Dock because I am not fond of the default hiding of the panel. My eyesight is not stellar so the app grid and Gnome's use of padding makes things really nice for my situation. Some years ago I had some serious surgery on my good eye. I could barely see for a few months. Gnome Shell's accessibility features and some help from the PCLinux Community and I could use a computer. 

I did tweak Debian with the usual things we all do, swappiness, etc but there was no rush this time, it seemed just fine stock in all honesty. I noticed I am not getting hammered with updates, seemed odd at first. Then again, nothing is broken. I noticed when I looked at the logs, there was only one error. I am used to there being a bunch! Yeah, it doesn't hurt anything but it's still interesting that I am not getting firmware errors like I always get with most any distro. 

Like many, I do not like where Ubuntu is heading with snaps. My system actually crashed multiple times with the Firefox snap package. I do not want ANYTHING updating without my knowledge, period! Debian went with Firefox ESR. I had never used it but I do like the idea of it not being updated constantly. I use the web browser every single day, I just want it to work!

I mostly like Debian's default apps, Gnome Shell is consistent, no mix and match. I get rid of all the default games though but that is just personal preference. People also complain about dated apps. Version numbers really do not mean much if you are still using the app the same way. More often regressions and bugs come with newer versions, why not give these time to mature? In the event there is a need for newer software, flatpacks offer a lot of choice and are a more accepted solution. 

Debian has always had a reputation for reliability. With the ever changing software environment these days, Wayland, Pipewire, etc, it amazes me such a level of quality can be achieved! The decision regarding non-free software makes Debian more accessible to new and seasoned users.  I do not see many users on the Debian Forums having issues with the new release, that is always a good sign! There has been very few updates since release, I attribute this to it being released when ready! I do not like Ubuntu's phased updates at all, you do not want to be the first to try them and if they were properly tested in the first place there would be no need for this!

Maybe I am just getting old, but I just want my systems in good working order. If the system does everything I want why do I need the latest version of Gnome for example? A couple of extensions added and I am perfectly happy. Gnome Shell does not drastically change each release anyway. People use Xfce and Mate for this very reason, I don't want change just for the sake of change. Debian Developer's and the Community did an amazing job of fitting all the pieces together perfectly, they set the bar for quality on an LTS release! 

In my daily use, I have not ran into a single problem. I would go as far as recommending Debian 12 to new user's. If you can read, there is really nothing to it! I ran Ubuntu 22.04 for a year thinking it would get better over time, well, it didn't for me... The choices made in Debian 12 are sound and I have complete faith that updates are not very likely to break anything. Ubuntu kernel updates have screwed up my systems more times than I can count... Only my opinion but Ubuntu updates the kernel way too often for my liking, some security threats are so trivial. Ubuntu mainline kernels are hit and miss unfortunately too.

Debian has never given up on the desktop, their quality standards are very high, and the system is truly mine to do with as I see fit. What more could I ask for?

---

### Post by Rubi1200 on 2023-06-25
I tried Debian years ago (don't recall which release) but found I was struggling with it. Have to say, the Bookworm release is really smooth and I am busy testing it on a spare laptop. So far, so good.

---

### Post by donald187 on 2023-06-25
I installed it.  My system froze.  On the Gnome desktop the extensions app would turn off at times after reboot or login.  The sound would sometimes change after reboot or login.  Sound Juicer could see my usb dvd reader in settings but couldn't see the disk when I put one in.  A few years ago I would have jumped in with gusto fixing things but I seem to have lost my desire to do that now.  I bought my computer a year ago now.  I thought the problems would have been ironed out now.

---

### Post by exploder on 2023-06-25
I don't care to jump in and fix things either. Just curious, did you try different sessions?

---

### Post by donald187 on 2023-06-25
> **exploder said:**
> I don't care to jump in and fix things either. Just curious, did you try different sessions?

Do you mean switching from Wayland to X11?  I did on the advice of one of the Debian forum members but then ran into the Sound Juicer problem.  I didn't stick with it after that.  Maybe I'll try it again on X11 for a bit.

---

### Post by exploder on 2023-06-25
Be interested in your results.

---

### Post by donald187 on 2023-06-25
> **exploder said:**
> 
I do use Dash To Dock because I am not fond of the default hiding of the panel. 

Are you aware of the Debian package gnome-shell-extension-dashtodock which packages the Dash To Dock extension?  I've used it when on Debian.  I wouldn't ordinarily suggest something like this to someone who knows so much more than I do but there was a long time, knowledgeable member of the Debian forums who just recently became aware of these packaged extensions so you never know.

---

### Post by exploder on 2023-06-25
The dash was something Ubuntu did right! Dash To Dock works fine on Debian but there was another dock extension I tried by accident, it didn't work so well, lol. I do wish it loaded like Ubuntu's dock does though but you can't have everything I guess.

Edit: I did notice something interesting about partitioning. Installing Mint or Ubuntu created a 1 MB partition at the beginning of my NVME drive. I have seen others report this too. It does not really hurt anything but it is annoying having to hide it from the system because it is pointless having it display in the file manager. I did not have this installing Debian. Just though that was odd.

---

### Post by donald187 on 2023-06-25
> **donald187 said:**
> I installed it.  My system froze.  On the Gnome desktop the extensions app would turn off at times after reboot or login.  The sound would sometimes change after reboot or login.  Sound Juicer could see my usb dvd reader in settings but couldn't see the disk when I put one in.  A few years ago I would have jumped in with gusto fixing things but I seem to have lost my desire to do that now.  I bought my computer a year ago now.  I thought the problems would have been ironed out now.

Turns out Sound Juicer has the same problem on this CD on Ubuntu as well.  It has had problems dealing with this usb dvd drive in the past.  Asunder works though.

---

### Post by HuTkW$* on 2023-06-25
In 2023, what is the link between Debian and Ubuntu ?

---

### Post by #&amp;thj^% on 2023-06-25
Debian is an original Linux distro that was developed back in 1993 whereas the other (Ubuntu) I think around 2004 is a fork of it.

Due to the fact that Ubuntu uses the same packaging management system, it merges with *its specific* customization and adds in more rich features and patches into the release cycle when required. Whatever changes it does with its releases they push changes to the other base code.

---

### Post by mikodo on 2023-06-26
@ exploder ... 

 Thank you, for the well-written expose on Debian 12. I enjoyed reading it.

---

### Post by BBQdave on 2023-06-27
> **exploder said:**
> For all the complaining about the Debian installer being old and dated, it's actually perfect just the way it is! It's not pretty or fancy but it gives you choice. You can install any DE you like and all your packages are current! I guess they could pretty it up but it works perfectly and for all the more time spent using it, if it's not broke why fix it?

+1 And nice instructions with each step of the install. Comparing: Ubuntu installer is very polished and is a good standard to measure against.

> **exploder said:**
> The vanilla Gnome Debian provides is excellent! ...I mostly like Debian's default apps...

In my daily use, I have not ran into a single problem. I would go as far as recommending Debian 12 to new user's. If you can read, there is really nothing to it!

I have had the same experience, with both Debian 11 and now Debian 12. With the latest release, I did a vanilla install (Gnome) and added Google Chrome and GIMP. Simple easy. Makes a great workstation and provides all the function I need :)

---

### Post by exploder on 2023-06-30
If anyone prefers the way Ubuntu handles the dock, I used Dash to Dock and No overview at start-up. If you use the dark theme, Legacy (GTK3) Theme Auto Switcher will take care of the apps that have not been ported to GTK4. I personally like the way Ubuntu uses the dock rather than Gnome's default behavior. I had been so used to the dock being already set up in Ubuntu and thought I would share this to save people time that might be interested.

---

### Post by TheFu on 2023-06-30
> **BBQdave said:**
> +1 And nice instructions with each step of the install. Comparing: Ubuntu installer is very polished and is a good standard to measure against.

Provided you like the defaults that Canonical provides. If you want to do anything non-standard, the Ubuntu installers are less than great. 

Plus, they seem to change every LTS, so what we've learned for the prior release installer doesn't apply to the next installer. It is very frustrating.  If they had little improvements with each installer, then it would be different. But Canoncial likes to throw out everything and start over far too much.  NIH - Not Invented Here doesn't describe Canonical's installers. NITY does - Not Invented This Year.

If you want to point-n-click and manually install the OS, then it probably doesn't matter. OTOH, if you need to install to 500+ desktops using PXE boot and all these desktops have different hardware, then it is a big problem.

With Debian, we have an installer with incremental improvements, so any changes aren't complete, throw out everything previously known.

---

### Post by bernard010 on 2023-07-02
Debian 12 is very impressive. Calamares installer,
I installed xfce desktop.
The release contains:[B]
11,089[/B] new packages for a total count of **64,419** packages.
Just think Ubuntu is derived from Debian, this just makes Ubuntu..Better.
There is support for Secure Boot on ARM64
Even more

---

### Post by Dennis N on 2023-07-02
> **bernard010 said:**
> Debian 12 is very impressive. Calamares installer,
I installed xfce desktop...


I understand Calamares is only available from the Live media. I used the net install which uses Debian Installer and is the promoted iso at the top of the download page:

[https://www.debian.org/download](https://www.debian.org/download)

In the past, where I encountered Calamares (in particular, Manjaro) it was NOT LVM aware. In Manjaro's case, I put aside my objection and installed it anyway to a partition.

But, Debian Installer IS LVM aware, thank goodness. I wouldn't have done this Debian 12 (Gnome Desktop) install if LVM were not available.

That net installer itself is only 740 MB, and the completed install with the default applications was 4.9GB.

---

### Post by Tadaen_Sylvermane on 2023-07-03
I did a chroot installation a week or so ago with KDE via xorg. Not a hitch. Solid as a rock. Only 5 updates since. Using flatpak for Bottles it runs my Blizzard games perfectly.

I started my Linux journey with Debian back with Wheezy. It's only gotten better since.

---

### Post by exploder on 2023-07-03
I have done the net install on four systems now with no problems. The last install was the most interesting, it was on a Dell XPS 8940. I did the install using the Intel graphics and added an NVidia 1650 super after I got it running.Started out with the open source drivers, the system was really fast! Ended up installing the NVidia drivers in the end because apps started crashing. I was shocked by how fast the open source driver was under wayland!

Installing the NVidia drivers left me with just xserver sessions. The system works flawlessly now and it was interesting that system knew to change the available sessions accordingly. I followed the Debian instructions for installing the NVidia drivers. According to the documentation, my system should not suffer from issues with kernel updates breaking the NVidia drivers. 

I have installed Debian 12 on systems now with AMD, Intel and NVidia graphics with no issues. No WiFi issues of any kind either, all my systems use a WiFi connection. Hardware support seems excellent! I have been reading a lot of documentation! I came across this and it offers some great advice!

[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)

I am honestly blown away by the quality of Debian 12, so much attention to detail where it really matters. I thought it was odd that since release there have only been a handful of minor updates. Seems that if you build it right in the first place there is no need to hammer the user with updates. This takes some getting used to!

---

### Post by mikodo on 2023-07-05
Debian has extensive documentation.  (This is not an exhaustive list).

Here is the Debian Users' Manuals page. It is a good reference:

[https://www.debian.org/doc/user-manuals](https://www.debian.org/doc/user-manuals)

And Debian FrontPage. (Collection of Portals):

[https://wiki.debian.org/](https://wiki.debian.org/)

If one doesn't know where a page on a subject is, often a simple search term is successful in finding it. 

Example: ```
Debian Virtualization

```
finds:

[https://wiki.debian.org/SystemVirtualization](https://wiki.debian.org/SystemVirtualization)

and:

[https://debian-handbook.info/browse/stable/sect.virtualization.html](https://debian-handbook.info/browse/stable/sect.virtualization.html)

---

### Post by exploder on 2023-07-06
I read and followed the documentation for nvidia drivers! In Ubuntu 22.04 kernel updates usually break the nvidia drivers. I installed a kernel update yesterday in Debian and the drivers were fine. Glad I did a little reading!

---

### Post by gezzer2 on 2023-07-07
i dont post much as i can normally sort most things on Ubuntu myself. ive been using Ubuntu since 'warty' (still have the install CD) then moved over to Ubuntu LTS. never had that many problems except now with 'snaps'. i think i will give Debian a whirl its been a long time since i last used Debian. thanks for the heads up best of luck too all ...

edit. 
i have just finished --purging snaps completely from a clean minimum install of 22.04.2 LTS. i have the SSD partitioned boot/efi 555MB, / 55555MB, /home rest of the 1TB drive. (no swap) as i have 64GB of DDR4 installed.
now Ubuntu is running as smooth as silk and everything just works as it should and i mean everything. ain't the world wonderful when things just work. all the best ...
ps. it now can work with my Ubuntu (pixel 3a) phone ...

---

### Post by donald187 on 2023-07-16
> **exploder said:**
> Be interested in your results.

I'm on Debian 12 now.  I tried X11 and it just froze when clicking a link (making a selection on the Panda Express website.)  Generally I can't pick a cause for the freeze so this is kind of unusual.

---

### Post by exploder on 2023-07-23
@ donald187

What graphics card are you using?

---

### Post by donald187 on 2023-07-23
Intel UHD Integrated Graphics 730.

---

### Post by gezzer2 on 2023-07-23
ive just installed Debian 12 after having it in VM for a while and its working very well for me.
First i must thank Ubuntu because without using Ubuntu for many many years i would have struggled with Debian, so thank you Ubuntu.

just a note the installer on Debian 12 is something to behold it, like just, follow the yellow brick road ...

---

### Post by ajgreeny on 2023-07-23
I currently have a Debian 12 Xfce but using the sid (unstable) repos running as a VM in KVM/QEMU which is running about as smoothly as any distro I have ever used.

I originally installed it as Debian 11 Xfce back in September 2021 but then upgraded to Debian 12 (can't remember when) and finally changed repos to sid quite recently.  I was expecting some potential difficulties from using unstable repos but there were none, making me think that I could easily use Debian Unstable as my default daily distro.

No messing about removing snaps which is the first thing I do on all my *buntu installs, and if it continues to work as it is now it would be a simple change and I could continue with all the commands I currently use to manage my Xubuntu and the much easier availability of the non-free repos for things such as audio and video codecs adds yet another advantage to Debian that was more complicated in the past.

---

### Post by donald187 on 2023-11-07
> **donald187 said:**
> I installed it.  My system froze.  On the Gnome desktop the extensions app would turn off at times after reboot or login.  The sound would sometimes change after reboot or login.  Sound Juicer could see my usb dvd reader in settings but couldn't see the disk when I put one in.  A few years ago I would have jumped in with gusto fixing things but I seem to have lost my desire to do that now.  I bought my computer a year ago now.  I thought the problems would have been ironed out now.

The freezing seems to be fixed now.  I suspect it was because I  had installed Firefox from the binaries downloaded from Mozilla.  It  had only happened when Firefox was open.  Also I was using my profile from Ubuntu.  I don't know if that had anything to do with it. This time around I just used  Firefox-esr from the Debian repositories and no problems.  But some  update could have solved the problem too I suppose.

The other problems are minor, don't occur most of the time, and can easily be ignored.

---

