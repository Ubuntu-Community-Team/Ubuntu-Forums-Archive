---
title: "Encrypting /boot"
date: 2010-12-03
forum: Security
---

### Post by dev.null on 2010-12-03
Your help needed ;-D

I work in a secure environment with a bunch of windows-lovers. (sigh)

I'm one of the few "linux-only" guys here. One cool thing - my manager doesn't really care what I use, as long as (a) I get the job done and (b) I don't break any company policies.

For the past several years I've typically always encrypted my /home partition using dm_crypt and felt that was "good enough".

Here they use Check Point FDE (Full Disk Encryption), which is windows-based, to encrypt their disks. In brief, FDE boots from the MBR, loads itself in a PBR (partition boot record) and prompts for password. According to their documentation, every partition is encrypted. I've checked the machines (booted w/ ubuntu on usb) and all of that looks essentially true.

I'm getting penalized by guys locally because the /boot partition has to be (or does it?) encrypted.

I may be forced to not be able to use linux as my primary OS.

So, I'm coming to you guys for help.

Is there a way to duplicate what FDE does? I'm thinking if grub could be "locked" where it prompts for a password which is used to decrypt the /boot partition I'd be golden.

Another thought is something done in the initrd - basically where you're prompted for a password before any partition is actually accessed, and the password is used to decrypt those passwords. I think the initrd is in the boot partition, so I don't think that one is an option, just an idea I'm throwing out for thought.

I've looked at grub2, but didn't see anything there jumping up and down as a solution...

Any ideas?

Thanks!

---

### Post by mathgeek2000 on 2010-12-03
The TSA Responder in me -- (keen eye on Security Theatre) reminds me of the 'Evil Maid' attack, which could defeat their Full Disk Encryption, if they haven't locked out other Boot Methods.

But: If you BIOS Lock out alternate boot methods, of course setting a BIOS password. & set Grub to boot from HDD only, with a Password -- It's similar to the PBA of products like Safe Guard Easy.

I know by default /boot is the one unencrypted partition when you set up Ubuntu w/ Luks FDE.
You could move /boot to a USB drive, still booting from the HDD - Grub would be on the HDD, and look to the USB for kernel, and initrd. -- Format a partition on the USB w/ ext2 or ext3.

Another option for Dual Factor Authentication is PAM_USB, or Pam_Bluetooth

---

### Post by mathgeek2000 on 2010-12-03
Heads up: take a look at 'http://lfde.org' for another 'Free `Dual Factor` Solution'.
   - I haven't tried this, as I don't use full disk encryption, instead I use eCrypts.
   - Unfortunately, the forum, wiki, and source code appear down at the moment.
But I see a few issues:

    -- Lose the USB Key -> You're scr**ed.
    -- Someone could copy the USB key, and get the random unlock passphrase.
    
Again - if your boss is open to reason -- remember these tech details, but - don't go over his head, in talking to him:
   -> The Encrypted Windows MBR & Initial Program Loader is not encrypted, not can it be.
   -> The /boot partition on Linux does not hold any data, critical apps, cookies, browser history etc.
          -> /boot can be minimal in size, well under today's flash drive capacity.

---

### Post by dev.null on 2010-12-03
> **mathgeek2000 said:**
> Heads up: take a look at 'http://lfde.org' for another 'Free `Dual Factor` Solution'.
   - I haven't tried this, as I don't use full disk encryption, instead I use eCrypts.
   - Unfortunately, the forum, wiki, and source code appear down at the moment.
But I see a few issues:

    -- Lose the USB Key -> You're scr**ed.
    -- Someone could copy the USB key, and get the random unlock passphrase.


Yeah, I never was excited about needing a usb to boot because it's the only copy of your security key. Leave that at home, and even though you left your machine up all night, one power outage and you're in for a headache. And then there's always the loss or the damage of that key (as you said).

