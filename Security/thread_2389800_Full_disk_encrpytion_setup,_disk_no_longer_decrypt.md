---
title: "Full disk encrpytion setup, disk no longer decrypts"
date: 2018-04-21
forum: Security
---

### Post by logisbroadcast on 2018-04-21
Yesterday I followed [this guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption") to setup full disk encryption on ubuntu 17.10. 

 Everything worked exactly as expected.  I could reboot perform decryption (would take about 15-20sec) and login. 

 Fast forward to today, I boot and I get to the Enter System Passphrase screen, but after typing in the correct passphrase the computer appears to be decrypting indefinitely. 

 If I type in a wrong passphrase, it recognizes and refuses access after about 15 seconds.  If I boot off a live USB I can perform decryption with no trouble through a terminal. 

 I've tried refreshing grub, no effect.  Not sure where to go from here.  Its blank slate, so I can start over, but it would be nice to know what went wrong. 

 Thanks.

---

### Post by Paddy Landau on 2018-04-21
I cannot imagine what is causing your problem, sorry.

Use the Troubleshooting Guide, specifically:

[LIST=1]
[*]Follow the instructions to [Boot goes to initramfs]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Boot_goes_to_initramfs"), steps 1&#8211;6 (don't reboot).
[*]Follow the instructions to [Computer fails to boot after upgrade or new installation]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation"), steps 5&#8211;7.
[/LIST]
I'm hoping that this solves the problem.

**EDIT:** I have heard that this process doesn't work correctly on 17.10. That might be a problem.

---

### Post by logisbroadcast on 2018-04-21
Thank you,

I just tried this and it seems to be hung on decryption again.  Dang.  I reckon 16.04 it is.

---

### Post by Paddy Landau on 2018-04-21
That's sad. I hope that it will work on the next LTS, which is 18.04.

Ubuntu really needs full-disk encryption; the current setup is insufficient for today's security needs.

I am going to continue to scout around for an alternative method, but don't hold your breath — I've been looking for years already.

---

### Post by CharlesA on 2018-04-22
> **logisbroadcast said:**
> Yesterday I followed [this guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption") to setup full disk encryption on ubuntu 17.10. 

 Everything worked exactly as expected.  I could reboot perform decryption (would take about 15-20sec) and login. 

 Fast forward to today, I boot and I get to the Enter System Passphrase screen, but after typing in the correct passphrase the computer appears to be decrypting indefinitely. 

 If I type in a wrong passphrase, it recognizes and refuses access after about 15 seconds.  If I boot off a live USB I can perform decryption with no trouble through a terminal. 

 I've tried refreshing grub, no effect.  Not sure where to go from here.  Its blank slate, so I can start over, but it would be nice to know what went wrong. 

 Thanks.

Are you using the same version of cryptsetup on the live USB as you are on the live machine? Is there any console output when it tries to accept the passphrase?

I've run into issues in the past with full disk encryption ([mostly this one]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1256730")), but once I got those ironed out, it's been running fine.

---

### Post by Paddy Landau on 2018-04-22
> **CharlesA said:**
> … issues in the past with full disk encryption ([mostly this one]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1256730"))
I've marked this bug as affecting me, to try to raise its priority.

Full-disk encryption needs a proper supported resolution.

---

### Post by hleroy on 2018-04-28
I have just tried the ManualFullSystemEncryption procedure with Ubuntu 18.04. It fails to boot. I don't even get asked for the passphrase. I get a message "no such device : " then follows the UUID of the /boot partition.

---

### Post by Paddy Landau on 2018-05-24
I've finally had time to look in depth at this installation with 18.04.

It installed for me without any problem.

There are two caveats that you need to remember, although I don't know if they applied to you:
[LIST=1]
[*]When you run any updates on your system, if the updates change the kernel or Grub, you must run the Grub refresh script as [described in the caveats]("https://help.ubuntu.com/community/ManualFullSystemEncryption/KnownBugs").
[*]If you forget to do this, you'll have to go through the Troubleshooting to correct it.
[/LIST]
There was also a bug in the refresh script. Please refer to the notes under "May 2018" in the [revised front page]("https://help.ubuntu.com/community/ManualFullSystemEncryption") for details. I'm sorry for any inconvenience if that's what affected you.

Finally, this hasn't been tested on all hardware. Apparently, some hardware does not quite correctly adhere to the EFI standards, and this could cause a problem.

If you are still interested in this full-system encryption, I'd love to hear whether or not this fixes your problem.

---

### Post by lordgallen on 2018-05-26
I don't understand what you mean?? I set up encryption during the installation of Ubuntu, isn't that Full Disk Encrypton, or is it not considered full disk encryption?? I have to enter a password before the system will boot. 

Thanks.

---

### Post by Paddy Landau on 2018-05-27
> **lordgallen said:**
> I set up encryption during the installation of Ubuntu, isn't that Full Disk Encrypton…
The built-in full-disk encryption:
[LIST=1]
[*]Doesn't encrypt [FONT=lucida console]/boot[/FONT].
[*]Erases the entire disk, so that if you already have another system (e.g. Windows), it is deleted.
[/LIST]
On the plus side, Canonical fully supports that method. Also, unless you have serious issues about confidentiality — you work with top-secret data, you are a dissident in in a dictatorship, you deal with massive databases with important client data, that type of thing — the first point shouldn't worry you.

---

### Post by lordgallen on 2018-05-27
> **Paddy Landau said:**
> The built-in full-disk encryption: 
[LIST=1] 
[*]Doesn't encrypt [FONT=lucida console]/boot[/FONT]. 
[*]Erases the entire disk, so that if you already have another system (e.g. Windows), it is deleted. 
[/LIST]
 On the plus side, Canonical fully supports that method. Also, unless you have serious issues about confidentiality — you work with top-secret data, you are a dissident in in a dictatorship, you deal with massive databases with important client data, that type of thing — the first point shouldn't worry you.  Well, I don't do any of those things, but I would like my data as secure as possible. i will be researching that, thank-you.

---

### Post by Paddy Landau on 2018-05-28
> **lordgallen said:**
> … i will be researching that, thank-you.
Bear in mind that the process is for the more experienced person. If you're a newcomer to Linux, you might find it somewhat tricky.

---

