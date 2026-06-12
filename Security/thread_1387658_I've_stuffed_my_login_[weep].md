---
title: "I've stuffed my login [weep]"
date: 2010-01-22
forum: Security
---

### Post by pcal on 2010-01-22
Hi guys,

I've muffed it this time. I'm using the karmic netbook remix on a fujitsu m2010, and while trying to sort out some other issues, created a new user account for myself.

Unfortunately, I failed to click the allow administrate system check box, thinking that I would be able to use sudo for that.

Anyway, now I only get to select the new user account at boot time. The root account is disabled, and the default user account that the remix install created (which previously loaded automatically on boot) seems to have vanished into the ether. Without access to sudo I can't fix the problem. I can't delete or edit the user account, I can even mount the filesystems that contain all my files. I would be happy if I could just get back the default user account that must still be there somewhere...

Please, is there any way I can fix this without having to wipe everything and start from scratch. It was all working really well - I was only chasing a minor improvement - now I can't get to everything important!

Thanks in anticipation,

Pcal

---

### Post by Grenage on 2010-01-22
Have a look here:

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by pcal on 2010-01-22
> **Grenage said:**
> Have a look here:

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

Thanks for the suggestion. Unfortunately, I don't have grub installed - the system boots directly into karmic - so I can't edit any boot options as your link suggests.

Does anyone know exactly what the username for the default account on a netbook remix is? I figure the root account is still there even though it doesn't come up in the user list, so perhaps the default user account is the same. I have the option to type in a user name, it's just not there to select from the list.

pcal

---

### Post by Grenage on 2010-01-22
Oh, netbook remix doesn't use Grub as a bootloader?  What does it use then?

---

### Post by HermanAB on 2010-01-22
Howdy,

The file that you got to edit is /etc/sudoers.  If you can, boot with a Lice CD, mount the local disk and edit that file.  It is quite self explanatory.

---

### Post by pcal on 2010-01-22
Grenage, I don't know what the bootloader is. I just went to the location where I have edited the grub configuration on other systems and there was nothing there.

Herman, thanks for the tip on what needed editing. I had figured the account I created wasn't in sudoers file, but had no idea where it was located. Unfortunately, my account didn't have sufficient privileges to edit it, and the Fujitsu, seeing as it's a netbook, doesn't have a cd dive to boot from which rules out a live disk as well.

Fortunately, I found a thread on another topic that identified the default user account as having the username "ubuntu". So I booted with that, leaving the password blank (as it had never asked for a password before), and it worked. So I have restored what was, and can now create the new user account with full access rights.

Thanks to you both for your offers of help...

Regards,

pcal

---

### Post by falconindy on 2010-01-22
> **HermanAB said:**
> Howdy,

The file that you got to edit is /etc/sudoers.  If you can, boot with a Lice CD, mount the local disk and edit that file.  It is quite self explanatory.

**A million times no. Never edit this file directly.**
If you're on a liveCD, you need to mount the partitions into a proper chroot and use 'sudo visudo'. Errors in the sudoers file (syntax or permissions) can make your problems even worse.

---

### Post by cariboo on 2010-01-22
Wouldn't it just be easier to hold down the shift key during boot to get to the grub menu, by default if you only have one OS on the computer grub is hidden, then select recovery mode. Once at the prompt add yourself to the admin group:

```
gpasswd -a <user> admin
```

There should be no need to chroot and manually edit the sudoers list.

---

### Post by pcal on 2010-01-25
> **cariboo907 said:**
> Wouldn't it just be easier to hold down the shift key during boot to get to the grub menu

Yep... Sounds a lot easier. (If only I had known):)

Thanks for the tip, will try to remember it if it ever happens again...

---

