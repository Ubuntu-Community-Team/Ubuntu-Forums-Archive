---
title: "Bug: Nautilus desktops tabs"
date: 2011-10-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-31
We've been talking about these one since Oneiric Alpha. I *think* it was fixed at some point before release (not sure). But I'm seeing it again on PP. Click anywhere on the desktop, press CTRL+T. You'll have a Nautilus Window opened at x-nautilus-desktop (makes no sense), and your desktop will be split into two non-working Nautilus tabs which will keep trying to load nothing forever.

It had been fixed before, right? Can anyone confirm? (I don't have Oneiric final release at hand here)

Thanks,
Effenberg

---

### Post by ventrical on 2011-10-31
> **effenberg0x0 said:**
> We've been talking about these one since Oneiric Alpha. I *think* it was fixed at some point before release (not sure). But I'm seeing it again on PP. Click anywhere on the desktop, press CTRL+T. You'll have a Nautilus Window opened at x-nautilus-desktop (makes no sense), and your desktop will be split into two non-working Nautilus tabs which will keep trying to load nothing forever.

It had been fixed before, right? Can anyone confirm? (I don't have Oneiric final release at hand here)

Thanks,
Effenberg

Not fixed here , either in Oneiric.  After the x-nautalis I get my background screen painted with the White Screen of Death.

---

### Post by Harry33 on 2011-10-31
> **effenberg0x0 said:**
> We've been talking about these one since Oneiric Alpha. I *think* it was fixed at some point before release (not sure). But I'm seeing it again on PP. Click anywhere on the desktop, press CTRL+T. You'll have a Nautilus Window opened at x-nautilus-desktop (makes no sense), and your desktop will be split into two non-working Nautilus tabs which will keep trying to load nothing forever.

It had been fixed before, right? Can anyone confirm? (I don't have Oneiric final release at hand here)

Thanks,
Effenberg

Have you tried to update your PP version of nautilus (3.2.1-0ubuntu1) to
OO-proposed version of Nautilus (3.2.1-0ubuntu2) which is newer than the one in PP?

PP (3.2.1-0ubuntu1):
[https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu1](https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu1)

OO-proposed (3.2.1-0ubuntu2):
[https://launchpad.net/ubuntu/oneiric/+source/nautilus/1:3.2.1-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/nautilus/1:3.2.1-0ubuntu2)

---

### Post by ventrical on 2011-10-31
White screen of Death also on Precise!!

---

### Post by mc4man on 2011-10-31
It was fixed in OO with the ubuntu2 package - mentioned in the changelog

---

### Post by effenberg0x0 on 2011-10-31
> **Harry33 said:**
> Have you tried to update your PP version of nautilus (3.2.1-0ubuntu1) to
OO-proposed version of Nautilus (3.2.1-0ubuntu2) which is newer than the one in PP?

PP (3.2.1-0ubuntu1):
[https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu1](https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu1)

OO-proposed (3.2.1-0ubuntu2):
[https://launchpad.net/ubuntu/oneiric/+source/nautilus/1:3.2.1-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/nautilus/1:3.2.1-0ubuntu2)

```
$ sudo apt-cache showpkg nautilus
Package: nautilus
Versions: 
1:3.2.1-0ubuntu1 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: 007268d365c98355ef914766c16ee43f
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 007268d365c98355ef914766c16ee43f

``````

[11:52 ][al:AL-DESK:/etc/apt]
$ cat /etc/apt/sources.list | grep proposed
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe

```Ah, I'm missing OO proposed in my sources...

```

$ sudo apt-cache showpkg nautilus
Package: nautilus
Versions: 
1:3.2.1-0ubuntu2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric-proposed_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: 007268d365c98355ef914766c16ee43f
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 007268d365c98355ef914766c16ee43f

```Thanks guys!

Effenberg

---

### Post by effenberg0x0 on 2011-10-31
```
Get:1 Changelog for nautilus (http://changelogs.ubuntu.com/changelogs/pool/main/n/nautilus/nautilus_3.2.1-0ubuntu2/changelog) [79,2 kB]
nautilus (1:3.2.1-0ubuntu2) oneiric-proposed; urgency=low

  [ Dmitry Shachnev ]
  * debian/patches/05_desktop_menu_export.patch (updated):
    - Destroy menubar on non-ubuntu sessions (LP: #826771)
    - Remove duplicate lines (LP: #874847)
  * debian/patches/17_dont_allow_new_tab_on_desktop.patch:
    - Don't allow "New tab" shortcut on desktop (LP: #814799)

  [ Martin Pitt ]
  * 05_desktop_menu_export.patch: Fix potential crash if $DESKTOP_SESSION is
    not set.

 -- Dmitry Shachnev <mitya57@gmail.com>  Tue, 25 Oct 2011 12:46:53 +0200

/tmp/tmpyFrUgc (END)
```

---

### Post by ventrical on 2011-10-31
> **mc4man said:**
> It was fixed in OO with the ubuntu2 package - mentioned in the changelog


Thanks harry and mac!

@effenberg,

yep .. me too .. missing proposed in Oneiric/Precise.

---

### Post by Harry33 on 2011-11-01
The Nautilus bug-fix update 3.2.1-0ubuntu2 is now in Precise repos too:

[https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu2](https://launchpad.net/ubuntu/+source/nautilus/1:3.2.1-0ubuntu2)

---

