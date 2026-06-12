---
title: "how to purge sick old pep Grub in multiboot Ubuntu20.4"
date: 2023-01-16
forum: Security
---

### Post by mkham on 2023-01-16
Have a 3 boot side-by-side installation:    Win10, which hasn't booted for 3 years (reboot virus on version update), Pep9, which was sick, + also recently stopped  booting, and Ubuntu 20.4.5, which got sick when I used the sick Peppermint for a week after 6 months with no problem. Have been running it only on RECOVERY Ubuntu.  **Just did full Boot-Repair Program from a boot stick,** inc fix Windows, purge and reinstall Grubs, but see the Pep9 grub is still there with old Ubuntu20.4 kernels, boot-repair script says it was purged and reloaded. Although the Repair seemed to all work OK, I haven't tried the Windows (or Ubuntu- still on boot stick) yet, wanted to clean any source of infection or problems.

 BUT I WANT TO PURGE IT COMPLETELY from the Live Ubuntu stick in Terminal. It IS booting up from the Ubun20.4 Grub Now, after that got sick, it had defaulted back to Pep9 GRUB. Notice those 2 Pep kernels are very fragmented, 4-15.0-196 has 114 pieces. Can I do that without messing up the new Ubun20.4 Grub?? Also wanted to purge + reinstall the last Ubun kernel (an option in Boot-Repair, but didnt check it- it purges ALL of them first). Could I do that ALONE, if I uncheck everything else on Advanced Boot-Repair? Best would be terminal commands to do those 2 things, remembering I'm running it off an identical LIVE UBUNTU stick. I am not a complete imbecile (been using Ubun since 2008), but terminal commands are never explained, and manuals have too few examples to really understand them. The Peppermint (+ then Ubuntu) gave all the signs of viral infection, erratic behavior, programs closing or disappearing suddenly. 

On another note, is there anything in Ubuntu 22.4 that doesn't work with my lappy? And what is a very light efficient Ubuntu, seems Peppermint gave up the ghost- newest still based on Ubun18.4?

Dell Inspiron 15-3467? CoreI5, 8gb ram, 2 Tb drive   
Thanks for any help.

---

### Post by oldfred on 2023-01-16
Post link to the summary report from Boot-repair, so we can see details and make specific suggestions.

Otherwise you need to remove UEFI boot entries & folders in ESP for any installs you do not want. And need to make sure they do not use same name as Ubuntu as both official and many unofficial flavors use ubuntu as UEFI boot entry.

And you have to make sure default boot entry is install you want. Boot-Repair's default is first install it sees. You have to use Boot-Repair's advanced mode to be able to choose which install to be reinstalled, so it then is the default.

---

### Post by mkham on 2023-01-16
Yeah, Ubuntu is first, I read all through the report, and when I started to boot, it came up first, although looked different- starker than original one., Peppermint is denoted in my Bios as an apostrophe! It doesn't seem to be showing any obvious errors or faults. Oh I want it, maybe to do a full reinstall of Peppermint 9, IF that doesn't destroy the installed programs. The video editing, and a bunch of programs, aren't duplicatible. Just want to clean the Ubuntu as well as possible. 