> **mathgeek2000 said:**
> Again - if your boss is open to reason -- remember these tech details, but - don't go over his head, in talking to him:
   -> The Encrypted Windows MBR & Initial Program Loader is not encrypted, not can it be.

According to Check Point, their program loader is encrypted. I'm guessing what they mean is if any hacker wanted to, he could just de-asm and figure out the decryption routine and easily modify the loader to look "normal" but have a keylogger.

> **mathgeek2000 said:**
>    -> The /boot partition on Linux does not hold any data, critical apps, cookies, browser history etc.
          -> /boot can be minimal in size, well under today's flash drive capacity.

I agree w/ your assessment, the problem is someone slipping in a kernel w/ a keylogger. I still see that same risk with the Check Point, but at least on their side they can say "all" partitions are encrypted (and that's all my boss will hear).

---

### Post by dev.null on 2010-12-03
> **mathgeek2000 said:**
> The TSA Responder in me -- (keen eye on Security Theatre) reminds me of the 'Evil Maid' attack, which could defeat their Full Disk Encryption, if they haven't locked out other Boot Methods.

But: If you BIOS Lock out alternate boot methods, of course setting a BIOS password. & set Grub to boot from HDD only, with a Password -- It's similar to the PBA of products like Safe Guard Easy.


What happens when the evil maid decides to stick your drive in her "cleaning cart" PC and installs a key-logger version of grub?

I don't really think a lot of bios passwords etc. It's to easy to just remove the HD and get right around that...

> **mathgeek2000 said:**
> 
I know by default /boot is the one unencrypted partition when you set up Ubuntu w/ Luks FDE.
You could move /boot to a USB drive, still booting from the HDD - Grub would be on the HDD, and look to the USB for kernel, and initrd. -- Format a partition on the USB w/ ext2 or ext3.


I've thought about that, the thing that scares me is losing the usb or having someone else pick it up and "modify" it for me.

> **mathgeek2000 said:**
> 
Another option for Dual Factor Authentication is PAM_USB, or Pam_Bluetooth

I already use pam_usb, but that of course is long after the OS is loaded.

---

### Post by SeijiSensei on 2010-12-03
> **dev.null said:**
> I agree w/ your assessment, the problem is someone slipping in a kernel w/ a keylogger. I still see that same risk with the Check Point, but at least on their side they can say "all" partitions are encrypted (and that's all my boss will hear).

Give /boot and directories like /boot/grub 0500 permissions, and its files 0400 permissions.  Then you'd need to be root already to make any changes to the kernel.  If the overall system is that insecure, what makes anyone think they couldn't end-run encryption of the boot partition if they already have root?

You won't be able to upgrade kernels without first changing the permissions, so automated updates are out.  When a new kernel is released, you'll need to reset /boot to read/write, run the update, then switch the permissions back.

---

### Post by frostschutz on 2010-12-03
I have /boot on USB, while the HDD is fully encrypted, and I think it's a good solution.

Nobody can modify the decryption routine or kernel on the USB key, provided that you carry it with you whereever you go (like you do with your wallet and old fashioned keys).

Nobody can boot your machine and/or get at your data without it, provided the system itself is secure and properly locked down when you leave it.

So the simple approach (modify the unencrypted boot partition to place a software keylogger) can't be done. The attacker would have to install a hardware keylogger (requires hands on access and $5) and even then they still need a copy of your USB stick (because what you're typing in is not the real password, but just the decryption passphrase of a random generated key stored on the USB stick).

So when your USB stick breaks, or gets stolen, you're screwed?

Not so, because with LUKS you can have up to 8 keys/passphrases, and you can revoke any of them any time (unless they thought of copying your LUKS master block along as well). So you can have a second passphrase which you only use in case your USB stick breaks or is lost; revoke the one the USB stick used, and make a new USB stick with a new random key and passphrase. If the USB stick gets stolen and if you're paranoid, you can redo the entire HDD encryption with a new LUKS master key.

As far as security goes it's hard to do better.

The Windows solutions have exactly the same problem, somewhere there must be a non encrypted program that does the authentication and encryption - you modify that and end of story. And I don't trust them to be secure - they tend to rely on security through obscurity far too much.

---

### Post by bodhi.zazen on 2010-12-03
> **frostschutz said:**
> I have /boot on USB, while the HDD is fully encrypted, and I think it's a good solution.

This ^^

Keep in mind, with physical access encryption is easily defeated (ie "evil maid") via a number of techniques.

---

### Post by dev.null on 2010-12-03
> **SeijiSensei said:**
> Give /boot and directories like /boot/grub 0500 permissions, and its files 0400 permissions.  Then you'd need to be root already to make any changes to the kernel.  If the overall system is that insecure, what makes anyone think they couldn't end-run encryption of the boot partition if they already have root?


The idea isn't that someone authorized to access the box will be trying to defeat the security. It's that someone who doesn't have authorization will try to boot the system and access the hard drives.

So I shut the machine down when I go home, evil-maid shows up and boots the box up off of her thumb drive, or takes the drive out and mounts it on her own PC. If the partitions aren't encrypted she'll have full access.

> **SeijiSensei said:**
> You won't be able to upgrade kernels without first changing the permissions, so automated updates are out.  When a new kernel is released, you'll need to reset /boot to read/write, run the update, then switch the permissions back.

Not so. Booting w/ the usb, a perpetrator is root on the box and can easily modify the kernels on the /boot partition.

---

### Post by dev.null on 2010-12-03
> **frostschutz said:**
> I have /boot on USB, while the HDD is fully encrypted, and I think it's a good solution.

Yeah, I think that's the route I'm going to propose.

Do you have a howto you can refer me to?

Did you go with dm-crypt or LUKS?

<insert other standard questions here>

Thanks frostschutz!

---

### Post by SeijiSensei on 2010-12-04
> **dev.null said:**
> The idea isn't that someone authorized to access the box will be trying to defeat the security. It's that someone who doesn't have authorization will try to boot the system and access the hard drives.

So I shut the machine down when I go home, evil-maid shows up and boots the box up off of her thumb drive, or takes the drive out and mounts it on her own PC. If the partitions aren't encrypted she'll have full access.

If your security needs are this high, maybe you should epoxy the USB ports and remove any optical drives.  Put the server away in a locked room where evil-maid can't enter.  Booting from a USB makes sense, I suppose, as long as you have the key available.  Still, if your security concerns are this substantial, I'd take a more aggressive approach to the machine's physical security.  Evil maids or any other unauthorized person shouldn't be able to get near the machine, much less disassemble it.

---

### Post by dev.null on 2010-12-04
> **SeijiSensei said:**
> If your security needs are this high, maybe you should epoxy the USB ports and remove any optical drives.  Put the server away in a locked room where evil-maid can't enter.  Booting from a USB makes sense, I suppose, as long as you have the key available.  Still, if your security concerns are this substantial, I'd take a more aggressive approach to the machine's physical security.  Evil maids or any other unauthorized person shouldn't be able to get near the machine, much less disassemble it.

I still don't think you get it. It is 100% possible to encrypt any disk partition where no one can decrypt it even if they have it in their possession.

I'm not worried about someone stealing the disk. We have adequate physical security. But we are required by law to take additional measures of securing the hard drive partitions so *if* they were taken or copied that the information on them couldn't be retrieved.

The subject of this thread isn't physical security, it's cryptographic security.

I'd love it if grub or initrd were loaded from a pbr and it requests the pwd required to decrypt all (or at least the boot) partition(s).

---

### Post by bastafidli on 2011-01-10
Start with this post
[http://xercestech.com/full-system-encryption-for-linux.geek](http://xercestech.com/full-system-encryption-for-linux.geek)
and track down the sources for the path which modifies grub2 to add luks support. Then you can have your disk fully encrypted (inlcuding /boot) and the only think you will need to have on your usb is the patched grub.

---

