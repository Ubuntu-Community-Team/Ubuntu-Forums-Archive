---
title: "Initial bootup encryption"
date: 2015-05-27
forum: Security
---

### Post by PsychedelicWonders on 2015-05-27
So I was setting up a new Ubuntu 14.04 install last night and it promped me to setup encryption with a password, which I did.

So now upon startup this password is required to unencrypt something in order to get access to the OS.

This install was on a Samsung SSD, which has it's own form of encryption, but unless you set a bios ATA password, the encryption key is accessible and therefore information on the drive is accessible, even though it's encrypted.

How does this Ubuntu encryption compare to the hardware encryption of the SSD?

Is this Ubuntu's option of adding the ATA password so that this is a hardware encryption, or is this just a software encryption aspect of Ubuntu?

If I I am able to set the ATA password in bios to encrypt the key for the SSD, would this be a better/more secure encryption process over the one that Ubuntu employs?

---

### Post by TheFu on 2015-05-27
HW encryption is probably better, except against "state actors" who may have keys to access it.

dm-crypt with "whole drive encryption" as setup by almost all Linux installations, requires the /boot partition to be unencrypted. It is SW encryption. That means an "**evil maid**" attack is most likely. There are techniques to mitigate that attack.  Others have asked similar questions here and links for some reading were provided.

If you are just trying to keep your boss, little brother, or mom off the system, either is fine.

I'd use the SSD password method, but don't have that option here.  My opinion is that all portable storage devices require as much encryption, as early as possible, as I can put on them. The less OS there is to hack encryption, but better. Disk firmware would be the best option.

I've had a smartphone that wasn't encrypted stolen in a foreign country. As soon as I realized it was gone, I spent the next 6 hrs of our vacation changing login credentials to prevent even more identity stealing actions while sitting in a police station to get a report for insurance.  Both my current Android devices use boot-level encryption with a 20+ character passphrase and my laptop uses 2FA (a cheap yubikey+short pin) to unlock the disk access at boot time.

Which is more secure depends on the attackers - mostly. Do NOT look for FIPS Stds in marketing - that is usually a shortcut to poor security.

---