[https://paste.ubuntu.com/p/wy8kBtr9SR/](https://paste.ubuntu.com/p/wy8kBtr9SR/)

---

### Post by oldfred on 2023-01-16
Last install always makes itself first in boot order.
Not sure how close Peppermint is to Ubuntu, its another unofficial flavor, so they base it on Ubuntu but make changes.

If you have not, you need to make full backups of all installs. Windows often is more difficult to reinstall so many image it.
With Ubuntu you can easier reinstall it and restore from backups, if backups include everything that is not system.
I export list of installed apps, backup my /home and data Partition(s). I edit a few system files like grub, so just copy those into /home rather than backup all of /etc. If server apps like database, we, etc, those are in folders in / and also need backup.

Do not know if it works with Peppermint, but you can do a "dirty" install. That is where you do not check the format box when you reinstall. It installs system & will overwrite any system configfiles to defaults. But your files are not changed.

If not using Windows best not to use NTFS. NTFS often needs repairs that you can only do from Windows like chkdsk or defrag. And Windows likes to turn on fast startup setting hibernation flag. That prevents the Linux NTFS driver from default mount as you cannot write into hibernated file system with out causing damage.

---

### Post by mkham on 2023-01-17
Thanks. Windows isn't too important, since I never used it, except to have the flexibility to use it or exclusive software, AND do the hardware updates, which haven't been done in 3 years, although I managed the Bios Update from the stick drive after 10 trys- the instructions were quite wrong. Are they actually written INTO the hardware for all OS's, or irrelevant for a Linux installation? I know the funkiness of non-compatible Windows Bios settings. My Bios always had some weird error where the SAVE, CONFIRM, CANCEL add boot option box goes off of screen, so I don't know what I'm doing! 

What is best backup- never figured out where that was or how to do it- have +800 gb unused so of course wanted to have that. Thought Ubuntu stopped it as an option.

Peppermint is very close, a much faster lighter netbook version, with alot of preferable programs (like file mngr) and options. Needed it's speed- LIGHTWORKS video editor was so power-hungry, it barely ran on Pep unless you shut off every other program, never even tried it with Windows, because it does those infuriating auto-saves that lock it up for 10 seconds, Great when you started some update or new prog. But I think the newest one still is based on 18.4, the genius Mark, who invented it, died 2 years ago.

BUT I WANT TO PURGE PEP9 GRUB COMPLETELY from the Live Ubuntu stick with the Terminal. It IS booting up from the Ubun20.4 Grub Now, after that got sick, it had defaulted back to Pep9 GRUB. I noticed those 2 Pep kernels are very fragmented, 4-15.0-196 has 114 pieces. Can I do that without messing up the new Ubun20.4 Grub?? Multiple Grubs seems like a bad idea, even without my problems.

 Also wanted to purge + reinstall the last Ubuntu kernel (an option in Boot-Repair, but didn't check it- it purges ALL of them first); or just reinstall it (4-15-0-58). Could I do that ALONE, if I uncheck everything else on Advanced Boot-Repair? Best would be terminal commands to do those 2 things, remembering I'm running it off an identical LIVE UBUNTU stick. When I tried to do Purge +/or Reinstall Grub from lousy instructions, I kept getting errors- "failed to get Canonical path of /Cow", think I didn't have proper CHROOT or Chown commands/permissions. But Boot-Repair managed it OK.

I will look up Dirty Installs

---

### Post by oldfred on 2023-01-17
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

There must be a million posts in the forum on backup and the many ways to do it. 
Mine is not the best, as I copy to multiple places, but not automatically.

TheFu - his history of backups
[https://ubuntuforums.org/showthread.php?t=2482329&p=14124545#post14124545](https://ubuntuforums.org/showthread.php?t=2482329&p=14124545#post14124545)
Restore broken system - TheFu
[https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2465713](https://ubuntuforums.org/showthread.php?t=2465713)
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)[[://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224|&p=13677224#post13677224]]
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) & 
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)

---

### Post by mkham on 2023-01-18
OK, guess no one knows Terminal commands anymore.  Don't trust any instructional 10 years old or more, Ubuntu, everything has changed too much since then.

Never noticed the Backup in Utilities, or it was too simple to be desirable. Never even heard of Deja Dup, but I'll try that. The Dirty Install seems way too simple, but I might try it, since Peppermint is unusable as it is. Afraid to run it at all, after it infected the Ubuntu, although maybe problems were in its Grub. That Fix Windows checkbox in Boot-Repair doesn't really do much?? We will see. The greyed out purge Grub option is cause it might actually might restore some files, eh, if I try to "Delete all kernels and reinstall last one".

---

### Post by ajgreeny on 2023-01-18
If all you want is for your Ubuntu installed version to be the OS that manages grub and as you have only a single internal hard disk, I think you should be able to get things working that way by booting to Ubuntu then running command ***sudo grub-install /dev/sda***.

As you have a UEFI boot system grub should be installed where it is needed automatically, ie, in your EFI partition.

However, it's a long time since I have done this personally and things may have changed so wait to see if **oldfred** agrees before you do this; he is our forum grub guru in my eyes so may have other important comments.

See [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) for some more info, but do wait for oldfred before leaping into action.
If I'm still correct with this suggestion, once Ubuntu is managing grub, you can delete the Pep 9 partition if you want to and regain that space for other use.

---

### Post by tea for one on 2023-01-18
> **mkham said:**
> OK, guess no one knows Terminal commands anymore.
Somewhat disingenuous - Have a look around the forum pages, there are thousands of terminal commands.
> **mkham said:**
> Never noticed the Backup in Utilities, or it was too simple to be desirable. Never even heard of Deja Dup, but I'll try that
It seems that you do not have any data backup at all?
If you do not, then, this is your _first priority_ (before removing the Peppermint partition and updating Grub)

To re-install Grub to UEFI via a running session (not a live session)
```
sudo grub-install --efi-directory=/boot/efi /dev/sda [COLOR="#0000FF"](other systems may be /dev/nvme0n1 or similar)[/COLOR]
```

---

### Post by oldfred on 2023-01-18
From a running system, you can just run sudo grub-install.
That uses all defaults and the ESP that is already mounted from fstab. If ESP gets reformatted and then new UUID, that has to be fixed first & efi system partition correctly mounted. 

I believe tea for one's command works then if ESP is not correct as it uses specific parameters.

---

