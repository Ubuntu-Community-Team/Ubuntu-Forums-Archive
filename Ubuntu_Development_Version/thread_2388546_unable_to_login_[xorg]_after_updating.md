---
title: "unable to login [xorg] after updating"
date: 2018-04-04
forum: Ubuntu Development Version
---

### Post by horizonbrave on 2018-04-04
Trying to run Bionic Beaver on my Dell Latitude E6530 Laptop.
Everything runs fine but after installing the updates and virtualbox I'm not able to login anymore (in x.org).
The screen becomes black and nothing happens.
I'm still able to login through a wayland session.
I don't recall doing any major change to the system, just a "sudo usermod -G vboxusers -a username" for enabling USB pass-through in virtual box.

Please,
any idea?

Thanks

---

### Post by dino99 on 2018-04-04
There is a 4.15.0-15 kernel being actually built to solve a dkms issue (affect vitualbox, fwts, ...)
Booting with 4.15.0-13 should let virtualbox being reinstalled without error, and get a working session.

---

### Post by harry332 on 2018-04-04
This is the newest one that is being built into the proposed repo:
[h=2]Publishing 4.15.0-15.16[/h]       [TABLE="class: listing"]
                 [TR]
          [TH]Series
[/TH]
          [TH]Pocket[/TH]
          [TH]Published
[/TH]
          [TH]Component[/TH]
          [TH]Section[/TH]
         [/TR]
                          [TR]
           [TD]             [Bionic]("https://launchpad.net/ubuntu/bionic")           [/TD]
           [TD]proposed[/TD]
           [TD]             1 hour ago           [/TD]
           [TD]main[/TD]
           [TD]devel[/TD]
          [/TR]
               [/TABLE]
                            [h=2]Builds[/h]                [Bionic]("https://launchpad.net/ubuntu/bionic"):                        [IMG]https://launchpad.net/@@/processing[/IMG]             [amd64]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530348")                                                [IMG]https://launchpad.net/@@/processing[/IMG]             [arm64]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530349")                                                [IMG]https://launchpad.net/@@/processing[/IMG]             [armhf]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530350")                                                [IMG]https://launchpad.net/@@/processing[/IMG]             [i386]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530351")                                                [IMG]https://launchpad.net/@@/processing[/IMG]             [ppc64el]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530352")                                                [IMG]https://launchpad.net/@@/build-success[/IMG]             [s390x]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530353")                                             (New)                                                

            


**********************
The version 4.15.0-13.14 is already in release pocket and the version 4.15.0-14.15 in in proposed now.

---

### Post by harry332 on 2018-04-05
This is now in proposed repo:


**Publishing       4.15.0-15.16**

       [TABLE="class: listing"]
[TR]
[TH]Series[/TH]
[TH]Pocket[/TH]
[TH]Published[/TH]
[TH]Component[/TH]
[TH]Section[/TH]
[/TR]
[TR]
[TD]             [Bionic]("https://launchpad.net/ubuntu/bionic")[/TD]
[TD]proposed[/TD]
[TD]             15 hours ago[/TD]
[TD]main[/TD]
[TD]devel[/TD]
[/TR]
[/TABLE]
                            **Builds**

                [Bionic]("https://launchpad.net/ubuntu/bionic"):                        [IMG]https://launchpad.net/@@/build-success[/IMG]             [amd64]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530348")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [arm64]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530349")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [armhf]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530350")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [i386]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530351")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [ppc64el]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530352")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [s390x]("https://launchpad.net/ubuntu/+source/linux/4.15.0-15.16/+build/14530353")

---

