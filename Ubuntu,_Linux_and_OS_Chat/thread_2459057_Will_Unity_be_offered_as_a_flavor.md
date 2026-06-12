---
title: "Will Unity be offered as a flavor?"
date: 2021-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by jmichaels29 on 2021-03-09
Will Unity desktop be offered as a flavor?

---

### Post by guiverc on 2021-03-09
You are aware of [https://ubuntuunity.org](https://ubuntuunity.org)

Many of the people involved are now Ubuntu Members, and whilst I've not kept myself fully informed, it was expected they'd meet the (sustained) criteria to become an official during this year (2021, if they still wish to do so).

For *up-to-date* information, I'd suggest checking up [https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev/19](https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev/19)

---

### Post by jmichaels29 on 2021-03-09
> **guiverc said:**
> You are aware of [https://ubuntuunity.org](https://ubuntuunity.org)

Many of the people involved are now Ubuntu Members, and whilst I've not kept myself fully informed, it was expected they'd meet the (sustained) criteria to become an official during this year (2021, if they still wish to do so).

For *up-to-date* information, I'd suggest checking up [https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev/19](https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev/19)

Thank you for your reply.

I don't think Unity (Unity Remix) is available to simply update to - one must do a clean install.
I'm running Unity now, but I'd like Remix to be a flavor, so that I could simply update to it - via using the Software Center.

---

### Post by crip720 on 2021-03-09
Do not think you can 'update' to a different flavour, gnome to Kubuntu.  Can install a desktop, did clean install of 18.04, stuff was broken in gnome, fixed everything by installing unity desktop and have upgraded to 20.04 since.  Do think it would be nice if they did have a Unity flavour also, saves having to install unity.

---

### Post by guiverc on 2021-03-09
> **jmichaels29 said:**
> Thank you for your reply.

I don't think Unity (Unity Remix) is available to simply update to - one must do a clean install.
I'm running Unity now, but I'd like Remix to be a flavor, so that I could simply update to it - via using the Software Center.

Sorry I don't use *Software Centre* very often so really don't know what it shows (I am aware that it contains a somewhat curated list, so not everything shows).  I'd suggest trying a package-manager (I like `aptitude`, but most would probably opt for `synaptic` or `muon`..)

A quick look finds

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   rmadison ubuntu-unity-desktop
 ubuntu-unity-desktop | 0.1 | bionic/universe  | amd64, arm64, armhf, i386, ppc64el
 ubuntu-unity-desktop | 0.2 | focal/universe   | amd64, arm64, armhf, ppc64el
 ubuntu-unity-desktop | 0.3 | groovy/universe  | amd64, arm64, armhf, ppc64el
 ubuntu-unity-desktop | 0.3 | hirsute/universe | amd64, arm64, armhf, ppc64el

```

I've not added them, but I can't see why they wouldn't work. 

My own install was a Ubuntu install, on which I added `xubuntu-desktop`, `lubuntu-desktop` and `ubuntu-mate-desktop` (long ago in 2017 or what was *artful* days.   I upgrade it every six months so now it's on *hirsute* though I removed `ubuntu-mate-desktop` a few months ago (*disk space issues primarily*).

There are *cons* to have multiple desktops installed, but I personally feel the *pros* outweigh them (hey I can select Ubuntu(GNOME), Lubuntu(LXQt) or Xubuntu(XFCE) when I login and love it), in fact most my boxes have multiple desktops installed (*they do vary*..) 

 I have no experience with `ubuntu-unity-desktop` though sorry; I never got used to the menu.
FYI:  *If you wonder why the spaces in front of the `rmadison` command; I don't want quick queries like that (support for others etc) clogging up my command `history`, the spaces in front mean it won't get recorded *:)

---

### Post by crip720 on 2021-03-09
Think unity remix is more of a separate related distro, compared to the action of just installing unity desktop.  Remix might require downloading ISO and installing to drive.

---

### Post by jmichaels29 on 2021-03-09
> **crip720 said:**
> Think unity remix is more of a separate related distro, compared to the action of just installing unity desktop.  Remix might require downloading ISO and installing to drive.

Yes, my understanding is that is exactly how it works.
I had read, that the kid that created Remix, was hoping that one day that Ubuntu would offer it as a "flavor."  I don't know exactly what a flavor is, but was hoping it would mean I could somehow upgrade to it easily via the software center.

---

### Post by guiverc on 2021-03-09
Yep currently Unity remix is a *unofficial* Ubuntu *remix*, I was aware of numerous discussions last year, but my memory is vague (*I didn't need to know, reading the it was part of my Ubuntu_News role*); and I was under the impression it was taking over from what Dale Beaudoin (user @ventrical here) originally led.
**[COLOR=#DD4814][B]**[/COLOR][/B]

---

### Post by deadflowr on 2021-03-09
> **jmichaels29 said:**
> Thank you for your reply.

I don't think Unity (Unity Remix) is available to simply update to - one must do a clean install.
I'm running Unity now, but I'd like Remix to be a flavor, so that I could simply update to it - via using the Software Center.

The remix uses the packages already available in the Ubuntu repositories.
All the remix does is make it so you can do a clean install.

If you're going to do an upgrade then no need to deal with a remix.

All the remix does is make it convenient to install unity directly during an install,
rather than having to install it post-installation.

---

### Post by crip720 on 2021-03-10
A flavour is an ISO for install that has a specific desktop and programs, you can't update to a flavour.  You can only install desktop and/or programs from a flavour to your system.

---

### Post by slickymaster on 2021-03-10
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2021-03-10
As I understand things, Unity 7 is in maintenance mode and it is not in the repositories of the latest Ubuntu versions. If you start with something Like Ubuntu 16.04 where Unity 7 is the default desktop and then upgrade to 18.04 and onwards a person would get the latest Ubuntu with Gnome 3 shell and a login option of Unity. But be careful. The upgrade process will ask for authorisation to remove obsolete packages. Give approval for that action and Unity 7 will be removed. That is how I lost Unity from my present install of 20.04 which originally started out as 16.04.

In my opinion the reason that the Unity 7 packages are considered obsolete is because they are not in the 20.04 repositories and cannot be upgraded .

I expect that there are conditions that the developers of Ubuntu Unity will have to meet for ubuntu Unity to become an official flavour. I guess that the developers would have to prove that they can keep up to date with security fixes and also follow the standard Ubuntu release schedule.

Regards

---

### Post by Frogs Hair on 2021-03-10
> As I understand things, Unity 7 is in maintenance mode and it is not in the repositories of the latest Ubuntu versions

It's not in the 21.04 repository at this point. I just downloaded and ran a U-unity 21.04 a live session.  


Not sure where Ubuntu Unity stands in the official flavor process. They have a forum @ the link.
[https://ubuntuunity.org/](https://ubuntuunity.org/)

---

### Post by jmichaels29 on 2021-03-10
Thanks all for the replies.

When I did a clean install of 20.04 lts, I then immediately installed Unity via the terminal/command line.  Not that this is a focus of this thread, but I simply like the more robust drag and drop features of Unity (being able to drag and drop to the desktop, being able to create folders on the desktop, drag and drop to a thumb drive icon or trash icon.  Gnome just doesn't have the robust drag and drop that I like - & I'm well aware that the makers of Gnome don't like people to have a cluttered desktop, but I think that goes against how modern operating systems should work and against the Linux philosophy of allowing users to choose to clutter up their desktop if they want to (smiles).

Over the years, Ubuntu has had desktop changes during upgrades, without having to do a clean install.  I'd just like that option with Unity - e.g. being able to simply update to Unity Remix while at the same time keeping your files/folders intact.

Regards

---

### Post by deadflowr on 2021-03-10
> **grahammechanical said:**
> As I understand things, Unity 7 is in maintenance mode and it is not in the repositories of the latest Ubuntu versions. If you start with something Like Ubuntu 16.04 where Unity 7 is the default desktop and then upgrade to 18.04 and onwards a person would get the latest Ubuntu with Gnome 3 shell and a login option of Unity. But be careful. The upgrade process will ask for authorisation to remove obsolete packages. Give approval for that action and Unity 7 will be removed. That is how I lost Unity from my present install of 20.04 which originally started out as 16.04.

In my opinion the reason that the Unity 7 packages are considered obsolete is because they are not in the 20.04 repositories and cannot be upgraded .

I expect that there are conditions that the developers of Ubuntu Unity will have to meet for ubuntu Unity to become an official flavour. I guess that the developers would have to prove that they can keep up to date with security fixes and also follow the standard Ubuntu release schedule.

Regards

Unity is definitely available in every release, including the development release.
You lost it because some packages related to unity were marked as no longer needed during an upgrade.
(This happened to me too).
You can get unity by installing the ubuntu-unity-desktop meta-package.
If you had that package installed, unity would have stayed.


They did, however, remove all the unity8 packages from the repositories.
But those are now being worked on by outside developers over at ubports.
They may, at some time in the future, return to the Ubuntu repositories but with a new name.
If they do, it'll be because the developers were able to the get them into Debian,
which Ubuntu will pull from when creating a new release.

---

### Post by jmichaels29 on 2021-03-11
This is an interesting post

[https://www.foss.ubuntuunity.org/forums/discussion/38/how-do-i-upgrade#latest](https://www.foss.ubuntuunity.org/forums/discussion/38/how-do-i-upgrade#latest)

---

### Post by mIk3_08 on 2021-03-11
Just can't believe Unity is on progress right now. Unbelievable.

---

### Post by Frogs Hair on 2021-03-11
> Unity is definitely available in every release, including the development release.  It did not come up in a synaptic search yesterday , but was found  today.:o

---

