---
title: "Password Protected BIOS"
date: 2012-01-27
forum: Security
---

### Post by 0011235813 on 2012-01-27
I've heard that an intruder who gains physical access might be able to log into my Ubuntu without root password. So I decided to password protect the BIOS to prevent booting from CD/USB etc. And to require password at startup.

I've also edited a file called "etc/inittab" (see link: [http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html](http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html)) to prevent root avoidance in recovery mode. Is there anything else I need to do?

---

### Post by CharlesA on 2012-01-27
Physical access is root access, so you should secure physical access to the machine if possible.

Keep in mind that Ubuntu does not use the root account, so you can boot into recovery mode without it asking for a password.

---

### Post by 0011235813 on 2012-01-27
> **CharlesA said:**
> Physical access is root access, so you should secure physical access to the machine if possible.

Keep in mind that Ubuntu does not use the root account, so you can boot into recovery mode without it asking for a password.

Fortunately, I don't allow anyone physical access to the computer, the measure was taken in hypothetically in case the laptop got stolen, however, I assume this will be enough protection to keep the average thief/hacker out?

I booted in recovery mode once, it just started a command-line and then stopped doing anything (although it did fix my problem). But would a person booting into recovery mode not have root privileges then?

---

### Post by CharlesA on 2012-01-27
They would be dropped to a root prompt, if they entered recovery mode and told it to give them a shell.

---

### Post by drs305 on 2012-01-27
You can password-protect the Grub 2 menu as well if you wish (normal and/or recovery modes).

Here is a thread describing the procedure.
[http://ubuntuforums.org/showthread.php?t=1369019]("http://ubuntuforums.org/showthread.php?t=1369019")

I imagine by now the official GNU Grub manual has information on passwords as well.

---

### Post by needhelppeeps on 2012-01-28
My understanding of a bios password is that one can simply pull the battery on the machine and reset this or sometimes a jumper on the motherboard, so I don't think that's going to accomplish much of anything. Also they could simply yank your hard disk and plug it in another machine.

If your laptop gets stolen, I would imagine your biggest concern would be purchasing a new laptop and transferring your information back onto it, so I would focus instead on my backup solution and encrypt the hard disk. You could also add some kind of biometric (fingerprint would be easiest, I believe) or card based access in addition to your password to make it harder to sign in to the laptop if you have sensitive information on it,

---

### Post by matt_symes on 2012-01-28
Hi

Ubuntu does not use /etc/inittab. That will have no effect under Ubuntu.

Kind regards

---

### Post by OpSecShellshock on 2012-01-28
A BIOS password on a home system isn't going to get you anything but an extra barrier to legitimate usage, really. Even on an enterprise system the best it probably gets anyone is the satisfaction of an arbitrary requirement. For mitigation of the risk of data exposure for most people, an encrypted home will do the job.

Most opportunistic hardware thieves are going to want to dispose of a hot system as soon as possible, so if they are going to do anything at all it's going to be deleting as much as they can in an effort to avoid exposing that they aren't the original owner in the view of whomever they sell it to. A lot of them frankly won't even do that much.

---

### Post by 0011235813 on 2012-01-28
> My understanding of a bios password is that one can simply pull the battery on the machine and reset this or sometimes a jumper on the motherboard, so I don't think that's going to accomplish much of anything. Also they could simply yank your hard disk and plug it in another machine.
I don't think pulling the battery will reset it. But the BIOS password was just an extra measure of protection to buy time, and anyway most thieves would be deterred by one enough to leave it.

> If your laptop gets stolen, I would imagine your biggest concern would be purchasing a new laptop and transferring your information back onto it, so I would focus instead on my backup solution and encrypt the hard disk. You could also add some kind of biometric (fingerprint would be easiest, I believe) or card based access in addition to your password to make it harder to sign in to the laptop if you have sensitive information on it,
I've backed up most of the stuff on it one way or another anyway, and I have made encrypted directories with EncFS. I don't know about fingerprint readers, I hear S76 has them, are there any you can buy for Linux?

> **matt_symes said:**
> Hi

Ubuntu does not use /etc/inittab. That will have no effect under Ubuntu.

Kind regards
OK. But if the file doesn't exist, then I don't need to do anything right? 

> **OpSecShellshock said:**
> A BIOS password on a home system isn't going to get you anything but an extra barrier to legitimate usage, really. Even on an enterprise system the best it probably gets anyone is the satisfaction of an arbitrary requirement. For mitigation of the risk of data exposure for most people, an encrypted home will do the job.

Most opportunistic hardware thieves are going to want to dispose of a hot system as soon as possible, so if they are going to do anything at all it's going to be deleting as much as they can in an effort to avoid exposing that they aren't the original owner in the view of whomever they sell it to. A lot of them frankly won't even do that much.

---

### Post by stefangr1 on 2012-01-28
A bios password can be avoided by simply resetting the BIOS (and this can indeed be done by taking out the battery). Furthermore, when the hard disk is removed and put in a different system, all data will still be accessible.

As noted earlier, your best option is to either encrypt the entire disk, or your home directory. Encryption is (practically) impossible to avoid.

---

### Post by 0011235813 on 2012-01-28
> **stefangr1 said:**
> A bios password can be avoided by simply resetting the BIOS (and this can indeed be done by taking out the battery). Furthermore, when the hard disk is removed and put in a different system, all data will still be accessible.

As noted earlier, your best option is to either encrypt the entire disk, or your home directory. Encryption is (practically) impossible to avoid.

Yeah, but do they know that? Most thieves don't actually know that much about PC's.

I already have encrypted sensitive information.

---

### Post by dirtrider1 on 2012-01-29
I rely on full disk encryption myself on my mobile computers that have sensitive info. But I know some newer computers use a BIOS HDD password that is stored on disk or other security features like TPM that will protect the drive from being removed and then read on a different device.

---

