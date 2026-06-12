---
title: "Ubuntu 21.04 LiveServer Beta AMD64 Missing"
date: 2021-04-01
forum: Server Platforms
---

### Post by genesoo77072 on 2021-04-01
I see arm64, ppc64el,  s390x, as well as several other preinstalled versions of Live Server 21.04 Beta however I do not see amd64.

 cdimage ubuntu com / releases / 21.04 / beta /

I am hoping someone on the team can investigate and rectify.

---

### Post by guiverc on 2021-04-02
I see them there (on the ISO tracker)

[http://iso.qa.ubuntu.com/qatracker/milestones/419/builds/228862/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/419/builds/228862/downloads)  via [http://iso.qa.ubuntu.com/qatracker/milestones/419/builds/228862/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/419/builds/228862/testcases)

Note the links I provided are for today's daily and the 228862 number will vary; ie. you can jump down from the usual ISO (QA) tracker site racker/milestones/419/builds

Ubuntu *hirsute* beta can be found via 422 and not 419, ie.  [http://iso.qa.ubuntu.com/qatracker/milestones/422/builds](http://iso.qa.ubuntu.com/qatracker/milestones/422/builds)

---

### Post by genesoo77072 on 2021-04-02
Thank you for the response. I was able to ultimately find the AMD64 version on the following link:

[http://releases.ubuntu.com/hirsute/ubuntu-21.04-beta-desktop-amd64.iso](http://releases.ubuntu.com/hirsute/ubuntu-21.04-beta-desktop-amd64.iso) (Hirsute Directory)

I obtained the original links to the Beta from the following announcement link 
[https://distrowatch.com/11207](https://distrowatch.com/11207) 

This page did not include a reference for the AMD64 Live Server File which caused me to start searching directories.

UBUNTU Desktop beta was in [http://releases.ubuntu.com/21.04/ubuntu-21.04-beta-desktop-amd64.iso](http://releases.ubuntu.com/21.04/ubuntu-21.04-beta-desktop-amd64.iso) (21.04 Directory) 
KUBUNTU Desktop beta was in [http://cdimage.ubuntu.com/kubuntu/releases/21.04/beta/kubuntu-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/releases/21.04/beta/kubuntu-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)
LUBUNTU Desktop [http://cdimage.ubuntu.com/lubuntu/releases/21.04/beta/lubuntu-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/21.04/beta/lubuntu-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)
MATE Desktop [http://cdimage.ubuntu.com/ubuntu-mate/releases/21.04/beta/ubuntu-mate-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-mate/releases/21.04/beta/ubuntu-mate-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)
XUBUNTU Desktop [http://cdimage.ubuntu.com/xubuntu/releases/21.04/beta/xubuntu-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/21.04/beta/xubuntu-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)
BUDGIE Desktop [http://cdimage.ubuntu.com/ubuntu-budgie/releases/21.04/beta/ubuntu-budgie-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-budgie/releases/21.04/beta/ubuntu-budgie-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)
UBUNTUSTUDIO Desktop [http://cdimage.ubuntu.com/ubuntustudio/releases/21.04/beta/ubuntustudio-21.04-beta-dvd-amd64.iso](http://cdimage.ubuntu.com/ubuntustudio/releases/21.04/beta/ubuntustudio-21.04-beta-dvd-amd64.iso) (21.04/Beta Directory)
UBUNTU KYLIN Desktop [http://cdimage.ubuntu.com/ubuntukylin/releases/21.04/beta/ubuntukylin-21.04-beta-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntukylin/releases/21.04/beta/ubuntukylin-21.04-beta-desktop-amd64.iso) (21.04/Beta Directory)

So most of the betas were in  subdirectories of 21.04/Beta under their respective distro names while UBUNTU Desktop and LiveServer were in others as noted.

---

