---
title: "Prevent user from downloading/running executables"
date: 2010-05-14
forum: Security
---

### Post by executivul on 2010-05-14
Hello,
I'm implementing a Kiosk like system using Ubuntu. A large number of systems boot over the network and run from ram a customised Ubuntu. Systems autologin as a normal user account, no privileges.
My question is, as in the title, how can I prevent users from downloading and running some executables?
I need users to be able to use only the programs I provide, Firefox, Opera and OpenOffice. They must be able to download stuff (documents) so blocking download in the browser is not an option. 
They must not gain terminal access, so the systems have no xterm, but I don't want them to download and start a downloaded xterm or who knows what.

Thank you.

---

### Post by HermanAB on 2010-05-14
squid-cache

---

### Post by executivul on 2010-05-14
sorry, squid-cache is not enough, they can still come with xterm on a usb flash...
i need something local

---

### Post by HermanAB on 2010-05-16
Configure the USB stick mounting with policykit so it can read and write but not execute.

---

### Post by psusi on 2010-05-16
Make sure they can only write to the /home partition and mount it with the noexec option.

---

### Post by executivul on 2010-05-19
1. mounting of usb media with noexec option seems to be part of the solution
2. entire system runs from a 1GB tmpfs, should I create another tmpfs for the home of the user, and mount that with noexec option?
3. what about the /tmp? everybody must be able to write to /tmp, so they can download to /tmp, chmod +x /tmp/wathever and run it...

---

### Post by teh_drizzle on 2010-05-19
I would suggest mounting /tmp separately with the noexec (this is suggestion no matter what the machine is being used for). For your case, maybe having /home and /tmp on the same partition (this way you only need one extra partition). And yes, /tmp should have the sticky bit set, but no one needs to exec from it! :)

---

### Post by executivul on 2010-05-19
As far as I can tell a normal user should not be able to write anywhere but his own home dir and the /tmp, is that correct? And that for a fully functional graphical system.
As a "bonus" the user should be able to write external usb media.
So by limiting the user to write only to these three locations, and making these locations noexec partitions I should solve the problem.

---

### Post by rookcifer on 2010-05-19
> **teh_drizzle said:**
> I would suggest mounting /tmp separately with the noexec (this is suggestion no matter what the machine is being used for). 

Depends on the distro.  Some distros, such as Gentoo, must have an executable /tmp.

---

### Post by bodhi.zazen on 2010-05-19
Mounting tmp noexec can cause problems with any distro, although it is rarely a problem in any distro (not sure about gentoo).

In this case, however, I would mount /home and /tmp and things in /media (usb devices / cdrom ) noexec,nosuid

---

### Post by executivul on 2010-05-20
I'm looking at other options:

1.Signing executables, which is ok only in theory, but in practice I've yet to find a working Linux kernel patch to enable me to check for signatures.

2.Using a "hypervisor", I mean an administrator app that monitors apps run by normal users, I'm looking at AppArmor profiles. Is there a way to create a generic AppArmor profile which prevents any file from running if it is not in other profile? I mean, I make a profile for every used executable (firefox, openoffice, pcmanfm, mplayer, compiz, etc) and AppArmor shoud prevent any other application from running.

---

### Post by bodhi.zazen on 2010-05-20
> **executivul said:**
> I'm looking at other options:

1.Signing executables, which is ok only in theory, but in practice I've yet to find a working Linux kernel patch to enable me to check for signatures.

2.Using a "hypervisor", I mean an administrator app that monitors apps run by normal users, I'm looking at AppArmor profiles. Is there a way to create a generic AppArmor profile which prevents any file from running if it is not in other profile? I mean, I make a profile for every used executable (firefox, openoffice, pcmanfm, mplayer, compiz, etc) and AppArmor shoud prevent any other application from running.

Yes, you make a new shell, call it "jailbash"

```
sudo ln /bin/bash /usr/local/bin/jailbash
```Must be a hard and not a soft link.

You then generalt an aa profile for jailbash.

Here is a template - It mostly works, you probably need to update a few paths (python for example).

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash)

You then set the login shell to jailbash (add the path to /etc/shells then sudo chsh user_name).

I use jailbash to lock down the guest account.

---

