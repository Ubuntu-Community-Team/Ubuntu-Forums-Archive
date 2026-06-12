---
title: "Wily 28-5-15 daily build LVM funny second decrypt code?"
date: 2015-05-28
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2015-05-28
I installed wily daily build ( 28-5-15) this morning and set it up with an encrypted LVM. 

Normally there's nothing to it. It's easy to set up and install, even though the install process is a bit longer than non-LVM install.

LVM runs great on my hardware, and this time I am testing LVM with encrypted /home. Still the system is responsive and fast.

In the boot process I have to type my de-crypt code, as always. But now, starting with this install, I also must type a password for the encrypted swap-partition :o.

I had *not* told the system that I want an encrypted swap, but apparently the installer have made one in the process of creating the LVM.

I have tried my usual de-crypt code and it works fine - The monkey part of it is; **so does hitting enter** without entering a code - This simply *has* to do with the very early state of wily, some thing being prepared as a new feature when creating an LVM.

Have any of you experienced this scenario? 

/Jimmy

---

### Post by dino99 on 2015-05-28
that happen but with ubuntu-next, like it was answered a couple days ago
[http://ubuntuforums.org/showthread.php?t=2279752](http://ubuntuforums.org/showthread.php?t=2279752)

---

### Post by jimmy-frydkaer on 2015-05-28
Problem is that it is *not* Ubuntu Next I have installed it is wily daily build and not in itself a support request as much a probe to find out if the function is a new security implementation for the regular Ubuntu - I am not talking about any four digit PIN-code but a password.

---

### Post by grahammechanical on 2015-05-28
> some thing being prepared as a new feature when creating an LVM.

That would be my guess. It is not unusual for things to be worked out during the development period. It could be a matter of concern that we can setup an encrypted home but not an encrypted swap partition as the swap partition just might have sensitive data on it.

I do not know if this was the case in the past and is now being rectified with the implementation not being completed. Or, if we always got encrypted swap with an encrypted home and now for some reason the functioning has been altered as improvements are made.

We need to see if there is a launchpad bug for this. Clearly, the ideal case would be to enter the decrypt code once and not be presented with a request for authentication to unlock every encrypted partition. I do not see that pressing enter as much of an issue as we would not be getting that far if we did not know the decrypt code. The issue is "enter decrypt code once and unlock all encrypted partitions of that user." Or is it more complex than that?

But it is still very much early days for Wily.

Regards.

---

### Post by jimmy-frydkaer on 2015-05-29
This seems to be a problem that also exist in Ubuntu 15.04 with encrypted /home: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1449555](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1449555)

It seem to be a systemd related problem and not cryptsetup (Ubuntu). But it is a flaw that have sailed on to wily too.

---

