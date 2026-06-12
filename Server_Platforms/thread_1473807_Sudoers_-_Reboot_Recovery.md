---
title: "Sudoers - Reboot Recovery"
date: 2010-05-05
forum: Server Platforms
---

### Post by timwebuk on 2010-05-05
Wasn't sure which forum entirely to post this in... I seem to have done something completely noob and remove myself from the sudoers file...?!  Somehow... I've no idea, I was playing with the chgrp last night, but upon reboot today I no longer am in it.

I read I need to reboot in recovery mode but how I can reboot without root?

Also, I'm still not entirely sure what I've done or how to resolve it, so any tips would be MUCH appreciated.

Cheers.

I'm running Ubuntu Lucid Server

---

### Post by cdenley on 2010-05-05
Did you try doing ctrl+alt+del? Maybe press the power button once? If you're really desperate, you can pull the plug, but that might risk file corruption.

You probably removed yourself from the admin group. When you get a root shell from recovery mode, run this command, replacing "username" with your username:
```

adduser username admin

```

---

### Post by timwebuk on 2010-05-05
Wow I feel like a noob!

Thanks for the help.

Should I add a password to the root account?  As I read that it's 'disabled' in Ubuntu by default.  I just didn't like the idea of booting in recovery and having straight access to root

Cheers.

---

### Post by sisco311 on 2010-05-05
EDIT: too late. :(

Try ["Raising Elephants"]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device") :).

Holding down Alt and SysRq while slowly typing REISUB will get you safely restarted.

---

### Post by cdenley on 2010-05-05
> **timwebuk said:**
> Wow I feel like a noob!

Thanks for the help.

Should I add a password to the root account?  As I read that it's 'disabled' in Ubuntu by default.  I just didn't like the idea of booting in recovery and having straight access to root

Cheers.

I recommend you don't set a password for root. That ensures nobody will authenticate as root, in case you install software for remote logins or someone gains local access somehow.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-05-05
> **cdenley said:**
> I recommend you don't set a password for root. That ensures nobody will authenticate as root, in case you install software for remote logins or someone gains local access somehow.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1

> **timwebuk said:**
> Wow I feel like a noob!

Thanks for the help.

Should I add a password to the root account?  As I read that it's 'disabled' in Ubuntu by default.  I just didn't like the idea of booting in recovery and having straight access to root

Cheers.

Then set up a grub password. A root password doesn't disable the ability to boot into a root shell, one could edit the grub entry and boot with the *rw init=/bin/bash* kernel parameters or simply boot a live CD/USB. ;)

Check out [thread=989517]*Physical access is root access*[/thread] from the Recurring Discussions forum. :)

---

### Post by timwebuk on 2010-05-05
Thanks guys, I'll have a look into passwording the grub file.  No doubt it'll go wrong, but I've learnt a hell of a lot so far just by doing things I probably shouldn't.

---

