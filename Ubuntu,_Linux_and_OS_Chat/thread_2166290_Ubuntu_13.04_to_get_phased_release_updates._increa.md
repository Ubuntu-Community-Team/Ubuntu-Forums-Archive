---
title: "Ubuntu 13.04 to get phased release updates. increasing the quality of the OS"
date: 2013-08-08
forum: Ubuntu, Linux and OS Chat
---

### Post by philinux on 2013-08-08
[http://iloveubuntu.net/quality-aimed-phased-updates-released-and-enabled-ubuntu-1304](http://iloveubuntu.net/quality-aimed-phased-updates-released-and-enabled-ubuntu-1304)

I dont think english is the guys first language. 

Interesting development

---

### Post by Linuxratty on 2013-08-09
> **philinux said:**
> [http://iloveubuntu.net/quality-aimed-phased-updates-released-and-enabled-ubuntu-1304](http://iloveubuntu.net/quality-aimed-phased-updates-released-and-enabled-ubuntu-1304)

I dont think english is the guys first language. 

 You may be onto something!:D

---

### Post by philinux on 2013-08-11
Another take on this with some interesting comments.

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by Gilad_Pellaeon on 2013-08-11
Interesting. Although with so many different combinations of PC hardware out there both old and new I wonder how long it'll take them to phase through each of the "10% of these machine's didnt have bugs so let's release the next 10%" and so on.

---

### Post by angryfirelord on 2013-08-11
Just to clarify, the developer who proposed this also posted this comment.

[http://www.murraytwins.com/blog/?p=127]("http://www.murraytwins.com/blog/?p=127")

> update-manager reads the Phased-Update-Percentage from the packages list at archive.ubuntu.com or your local mirror. Yes, if you use apt-get then you will get all updates immediately.
So, before people misinterpret and say, "Canonical is forcing beta quality software on us!", the default behavior is to get all updates, including potential broken ones. But now if you use update-manager, they will be staggered.

---

### Post by craig10x on 2013-08-11
The updates coming in seem to be working fine since they switched to this on 13.04....only problem is that the list doesn't come up when there are updates...i am finding that the area is blank....when you hit install, then you see the names of the items being installed...am i the only one here experiencing this bug now in the update manager?

---

### Post by alphacrucis2 on 2013-08-11
I can't say I have ever been bitten by updates with an actual release version, even with proposed repo enabled. A different story when running dev versions though :lolflag: .

---

### Post by 3rdalbum on 2013-08-12
I thought the "-proposed" repository was to fix those problems by making sure only early adopters and bleeding-edge users got updates at first?

When they started doing that, people said "But everyone will just use proposed anyway and systems will still break" or "Nobody will want system breakage so nobody will use proposed and systems will still break". Did either of those come true or something?

---

### Post by philinux on 2013-08-12
> **3rdalbum said:**
> I thought the "-proposed" repository was to fix those problems by making sure only early adopters and bleeding-edge users got updates at first?

When they started doing that, people said "But everyone will just use proposed anyway and systems will still break" or "Nobody will want system breakage so nobody will use proposed and systems will still break". Did either of those come true or something?

In a stable release proposed is still used to test out stuff. Quote from wiki.
> This repository is recommended only to those interested in helping to test updates and provide feedback. 

But in ubuntu +1 testing proposed is not recommended as it's used by the devs and can very easily bork the testing release.

---

### Post by craig10x on 2013-08-12
> **craig10x said:**
> The updates coming in seem to be working fine since they switched to this on 13.04....only problem is that the list doesn't come up when there are updates...i am finding that the area is blank....when you hit install, then you see the names of the items being installed...am i the only one here experiencing this bug now in the update manager?

No one else commented about this...but i just wanted to mention that when i got today's updates, the list was back, so it looks like it got fixed... :)

---

### Post by NormanFLinux on 2013-08-12
You can get a rolling release on 12.04 LTS by activating the backports. Updates from Quantal will be ported to work with Precise.

I'd like to see Ubuntu become a rolling release distro.

---

### Post by tgalati4 on 2013-08-12
I think it's a good idea, but the stagger interval may need to be adjusted for xorg and kernel updates since they tend to cause the most immediate breakage.  Perhaps 12 hrs or 24 hrs to allow more time to test the updates.

---

### Post by NoBugs! on 2013-08-21
There were rarely ever any breaking updates in the normal updates, but recently some have been causing major breakage:
[https://bugs.launchpad.net/unity/+bug/1209442](https://bugs.launchpad.net/unity/+bug/1209442)
I hadn't noticed this before, a normal update breaking the system, until recently, around the time phased updates were introduced. Coincidence?

---

### Post by NoBugs! on 2013-08-24
Does anyone know if there is a tool to tell which bad phased updates are on your machine? Since it looks like they aren't cleaned up afterward. Is there a list of which phased updates were cancelled, so we might manually set those packages back in synaptic?

---

### Post by nenadlatinovic on 2013-08-25
Wow, sounds like a great solution.

---

