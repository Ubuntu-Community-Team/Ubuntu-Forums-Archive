---
title: "Luks pwned, is there a fix  in sight?"
date: 2014-01-22
forum: Security
---

### Post by frostyhonky on 2014-01-22
I've been using Luks full disc encryption for a while, thinking it granted me some modicum of saftey. Apparently it's completely pointless, other than to the most garden variety laptop snooper.

[https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/](https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/)

Is there any actual fix in sight for future OS versions? I mean, truecrypt is able to boot from an encrypted partition, why are us "free as in freedom" users open to these attacks?

Just curious.

---

### Post by Hungry Man on 2014-01-22
There are a few potential methods for protection here:1) Hardware encrypted hard drives. These, when properly implemented, will only store sensitive information in the TPM.2) Moving your bootloader to a USB drive.3) Write protecting your drive.Keep in mind that this attack requires:1) Physical access2) For you to then access the drive and decrypt it3) Repeated physical access after (2)So, if you believe your laptop has been accessed by someone you do not trust, you should not trust that laptop, even if you keep your bootloader on a USB drive, or any other defense.

---

### Post by frostyhonky on 2014-01-22
I'm aware of the attack vector, but I'm just wondering if there is a fix in sight. If memory serves ,isn't the Truecrypt Bootloader MB partition encrypted? And if it's open source, why can't devs borrow the code, and use it to do something similar for Ubuntu?

I dislike the idea of having to keep a USB around just to boot my computer. I mean, if I lose the thumbdrive, or accidentally leave it in my pocket in the wash or something, then I have a brick until I re-install an OS.

I'm not really TOO worried about it, I don't have nuclear bomb plans or anything, but it is worrisome, especially in the current security climate of the United States, where it seems we are all under suspicion. 

I didn't even think they made hardware encrypted laptop drives. I guess I'll look into that option also. It is time for an upgrade soon. Only issue I have with the hardware encryption, is it's proprietary (as far as I'm aware), and again, given how the NSA is attempting to backdoor everything in sight, I'd prefer to see an open source solution.

---

### Post by Dave_L on 2014-01-22
> **Hungry Man said:**
> Keep in mind that this attack requires:1) Physical access2) For you to then access the drive and decrypt it3) Repeated physical access after (2)

Physical access is helpful, but is it necessary?

If someone tricked you into installing malicious software via the internet, couldn't it accomplish the same thing?

---

### Post by Habitual on 2014-01-22
Ouch! I like his writing style of the exploit too, no politics, no fanboy'isms, just a recipe.

---

### Post by Hungry Man on 2014-01-23
> **frostyhonky said:**
> I'm aware of the attack vector, but I'm just wondering if there is a fix in sight. If memory serves ,isn't the Truecrypt Bootloader MB partition encrypted? And if it's open source, why can't devs borrow the code, and use it to do something similar for Ubuntu?I dislike the idea of having to keep a USB around just to boot my computer. I mean, if I lose the thumbdrive, or accidentally leave it in my pocket in the wash or something, then I have a brick until I re-install an OS.I'm not really TOO worried about it, I don't have nuclear bomb plans or anything, but it is worrisome, especially in the current security climate of the United States, where it seems we are all under suspicion. I didn't even think they made hardware encrypted laptop drives. I guess I'll look into that option also. It is time for an upgrade soon. Only issue I have with the hardware encryption, is it's proprietary (as far as I'm aware), and again, given how the NSA is attempting to backdoor everything in sight, I'd prefer to see an open source solution.T




here is no 'patch' here. The solutions I listed are, for the most part, the only ones possible. If you encrypted the entire drive, how would you decrypt it? Something needs to remain decrypted in order to decrypt the rest of the system. Therefor it will always be vulnerable to this attack, unless one takes the precautions I listed.


Samsung 840 Pro is an encrypted SSD. It is just one layer, you can still use software encryption on top of it. The important part is that an attacker would not have access to the decrypted areas.


Proper SecureBoot/TrustedBoot would also likely prevent this attack as the bootloader would be verified by a TPM.


Dave_L"If someone tricked you into installing malicious software via the internet, couldn't it accomplish the same thing?"Yes, if the machine is *already booted* there are numerous other attacks that are possible. The attack in the first post is against a coldbooted PC.

---

