---
title: "gnome remote desktop"
date: 2023-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by maglin2 on 2023-03-04
In my 22.04 install I see I have gnome-remote-desktop, and looking at the manifest I see it's part of the the default install. 

According to the synaptic description 'This daemon enables GNOME to offer remote desktop sharing using VNC with PipeWire. It supports both GNOME on X and GNOME on Wayland. Remote sharing can be enabled and managed in the GNOME Settings app.'

The Help section says 'You can let other people view and control your desktop from another computer with a desktop viewing application.'

This doesn't seem like something I much want - I'd really rather that the facility for someone else to control my machine wasn't there at all unless I deliberately choose (as admin) to install it. Then it can't be enabled and insecurely configured by me or anyone else.

I take the same (admittedly uninformed) view of some of its dependencies like libvncserver and libfreerdpserver, which seem to march me along the way towards having a server installed in my box that someone can try to connect to.

Anyone else have thoughts - am I just being paranoid about this?

---

### Post by DuckHook on 2023-03-04
Not paranoid at all. I sympathize with your concern, given that I'm "paranoid" myself.

But I also sympathize with the devs. They are damned if they do and damned if they don't. We get innumerable gripes about Ubuntu being too difficult for ordinary users. So the devs have been hounded into the dumb&#8209;it&#8209;down syndrome over the years.

A similar option that drives me bonkers is the install option that allows automatic logins. No&#8209;challenge logins is a primary reason why Windows is such a malware cesspool. They condition users to avoid/ignore even the slightest inconveniences for the sake of frictionless (I would say "brainless") computing. This habituates users to treating security frivolously. It's a terrible habit that I had hoped would never be dragged in to Linux. So what happens? The devs decide to allow it in Ubuntu.

None of these options are turned on by default, so yeah, the typical refrain that you can ignore them is superficially accurate. The problem is that their mere presence is another concession to insecure computing, so I'm with you in questioning the inclusion of such stuff at all.

[Here is a contemporary thread]("https://ubuntuforums.org/showthread.php?t=2484562") that illustrates what problems can arise. The OP of this thread swears that he never turned on desktop sharing, in fact has turned it off, and yet it keeps turning back on by itself with every reboot. Apart from how scary this is in and of itself, the problem wouldn't even exist were it not for the presence of this daemon.

I would much prefer that stuff like this not be included by default. If a user wants desktop sharing (or auto login for that matter), they must take user&#8209;initiated steps to install the damn utilities. That way, they must also take ownership of their risky behaviour and not blame Ubuntu or come crying for help when they get pwned.

But hey… that's me. Most "ordinary users" think that I'm a paranoid crank.

---

### Post by #&amp;thj^% on 2023-03-04
From a previous bug:
```
sudo unlink /etc/systemd/user/gnome-session.target.wants/gnome-remote-desktop.service
```

Now when enabling/disabling the remote desktop service a symlink is instead created/removed at

```
~/.config/systemd/user/gnome-session.target.wants/gnome-remote-desktop.service
```

and as such the user's on/off preference is respected.
Will the OP confirm?

---

### Post by DuckHook on 2023-03-04
Thanks for this! I've linked to your proposed solution in that other thread. Feel free to dive in over there.

---

### Post by #&amp;thj^% on 2023-03-04
That's what we do here, no thanks needed. ;)
I'll do what I can here DuckHook....PS good to see you stomping around in the forums lately.

---

### Post by DuckHook on 2023-03-04
To further reinforce @maglin2's concerns:

RDP is an insecure protocol. Its inclusion by default presents a large juicy attack surface. In my not&#8209;so&#8209;humble opinion, the only secure way to use it is through an encrypted tunnel: either SSH or a VPN. Any other way is a walking dumpster fire.

It's inclusion is therefore *very* problematic. Once again, the knowledgeable few will know how to guard against its dangers; the large majority will not. They will just use it as is and risk getting themselves pwned.

But what's a developer to do? The recent pandemic has made working remotely a necessity. Windows refugees have been conditioned to use RDP and demand its inclusion. They don't know X2Go and wouldn't use it anyway. For one thing, it can't be used except in a pure X environment, so if one end is Windows, it's a non&#8209;starter. For another, there will be no end of griping and whining if they can't use something they are used to. So, the devs&#8212;caught between hammer and anvil&#8212;hold their noses and include RDP in the distro.

I think the inclusion of RDP is a mistake. But I'm not about to blame Canonical.

---

### Post by maglin2 on 2023-03-05
Thanks DuckHook. It was reading the thread you linked in #2 that got me looking at the gnome desktop sharing setting for the first time. 
I note your comment 'the knowledgeable few will know how to guard against its dangers', and freely admit that I am not among them.

---

### Post by DuckHook on 2023-03-05
Learning how to use RDP safely is not that hard. Part of the problem is that some people start out convinced that it is hard, so don't bother learning. Most don't even know that they are in danger.

A VPN is actually pretty easy to set up and plenty of walk&#8209;throughs are available online. SSH is also a reliable old standby and setting RDP up to tunnel through SSH is not too challenging either. Websearches will return good tutorials that are pretty straightforward to implement.

I suspect that you are more knowledgeable than you give yourself credit for.

A family member was hacked a few years ago through RDP, so it's rather personal for me. She used a poor password, the default port and no safeguards like fail2ban. It took no more than a few hours from the time she opened the port for her computer to get trashed. The vandals wiped her whole HDD while she was momentarily away from the computer and she couldn't understand why her work had suddenly disappeared. It could have been worse&#8212;at least they didn't make off with her bank credentials or other sensitive stuff. She lost a lot of photos though. No backups. A harsh hard lesson.

---

### Post by maglin2 on 2023-03-06
The more I hear the scarier it becomes!
Thanks for the info, but I don't think I am ever likely to have any use for this feature (I never have in the last ten years).
I'm not happy to remove a package that is part of the default install. Maybe I'll see if I can track down the service used and mask it.

