---
title: "How do new Ubuntu releases work?"
date: 2007-03-11
forum: The Cafe
---

### Post by Atreus12 on 2007-03-11
Ubuntu 7.04 will be the first time I will be around for a new version, and I was wondering how the release worked.

When 7.04 is released, will it be modified after that point? For example, if it is released on April 19, should I wait a week to allow any bugs to be fixed? Or is it set in stone when it is released?

A little over a month away, and if you can't tell, I'm getting anxious. :)

---

### Post by OffHand on 2007-03-11
> **Atreus12 said:**
> Ubuntu 7.04 will be the first time I will be around for a new version, and I was wondering how the release worked.

When 7.04 is released, will it be modified after that point? For example, if it is released on April 19, should I wait a week to allow any bugs to be fixed? Or is it set in stone when it is released?

A little over a month away, and if you can't tell, I'm getting anxious. :)

It's not set in stone. There will be security updates and bug fixes. No new versions of applications though unless they are backported. So waiting a week, maybe 2, doesn't hurt.

---

### Post by terrysalmi on 2007-03-11
How easy is it typically to upgrade a system?  Will the upgrade show up in the taskbar and be seamless?  Or is it like Windows where it's always recommended to do a fresh install?

---

### Post by LMP900 on 2007-03-11
> **terrysalmi said:**
> How easy is it typically to upgrade a system?  Will the upgrade show up in the taskbar and be seamless?  Or is it like Windows where it's always recommended to do a fresh install?

It should be fairly straightforward. The update process may take some time if you're not on a high-speed connection and sometimes a restart is necessary, but updating your system should be painless.

---

### Post by The Noble on 2007-03-11
The amount of dependency hell depends on how big the upgrade is and how many third party applications you have installed. If you have not installed countless random programs, and you are willing to force a few installs, it won't ben any hard to upgrade.

---

### Post by Atreus12 on 2007-03-11
> **OffHand said:**
> It's not set in stone. There will be security updates and bug fixes. No new versions of applications though unless they are backported. So waiting a week, maybe 2, doesn't hurt.


Will the .iso file that you download from Ubuntu change?

-Andrew

---

### Post by DoctorMO on 2007-03-11
yes, but the ship-it cds will still be dapper I believe.

Do they have a new upgrade tool or do you still need to change your sources.list config file?

---

### Post by LMP900 on 2007-03-11
> **Atreus12 said:**
> Will the .iso file that you download from Ubuntu change?

-Andrew

As far as I know, it doesn't.

Ubuntu 6.06 LTS has point releases (e.g. Ubuntu 6.06.1), but non-LTS versions such as Edgy and Feisty do not.

If you wait a few weeks after its initial release to download Feisty, you will still be getting the same ISO as everyone who downloaded it on release day - unless there was a significant problem with the original ISO. This means that you will have to update in order to get the latest security fixes and application updates.

Edit: According to the post above this one, the ISO does change... Can someone else clarify this confusion?

---

### Post by qamelian on 2007-03-11
> **DoctorMO said:**
> yes, but the ship-it cds will still be dapper I believe.

Do they have a new upgrade tool or do you still need to change your sources.list config file?

It hasn't been necessary to edit your sources.list for a while. Update Manager does all the necessary work for you when it detects a new Ubuntu release and you choose to upgrade. If the upgrade is unable to complete for some reason it automatically reverts to you previous sources list.

I've use the update manager exclusively to update on of my systems from Breezy to Dapper to Edgy, and recently to Feisty. Haven't had to edit any files yet!

---

### Post by prizrak on 2007-03-11
> **DoctorMO said:**
> yes, but the ship-it cds will still be dapper I believe.

Do they have a new upgrade tool or do you still need to change your sources.list config file?

You haven't had to edit sources.list since Dapper. Update-notified will just pop up with "You need to do a dist-upgrade if you want all the updates" and OK/Cancel to press on. This won't happen on Dapper because Dapper is LTS and there you have to run the updater from CLI with an -a flag I believe (don't remember for sure so Google it). 

> dit: According to the post above this one, the ISO does change... Can someone else clarify this confusion?
The ISO will change from Edgy to Feisty and that is all. It will not include any updates after it goes final (aside from some very big problem with the ISO).

---

### Post by jdhore on 2007-03-11
i just updated to Feisty last night and i have quite a few 3rd party apps installed and the upgrade went quite well...had 1 or 2 minor snags, but i think they're more my fault than anything else

---

