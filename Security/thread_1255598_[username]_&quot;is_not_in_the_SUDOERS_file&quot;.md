---
title: "[username] &quot;is not in the SUDOERS file&quot;"
date: 2009-09-01
forum: Security
---

### Post by misteralexander on 2009-09-01
Okay, I did a CLI-minimal install on my PS3 in an effort to conserve it's meager resources.

It all went fine until I tried to "sudo apt-get install", and I'm met with "Please Enter Your Password" . . . did that, [username] isn't in the SUDOERS file.

Okay, so I went to [https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers") for help, and while it seems pretty straight forward, there was a snag.

**YOU MUST BE ROOT TO EDIT THIS FILE**

Okay, no problem, right? Wrong.

I went to: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") to learn how to enable the ROOT account, since I'm not in the damn sudo file.  Also, as a side note "sudo -i" & "sudo su-" didn't work.

So, the ROOT page told me to type "sudo passwd root", but alas, I'm not in the SUDOERS file.  I'm caught between a rock and a hard place, left with only a blinking cursor to anagonize me. LOL.

Please help, as I've tried to help myself first.

Thanks,
Alex.

---

### Post by lykwydchykyn on 2009-09-01
Rather than enabling root, which is a bad idea, boot into recovery mode (from the GRUB prompt), where you have the option to drop to a root shell.  From there, you can add yourself to the sudoers file with the visudo command.

---

### Post by sisco311 on 2009-09-01
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by sisco311 on 2009-09-01
> **misteralexander said:**
> Okay, I did a CLI-minimal install on my PS3 in an effort to conserve it's meager resources.


D'oh!!! It's a PS3... :)

[list=i]
[*]
reboot and at the kboot screen type:
```
sudo -i
```
this will start a root shell.(it will NOT prompt for a password)


[*]
remount the root ("/") partition as read/write:
```
mount -o remount,rw /
```


[*]
add your user to the admin group
```
adduser username admin
```
(replace username with your log in name)

[*]
edit the sudoers file:
```
EDITOR=nano sudo -E visudo
```

[*]
and make sure it looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL
**%admin ALL=(ALL) ALL**
```

[*]
to save the file and exit press Ctrl+x, y, Enter.


[*]
and press Ctrl+Alt+Del to reboot.
[/list]

---

### Post by misteralexander on 2009-09-01
> **lykwydchykyn said:**
> Rather than enabling root, which is a bad idea, boot into recovery mode (from the GRUB prompt), where you have the option to drop to a root shell.  From there, you can add yourself to the sudoers file with the visudo command.

Man, and I got all excited and everything too, LOL.

That sounded like a great idea, I've seen that menu before.  Well, I'm using my PS3 as my host & as such, I don't think i'm using GRUB. I'm using "[PETIBOOT]("http://ozlabs.org/~jk/projects/petitboot/")".

So, there is no loading stage for me to press a key and get to the recovery menu. I do, however, remember that if I did a hard shutdown ( ~$ sudo shutdown now ) it would kill the system and take me to a recovery console.

But, alas, the circle of death "[username] isn't in the SUDOERS file".

This is starting to suck,
Any ideas now?
-Alex.

---

### Post by misteralexander on 2009-09-01
> **sisco311 said:**
> reboot and at the kboot screen

I'm using PETIBOOT, a graphical boot manager, based on KBOOT.  do you recommend I just screw ease of use and go with KBOOT?  Not trying to be sarcastic here, really asking a question.

LOL.

-Alex.

---

### Post by sisco311 on 2009-09-01
2 x D'oh!!!

0. at the petiboot screen press Alt+F1, then follow  my previous instructions.

---

### Post by misteralexander on 2009-09-01
> **sisco311 said:**
> at the petiboot screen press Alt+F1, then follow my previous instructions.

Well, it was certainly something I didn't know.  When I hit Alt+F1, it took me to "BusyBox the build in shell (ash)".  I typed "sudo -i" and it dropped me to

root@OpenWRT:

Once there I typed:

mount -o remount,rw /  (this went fine)

adduser username admin (had an error: "bin/ash unknown: adduser")

**Kept on going, just incase**

EDITOR=nano sudo -E visudo (had an error: "bin/ash unknown: sudo)


So, I think, with your help . . . I'm definitely on the right track, I'm just not expirenced enough to navigate this problem in the terminal.

Hope your able to still help,
-Alex.

---

### Post by sisco311 on 2009-09-02
I have no experience with PETITBOOT, but according to the web site, ubuntu should be mounted on /var/tmp/mnt/ps3da1.

Try to chroot into ubuntu:
```
chroot /var/tmp/mnt/ps3da1
```
and then add your user to the admin group and edit the sudoers file.

Or you can try to boot in ubuntu's recovery mode:
```
kexec -f --append="root=/dev/ps3da1 ro single" /var/tmp/mnt/ps3da1/boot/**vmlinuz-XYZ**
```

replace vmlinuz-XYZ with the actual name of the kernel image.
to get the name type:
```
ls /var/tmp/mnt/ps3da1/boot/vmlinuz*
```

HTH

---

### Post by adameliaz on 2009-10-11
Hi Alex

Did you solve this problem? I'm having a similar problem. Did an installation, and experiencing the same as you, when i'm trying to run sudos. 

However, I'm not using petiboot, just kboot. So i'm lookin for a way to access recovery mode on my ps3!, or alternately running a root shell from kboot.

By the way, I'm a newbie, just did an installation also on my ps3.

Any help much appreciated.

Adam

---

