---
title: "blurry screen after upgraded from 22.10 to 23.04"
date: 2022-12-27
forum: Ubuntu Development Version
---

### Post by hoboy on 2022-12-27
I have upgraded from ubuntu 22.10 to ubuntu 23.04 since that my screen is blurry 
have googled but can't find a solution... any advice will be welcomed 

Cheers

---

### Post by MAFoElffen on 2022-12-27
What is the graphics specs of the Host? GPU? (NVida, AMD, Intel, etc.) Desktop? (Am assumming KDE related such as Plasma) Graphics Engine? (Xorg or Wayland) Video driver being used? Etc...

---

### Post by ajgreeny on 2022-12-27
What hardware are you using? Are you using xorg or wayland? How did you upgrade as it is not yet available using the update-manager as far as I'm aware?
I assume you also are aware that the version you are now running, 23.04, is currently 4 months away from release so may be missing several required utilities for running for some while.

If stability is important to you my advice would simply be to clean install 22.04 which is an LTS version and therefore has 5 years of support, unlike 22.10 and the coming 23.04 which have 9 months support.

If, however, you really want to continue trying the intermediate versions between the LTS versions you will probably do better to wait at least until much closer to the release dates of them before installing or upgrading to them; 4 months prior to release really is asking for problems.

---

### Post by MAFoElffen on 2022-12-27
It is not even at beta yet. Still considered as Alpha. I would say early alpha. 

Is your goal is to help test(?) then thank you and be patient... Understanding that in a development distro, that there are different things each day that are there for testing. Expect problems.

I've been testing everyday, and been actively submitting bug reports to Launchpad. Although there has been other problems, being blurring has not been my experience so far with this, so any problems that you do run into should also be reported to launchpad so that they can addressed and dealt with in the development of this release.

In being that is hasn't occurred, I am curious what might b going on with yours.

---

### Post by hoboy on 2022-12-28
hi guys
echo $XDG_SESSION_TYPE 
wayland
I am using asus desktop.
using 23.04 is an accident, I had issue with my desktop it had disappeared, I was using 22.10. no matter what I did, I was coming to terminal prompt.
so after googling I decided to try upgrade,then now here I am using 23.04...
but, yes will like to downgrade it if possible, but after a while search in google downgrade ubuntu seem to be like a Ph.d topic (smile)... to ubuntu team why upgrade happened out of box but downgrade is not for everybody ???
it seem like I will have to continuous with 23.04, as I don't want to loose stuffs in my installation.
or does anybody has a good link one can follow to downgrade it ???
Can this link be used [https://linuxconfig.org/how-to-downgrade-ubuntu-linux-system-to-its-previous-version](https://linuxconfig.org/how-to-downgrade-ubuntu-linux-system-to-its-previous-version) ???

Cheers

---

### Post by #&amp;thj^% on 2022-12-28
Can we "ASSUME" you want to downgrade to 22.04.1 then?
Details matter.

---

### Post by hoboy on 2022-12-28
>Can we "ASSUME" you want to downgrade to 22.04.1 then?
YES.
>Dalai Lama>>
Very wise man (smile)

Nmmmm I may be in trouble
apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.19.0-28-generic/now 5.19.0-28.29 amd64 [installed,local]
linux-image-generic/now 5.19.0.28.25 amd64 [installed,local]
------

I do not seem to have an older kernel.

Cheers

---

### Post by #&amp;thj^% on 2022-12-28
I run kernel 5.19 on jammy(22.04) and lunar(23.04)
Everything is doable, but you will need to be prepared, most likely will be a test of your Linux skills.
Please have good back-ups before following that link.
Just for your info on this to change your sources you would use:
```
sudo sed -i 's/lunar/jammy/g' /etc/apt/sources.list
```
Make sure you pin your new sources to eliminate newer vs older packages:
```
Package: *
Pin: release a=jammy
Pin-Priority: 1001
```
That change resides in "/etc/apt/preferences"
If an older kernel is needed it should now show for a manual installation.
**[COLOR="#FF0000"]WARNING***[/COLOR]** **_Disable any and all PPA's you may have first, and you will need to reinstall any third party application's you have now._**
Good Luck should you decide to proceed...;)
```
apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-6.0.0-1kaisen-amd64/kaisen-rolling,now 6.0.7-1kaisen amd64 [installed,automatic]
linux-image-amd64/kaisen-rolling,now 6.0.7-1kaisen amd64 [installed]


```

---

### Post by hoboy on 2022-12-29
1fallen
Thanks

---

### Post by MAFoElffen on 2022-12-30
That works great if you are going Up to a newer version but doesn't work well with going backwards to older. What happens is that APT see's the newer packages, so it doesn't think it has anything to do. For example the kernel versions... That make sense???

Better would be to do a migration. 

Run the system-info script in my signature line. At the end of the report will be a list of your manually installed packages. 

Then backup all your data and any configs... 

Install your older OS as fresh/clean... 

Install the manually installed packages to end up with any mod's you did on your system beyond the fresh install. I use the list and create an install script out of it.

Then restore your data and config's on that.

Doing it that way will actually end of being faster than trying to adapt things forcefully... And you are at a better chance of having a working/clean system.

---

### Post by #&amp;thj^% on 2022-12-30
Just downgraded from lunar to jammy all good here, It did get a bit messy a time or two though.
```
~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

```
This will for certain test your Linux Skills
MAFoElffen has a *safer* choice for you think over.
The upgrade back was very smooth:
```
cat /etc/os-release
PRETTY_NAME="Ubuntu Lunar Lobster (development branch)"
NAME="Ubuntu"
VERSION_ID="23.04"
VERSION="23.04 (Lunar Lobster)"
VERSION_CODENAME=lunar
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=lunar
LOGO=ubuntu-logo

```
```
$ cat /etc/apt/preferences
Package: *
Pin: release a=lunar
Pin-Priority: 1001

```
```
me@me-Standard-PC-Q35-ICH9-2009:~$ last reboot | head -1
reboot   system boot  5.19.0-21-generi Fri Dec 30 13:41   still running
me@me-Standard-PC-Q35-ICH9-2009:~$ 
last -x shutdown
shutdown system down  5.15.0-56-generi Fri Dec 30 13:39 - 13:41  (00:01)
shutdown system down  5.15.0-56-generi Fri Dec 30 09:41 - 12:21  (02:39)
shutdown system down  5.15.0-56-generi Fri Dec 30 09:31 - 09:32  (00:01)

wtmp begins Fri Dec 30 09:29:42 2022

```

---

### Post by hoboy on 2022-12-31
Tks Guys, I did some tried after googling, my screen got back to normal 100%... well as it seem a complicated process to go back to an older version, I will stay on this 23.04 for now at least,
Ubuntu team ...This may be an area to look at how people who are not linux expert can go back to an roll back to an older version ?
like windows has restore point ...
Cheers

---

### Post by ajgreeny on 2022-12-31
If you want a restore point like Windows you could in future use **timeshift** which allows snapshots of your filesystem to be created that you can restore if needed following a system upgrade or some other problem.

Do not include your home in the snapshot or you will lose any newly created files when you restore the snapshot. Backup all your home files separately and often.

I have no personal experience of timeshift so can't tell you any more about its use.

---

### Post by hoboy on 2023-01-03
How can I mark this solved ???

---

### Post by zika on 2023-01-03
> **hoboy said:**
> How can I mark this solved ???
Upper right corner: “Thread tools“...

---

