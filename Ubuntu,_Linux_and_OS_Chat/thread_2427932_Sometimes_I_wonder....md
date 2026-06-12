---
title: "Sometimes I wonder..."
date: 2019-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by uRock on 2019-09-27
Sometimes I wonder if there should be a popup informing the user that they will have to enter their password often in the keyring when selecting this option.

I've only ever made the mistake of installing that way once. I'd rather enter the password at login and be done with it.

On the flip side of this, I also think people installing a new operating system should be reading documentation or at least testing it in a virtual machine to see how it acts.

What are your thoughts?

---

### Post by VMC on 2019-09-27
I use to auto login, and had a hard time getting keyring out of the picture. In the end its much easier to just login from the start. Only chrome was the trouble child anyway.

---

### Post by TheFu on 2019-09-27
I've never setup automatic logins.  To me, doing that just seems foolish on a multiuser OS.

I've never used/seen the keyring stuff.  Is it really an issue?  I suppose it is part of the KDE/Gnome experience? That would explain why I've never seen it.

---

### Post by uRock on 2019-09-27
> **TheFu said:**
> I've never setup automatic logins.  To me, doing that just seems foolish on a multiuser OS.

I've never used/seen the keyring stuff.  Is it really an issue?  I suppose it is part of the KDE/Gnome experience? That would explain why I've never seen it.

The people who set up their system like such are usually single user systems. I can understand the wanting of that. I think there was a time back in my XP days when our system was auto login and we shared the same login.

It is a DE thing. Not sure if all of them do it as I've only ever tried it with the default ubuntu desktop. I only ever lock my screen when leaving home, going to bed, or when there's company over. The wife and kid don't touch my computer unless invited to do so. 

They've both used ubuntu as their primary in the past, but have switched their computers to Windows because they both like to game.

---

### Post by mastablasta on 2019-09-30
keyring or Kwallet replace the need for password manager. so they have their use.

as for me i auto login at boot, kwallet opens up only when running chromium. i think the updates are handled with a different interface.

---

### Post by kansasnoob on 2019-09-30
For people like me that live alone it makes sense to auto-login. I mean if someone else has physical access to my computers they can walk away with the whole darn things. All 13 of them - presently 13, the number changes as projects begin and end. I do wish that the key-ring itself was unlocked during auto-login, and the various "how-tos" don't really work consistently.

I do however treat individual logins and passwords with a heightened level of concern, escalating based on sensitivity of info involved. I mean, I'm not sure about other browsers but in Firefox it's easy to view ALL saved logins and passwords with just a couple of clicks. Based on history though the greatest threats are of the info-holders end of things ......... like Equifax.

---

### Post by uRock on 2019-09-30
> **kansasnoob said:**
> For people like me that live alone it makes sense to auto-login. I mean if someone else has physical access to my computers they can walk away with the whole darn things. All 13 of them - presently 13, the number changes as projects begin and end. I do wish that the key-ring itself was unlocked during auto-login, and the various "how-tos" don't really work consistently.

I do however treat individual logins and passwords with a heightened level of concern, escalating based on sensitivity of info involved. I mean, I'm not sure about other browsers but in Firefox it's easy to view ALL saved logins and passwords with just a couple of clicks. Based on history though the greatest threats are of the info-holders end of things ......... like Equifax.

You can set a password for Firefox's password manager, so stored passwords can not be viewed without entering it.

---

### Post by Skaperen on 2019-09-30
if you live alone, or with very trusted people (maybe spouse, not kids, especially not teenagers) i can see the advantage of autologin.  i live alone and do that.  but i do have encrypted storage, mostly in case of theft.  the thief is likely more interested in the money instead of the data, but you never know about the people why buy from thieves.

actually my many userids on here are autologin as lightdm handles it so i can switch users faster.  it would be nicer if lightdm would require a password once for any to login then let me switch fast while they are in logged in state.

---

### Post by uRock on 2019-09-30
> **Skaperen said:**
> if you live alone, or with very trusted people (maybe spouse, not kids, especially not teenagers) i can see the advantage of autologin.  i live alone and do that.  but i do have encrypted storage, mostly in case of theft.  the thief is likely more interested in the money instead of the data, but you never know about the people why buy from thieves.

actually my many userids on here are autologin as lightdm handles it so i can switch users faster.  it would be nicer if lightdm would require a password once for any to login then let me switch fast while they are in logged in state.

Does lightmd give you any kind of keyring pop-ups? It has been several years since I've tried any auto-logins, but I do still see threads about it being an issue in the standard ubuntu installs.

---

### Post by mastablasta on 2019-10-01
i am not sure lightdm is connected with the keyring. keyring is password manager so it should open for certain applications only (those where passwords are stored for example).
[URL="https://wiki.gnome.org/Projects/GnomeKeyring"]
https://wiki.gnome.org/Projects/GnomeKeyring[/URL]

if you look here you can see that GDM is outside: [https://wiki.gnome.org/Projects/GnomeKeyring/Architecture](https://wiki.gnome.org/Projects/GnomeKeyring/Architecture)

you are supposed ot have a different password for these. but i just use the login one since it only pops up when using chromium, which i rarely use.

---

### Post by VMC on 2019-10-01
With Lubuntu, keyring never shows its ugly face. Its very active on Xubuntu. I just tested it using the "[getty]("https://wiki.archlinux.org/index.php/Getty")" autologin on lubuntu. chrome is the only one that complains when keyring is active on all my systems, except Lubuntu.

---

