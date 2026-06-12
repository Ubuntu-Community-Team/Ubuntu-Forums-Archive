---
title: "encrypted root with keyfile on disk"
date: 2007-12-27
forum: Server Platforms
---

### Post by davidcopper on 2007-12-27
Hi.

I want to encrypt root filesystem by using cryptsetup with luks.  Is there a way to put a key file on disk and load it when the system boots up?

I cannot allow manual input of password, as the system contains sensitive information and will be used by third parties. But the problem is if I put the keyfile on disk, how can I mount it before root filesystem is mounted? 

Thank you for any suggestions you may give.

Dave

---

### Post by jtc on 2007-12-28
Well, normally you do leave /boot unencrypted. No matter what you do with the key/passphrase, you still need some software to actually initialize the encrypted. I guess it would be possible to somehow modify your initrd to also contain the actual key.

What I don't understand is what you expect to gain of such a setup.

---

### Post by davidcopper on 2007-12-30
I have worked out how to encrypt root filesystem without inputing passowrd manually when booting up. The size of pdf is larger than defined by this forum. So I put it in a zip file. If you are interested, find in it attachment.

---

### Post by g2g591 on 2007-12-30
nevermind (firefox 3 nightly downloaded the page to download the zip file instead of the actual zip)

---

### Post by bernied on 2007-12-30
What you describe is how I have my laptop set up. But you can't put the key on the disk that you are encrypting, that would be like putting the key inside a locked house, when you are on the outside wanting to get in.

Instead, you can put the key on another device, in my case a USB stick. So the stick acts as a physical key, and the machine will not start without it.

The USB stick contains the contents of /boot, so the grub bootloader, the kernel and the intrd file. It is the initrd filesystem that contains the key to the root filesystem. I can't remember where I found the instructions, but I had to hack the script that decrypts the root directory, because it is set up to request the key from the user at boot time. I changed it so that it just presented the hardcoded key to cryptsetup. This is safe enough for me as the key exists in unencrypted form only on the usb stick.

Is this what you want?

---

### Post by bernied on 2007-12-30
Sorry, I only just read the pdf. This seems simpler than what I went through, at first glance.

But I don't understand why you'd store the key, unencrypted, on the same physical device as the encrypted root partition. That seems like putting the key to your locked house on a hook by the front door.

---

### Post by davidcopper on 2007-12-31
Umm, yes, are you right. In theory, I should put the key in external device to make it safer. I just provide this as a basic guide, and base on this, people can make changes to that suit them. 

I have a question. The partition /media/sda1 is not encrypted. What if I set the permission of the folder sda1 to 500? In that case only root can read and execute it, would it be safe to protect the key?

Thanks for your ideas.

---

### Post by davidcopper on 2007-12-31
It should be "you are right" at the beginning in my reply above.  I am not questioning your correctness. :P   There was network problems when I submitted my reply, and I didn't notice I changed order of texts.

---

### Post by bernied on 2007-12-31
> **davidcopper said:**
> I have a question. The partition /media/sda1 is not encrypted. What if I set the permission of the folder sda1 to 500? In that case only root can read and execute it, would it be safe to protect the key?
Anyone who has physical access to the machine can read the file, using an alternative operating system, such as a live-cd. Software permissions cannot protect you from that. Even if you have no cd drive, or if you have password protected the bios, the disk can be removed and connected to another machine.

I don't think there is a software solution to this, because the key needs to be available to cryptsetup at boot, so it can't be encrypted. And if it's not encrypted, and someone has physical access, then they can read it.

I think there always has to be some physical element to securing data, either a password/key that you type in at boot, or a locked cabinet or room, or a physical key (either an actual key, or a separate device containing a software key, like I have).

---

