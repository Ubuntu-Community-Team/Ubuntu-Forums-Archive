---
title: "How do I keep everybody out of Ubuntu!!"
date: 2008-05-12
forum: Security
---

### Post by ownaginatious on 2008-05-12
I have a computer at school with Ubuntu installed, and these stupid jerks keep changing around all the passwords and generally screwing around with everything while I'm not there. I tried removing the recovery console from the boot loader, but they still managed to get in - possibly with a Live CD. Is there a way to keep them completely out?

I find it to be incredibly stupid that Ubuntu has such a large security loop hole like this. Anybody could walk up to any server/workstation running Ubuntu, and change the computer in seconds to their control... but whatever...

Any help would be GREATLY appreciated! Thanks!

---

### Post by Monicker on 2008-05-12
> **ownaginatious said:**
> I have a computer at school with Ubuntu installed, and these stupid jerks keep changing around all the passwords and generally screwing around with everything while I'm not there. I tried removing the recovery console from the boot loader, but they still managed to get in - possibly with a Live CD. Is there a way to keep them completely out?

I find it to be incredibly stupid that Ubuntu has such a large security loop hole like this. Anybody could walk up to any server/workstation running Ubuntu, and change the computer in seconds to their control... but whatever...

Any help would be GREATLY appreciated! Thanks!

Physical access is root/administrator access, regardless of the operating system.  Windows is no exception.  If you want them to be truly secure from tampering with live cds and such, lock the machines away, and only allow remote access.

---

### Post by Mr A Mouse on 2008-05-12
Anytime someone can get physical access to a computer, "security" is gone. That's not a function of Ubuntu or of Linux, that's any computer, anywhere.

That being said, if the computer is yours (as in you own it), delete all user accounts except for your own and root, and change the passwords to strong passwords--this includes the guest account. Reboot the computer, change the boot disk options in bios, set a supervisor password for bios, and reboot. However, please note that this is NOT an absolute preventative--also note that not all computers can use a supervisor password for the system bios. 

If it's a school computer, then password policy is set by the school administrator, and there's not much you can do about it.

---

### Post by sub2007 on 2008-05-12
I would password protect the BIOS. Then the only way (I think) that they could do anything would be to enter the BIOS password and to reset the BIOS would involve opening up the computer.

As said it's not perfect, but it will hopefully be more secure.

---

### Post by Meson on 2008-05-12
I would use LUKS (and I do use it) for full disk encryption.  Use the lowest possible setting (128 I believe) with the fastest algorithm (aes, twofish, blowfish, etc ... not sure which).

You don't need any really really strong encryption because even the lowest grade will be enough to deter your roomates.

You can set it up to use a password when you bootup, a usb key, or both (not at the same time, just the option to use a password in case you don't have your key).

---

### Post by cdtech on 2008-05-12
I agreee "full disk encryption". As mentioned, any computer can be breached but the files can't if their encrypted properly. I use encryption on my laptop for this reason.

---

### Post by vrangforestillinger on 2008-05-13
You might want to password protect grub as well, to make it harder to fool around with it. (By default you can edit the bootup-commands from within grub.) Here is a howto:[HOWTO: Password protect your GRUB entries]("http://ubuntuforums.org/showthread.php?t=7353"). Be shure to check out the comments further down in the linked thread, particularly the comment by soul_rebel: Instead of adding the password to every boot-entry, use the password-entry found in the commments of menu.lst. This will disable interactive changing of commands during bootup until the user press "p" and enters the correct password.

---

### Post by dendrobates on 2008-05-13
if you install Ubuntu using the alternate CD, you can select encrypt+lvm during install, and that might keep them out.  If they are a bit more skilled you will need to put your private key on a usb drive.

---

### Post by yaztromo on 2008-05-14
If you're fairly certain that they won't be taking the PC case apart to upset you then:

Set BIOS to boot HDD first then password it
Lock Grub so only you can boot to recovery console or edit kernel params
Disable the Magic SysRq key in sysctl.conf (google it)
Add the Don't Zap Option to xorg.conf
Remove the control-alt-delete event from /etc/event.d
Use strong passwords

That should prevent a lot of tomfoolery, others may think of more

HDD encryption is a step you may want to think about before you decide on it.

---

### Post by az on 2008-05-14
Use full-root encryption.

---

### Post by DigitalDuality on 2008-05-14
d

---

### Post by fmartinez on 2008-05-14
If they are using a live CD. 
Change the root/admin password. 
Then change the config file in /etc/fstab so it won't auto load the cd-rom. 
or you can remove the cd rom and mount another cd rom from another location. 
Yes, when physical security is comprimised everything else goes out the window. 
You can also look at getting a removable drive. I use these in school. You can load the OS on the drive and when your done just pop the drive right out and your done for the day.

---

### Post by yomaoni on 2008-05-15
I would have to agree with several of the posts, once physical security has been breached then all bets are off.  I am reminded of a quote I heard a while ago,

> The only truly secure system is one that is powered off, cast in a block of concrete and sealed in a lead-lined room with armed guards - and even then I have my doubts. -Eugene H. Spafford

---

### Post by hyper_ch on 2008-05-15
+1 to full disk encryption and set your "screensaver" so that it will lock the user after a certain amount of time (like 5min of inactivity)

---

