---
title: "i want to boot an encrypted kernel"
date: 2021-03-18
forum: Security
---

### Post by Skaperen on 2021-03-18
i want to boot a kernel that is stored on disk encrypted.  such a process would need to get a key or pass-phrase to decrypt that kernel.  can GRUB2 do this for me?

---

### Post by CharlesA on 2021-03-18
Do you mean that you want to be prompted for your passphrase before the system completes booting?

You are able to run full-disk encryption via LUKS on Ubuntu, but as far as I am aware, you still need to have /boot on an unencrypted disk (I use a thumb drive).

See here:
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

---

### Post by Skaperen on 2021-03-20
yes.  by whatever mechanism.  i'm exploring kexec as a possibility.

---

### Post by lordgallen on 2021-04-26
> **CharlesA said:**
> 

See here:
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

I did this, by following these instructions, which are the best I have ever seen for an Ubuntu tutorial. The question I have now, is why is this not in the default install, that is, Why is /boot , the kernel, and initram fs not encrypted in the default encryption option during install?

---

### Post by TheFu on 2021-04-26
> **lordgallen said:**
> I did this, by following these instructions, which are the best I have ever seen for an Ubuntu tutorial. The question I have now, is why is this not in the default install, that is, Why is /boot , the kernel, and initram fs not encrypted in the default encryption option during install?

I'd bet it isn't the default due to future upgrade issues and the use isn't enough that Canonical thinks putting a paid developer on to solve those upgrade issues for every flavor and release and for dual boot would make financial sense.  But I really don't know. Those are just guesses.

---

### Post by deadflowr on 2021-04-27
> **lordgallen said:**
> I did this, by following these instructions, which are the best I have ever seen for an Ubuntu tutorial. The question I have now, is why is this not in the default install, that is, Why is /boot , the kernel, and initram fs not encrypted in the default encryption option during install?
Some discussion on it in this bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457")

---

### Post by lordgallen on 2021-04-27
With the above instructions, does grub end up encrypted?

---

### Post by Skaperen on 2021-04-27
> **lordgallen said:**
> With the above instructions, does grub end up encrypted?

No, as far as i can tell.  so that means there are *some* sectors on disk that are not encrypted.  so it would *not* be a full-disk encryption but, instead, would be a logical volume encryption (not sure how this could be expanded very easily while it is in an encrypted state).  in my case, it is the 2nd and/or 3rd disk i want to encrypt.  i prefer not to have LVM.  i just want to allocate all the space and be done with it.  unless LUKS depends on LVM, i see no reason to use LVM.  so true full-disk encryption seems right for me.  that would mean the partition table and/or LVM data would be encrypted.

i'm thinking that the best encryption needs to be in hardware or immutable BIOS.  that could get around a lot of software issues like the evil maid substituting an evil bootloader.  OTOH, substituted hardware is the next issue.  how far do we need to go?  do we need to protect against the evil workers of an evil government's evil agency and their clever children?

my latest thought is to hide the encryption and have it behave as a normal laptop ... at least one with Ubuntu on it.  no pass phrase prompt.

---

### Post by TheFu on 2021-04-27
LVM isn't required for LUKS, but it is so much more convenient if any changes are needed .... plus snapshots are great for getting clean backups.

If you want a tiny install of some Linux on the side of your encrypted Ubuntu ... check out the ChromiumOS versions. They are like chromebooks, have a guest account, so you can show border agents a working system and fit into 16G of storage last time I checked. Like ChromeOS, ChromiumOS is mounted read-only when in use. Updates go to ROOT-B or ROOT-A partitions, depending on which is not currently in use.  At least that's how I think it works.  Plus it is very fast for a quick web browser need.

The solution to the evil maid attack will always be to boot from USB storage that never leaves your person when traveling.

I believe there are hardware encrypted HDDs that are tied to the TPM or TPM2 chip inside your computer. This assumes anyone who cares about this level of security would go to the effort to ensure their hardware has a TPM2 chip. I found a number of blog articles with details, but not any known-reputable site (to me) with a how-to.

