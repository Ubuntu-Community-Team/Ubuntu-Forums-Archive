---
title: "So easy to break users password from recovery"
date: 2020-06-11
forum: Security
---

### Post by bsimjoo on 2020-06-11
I use Windows and Ubuntu together on my system and I use default grub boot loader. I found a very very simple way to break users and root password by using root shell in Ubuntu recovery option in grub and just typing ```
passwd <my-username>
``` I know there's a way to protect my grub with password or encrypt whole disk. but it's extra simple to break password of a beginner user just by a single command-line! So if it's such simple to break, why should we set a simple user account password and do not encrypt whole disk? it would be so better if Ubuntu inform users about low security of users password if they don't use encryption.

---

### Post by The Cog on 2020-06-11
That's not breaking the password - it's replacing the password. I'm pretty sure that without encryption the same is possible with Windows too (and with your router). 
So what's your point? That you don't know how to do it on other devices?
[https://support.microsoft.com/en-gb/help/4490115/windows-change-or-reset-your-password](https://support.microsoft.com/en-gb/help/4490115/windows-change-or-reset-your-password)

---

### Post by ajgreeny on 2020-06-11
This is nothing new; it has been known and discussed in these forums for years when, for example, a new user has forgotten their password, or not understood when installing how important their user password really is.

Bear in mind however, that what you have said in your post would be total gobbledegook to someone who has no knowledge that Linux even exists, and talking of Recovery mode from grub would mean nothing to most computer users.

You are somewhat privileged that you know all about this compared to most, and also don't  forget that in any situation where encryption is not used, physical access to a computer means all security has disappeared.

---

### Post by The Cog on 2020-06-11
Yes, it's a balancing act. Security vs the horrors of unintended lockout. Requiring physical access is probably an acceptable compromise for most folk, especially home use. It's one I'm happy with. You can always keep your really secret stuff on an encrypted partition. You see occasional posts here from people who can be quite distraught about losing everything because of full encryption and some hiccup - photo albums, wedding video, contact lists etc. 
On the other hand, at my work all machines are encrypted, and recovery is based on reinstall the OS. Data is kept on fully backed up servers. There's a big investment in that security.

---

### Post by EuclideanCoffee on 2020-06-11
You can do the following accelerating levels of complexity:

1. Enable root user with password.
2. Lock grub menu.
3. Lock single user sign on.

1/3 of these options should be sufficient. However security will improve with each added, with 2 and 3 swapping.

I'd need more time to go into each detail, but I'm sure there is plenty of help on all three topics.

---

### Post by Paddy Landau on 2020-06-12
The very best way to avoid this mess is to encrypt your entire disk with LUKS.
That way, no one can get in (not even recovery mode) until the disk is unlocked.

Unfortunately&#8230;

Canonical has not taken this issue seriously. Although it's possible to encrypt your entire disk with Ubuntu's default installation, that only works if you don't dual-boot, because this method wipes out other installations on the disk.

We know that [full-disk encryption (including /boot)]("https://help.ubuntu.com/community/ManualFullSystemEncryption") while allowing dual-boot is possible, because it's been proven.
But it's a mess at the moment, because Canonical doesn't support it and pretty much refuses to do so.

The best way, I believe, is to use Ubuntu's default full-disk encryption (even though it doesn't encrypt /boot), and run Windows in a virtual machine. The problem, of course, is that you need a sufficiently powerful machine to run this at a reasonable speed.

---

### Post by EuclideanCoffee on 2020-06-12
In the case where multiple users access a computer, encryption would not work. LUKS is essential, but it doesn't solve the problem.

Only blocking single user sign-on will prevent users from gaining root access without authentication.

This can be done with a root password and/or grub menu password.

---

### Post by ajgreeny on 2020-06-12
And as has been said many times before, but is always worth repeating, **[COLOR="#FF0000"]MAKE SURE YOU HAVE FULL WORKING BACKUPS ON ANOTHER DISK[/COLOR]**, preferably off site, as if there is a problem with the disk or encryption you will have lost everything with no chance of getting it back.

Sorry to bang on about this but we've seen too many losses where backups are thought about far too late.

---

