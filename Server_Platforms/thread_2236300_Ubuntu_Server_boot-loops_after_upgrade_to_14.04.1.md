---
title: "Ubuntu Server boot-loops after upgrade to 14.04.1"
date: 2014-07-25
forum: Server Platforms
---

### Post by jethro1138 on 2014-07-25
Hi all,

I recently upgraded one of my servers from 12.04 to 14.04.1 using do-release-upgrade. It went smoothly, no errors, no warnings, no problem.

Except now it boot-loops.

Server starts, grub automatically sends it to "ubuntu", I get the normal bootup messages (again, nothing unusual). Last thing I see is SWAP being enabled, and then it reboots itself.

Once booted, it blackscreens after the grub menu and reboots itself. This continues until powercycled.

However, if I catch it at the first grub menu and tell it to boot in recovery mode, I can get to the recovery menu and then exit it without doing anything, and it continues to boot up just fine. 


I've had this happen on another server which I ended up just reinstalling from scratch - I'd rather not do that with this server (and the next one, which would be even worse). I posted about that one (and this one) on the Upgrades forum but never got any responses. 

Anyone have any ideas?...

---

### Post by oldfred on 2014-07-26
Even though it is a sever do you have a video card?

Recovery mode includes the nomodeset which often is required until you install proprietary drivers.
Your upgrade probably did not reinstall any proprietary drivers.

If you add nomodeset to first grub entry does it then boot ok?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

### Post by jethro1138 on 2014-07-26
> **oldfred said:**
> Even though it is a sever do you have a video card?

Recovery mode includes the nomodeset which often is required until you install proprietary drivers.
Your upgrade probably did not reinstall any proprietary drivers.

If you add nomodeset to first grub entry does it then boot ok?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

Thank you, I will give that a try... however... I think it does do a modeset while booting (the thing where the console font changes, right?) and it doesn't blackscreen - it full-on reboots itself. If it just blackscreened but was still running I wouldn't care. There's only a monitor plugged into that thing when it reboots or I'm doing a big upgrade or something. 

Also, "quiet splash" has long since been removed from any grub configuration in my household. I like seeing all the boot messages. 

Still, it's worth a try!

---