---

### Post by lordgallen on 2021-04-28
> **Skaperen said:**
> No, as far as i can tell.  so that means there are *some* sectors on disk that are not encrypted.  so it would *not* be a full-disk encryption but, instead, would be a logical volume encryption (not sure how this could be expanded very easily while it is in an encrypted state).  in my case, it is the 2nd and/or 3rd disk i want to encrypt.  i prefer not to have LVM.  i just want to allocate all the space and be done with it.  unless LUKS depends on LVM, i see no reason to use LVM.  so true full-disk encryption seems right for me.  that would mean the partition table and/or LVM data would be encrypted.

i'm thinking that the best encryption needs to be in hardware or immutable BIOS.  that could get around a lot of software issues like the evil maid substituting an evil bootloader.  OTOH, substituted hardware is the next issue.  how far do we need to go?  do we need to protect against the evil workers of an evil government's evil agency and their clever children?

my latest thought is to hide the encryption and have it behave as a normal laptop ... at least one with Ubuntu on it.  no pass phrase prompt.

This encryption scheme is much better than the default provided by Ubuntu. I try to maintain physical security of my devices. It's the only way to assure an evil made attack does not occur.

---

### Post by lordgallen on 2021-04-28
> **TheFu said:**
> LVM isn't required for LUKS, but it is so much more convenient if any changes are needed .... plus snapshots are great for getting clean backups.

If you want a tiny install of some Linux on the side of your encrypted Ubuntu ... check out the ChromiumOS versions. They are like chromebooks, have a guest account, so you can show border agents a working system and fit into 16G of storage last time I checked. Like ChromeOS, ChromiumOS is mounted read-only when in use. Updates go to ROOT-B or ROOT-A partitions, depending on which is not currently in use.  At least that's how I think it works.  Plus it is very fast for a quick web browser need.

The solution to the evil maid attack will always be to boot from USB storage that never leaves your person when traveling.

I believe there are hardware encrypted HDDs that are tied to the TPM or TPM2 chip inside your computer. This assumes anyone who cares about this level of security would go to the effort to ensure their hardware has a TPM2 chip. I found a number of blog articles with details, but not any known-reputable site (to me) with a how-to.

Can Luks work with a tpm or tpm2 module?

---

### Post by TheFu on 2021-04-28
> **lordgallen said:**
> This encryption scheme is much better than the default provided by Ubuntu. I try to maintain physical security of my devices. It's the only way to assure an evil made attack does not occur.

You take a computer to the shower with you ... when staying at a hotel?  You know - with an evil maid?
When you work in a coffee shop for a few hours, you take the computer with you for refills or a little pee break?  It only takes a few seconds to insert a USB flash drive, have the driver install and run as root, then infect the boot area.

My point is that there are always ways for someone to gain quick access to a computer when the environment isn't completely under your control.
The hotel chain on the door is easily defeated, so security people take extra sensor devices and video recording devices at least record someone entering. There are a number of counter-measures, but the easiest is to always boot from a flash drive that doesn't leave your person when traveling. Always completely shut down the computer if you leave the immediate area so the encryption is truly locked, but take the flash boot device with you.  Shower, kitchen, snacks, touring Paris, Beijing, whatever.

---

### Post by lordgallen on 2021-04-28
> **TheFu said:**
> You take a computer to the shower with you?


When I leave my home it's with me.

---

### Post by lordgallen on 2021-04-29
> **TheFu said:**
> You take a computer to the shower with you ... when staying at a hotel?  You know - with an evil maid?
When you work in a coffee shop for a few hours, you take the computer with you for refills or a little pee break?  It only takes a few seconds to insert a USB flash drive, have the driver install and run as root, then infect the boot area.

My point is that there are always ways for someone to gain quick access to a computer when the environment isn't completely under your control.
The hotel chain on the door is easily defeated, so security people take extra sensor devices and video recording devices at least record someone entering. There are a number of counter-measures, but the easiest is to always boot from a flash drive that doesn't leave your person when traveling. Always completely shut down the computer if you leave the immediate area so the encryption is truly locked, but take the flash boot device with you.  Shower, kitchen, snacks, touring Paris, Beijing, whatever.


