---
title: "What hasn't been tested yet?"
date: 2023-12-17
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-12-17
Ubuntu Desktop's installer was broken today... That got me thinking about how else we can help quiverc on things that might not be tested yet. He gets statuses from the ISO tracker, so I figure he would be the person that would know on those...

I figure I can edit this first post, with a list of things from the ISO tracker, so if there is something that hasn't been tested yet, and someone has time, tht maybe they can pick something off that list to test.

Of things I know have been done:
```

Ubuntu Desktop (iso)
Ubuntu Desktop (preinstalled)
Ubuntu Server (iso)
Ubuntu Server (pre-installed img)
Ubuntu Noble N Cloud (pre-installed)
Kubuntu (iso)
Lubuntu (iso)
Ubuntu Budgie (iso)
Xubuntu (iso)
Ubuntu MATE (iso)
Ubuntu Kylin (iso)
Edubuntu (iso)
Ubuntu Unity (iso)
Ubuntu Cinnamon (iso)
Ubuntu Base (pre-installed img)
Ubuntu WSL (pre-installed img)

```

Of things I'm not sure have been done yet
```

Ubuntu Core 22 Edge. (pre-installed img)
Ubuntu Studio (iso, not until January)

```
If you know something in that list has been tested, tell me and I'll update this list.

These are things I know haven't worked yet:
```

Ubuntu Desktop - LVM encrypted
Ubuntu Desktop - Hardware backed Encrypted
Ubuntu Server - arch S390X
Ubuntu Studio

```
If you know of more that is stalled, then we know it still needs attention to watch...

Is there anything I missed in those lists?  Let's see if we can check all quiverc's blocks... Or at least those we can help with.

---

### Post by Irihapeti on 2023-12-17
I can't commit to being a daily tester like some (dedicated) people, but I can pick up the odd one or two from time to time.

---

### Post by MAFoElffen on 2023-12-17
That's why I thought this might help... to quickly ID things that 'no-one' has tested yet at all. There are things that I go to and test often. There are other things that I'll take on every once in a while as a challenge. 

I suspect there are "some things" that no-one has tested. 

Not asking for any commitments from anyone... just help ID'ing things that might be slipping through the cracks. Right? That way we know things that have been tested, and things that haven't. If I have some time, I think I can take on a few odd things that haven't. I just need to know which they are.

But if you all think that's a waste of time, I'll accept that also.

---

### Post by Irihapeti on 2023-12-18
I think it's one of those things that... well, it would be nice if everything could be done, but it can't, so we do what we can.

It can't be any more a waste of time than the effort we put into tug of war... :P

---

### Post by MAFoElffen on 2023-12-18
I do seem to put a lot of time into tug of war. LOL ](*,)

---

### Post by Irihapeti on 2023-12-18
> **MAFoElffen said:**
> I do seem to put a lot of time into tug of war. LOL ](*,)

I suppose it's something we do to stop ourselves from going mad. :)

---

### Post by Irihapeti on 2023-12-18
Anyway, as for the real subject of this thread, I've occasionally installed Edubuntu, Unity, Ubuntu base arm64 version (and amd64). I think I did Cinnamon once, too. Does Ubuntukylin require one to know Chinese? Because I'd fail seriously on that score.

---

### Post by MAFoElffen on 2023-12-18
@Irihapeti -- I didn't know, so I downloaded it and installed it. Success. Default was for Chinese, but initial screen was to the language panel, where I switched it to English.

Updated the first post. to reflect that, and what you said you tested.

---

### Post by Irihapeti on 2023-12-18
I don't see Raspberry Pi on that list. I do know that some people have tested it.

