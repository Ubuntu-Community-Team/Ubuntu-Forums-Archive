---
title: "How to password-protect root."
date: 2013-09-02
forum: Security
---

### Post by Jonathan Precise on 2013-09-02
Hello all!

I have heard that if you go in recovery mode you can use "Drop to root-shell prompt" to preform administrative tasks (no password).
Is there a way to password-protect root (or recovery entries)? Security is a priority here.

---

### Post by Bucky Ball on 2013-09-02
*Thread moved to **Security Discussions**.*

You'll probably have more luck here. ;)

---

### Post by deadflowr on 2013-09-02
You can either set up a grub2 password, in which case you set passwords and users(vice versa) per situation.
Or an easier, yet one prone with possible problems is to edit the /etc/default/grub file and uncomment the line
GRUB_DISABLE_RECOVERY="true".
Doing so will remove the recovery option from grub.
It'll also make trying to run recovery mode very hard, if even possible.
[Grub2 Password]("https://help.ubuntu.com/community/Grub2/Passwords")

Edit: And can we please avoid the inevitable moving of goal posts here(ie what if the perp uses a live cd, then change the bios settings, and then what if the perp resets the bios, etc etc)

---

### Post by Elfy on 2013-09-02
Have a look through here - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Hungry Man on 2013-09-02
> 
[COLOR=#000000]Edit: And can we please avoid the inevitable moving of goal posts here(ie what if the perp uses a live cd, then change the bios settings, and then what if the perp resets the bios, etc etc)[/COLOR]
Why?

This is about protecting against physical access. Setting a password like this is just a stupid and trivially bypassed way to do this, and it would be wrong not to explain that.

Yes, they have physical access, write access to the device, read access, etc - grub is irrelevant. If you want to prevent someone with physical access to the device from accessing data you need encryption. That's all there is to it.

---

### Post by sandyd on 2013-09-02
> **Jonathan Precise said:**
> Hello all!

I have heard that if you go in recovery mode you can use "Drop to root-shell prompt" to preform administrative tasks (no password).
Is there a way to password-protect root (or recovery entries)? Security is a priority here.

Encrypted LVM (LUKS)

There should be an option in the Ubuntu installer to select that.

---

