---
title: "Is there an easy wasy to get apt to show updates that are held back as phased updates"
date: 2022-08-01
forum: Server Platforms
---

### Post by bigmonmulgrew on 2022-08-01
This morning I ran into an issue with apt not updating. I got the fairly familiar 

> The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


After some digging I found that this is due to the updates being phased. The updates are held back so that not everyone gets the upgrades at once.

```
sudo apt-cache policy ubuntu-release-upgrader-core python3-distupgrade
```

> ubuntu-release-upgrader-core:
  Installed: 1:22.04.11
  Candidate: 1:22.04.12
  Version table:
     1:22.04.12 500 (phased 0%)
        500 [http://nova.clouds.archive.ubuntu.com/ubuntu](http://nova.clouds.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
 *** 1:22.04.11 100
        100 /var/lib/dpkg/status
     1:22.04.10 500
        500 [http://nova.clouds.archive.ubuntu.com/ubuntu](http://nova.clouds.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
python3-distupgrade:
  Installed: 1:22.04.11
  Candidate: 1:22.04.12
  Version table:
     1:22.04.12 500 (phased 0%)
        500 [http://nova.clouds.archive.ubuntu.com/ubuntu](http://nova.clouds.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
 *** 1:22.04.11 100
        100 /var/lib/dpkg/status
     1:22.04.10 500
        500 [http://nova.clouds.archive.ubuntu.com/ubuntu](http://nova.clouds.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages


Is there an easier way I can identify phased packages, when running upgrade it isn't completely obvious why these updates are being kept back. I immediately took to gogole and found someone far more informed than me who knew they were phased. Ideally apt would identify this, eg

> The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core
0 upgraded, 0 newly installed, 0 to remove, 2 awaiting phased update, 2 not upgraded.


Is there anything simple I can do to have this made more obvious, or would I need to be scripting something to check the policy on each package apt spits our that its kept back.

---

### Post by #&amp;thj^% on 2022-08-01
I knew this would be asked sooner or later, and I offer a poor way of showing and identifying phased packages,
Update Manager is currently the only package manager that supports phased updates.
Not the best, but it works:
```
update-manager --debug
```
Like I said not the best, but will provide what your looking for IE:
```

INFO:root:holding back phased update fonts-opensymbol (10 < 48)
INFO:root:holding back phased update libegl-mesa0 (10 < 32)
INFO:root:holding back phased update libgbm1 (10 < 32)
INFO:root:holding back phased update libgl1-mesa-dri (10 < 32)
INFO:root:holding back phased update libglapi-mesa (10 < 32)
INFO:root:holding back phased update libglx-mesa0 (10 < 32)
INFO:root:holding back phased update libxatracker2 (10 < 32)
INFO:root:holding back phased update mesa-va-drivers (10 < 32)
INFO:root:holding back phased update mesa-vdpau-drivers (10 < 32)
INFO:root:holding back phased update mesa-vulkan-drivers (10 < 32)
INFO:root:holding back phased update python3-distupgrade (0 < 67)
INFO:root:holding back phased update ubuntu-release-upgrader-core (0 < 67)
INFO:root:holding back phased update ubuntu-release-upgrader-gtk (0 < 67)


```
Just found a viewable link as well: [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)

---

### Post by deadflowr on 2022-08-01
> Update Manager is currently the only package manager that supports phased updates.
No, not anymore. Now it affects/applies to apt as a whole for versions used in newer releases of Ubuntu. (So 22.04, at least; I don't think it's been backported to older release... Yet)
See: [https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")

---

### Post by #&amp;thj^% on 2022-08-01
> **deadflowr said:**
> No, not anymore. Now it affects/applies to apt as a whole for versions used in newer releases of Ubuntu. (So 22.04, at least; I don't think it's been backported to older release... Yet)
See: [https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")

Yep I saw that, I meant the only way to view those held phased pkgs, was with "update-manager --debug"
But clarity is always welcomed and needed.

---

### Post by LHammonds on 2022-08-01
I saw this with my MariaDB server on 22.04.  I created a snapshot on the VM and did "apt install" for each one held back.  Nothing broke.  At least now my monitoring / alert system is no longer screaming about patches not being applied. ;)

EDIT: Now that I think about it....probably should have modified the monitoring scripts to ignore the held-back entries...Not entirely sure what the correct method to use in this situation.  I opted for silence.

LHammonds

---

### Post by TheFu on 2022-08-01
Not what you asked, but might be helpful for others only reading the thread title.   ;)

Held packages can be listed by 
```
apt-mark showhold
```

I don't think that's the same, but it will certainly show a subset of problem packages.

No update manager here. I probably purged it as useless (nagging too much).
```
$ update-manager --debug

Command 'update-manager' not found, but can be installed with:
....
```

---

### Post by LHammonds on 2022-08-01
> **TheFu said:**
> No update manager here. I probably purged it as useless (nagging too much).
update-manager is NOT installed by default on 18.04, 20.04 and 22.04

LHammonds

---

### Post by &amp;KyT$0P# on 2022-08-01
> **1fallen said:**
> the only way to view those held phased pkgs, was with "update-manager --debug"

I wouldn't trust that.  update-manager might phase updates completely differently from apt, because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1979238").

I solved this problem based on the link deadflowr posted, I created an alias
```
alias apt-nophase='apt -o="APT::Get::Always-Include-Phased-Updates=true"'
```
It used to be as simple as checking difference between [FONT=Courier New]apt list --upgradable[/FONT] and [FONT=Courier New]apt-nophase list --upgradable[/FONT] .  However since latest update of apt both commands are now showing the same output regardless of phasing, so now I would compare the behavior of [FONT=Courier New]apt-get -s dist-upgrade[/FONT] vs [FONT=Courier New]apt-nophase -s dist-upgrade[/FONT] .

---

### Post by #&amp;thj^% on 2022-08-01
Mine still rings true as in post #2
I'll call it with apt then:
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt -o='Apt::Get::Always-Include-Phased-Updates=true' list --upgradable
Listing... Done
fonts-opensymbol/jammy-updates,jammy-updates 2:102.12+LibO7.3.5-0ubuntu0.22.04.1 all [upgradable from: 2:102.12+LibO7.3.4-0ubuntu0.22.04.1]
libegl-mesa0/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
libgbm1/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
libgl1-mesa-dri/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
libglapi-mesa/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
libglx-mesa0/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
libsnmp-base/jammy-updates,jammy-updates,jammy-security,jammy-security 5.9.1+dfsg-1ubuntu2.2 all [upgradable from: 5.9.1+dfsg-1ubuntu2.1]
libsnmp40/jammy-updates,jammy-security 5.9.1+dfsg-1ubuntu2.2 amd64 [upgradable from: 5.9.1+dfsg-1ubuntu2.1]
libxatracker2/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
mesa-va-drivers/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
mesa-vdpau-drivers/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
mesa-vulkan-drivers/jammy-updates 22.0.5-0ubuntu0.1 amd64 [upgradable from: 22.0.1-1ubuntu2.1]
python3-distupgrade/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11]
ubuntu-release-upgrader-core/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11]
ubuntu-release-upgrader-gtk/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11]

```
Just cumbersome to view is all, .vs Post #2
EDIT: Come to think of it....isn't update-manager alias for apt:
```
update-manager
  Depends: <python3:any>
    python3:i386
    python3
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: update-manager-core
  Depends: libgtk3-perl
 |Depends: python3-aptdaemon.gtk3widgets
  Depends: synaptic
  Depends: policykit-1
    policykit-1:i386
  Depends: python3-dbus
  Depends: python3-gi
  Depends: python3-yaml
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-handy-1
  Depends: gir1.2-snapd-1
  Depends: ubuntu-release-upgrader-gtk
  Depends: update-notifier
    gnome-packagekit
 |Depends: gnome-shell
 |Depends: policykit-1-gnome
 |Depends: polkit-kde-agent-1
 |Depends: lxpolkit
 |Depends: lxqt-policykit
 |Depends: mate-polkit
  Depends: <polkit-1-auth-agent>
    gnome-flashback
    gnome-shell
    lxpolkit
    lxqt-policykit
    mate-polkit
    phosh
    policykit-1-gnome
    polkit-kde-agent-1
    ukui-polkit
  Breaks: update-notifier
  Recommends: software-properties-gtk
  Recommends: python3-launchpadlib
  Suggests: gir1.2-dbusmenu-glib-0.4
  Suggests: <gir1.2-unity-5.0>
    gir1.2-unity-7.0

```

---

### Post by bigmonmulgrew on 2022-08-02
Appreciate the feedback guys, I've been reading through some of the posts linked and I have to say I do really appreciate phasing as a concept.

None of it really addresses the issue here though, there is no way to know that phasing is the thing stopping the update. A google search "ubuntu  The following packages have been kept back" give a page full of results that doesn't even mention the real issue.

All of them suggest variants of "sudo apt-get --with-new-pkgs upgrade" or to manually install the packages one at a time.

I have been around linux for some time, I was able to eventually work out what was going on but for someone new to linux/ubuntu the error message given by apt isn't even useful for working out what the problem is. Many of the experienced linux admins I've spoke to guessed the problem was phasing and it was fairly easy to work it out once you have an idea what to guess at. But put on your newbie hat for a moment, all you see is an error message and all the fixes it leads to don't work. 

Its not even really an error, its working as intended but to many it looks like updates are broken and searching the message gives no clues.

I was hoping there would be an easy solution to change the output message but I suspected it wasnt the case. I wouldnt even know where to begin with editing apt to even attempt to change it myself, nor would I know where is the proper place to submit changes, sadly.

Ah well at least its getting dicussed, appreciate the input guys

---

