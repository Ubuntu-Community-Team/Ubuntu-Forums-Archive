---
title: "stupid noob question"
date: 2006-03-27
forum: Server Platforms
---

### Post by sas13 on 2006-03-27
sorry for the spam but:

The chorus line for answers to security (firewall/AV/etc.) questions for simple desktop users like me seems to be -

"as long as you keep your root password safe, and don't use the root account without need, your system is pretty safe straight out of the box"

the logic being that it would be hard for anything you meet on the net etc. to gain privileges to make changes to your core system.

here's my problem with that (or is it?) - 
if my system got messed up, sure it would be a drag but worst case is a reinstall, and maybe a few hours of setup.

on the other hand if my <user> files are messed up - all of my work, email archives, music and video collections etc. - now that's something not easly fixed.

sure I know about making backups, but you get my point.

---

### Post by Sef on 2006-03-27
> on the other hand if my <user> files are messed up - all of my work, email archives, music and video collections etc. - now that's something not easly fixed.

Well a firewall is something that you should have on your computer to make it harder  to break into your computer and messing up your /home.

---

### Post by sas13 on 2006-03-27
ok, so I'm glad I have a firewall set up.

how likely is anything like that to happen?

I mean, what kind of bad things are out there, and is /home generally safe from them?

(I'm just saying this because all those "just keep root safe" threads I've read seem to imply that "stuff happens" but it's possible to keep it out of the admin areas)

---

### Post by lean on 2006-03-28
Do you want security or safety or both?
Security is just that no other person can read your files. Safety is that your files does not disapear (and the system works).

None of these is handled by Ubuntu. Just run a .sh, .pl or .bin file - suggested in a forum, and you could be completely b0rked.

The good thing about userspace, is that your boot process and hardware has not suffered. So you could in theory log in as a new (super) user, examine the files in your home directory and make sure no trojans has been installed.

There are no good tools for resetting launch activity in Ubuntu. So it is a lot of manual work (is gnome-session launching any trojans, has firefox any plugins installed, has open office.. etc).

So, no, you are not safe in using Ubuntu. You can take backup of important data, but it will not ensure:
1. the files are corrupted - a userspace program could trick gnome-vfs into encrypting all your files. From a user perspective it looks like all the files are still there, but as soon as the malicious program decides you do not need the data anymore, it deletes its own key from memory and disk. Now you have an encrypted backup, and no way of getting your data back.

2. All your personal information is send into the net. There is no way you can see what information is send to where.

---

