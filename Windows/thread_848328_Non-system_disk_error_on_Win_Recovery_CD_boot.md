---
title: "Non-system disk error on Win Recovery CD boot"
date: 2008-07-03
forum: Windows
---

### Post by VChief on 2008-07-03
I don't think this is really a "Windows" issue, but it's on a Windows computer and I guess anything's possible. Working on a computer for a co-worker. He must have downloaded something nasty because his computer took a dump. Everytime I run something, it fixes one thing and breaks another. It all started with a continuous logging off right after login. I couldn't find anything on the net that seemed to pertain, so I ran chkdsk and that took a few hours. After that, it just rebooted over and over again. I could never figure out which was the offending driver (this included safe mode). Finally, it just decided to tell me that pci.sys was corrupted. Anyway, this is a long story just in case someone has any ideas they want to throw my way.

The main point of this thread is the Recovery CD won't boot. The computer is a 4-5 year old HP. When attempting to boot the recovery disk (HP's own disk), it begins to boot then comes back with the classic non-system disk error. As far as I can tell, it's not the drive. Knoppix booted up without a problem and so does my WinXP Pro disk. Problem is he's got Home so not much I can do with it, except use the recovery console. I think I have a Dell Home recovery disk somewhere around here. Don't know if that'll work though. I wanted to try to do a system restore and, if that didn't work, re-install (still trying to avoid that at all costs).

From what I can tell, the CD is booting like it should but that the file that should be kick-starting the thing is corrupt somehow. I have no other computer to test it on. Any other computer says that it's not an HP. Any ideas about what to do?

EDIT: He has used the disks before. So, I know they didn't come from HP jacked up.

---

### Post by fiddledd on 2008-07-03
Well, first question, have you checked the Recovery CD in another PC to see if it boots.?

---

### Post by fiddledd on 2008-07-03
Just realised I'm treating this like IRC instead of a Forum. :)

Ok, so the Non-system disk error means the Device it's trying to boot from doesn't contain boot files. Simple things to try:

Try the CD in another PC
Check your boot order in the BIOS
Make sure you have no external devices (USB Flash Drive, USB Hard Drive) it's trying to boot from

EDIT:
And make sure there's no disk in the Floppy Drive, if you have one.

---

### Post by VChief on 2008-07-03
The CD just reports back that it's not in an HP computer if I put it in any other computer. All the settings are correct and other CDs boot fine (both Knoppix and my XP Pro CD booted with no problem).

---