I don't have a test-case RPi, so my testing wouldn't be valid. (Mine's 2GB; test cases are 4GB and 8GB)

---

### Post by MAFoElffen on 2023-12-18
I have a Pi4 8GB. Ubuntu Desktop (pre-installed) & Ubuntu Server Pre-installed... Should I have included other flavors for Rasp Pi? I also installed Ubuntu for amd64, arm64, RISC-V 64 that were successes. S390X is still a no-go.

---

### Post by corradoventu on 2023-12-18
?? Ubuntu Studio (iso, not until January) whi [COLOR="#FF0000"]not until January[/COLOR]
I see the ISO in: [https://cdimages.ubuntu.com/ubuntustudio/dvd/pending/](https://cdimages.ubuntu.com/ubuntustudio/dvd/pending/)

---

### Post by Irihapeti on 2023-12-18
Ah right I see the "preinstalled" items; I guess I didn't stop to think that RPi would be included in them.

---

### Post by guiverc on 2023-12-18
I don't get status reports from the ISO tracker.  All I'm doing  is manually going to the site regularly (pages such as [https://iso.qa.ubuntu.com/qatracker/...nes/450/builds]("https://iso.qa.ubuntu.com/qatracker/milestones/450/builds")) and looking at what is done; number of tests, and bugs reported. I'm getting a *feel* from viewing this summary page, and just hovering my mouse of bugs reported (*do I recognize it; I'll open it if I don't*).

When at that page, I concentrate particularly on Lubuntu (*I'm on that team*), and where time allows go beyond that (*usually dictated by my own preferences; so Xubuntu next, etc..*)

I know reports are created from that detail; have been sent links so I can peruse that detail, but it's mostly bug related data from reports, and most of the bugs on it were already appearing in my email inbox due to launchpad subscriptions.

> **corradoventu said:**
> ?? Ubuntu Studio (iso, not until January) whi [COLOR=#FF0000]not until January[/COLOR]
I see the ISO in: [https://cdimages.ubuntu.com/ubuntustudio/dvd/pending/](https://cdimages.ubuntu.com/ubuntustudio/dvd/pending/)

The ISOs are being generated, as build is triggered by a cron job, however it is believed that until January, when a change is made, those ISOs will not [boot and be usable]("https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/2046386") (*as they've not for awhile now*).

I'll quote from [UWN 818 which is soon to publish]("https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-818/40946/1")

> **Ubuntu Studio: Noble Numbat Updates for December**

 The Ubuntu Studio team provide us with an update of progress, in  relation to Ubuntu Studio 24.04 LTS. Covered is the move to the new  flutter-based frontend of Subiquity, which has the current unintended  consequence of daily images not booting. We&#8217;re given reasons for this  and told it&#8217;ll be fixed in the new year.

 [https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/](https://ubuntustudio.org/2023/12/noble-numbat-updates-for-december/)



 Erich wrote in the linked post

 > "We do not expect this issue to be resolved until January"

and gave his reasoning.  When it'll be fixed, we'll have to wait and see.

---

### Post by MAFoElffen on 2023-12-18
Just finishing an install of Noble Mate right now...

That will leave just a few left that I am not sure have been tested yet... And 3 of the 4 are pre-installed images.

---

### Post by MAFoElffen on 2023-12-18
I'm not sure I can test a Noble WSL daily image... All I can find on running it is this:
[https://ubuntu.com/blog/improved-testing-ubuntu-wsl](https://ubuntu.com/blog/improved-testing-ubuntu-wsl)

...which says it doesn't run on Windows with WSL directly, but rather in a GitHub workflow, inside an Azure Windows VM image that supports WSL... I don't have an Azure account to be able to do that, that way. I can't see any other information on that, to do it any other way for Noble.

EDIT:
Though I did find this, when they were testing Focal WSL: [https://discourse.ubuntu.com/t/how-you-can-help-test-ubuntu-20-04-lts-on-wsl/15211](https://discourse.ubuntu.com/t/how-you-can-help-test-ubuntu-20-04-lts-on-wsl/15211)
 I might be able to sideload the daily WSL images into Windows WSL, modifying the URLs and such for Noble to try to make that work. Hmmm.

---

### Post by MAFoElffen on 2023-12-18
FYI:
Was actually fairly painless to test... That is, compared to not having starting Win10 in forever, having to apply all the updates, converting WSL1 to WSL2, updating ad converting all my older WSL distros to current on WSL2.

Created a script to download the daily image, import that archive into a directory to install the filesystem, then start it... Installed and ran fine.
```

root@OGLLENOI07U0021:/mnt/c/WINDOWS/system32# uname -r && cat /etc/os-release
5.15.90.1-microsoft-standard-WSL2

PRETTY_NAME="Ubuntu Noble Numbat (development branch)"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04 (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

```
After I got to the ISO tracker, that actually had better instructions for that, and saw that someone had already tested it. LOL. Oh well.

---