---

### Post by DuckHook on 2023-03-06
> **maglin2 said:**
> The more I hear the scarier it becomes!
Thanks for the info, but I don't think I am ever likely to have any use for this feature (I never have in the last ten years).
I'm not happy to remove a package that is part of the default install. Maybe I'll see if I can track down the service used and mask it.
Good point. Though I don't like the fact that I have RDP installed by default, I too am a bit hesitant to outright nuke it. How deeply is it hooked in to the OS? What needed dependencies will it take with it?

I have no problem with purging apps like Firefox and Libreoffice, but those are apps. This is a system service.

If I work up the energy to spin up a VM and purge it there (where it won't damage my real system, I will report results back to this thread.

---

### Post by maglin2 on 2023-03-07
I tried rdepends
```

$ apt-cache rdepends --installed gnome-remote-desktop
gnome-remote-desktop
Reverse Depends:
  gnome-control-center
  gnome-shell
  gnome-shell
  ubuntu-desktop-minimal
  ubuntu-desktop
```

---

### Post by maglin2 on 2023-03-07
Tried in VM and as expected gnome-control-center (ie settings) disappears. A whole lot of other packages were left at the mercy of autoremove.

Interestingly this doesn't happen with 22.10 - there it is possible to remove gnome-remote-desktop without apparent collateral damage. FreeRDP goes, along with a TPM package, but they both seem specific to RDP desktop sharing. 
Perhaps someone influential doesn't think its compulsory inclusion was such a good thing.

---

### Post by #&amp;thj^% on 2023-03-07
Your rdepends looks different than mine IE:
```
apt rdepends gnome-remote-desktop
gnome-remote-desktop
Reverse Depends:
  Breaks: gnome-control-center (<< 42)
  Recommends: gnome
  Recommends: gnome-shell
  Recommends: gnome-control-center (>= 42)

```
I don't see a show stopper there:
```
sudo apt remove --auto-remove gnome-remote-desktop -s
```
curious to see that output
Also jbicha is working here: [https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/1825](https://gitlab.gnome.org/GNOME/gnome-control-center/-/issues/1825)
Maybe a lending hand at helping here.
I just did a VM install:
```
apt policy gnome-remote-desktop
gnome-remote-desktop:
  Installed: 43.0-0ubuntu1
  Candidate: 43.2-0ubuntu1
  Version table:
     43.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic-updates/main amd64 Packages
 *** 43.0-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        100 /var/lib/dpkg/status

```
now:
```
sudo apt autoremove --purge gnome-remote-desktop
[sudo] password for oem: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  gnome-remote-desktop* libfreerdp-server2-2* libfreerdp2-2* libtss2-tctildr0*
  libwinpr2-2*
0 upgraded, 0 newly installed, 5 to remove and 129 not upgraded.
3 not fully installed or removed.
After this operation, 3,906 kB disk space will be freed.
Do you want to continue? [Y/n] 

```
Of course I said yes!
I'll now do the 129 packages for the update, and post back
The Verdict is.....2 big thumbs up:
```
apt policy gnome-remote-desktop
gnome-remote-desktop:
  Installed: (none)
  Candidate: 43.2-0ubuntu1
  Version table:
     43.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic-updates/main amd64 Packages
     43.0-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
oem@oem-Standard-PC-Q35-ICH9-2009:~$ apt policy gnome-control-center
gnome-control-center:
  Installed: 1:43.0-1ubuntu2
  Candidate: 1:43.0-1ubuntu2
  Version table:
 *** 1:43.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        100 /var/lib/dpkg/status
oem@oem-Standard-PC-Q35-ICH9-2009:~$ apt policy gnome-shell
gnome-shell:
  Installed: 43.1-0ubuntu1
  Candidate: 43.1-0ubuntu1
  Version table:
 *** 43.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     43.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
oem@oem-Standard-PC-Q35-ICH9-2009:~$ 


```
There you go.... gone and long forgotten. LOL

---

### Post by maglin2 on 2023-03-07
Thanks.
Yes, different output for rdepends (never used it before, so quite possibly I messed up!)

Here it is using apt as you did (rather than apt-cache)

 ```
$ apt rdepends gnome-remote-desktop
gnome-remote-desktop
Reverse Depends:
  Depends: gnome-control-center (>= 42)
  Recommends: gnome-shell
  Recommends: gnome-shell
  Recommends: gnome
  Recommends: budgie-desktop-environment
  Recommends: ubuntu-desktop-minimal
  Recommends: ubuntu-desktop
```

Just a thought are you on 22.04 or 22.10 (or even Lunar)?

---

### Post by maglin2 on 2023-03-07
And the simulation
```
$ sudo apt remove --auto-remove gnome-remote-desktop -s
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED
  apg gnome-control-center gnome-control-center-faces gnome-online-accounts
  gnome-remote-desktop libcolord-gtk1 libfreerdp-server2-2 libgsound0
  libgssdp-1.2-0 libgupnp-1.2-1 libgupnp-av-1.0-3 libgupnp-dlna-2.0-4
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libvncserver1 mobile-broadband-provider-info
  network-manager-gnome python3-certifi python3-macaroonbakery
  python3-protobuf python3-pymacaroons python3-requests python3-rfc3339
  python3-tz rygel ubuntu-desktop ubuntu-desktop-minimal
0 to upgrade, 0 to newly install, 29 to remove and 0 not to upgrade.
Remv ubuntu-desktop [1.481]
Remv ubuntu-desktop-minimal [1.481]
Remv gnome-control-center [1:41.7-0ubuntu0.22.04.6]
Remv apg [2.2.3.dfsg.1-5build2]
Remv gnome-control-center-faces [1:41.7-0ubuntu0.22.04.6]
Remv gnome-online-accounts [3.44.0-1ubuntu1]
Remv gnome-remote-desktop [42.7-0ubuntu1]
Remv libcolord-gtk1 [0.3.0-1]
Remv libfreerdp-server2-2 [2.6.1+dfsg1-3ubuntu2.3]
Remv libgsound0 [1.0.3-2build1]
Remv rygel [0.40.3-1ubuntu2]
Remv librygel-server-2.6-2 [0.40.3-1ubuntu2]
Remv librygel-db-2.6-2 [0.40.3-1ubuntu2]
Remv librygel-core-2.6-2 [0.40.3-1ubuntu2] [librygel-renderer-2.6-2:amd64 ]
Remv libgssdp-1.2-0 [1.4.0.1-2build1] [libgupnp-1.2-1:amd64 librygel-renderer-2.6-2:amd64 ]
Remv librygel-renderer-2.6-2 [0.40.3-1ubuntu2] [libgupnp-1.2-1:amd64 ]
Remv libgupnp-1.2-1 [1.4.3-1]
Remv libgupnp-av-1.0-3 [0.14.0-3]
Remv libgupnp-dlna-2.0-4 [0.12.0-3]
Remv libvncserver1 [0.9.13+dfsg-3build2]
Remv mobile-broadband-provider-info [20220315-1]
Remv network-manager-gnome [1.24.0-1ubuntu3]
Remv python3-macaroonbakery [1.3.1-2ubuntu0.1]
Remv python3-requests [2.25.1+dfsg-2]
Remv python3-certifi [2020.6.20-1]
Remv python3-protobuf [3.12.4-1ubuntu7]
Remv python3-pymacaroons [0.13.0-4]
Remv python3-rfc3339 [1.1-3]
Remv python3-tz [2022.1-1ubuntu0.22.04.0]
```

---

### Post by #&amp;thj^% on 2023-03-07
> **maglin2 said:**
> Thanks.
Yes, different output for rdepends (never used it before, so quite possibly I messed up!)

Here it is using apt as you did (rather than apt-cache)

 ```
$ apt rdepends gnome-remote-desktop
gnome-remote-desktop
Reverse Depends:
  Depends: gnome-control-center (>= 42)
  Recommends: gnome-shell
  Recommends: gnome-shell
  Recommends: gnome
  Recommends: budgie-desktop-environment
  Recommends: ubuntu-desktop-minimal
  Recommends: ubuntu-desktop
```

Just a thought are you on 22.04 or 22.10 (or even Lunar)?

22.10
If you want I'll upgrade to Lunar

---

### Post by maglin2 on 2023-03-07
OK -that explains the different behaviour. 
I got much the same with 22.10 VM, but I run 22.04.

---

### Post by #&amp;thj^% on 2023-03-07
> **maglin2 said:**
> And the simulation
```
$ sudo apt remove --auto-remove gnome-remote-desktop -s
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED
  apg gnome-control-center gnome-control-center-faces gnome-online-accounts
  gnome-remote-desktop libcolord-gtk1 libfreerdp-server2-2 libgsound0
  libgssdp-1.2-0 libgupnp-1.2-1 libgupnp-av-1.0-3 libgupnp-dlna-2.0-4
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libvncserver1 mobile-broadband-provider-info
  network-manager-gnome python3-certifi python3-macaroonbakery
  python3-protobuf python3-pymacaroons python3-requests python3-rfc3339
  python3-tz rygel ubuntu-desktop ubuntu-desktop-minimal
0 to upgrade, 0 to newly install, 29 to remove and 0 not to upgrade.
Remv ubuntu-desktop [1.481]
Remv ubuntu-desktop-minimal [1.481]
Remv gnome-control-center [1:41.7-0ubuntu0.22.04.6]
Remv apg [2.2.3.dfsg.1-5build2]
Remv gnome-control-center-faces [1:41.7-0ubuntu0.22.04.6]
Remv gnome-online-accounts [3.44.0-1ubuntu1]
Remv gnome-remote-desktop [42.7-0ubuntu1]
Remv libcolord-gtk1 [0.3.0-1]
Remv libfreerdp-server2-2 [2.6.1+dfsg1-3ubuntu2.3]
Remv libgsound0 [1.0.3-2build1]
Remv rygel [0.40.3-1ubuntu2]
Remv librygel-server-2.6-2 [0.40.3-1ubuntu2]
Remv librygel-db-2.6-2 [0.40.3-1ubuntu2]
Remv librygel-core-2.6-2 [0.40.3-1ubuntu2] [librygel-renderer-2.6-2:amd64 ]
Remv libgssdp-1.2-0 [1.4.0.1-2build1] [libgupnp-1.2-1:amd64 librygel-renderer-2.6-2:amd64 ]
Remv librygel-renderer-2.6-2 [0.40.3-1ubuntu2] [libgupnp-1.2-1:amd64 ]
Remv libgupnp-1.2-1 [1.4.3-1]
Remv libgupnp-av-1.0-3 [0.14.0-3]
Remv libgupnp-dlna-2.0-4 [0.12.0-3]
Remv libvncserver1 [0.9.13+dfsg-3build2]
Remv mobile-broadband-provider-info [20220315-1]
Remv network-manager-gnome [1.24.0-1ubuntu3]
Remv python3-macaroonbakery [1.3.1-2ubuntu0.1]
Remv python3-requests [2.25.1+dfsg-2]
Remv python3-certifi [2020.6.20-1]
Remv python3-protobuf [3.12.4-1ubuntu7]
Remv python3-pymacaroons [0.13.0-4]
Remv python3-rfc3339 [1.1-3]
Remv python3-tz [2022.1-1ubuntu0.22.04.0]
```
:!:NO NO:!:, I don't like this at all...Don't go there unless you want to do some rabbit hole exercise.

---

### Post by #&amp;thj^% on 2023-03-07
Hold tight I'll beck back.

---

### Post by maglin2 on 2023-03-07
> **1fallen said:**
> :!:NO NO:!:, I don't like this at all...Don't go there unless you want to do some rabbit hole exercise.

Nope - that's what I'm trying to avoid with 22.04 (with 22.10 it's painless - at least in a VM).

With 22.04 I've tried masking service instead.

Of course this is a bit belt and braces anyway, since I don't (and won't) have desktop sharing enabled.


```
$ gsettings get org.gnome.desktop.remote-desktop.rdp enable
false
```

and I have no intention of opening any ports in UFW

---

### Post by #&amp;thj^% on 2023-03-07
maglin2, I ended up just fine, I'm not sure why yours wants remove some of what I see, so your mileage may vary.
It may have to do with what you have installed after you installed>> 22.04
```
inxi -SP && apt policy gnome-remote-desktop
System:
  Host: oem-Standard-PC-Q35-ICH9-2009 Kernel: 5.19.0-35-generic x86_64
    bits: 64 Desktop: GNOME 43.1 Distro: Ubuntu 22.04 (Jammy Jellyfish)
Partition:
  ID-1: / size: 17.71 GiB used: 3.63 GiB (20.5%) fs: zfs
    logical: rpool/ROOT/ubuntu_ws4bqe
  ID-2: /boot size: 1.5 GiB used: 284.2 MiB (18.5%) fs: zfs
    logical: bpool/BOOT/ubuntu_ws4bqe
  ID-3: /boot/efi size: 512 MiB used: 15.9 MiB (3.1%) fs: vfat
    dev: /dev/vda2
  ID-4: /var/log size: 14.08 GiB used: 2.2 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_ws4bqe/var/log
  ID-5: swap-1 size: 2.62 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/vda3
gnome-remote-desktop:
  Installed: (none)
  Candidate: 42.7-0ubuntu1
  Version table:
     42.7-0ubuntu1 500 (phased 0%)
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     42.0-4ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
oem@oem-Standard-PC-Q35-ICH9-2009:~$ 


```
I did find this very interesting though:
```
apt policy gnome-remote-desktop
gnome-remote-desktop:
  Installed: (none)
  Candidate: 42.7-0ubuntu1
  Version table:
     42.7-0ubuntu1 500 **[COLOR="#FF0000"](phased 0%)[/COLOR]**
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     42.0-4ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

---

### Post by #&amp;thj^% on 2023-03-07
> **maglin2 said:**
> 

With 22.04 I've tried masking service instead.

Of course this is a bit belt and braces anyway, since I don't (and won't) have desktop sharing enabled.


```
$ gsettings get org.gnome.desktop.remote-desktop.rdp enable
false
```

and I have no intention of opening any ports in UFW

So wait now, did that actually work for you?
```
systemctl status gnome.desktop.remote-desktop
Unit gnome.desktop.remote-desktop.service could not be found.

```
Put to bed and R.I.P

---

### Post by #&amp;thj^% on 2023-03-07
Lunar was simple:
```
apt policy gnome-remote-desktop && inxi -p
gnome-remote-desktop:
  Installed: (none)
  Candidate: 43.3-1
  Version table:
     43.3-1 1001
       1001 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lunar/main amd64 Packages
Partition:
  ID-1: / size: 420.65 GiB used: 6.03 GiB (1.4%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu
  ID-2: /boot size: 519 MiB used: 288.1 MiB (55.5%) fs: zfs
    logical: bpool/BOOT/ubuntu_gtwslu
  ID-3: /boot/efi size: 511 MiB used: 38.2 MiB (7.5%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-4: /home/me size: 419.92 GiB used: 5.3 GiB (1.3%) fs: zfs
    logical: rpool/USERDATA/me_ki0pt5
  ID-5: /root size: 414.62 GiB used: 3 MiB (0.0%) fs: zfs
    logical: rpool/USERDATA/root_ki0pt5
  ID-6: /run/keystore/rpool size: 437 MiB used: 28 KiB (0.0%) fs: ext4
    dev: /dev/dm-0
  ID-7: /srv size: 414.62 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/srv
  ID-8: /usr/local size: 414.62 GiB used: 512 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/usr/local
  ID-9: /var/games size: 414.62 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/games
  ID-10: /var/lib size: 417.64 GiB used: 3.02 GiB (0.7%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/lib
  ID-11: /var/lib/AccountsService size: 414.62 GiB used: 256 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/AccountsService
  ID-12: /var/lib/NetworkManager size: 414.62 GiB used: 384 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_gtwslu/var/lib/NetworkManager
  ID-13: /var/lib/apt size: 414.7 GiB used: 86.1 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/lib/apt
  ID-14: /var/lib/dpkg size: 414.7 GiB used: 82.8 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/lib/dpkg
  ID-15: /var/log size: 414.67 GiB used: 50.1 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/log
  ID-16: /var/mail size: 414.62 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/mail
  ID-17: /var/snap size: 414.62 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/snap
  ID-18: /var/spool size: 414.62 GiB used: 384 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/spool
  ID-19: /var/www size: 414.62 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_gtwslu/var/www
  ID-20: swap-1 size: 2 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1

```
and:
```
me@me-ThinkPad-X1-Carbon-7th:~$ systemctl status gnome-remote-desktop
Unit gnome-remote-desktop.service could not be found.
me@me-ThinkPad-X1-Carbon-7th:~$ 


```
I'm taking jbicha off my Christmas card list, I'll pour a beer with him but No  Christmas card :P

---

### Post by deadflowr on 2023-03-07
look at
```
systemctl --user status gnome-remote-desktop
```

Edit; You can also use the gdrctl command like
```
grdctl status
```

---

### Post by #&amp;thj^% on 2023-03-07
> **deadflowr said:**
> look at
```
systemctl --user status gnome-remote-desktop
```

Edit; You can also use the gdrctl command like
```
grdctl status
```

+1 Nice
```
$ systemctl --user status gnome-remote-desktop
Unit gnome-remote-desktop.service could not be found.
me@me-ThinkPad-X1-Carbon-7th:~$ grdctl status
Command 'grdctl' not found, but can be installed with:
sudo apt install gnome-remote-desktop

```
where did you think of that? ;)

---

### Post by DuckHook on 2023-03-07
deadflowr beat me to it.

Dealing only with LTS (Jammy):
```
duckhook@Zeus:~$  systemctl --user status gnome-remote-desktop
&#9675; gnome-remote-desktop.service - GNOME Remote Desktop
     Loaded: loaded (/usr/lib/systemd/user/gnome-remote-desktop.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
duckhook@Zeus:~$  grdctl status
RDP:
	Status: disabled
	TLS certificate: 
	TLS key: 
	View-only: yes
	Username: (empty)
	Password: (empty)
VNC:
	Status: disabled
	Auth method: prompt
	View-only: yes
	Password: (empty)

```
In its pristine state, the TLS certificate and key are empty. This makes it very difficult (though not impossible) for outsiders to gain entry. However, it takes just one activation for these keys to be created and these fields populated. Best then to mask the service altogether.

For the benefit of lurkers out there:
```
systemctl --user mask gnome-remote-desktop.service
```
If using Kinetic (or higher), then, based on maglin2's and 1fallen's research, it is "safest" to:```
sudo apt purge gnome-remote-desktop
```Caveat: while this does delete the daemon altogether thus making it impossible for anyone to run it, we don't know what it breaks when we eventually must do-release-upgrade. The devs may decide to make it system dependent again. Thus, "safest" is true in one sense but maybe not in another.

---

### Post by #&amp;thj^% on 2023-03-07
> **DuckHook said:**
> Caveat: while this does delete the daemon altogether thus making it impossible for anyone to run it, we don't know what it breaks when we eventually must do-release-upgrade. The devs may decide to make it system dependent again. Thus, "safest" is true in one sense but maybe not in another.

We are good through Lunar so far.
Upgrade from jammy to lunar, still won't pull remote-desk back in:
```
sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libabsl20210324 libbpf0 libflac8 libfwupdplugin7 libgs9-common
  libgssdp-1.2-0 libgupnp-1.2-1 libldap-2.5-0 liblerc3 libperl5.34
  libplacebo192 libpoppler123 libprotobuf23 libpython3.10
  libpython3.10-minimal libpython3.10-stdlib libqpdf28 libquadmath0
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 netkit-telnet perl-modules-5.34 python3.10
  python3.10-minimal
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libgs9
The following NEW packages will be installed:
  cron-daemon-common fonts-sil-annapurna gcc-13-base gir1.2-gnomeautoar-0.1
  libabsl20220623 libboost-filesystem1.74.0 libboost-iostreams1.74.0
  libboost-locale1.74.0 libboost-thread1.74.0 libbpf1 libclucene-contribs1v5
  libclucene-core1v5 libeditorconfig0 libeot0 libexttextcat-2.0-0
  libexttextcat-data libflac12 libgpgmepp6 libgs-common libgs10 libgs10-common
  libgssdp-1.6-0 libgupnp-1.6-0 libhwy1 libicu72 libjxl0.7 liblangtag-common
  liblangtag1 liblc3-0 libldap2 liblerc4 libmbim-utils libmhash2
  libmythes-1.2-0 liborcus-0.17-0 liborcus-parser-0.17-0 libperl5.36
  libplacebo208 libpoppler126 libprotobuf32 libpython3.11
  libpython3.11-minimal libpython3.11-stdlib libqmi-utils libqpdf29
  libraptor2-0 librasqal3 librav1e0 librdf0 libreoffice-common
  libreoffice-core libreoffice-style-colibre libreoffice-style-yaru
  librevenge-0.0-0 librygel-core-2.8-0 librygel-db-2.8-0
  librygel-renderer-2.8-0 librygel-server-2.8-0 libtiff6 libuno-cppu3
  libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3
  libuno-salhelpergcc3-3 libxmlsec1 libxmlsec1-nss libyajl2
  linux-headers-6.1.0-16 linux-headers-6.1.0-16-generic
  linux-image-6.1.0-16-generic linux-modules-6.1.0-16-generic
  linux-modules-extra-6.1.0-16-generic perl-modules-5.36 python3-certifi
  python3-idna python3-jaraco.classes python3-markdown-it python3-mdurl
  python3-pygments python3-requests python3-rich python3-uno python3-urllib3
  python3.11 python3.11-minimal uno-libs-private ure
The following packages will be upgraded:
  accountsservice acl adduser alsa-ucm-conf alsa-utils anacron apparmor apport
  apport-gtk appstream apt apt-config-icons apt-config-icons-hidpi apt-utils
  aptdaemon aptdaemon-data at-spi2-common at-spi2-core base-files base-passwd
  bash bind9-dnsutils bind9-host bind9-libs bluez bluez-cups bluez-obexd bolt
  brltty bsdextrautils bsdutils btrfs-progs bubblewrap busybox-initramfs
  busybox-static ca-certificates chromium-codecs-ffmpeg-extra
  command-not-found console-setup console-setup-linux coreutils cpp cpp-12
  cracklib-runtime cron cryptsetup cryptsetup-bin cryptsetup-initramfs
  cups-browsed cups-filters cups-filters-core-drivers dash dbus dbus-bin
  dbus-daemon dbus-session-bus-common dbus-system-bus-common dbus-user-session
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service debconf
  debconf-i18n debianutils desktop-file-utils dictionaries-common diffutils
  dirmngr distro-info distro-info-data dns-root-data dnsmasq-base dpkg
  dpkg-repack e2fsprogs ed eject emacsen-common enchant-2 eog espeak-ng-data
  evince evince-common evolution-data-server evolution-data-server-common
  fdisk file firefox firmware-sof-signed fontconfig fontconfig-config
  fonts-dejavu-core fonts-deva fonts-deva-extra fonts-freefont-ttf fonts-gargi
  fonts-gubbi fonts-gujr fonts-kalapi fonts-lohit-beng-bengali
  fonts-lohit-deva fonts-lohit-guru fonts-opensymbol fonts-samyak-deva
  fonts-samyak-gujr fonts-samyak-mlym fonts-samyak-taml fonts-smc
  fonts-smc-chilanka fonts-smc-manjari fonts-urw-base35
  foomatic-db-compressed-ppds fuse3 fwupd fwupd-signed gcc-12-base gdb gdisk
  gdm3 geoclue-2.0 gettext-base ghostscript ghostscript-x
  gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-freedesktop gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gdm-1.0 gir1.2-geoclue-2.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomedesktop-4.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtk-4.0 gir1.2-gweather-4.0
  gir1.2-handy-1 gir1.2-harfbuzz-0.0 gir1.2-ibus-1.0 gir1.2-mutter-11
  gir1.2-nm-1.0 gir1.2-nma-1.0 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gir1.2-peas-1.0 gir1.2-secret-1 gir1.2-snapd-2 gir1.2-soup-3.0
  gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gir1.2-wnck-3.0 gjs glib-networking
  glib-networking-common glib-networking-services gnome-accessibility-themes
  gnome-bluetooth-3-common gnome-bluetooth-sendto gnome-calculator
  gnome-characters gnome-control-center gnome-control-center-data
  gnome-control-center-faces gnome-desktop3-data gnome-disk-utility
  gnome-font-viewer gnome-initial-setup gnome-menus gnome-session-canberra
  gnome-shell gnome-shell-common gnome-shell-extension-appindicator
  gnome-shell-extension-desktop-icons-ng gnome-shell-extension-ubuntu-dock
  gnome-system-monitor gnome-terminal gnome-terminal-data gnome-text-editor
  gnome-themes-extra gnome-themes-extra-data gnupg gnupg-l10n gnupg-utils gpg
  gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv grep groff-base
  grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-pc grub-pc-bin
  grub2-common gsettings-desktop-schemas gstreamer1.0-alsa gstreamer1.0-gl
  gstreamer1.0-libav gstreamer1.0-packagekit gstreamer1.0-pipewire
  gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps
  gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-tools
  gstreamer1.0-vaapi gstreamer1.0-x gtk-update-icon-cache gvfs gvfs-backends
  gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hdparm hostname hplip
  hplip-data ibus ibus-data ibus-gtk ibus-gtk3 ibus-gtk4 ibus-table im-config
  info init init-system-helpers initramfs-tools initramfs-tools-bin
  initramfs-tools-core install-info intel-media-va-driver intel-microcode inxi
  ipp-usb iproute2 iptables iputils-ping iputils-tracepath irqbalance
  isc-dhcp-client isc-dhcp-common iso-codes iucode-tool kbd
  keyboard-configuration klibc-utils kmod kpartx kpartx-boot krb5-locales
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base language-selector-common language-selector-gnome
  less libaacs0 libaccountsservice0 libacl1 libadwaita-1-0 libaio1 libaom3
  libapparmor1 libappstream4 libapt-pkg6.0 libarchive13 libasound2
  libasound2-data libass9 libassuan0 libatk-adaptor libatk-bridge2.0-0
  libatk1.0-0 libatomic1 libatopology2 libatspi2.0-0 libattr1 libaudit-common
  libaudit1 libauthen-sasl-perl libavcodec59 libavfilter8 libavformat59
  libavutil57 libayatana-appindicator3-1 libayatana-indicator3-7
  libbabeltrace1 libbdplus0 libblas3 libblkid1 libblockdev-crypto2
  libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 libblockdev-part2
  libblockdev-swap2 libblockdev-utils2 libblockdev2 libbluetooth3 libbluray2
  libboost-regex1.74.0 libbrlapi0.8 libbrotli1 libbs2b0 libbsd0 libcaca0
  libcairo-gobject-perl libcairo-gobject2 libcairo-perl
  libcairo-script-interpreter2 libcairo2 libcairomm-1.0-1v5 libcamel-1.2-64
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcap-ng0 libcap2 libcap2-bin libcdio-cdda2 libcdio-paranoia2 libcdio19
  libclone-perl libcom-err2 libcrack2 libcrypt1 libcryptsetup12
  libcupsfilters1 libcurl3-gnutls libcurl4 libdb5.3 libdbus-1-3
  libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdebian-installer4 libdebuginfod-common libdebuginfod1 libdee-1.0-4
  libdeflate0 libdjvulibre-text libdjvulibre21 libdpkg-perl libdrm-amdgpu1
  libdrm-common libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libdw1
  libebackend-1.2-11 libebook-1.2-21 libebook-contacts-1.2-4 libecal-2.0-2
  libedata-book-1.2-27 libedata-cal-2.0-2 libedataserver-1.2-27
  libedataserverui-1.2-4 libedit2 libegl-mesa0 libegl1 libelf1 libenchant-2-2
  libencode-locale-perl libespeak-ng1 libevdocument3-4 libevview3-3 libexempi8
  libexiv2-27 libexpat1 libext2fs2 libextutils-depends-perl libfdisk1 libffi8
  libfftw3-single3 libfido2-1 libfile-basedir-perl libfile-desktopentry-perl
  libfile-fcntllock-perl libflashrom1 libflite1 libfont-afm-perl
  libfontconfig1 libfontembed1 libfreetype6 libftdi1-2 libfuse3-3 libfwupd2
  libgbm1 libgcc-s1 libgcrypt20 libgd3 libgdbm-compat4 libgdbm6
  libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgdm1
  libgeoclue-2-0 libgeocode-glib-2-0 libgfortran5 libgirepository-1.0-1
  libgjs0g libgl1 libgl1-amber-dri libgl1-mesa-dri libglapi-mesa libgles2
  libglib-object-introspection-perl libglib-perl libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglibmm-2.4-1v5 libglu1-mesa libglvnd0 libglx-mesa0
  libglx0 libgme0 libgmp10 libgnome-bg-4-2 libgnome-bluetooth-3.0-13
  libgnome-bluetooth-ui-3.0-13 libgnome-desktop-3-20 libgnome-desktop-4-2
  libgnome-menu-3-0 libgnome-rr-4-2 libgnutls30 libgomp1 libgpg-error0
  libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port12 libgs9-common
  libgsm1 libgspell-1-2 libgspell-1-common libgssapi-krb5-2
  libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-4-1
  libgtk-4-bin libgtk-4-common libgtk3-perl libgtksourceview-5-0
  libgtksourceview-5-common libgweather-4-0 libgweather-4-common libgxps2
  libhandy-1-0 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.7-0 libibus-1.0-5 libical3 libidn2-0
  libiec61883-0 libigdgmm12 libimobiledevice6 libinput-bin libinput10
  libio-socket-ssl-perl libip4tc2 libip6tc2 libipc-system-simple-perl
  libjack-jackd2-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-c5 libk5crypto3
  libkeyutils1 libklibc libkmod2 libkpathsea6 libkrb5-3 libkrb5support0
  libksba8 liblapack3 liblcms2-2 liblcms2-utils libldap-common libldb2
  libllvm15 liblocale-gettext-perl liblouis-data liblouis20 liblouisutdml-bin
  liblouisutdml-data liblouisutdml9 libltdl7 liblua5.3-0
  liblwp-mediatypes-perl liblz4-1 liblzma5 libmagic-mgc libmagic1
  libmailtools-perl libmaxminddb0 libmbedcrypto7 libmbim-glib4 libmbim-proxy
  libmfx1 libmm-glib0 libmount1 libmozjs-102-0 libmpc3 libmpfr6 libmpg123-0
  libmutter-11-0 libmysofa1 libnautilus-extension4 libncurses6 libncursesw6
  libndp0 libnet-dbus-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnetplan0 libnewt0.52 libnftables1 libnftnl11 libnghttp2-14 libnm0
  libnma-common libnma-gtk4-0 libnma0 libnspr4 libnss-mdns libnss-systemd
  libnss3 libntfs-3g89 libnuma1 libnvpair3linux libogg0 libopencore-amrnb0
  libopencore-amrwb0 libopengl0 libopenjp2-7 libopenmpt0 libopus0 liborc-0.4-0
  libp11-kit0 libpackagekit-glib2-18 libpam-cap libpam-modules
  libpam-modules-bin libpam-pwquality libpam-runtime libpam-sss libpam-systemd
  libpam0g libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangoxft-1.0-0 libparted-fs-resize0 libparted2 libpcap0.8 libpcaudio0
  libpci3 libpciaccess0 libpcre2-32-0 libpcre2-8-0 libpcre3 libpeas-1.0-0
  libpeas-common libphonenumber8 libpipeline1 libpipewire-0.3-0
  libpipewire-0.3-common libpipewire-0.3-modules libpixman-1-0 libplist3
  libplymouth5 libpng16-16 libpocketsphinx3 libpoppler-cpp0v5 libpoppler-glib8
  libpopt0 libportal-gtk4-1 libportal1 libpostproc56 libprotobuf-c1 libpsl5
  libpulse-mainloop-glib0 libpulse0 libpwquality-common libpwquality1
  libpython3-stdlib libpython3.10 libpython3.10-minimal libpython3.10-stdlib
  libqmi-glib5 libqmi-proxy libquadmath0 libraqm0 libreadline8 librest-1.0-0
  librubberband2 libsamplerate0 libsane-common libsane-hpaio libsane1
  libsasl2-2 libsasl2-modules libsasl2-modules-db libsasl2-modules-gssapi-mit
  libseccomp2 libsecret-1-0 libsecret-common libselinux1 libsemanage-common
  libsemanage2 libserd-0-0 libsigc++-2.0-0v5 libslang2 libsmartcols1
  libsmbclient libsnapd-glib-2-1 libsnappy1v5 libsndfile1 libsnmp-base
  libsnmp40 libsord-0-0 libsoup-3.0-0 libsoup-3.0-common
  libsource-highlight-common libsource-highlight4v5 libspa-0.2-bluetooth
  libspa-0.2-modules libspectre1 libspeechd2 libspeex1 libsphinxbase3
  libsqlite3-0 libsratom-0-0 libsrt1.5-gnutls libss2 libssh-4 libssh-gcrypt-4
  libssl3 libstdc++6 libstemmer0d libsvtav1enc1 libswresample4 libswscale6
  libsynctex2 libsystemd-shared libsystemd0 libtag1v5 libtag1v5-vanilla
  libtalloc2 libtasn1-6 libtcl8.6 libtdb1 libtevent0 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libtie-ixhash-perl
  libtiff5 libtinfo6 libtracker-sparql-3.0-0 libtry-tiny-perl
  libtss2-esys-3.0.2-0 libtss2-mu0 libtss2-rc0 libtss2-sys1 libtss2-tcti-cmd0
  libtss2-tcti-device0 libtss2-tcti-mssim0 libtss2-tcti-swtpm0 libudev1
  libudisks2-0 libunistring2 libunwind8 libupower-glib3 liburi-perl libuuid1
  libuutil3linux libv4l-0 libv4lconvert0 libva-drm2 libva-wayland2 libva-x11-2
  libva2 libvdpau1 libvisual-0.4-0 libvolume-key1 libvte-2.91-0
  libvte-2.91-common libvulkan1 libwacom-common libwacom9 libwavpack1
  libwbclient0 libwebp7 libwebpdemux2 libwebpmux3 libwireplumber-0.4-0
  libwnck-3-0 libwnck-3-common libwpebackend-fdo-1.0-1 libwrap0 libx11-6
  libx11-data libx11-protocol-perl libx11-xcb1 libxatracker2 libxdamage1
  libxfixes3 libxfont2 libxft2 libxkbcommon-x11-0 libxkbcommon0
  libxkbregistry0 libxml-parser-perl libxml-twig-perl libxml2 libxmlb2 libxpm4
  libxtables12 libxxf86dga1 libzfs4linux libzmq5 libzpool5linux libzstd1
  libzvbi-common libzvbi0 linux-firmware linux-generic-hwe-22.04
  linux-headers-generic-hwe-22.04 linux-image-generic-hwe-22.04 login
  logrotate logsave lsb-base lsb-release man-db manpages media-types
  memtest86+ mesa-utils mesa-utils-bin mesa-va-drivers mesa-vdpau-drivers
  mesa-vulkan-drivers mobile-broadband-provider-info modemmanager mount
  mousetweaks mscompress mutter-common nano nautilus nautilus-data
  nautilus-extension-gnome-terminal ncurses-base ncurses-bin netbase
  netcat-openbsd netplan.io network-manager
  network-manager-config-connectivity-ubuntu network-manager-gnome
  network-manager-openvpn network-manager-openvpn-gnome networkd-dispatcher
  nftables ntfs-3g ocl-icd-libopencl1 oem-config oem-config-gtk
  openprinting-ppds openssh-client openssl openvpn orca p11-kit
  p11-kit-modules packagekit packagekit-tools parted passwd pci.ids pciutils
  pcmciautils perl perl-base pinentry-curses pinentry-gnome3 pipewire
  pipewire-bin pipewire-pulse plymouth plymouth-label plymouth-theme-spinner
  plymouth-theme-ubuntu-text pocketsphinx-en-us poppler-utils
  printer-driver-hpcups printer-driver-postscript-hp psmisc publicsuffix
  python-apt-common python3 python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-blinker python3-brlapi python3-cairo
  python3-cffi-backend python3-chardet python3-click python3-colorama
  python3-commandnotfound python3-cryptography python3-cups
  python3-cupshelpers python3-dateutil python3-dbus python3-debconf
  python3-debian python3-distro python3-distro-info python3-distupgrade
  python3-gdbm python3-gi python3-gi-cairo python3-httplib2 python3-ibus-1.0
  python3-icu python3-importlib-metadata python3-jeepney python3-jwt
  python3-keyring python3-launchpadlib python3-lazr.restfulclient
  python3-lazr.uri python3-louis python3-minimal python3-netifaces
  python3-oauthlib python3-pam python3-pexpect python3-pil
  python3-pkg-resources python3-problem-report python3-ptyprocess
  python3-pyatspi python3-pyparsing python3-renderpm python3-reportlab
  python3-reportlab-accel python3-software-properties python3-speechd
  python3-systemd python3-update-manager python3-wadllib python3-xdg
  python3-xkit python3-yaml python3-zipp python3.10 python3.10-minimal rdate
  readline-common rfkill rsync rsyslog rygel samba-libs sane-utils sbsigntool
  seahorse sed sensible-utils sgml-base snapd software-properties-common
  software-properties-gtk speech-dispatcher speech-dispatcher-audio-plugins
  speech-dispatcher-espeak-ng strace sudo system-config-printer
  system-config-printer-common system-config-printer-udev systemd
  systemd-hwe-hwdb systemd-oomd systemd-resolved systemd-sysv
  systemd-timesyncd sysvinit-utils tar tcl8.6 tcpdump thermald time tpm-udev
  tracker tracker-extract tracker-miner-fs tree tzdata ubiquity
  ubiquity-casper ubiquity-frontend-gtk ubiquity-ubuntu-artwork
  ubuntu-advantage-tools ubuntu-desktop ubuntu-desktop-minimal
  ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-restricted-addons ubuntu-settings
  ubuntu-standard ubuntu-wallpapers ubuntu-wallpapers-kinetic ucf udev udisks2
  ufw unattended-upgrades update-inetd update-manager update-manager-core
  update-notifier update-notifier-common upower usb.ids usrmerge util-linux
  util-linux-extra uuid-runtime va-driver-all vdpau-driver-all vim-common
  vim-tiny webp-pixbuf-loader whiptail wireplumber wpasupplicant xauth xbrlapi
  xdg-dbus-proxy xdg-desktop-portal xdg-desktop-portal-gnome
  xdg-desktop-portal-gtk xdg-user-dirs xdg-user-dirs-gtk xfonts-base
  xfonts-scalable xkb-data xserver-common xserver-xephyr xserver-xorg-core
  xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-vmware
  xwayland xxd xz-utils yaru-theme-gnome-shell yaru-theme-gtk yaru-theme-icon
  yaru-theme-sound zenity zenity-common zfs-initramfs zfs-zed zfsutils-linux
  zlib1g zstd
1014 upgraded, 87 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,028 MB of archives.
After this operation, 1,196 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```

---

### Post by maglin2 on 2023-03-07
Having kicked this off I'm afraid I've lost the plot toward the end
$ ```
apt policy gnome-remote-desktop
gnome-remote-desktop:
  Installed: 42.7-0ubuntu1
  Candidate: 42.7-0ubuntu1
  Version table:
 *** 42.7-0ubuntu1 500 (phased 0%)
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     42.0-4ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```

At the risk of turning this into a support thread, could someone explain what the 42.7 Phased 0% means in this context.
I can't see how it can be Phased 0% when we've all got it?
And why is it now phased?
Thanks - and sorry if I'm missing something obvious.

---

### Post by #&amp;thj^% on 2023-03-07
It's now entered a phased upgrade.
just wait it out.

---

### Post by maglin2 on 2023-03-07
Waiting I can do as well as most.
It would be nice if the next update didn't just address the 'Turning Remote Desktop off doesn't fully disable it' issue but also made it possible to completely purge desktop sharing in 22.04 without other impact on the OS. I have no realistic expectation that it will though.

---