/boot is encrypted, Am I still at risk? I also have a user and administrator passwords set on the bios, so it makes it harder to boot from any potential usb malware stick. However, you do make a good point, with the booting from a separate usb stick to make things even more secure.

---

### Post by TheFu on 2021-04-29
> **lordgallen said:**
> /boot is encrypted, Am I still at risk? I also have a user and administrator passwords set on the bios, so it makes it harder to boot from any potential usb malware stick. However, you do make a good point, with the booting from a separate usb stick to make things even more secure.

Humans are bad at passwords. 

We know this. When physical access is possible for more than a few minutes, the ability to crack into the system raises exponentially.  For short periods of time, the risks are fairly low for all of us, everywhere. And there is always the rubber-hose decryption method that can be used in a very effective way by criminals or many govts have legal mandates to unlock encrypted storage on demand.

So, we are left with either a clandestine effort or a criminal or a little brother trying to be funny.  

Depending on the skill of the attacker, we'd want to alter our mitigations.

My big brother inserted a key lock to prevent power from working with his stereo as a teen. He didn't want anyone else using it.  Today, what would be using encryption on a computer to prevent use by a little brother.  Simple, nothing crazy, but sufficiently effective.  If someone really wanted to use the computer, they could insert a *Try Ubuntu* flash drive and boot. Provided the computer was off before that, no harm done, probably. The encrypted storage wouldn't be available, but they could delete the /boot/ partition to be mean.

An attacker interested in more than short-term access to the system, but who wants to capture files and keystokes would probably modify the initrd to embed a keylogger and remote transmission capability. This would happen in the /boot area or in the EFI area.  
[LIST]
[*][https://www.zdnet.com/article/chinese-hacker-group-spotted-using-a-uefi-bootkit-in-the-wild/](https://www.zdnet.com/article/chinese-hacker-group-spotted-using-a-uefi-bootkit-in-the-wild/)
[*][https://www.csoonline.com/article/3599908/trickbot-gets-new-uefi-attack-capability-that-makes-recovery-incredibly-hard.html](https://www.csoonline.com/article/3599908/trickbot-gets-new-uefi-attack-capability-that-makes-recovery-incredibly-hard.html)
[*][https://eclypsium.com/2018/10/01/uefi-attacks-in-the-wild/](https://eclypsium.com/2018/10/01/uefi-attacks-in-the-wild/)
[/LIST]
So, the way to bypass these is not to boot using storage left with the system. That's where moving /boot off to a USB flash drive that never leaves your person comes in.  Some laptops can boot from SDHC or microSD cards too, so now we can have a fingernail sized boot or even full OS for travel with us and use the internal encrypted storage for backups and data.

BIOS passwords have a reset capability. 2 minutes with a screwdriver and that can be disabled. Less on a desktop.

With LUKS encryption, be certain to use a challenge/response 2FA solution.  [https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks](https://www.howtoforge.com/ubuntu-two-factor-authentication-with-yubikey-for-harddisk-encryption-with-luks)  The LUKS device in the link will be different in 21.04 now they don't use MSDOS partitioning. At least I think that's true.

The more I think about this, the more traveling with a persistent Ubuntu created using **mkusb** loaded onto a microSD card with a USB 3.x+ adapter makes sense.  Hummmm.  I have a number of Samsung MicroSD high endurance 32-64G cards and a very fast Kinston USB 3.2 micro-to-USB converter [https://www.amazon.com/dp/B085P5FDXQ/](https://www.amazon.com/dp/B085P5FDXQ/)  These things would effectively make almost any laptop into my workstation when traveling.  Certainly good for a few weeks at a time. I should test this with an encrypted install onto the microSD. Hummmm.  Hope I don't end up with 100% security and 0% usability.  ;)

---

