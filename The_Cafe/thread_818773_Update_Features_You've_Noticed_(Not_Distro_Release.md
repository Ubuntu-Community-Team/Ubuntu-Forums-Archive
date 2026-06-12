---
title: "Update Features You've Noticed (Not Distro Release Updates)"
date: 2008-06-04
forum: The Cafe
---

### Post by Exsecrabilus on 2008-06-04
So like usual, I saw updates available in the *Important security* and *Recommended* sections.

I installed, and it asked me to reboot. So I did.

I went along with what I was doing, but when my mouse hovered over **Applications Places System**, I noticed something.
Under **System**, there was a new section: **Control Center**!
At first I thought something was wrong, but then I remembered the updates.

This is cool, now there is **System** >> **Preferences**/**Administration**/**Control Center**.

Go Ubuntu updates!!!!! Post your update comments here (not distribution release upgrades, just plain updates.)

---

### Post by 23meg on 2008-06-04
[Stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates") do not introduce new features or change the behavior of the system substantially. You must have installed something else that enabled the Control Center menu item, or manually enabled (in System / Preferences / Main Menu) and forgotten about it.

---

### Post by klange on 2008-06-04
> **23meg said:**
> [Stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates") do not introduce new features or change the behavior of the system substantially. You must have installed something else that enabled the Control Center menu item, or manually enabled (in System / Preferences / Main Menu) and forgotten about it.

He did not manually enable it. Same happened to me. Of course, I don't like it being there (personally despise the look of the Control Center, if they adopted the CCSM look [which was based off the CC look], I would like it a lot better), so I immediately removed it.

---

### Post by BlueSkyNIS on 2008-06-04
I don't have Control Center and I updated just a minute ago, so it looks like you enabled it somehow yourself :-?

---

### Post by 23meg on 2008-06-04
[QUOTE=WindowsSucks]He did not manually enable it. Same happened to me.[/QUOTE]

Sounds inadvertent (= a bug). Do you know which update did it? I don't have it.

---

### Post by sports fan Matt on 2008-06-04
I agree with 23meg..Nothing of the sort here either

---

### Post by Rhubarb on 2008-06-04
The control centre managed to appear automatically for me as well after one of the updates.
If it makes a difference I'm running 64bit Ubuntu here.

---

### Post by 23meg on 2008-06-04
Looks like it's the gnome-menus 2.22.2-0ubuntu1 update. From the changelog:

>     - Explicitly do not include gnomecc.menu in the preferences menu
      instead of explicitly excluding it, so that alacarte doesn't know 
      it was excluded 


---

### Post by Exsecrabilus on 2008-06-04
Rhubarb, I'm running 64-bit too, LOL.

For others, did you reboot?

23meg, so the feature was excluded?
How come I have it then?

BTW guys, we're kinda going off-topic. XD


Another feature I noticed is:

In Synaptic, under **Status**, there is a new tab called **New in repository**.
Finally, a chance for new packages to shine! XD

---

### Post by 23meg on 2008-06-04
[QUOTE=Exsecrabilus]23meg, so the feature was excluded?
How come I have it then?[/QUOTE]

The update didn't mean to add a feature; stable release updates don't, so the basis of this thread is flawed. As far as I can tell, a side effect of the update caused the menu item to be shown when it shouldn't have been. It could be that it's only enabled if you've enabled and then disabled it before.

---

