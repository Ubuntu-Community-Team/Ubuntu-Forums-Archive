---
title: "Install ubuntu in virtualbox from USB"
date: 2012-09-23
forum: Virtualisation
---

### Post by Wim Sturkenboom on 2012-09-23
I'm running Ubuntu 12.04 (desktop) and have virtualbox installed. I'm trying to install another Ubuntu in virtualbox using a memory stick and don't manage :(

Installed is:
```

wim@i3-2120:~$ dpkg --get-selections |grep virtualbox
virtualbox					install
virtualbox-dkms					install
virtualbox-guest-additions			install
virtualbox-guest-additions-iso			install
virtualbox-guest-dkms				install
virtualbox-guest-utils				install
virtualbox-guest-x11				install
virtualbox-ose-guest-utils			install
virtualbox-ose-guest-x11			install
virtualbox-qt					install
wim@i3-2120:~$ 

```

First of all I can't select USB2.0; it tells me that 'this requires the Oracle VM VirtualBox Extension Pack to be installed'; did I miss a package in Synaptic? Secondly, when pressing F12 for boot options, there is no option for the memory stick (related with first issue?). When I move the mouse over the USB icon, it sees the memory stick (possibly not immediately).

Any assistance is appreciated.

---

### Post by gordintoronto on 2012-09-23
There are advantages to installing the VirtualBox from the VirtualBox web site, and then installing the Extension Pack from the same site. Then you would be able to use USB. I know, that's the Windows approach, but that's Oracle for you.

---

### Post by Habitual on 2012-09-23
Unless you are testing a USB installation media, then I suggest allowing Virtualbox to use the ISO *before installation* (Under [COLOR=Red]Settings[/COLOR] > [COLOR=Red]Storage[/COLOR] and click the Drive Icon there, "[COLOR=Red]Choose a Virtual CD/DVD disk file...[/COLOR]" navigate to the ubuntu.iso and save those settings.
When you [COLOR=Red]start Virtualbox, press F12[/COLOR] and select "Other boot devices: > c) CD-ROM

Hope that helps.

---

### Post by Wim Sturkenboom on 2012-09-24
Thanks for the replies; for now my question is solved. I will leave it open for a while till I have tried one of the proposed solutions and to 'allow' others to give their view.

> **gordintoronto said:**
> There are advantages to installing the VirtualBox from the VirtualBox web site, and then installing the Extension Pack from the same site. Then you would be able to use USB.
May I conclude that what I want to do is not possible (at this moment) with packages from the repository? Any other advantages (as the Oracle version is slightly newer)?

> **gordintoronto said:**
> I know, that's the Windows approach, but that's Oracle for you.
I don't understand. Is the extension pack proprietary? Or is it just the fact that Ubuntu overlooked the extension pack and that it therefor is not included in the repository.

> **Habitual said:**
> Unless you are testing a USB installation media, then I suggest allowing Virtualbox to use the ISO *before installation* (Under [COLOR=Red]Settings[/COLOR] > [COLOR=Red]Storage[/COLOR] and click the Drive Icon there, "[COLOR=Red]Choose a Virtual CD/DVD disk file...[/COLOR]" navigate to the ubuntu.iso and save those settings.
When you [COLOR=Red]start Virtualbox, press F12[/COLOR] and select "Other boot devices: > c) CD-ROM

I will give that a shot in the future; sounds easier ;) Although I don't mind trying the Oracle route above if necessary.

---

### Post by Cheesemill on 2012-09-24
I think you're having problems because VirtualBox doesn't support booting from USB ***at all*** (even with the extension pack installed).

To install a guest OS you need to do it from either an .iso file or a physical CD.

---

### Post by Wim Sturkenboom on 2012-09-25
> **Cheesemill said:**
> I think you're having problems because VirtualBox doesn't support booting from USB ***at all*** (even with the extension pack installed).

To install a guest OS you need to do it from either an .iso file or a physical CD.
Thanks; gave up on USB ;)

> **Habitual said:**
> Unless you are testing a USB installation media, then I suggest allowing Virtualbox to use the ISO *before installation* (Under [COLOR=Red]Settings[/COLOR] > [COLOR=Red]Storage[/COLOR] and click the Drive Icon there, "[COLOR=Red]Choose a Virtual CD/DVD disk file...[/COLOR]" navigate to the ubuntu.iso and save those settings.
When you [COLOR=Red]start Virtualbox, press F12[/COLOR] and select "Other boot devices: > c) CD-ROM

Hope that helps.
It did indeed help; tricky part was your second instruction, but I found it. There are two controllers in the storage tree (IDE and SATA). I picked the IDE one, clicked on the CD icon and could add a 'virtual cd/dvd'. Installing now and will mark as solved.

Thanks everybody

---

### Post by JKyleOKC on 2012-09-25
> **Wim Sturkenboom said:**
> I don't understand. Is the extension pack proprietary? Or is it just the fact that Ubuntu overlooked the extension pack and that it therefor is not included in the repository.Yes, the extension pack **is** proprietary. Before version 4.x came out, VBox had two editions of each version: the OSE (Open Source Edition) and the PUEL (Personal Use Evaluation License). Only the OSE version was in the repositories; to get the PUEL (which was still free as in beer) you had to go to Sun/Oracle for it.

With version 4.0, the non-proprietary parts of the PUEL version were moved into the OSE, and the "OSE" term was dropped. The remaining stuff from PUEL became the extension pack, and again you have to get it direct from Oracle.

They're now up to version 4.2, while the repositories remain frozen at older releases, so going to Oracle is advisable in any case.

---

### Post by Wim Sturkenboom on 2012-09-26
Thanks; I thought it was all non-proprietary now; my mistake. I saw that Oracle was already further.

I don't think it matters to much for me. I just need it to be able to play with different distros and to be able to help people here without screwing up my main OS.

---

### Post by JKyleOKC on 2012-09-26
Apparently, USB 2.0 has some sort of patent problem, or perhaps it's simply that the code to make it work is licensed and Oracle has to keep some sort of restriction on it. At least that's the impression I've gotten from things said on their forum... Fortunately, their PUEL license allows commercial use of the extension pack so long as it's not being re-sold itself. It's the only EULA I've seen that is quite explicit about it!

---

### Post by Habitual on 2012-09-27
> **Wim Sturkenboom said:**
> ...tricky part was your second instruction, but I found it. There are two controllers in the storage tree (IDE and SATA). I picked the IDE one, clicked on the CD icon and could add a 'virtual cd/dvd'. Installing now and will mark as solved...

Well, I had to leave you something for an "Aha!" moment now didn't I? :wink:

---

### Post by Wim Sturkenboom on 2012-09-28
It was more a 'shiver and pray' moment :lol:

Everybody thanks; it's working.

---

### Post by Habitual on 2012-09-28
There's a clone feature in my VirtualBox Version 4.1.18 r78361 and surprisingly enough a "Live CD/DVD" option that I have never used, but I do Pray quite often.

Peace

---

