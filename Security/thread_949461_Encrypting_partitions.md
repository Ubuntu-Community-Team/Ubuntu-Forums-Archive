---
title: "Encrypting partitions"
date: 2008-10-16
forum: Security
---

### Post by rosv on 2008-10-16
Hi,
I need some advice on encrypting partitons.

I'd like to do a fresh install of ubuntu where I create an encrypted partition that I can use for my home directory.

Is this possible during setup or do I need to configure truecrypt or something similar after the installation?

I would be nice if I could mount the encrypted partition in fstab and then efter a password during boot.

---

### Post by offthegrid2 on 2008-10-16
I just used this tutorial yesterday with a fresh install of 8.10 and it works great. Even encrypts the swap. I did refuse set up Private folder when asked due to entire disk being encrypted. I use one password for boot and one for home plus user password making three needed to even log in. Yes I'm paranoid, this was on my e-machines laptop that travels.

[URL="http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04"]
Clean install tutorial[/URL]

---

### Post by hyper_ch on 2008-10-16
offthegrid: You should have a look at my other tutorial (besides the one you already followed) to auto-unlock the other partitions upon booting, so that you have to enter only one password:  [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

And depending on what you want to do you might also think this is handy (for a server or so): [http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu)

Besides, if you have a fully encrypted system, why don't you auto-login your user automatically? I mean without knowing the encryption password they can't do anythign.

And if you travel a lot you might also want to set yourself to lock the session when you the notebook has been inactive for xx minutes (use the screen saver and the session locking there).

---

### Post by rosv on 2008-10-16
Thanx! Exactly what I was looking for.

---

### Post by offthegrid2 on 2008-10-16
Thanks hyper...I do not mind the passwords but I agree and am going to auto login user. I have 2 separate HD's for my laptop and now I will put them to better use. I'm going to keep one unencrypted to use going through security and the other I encrypted yesterday will be placed in my luggage and swapped upon arrival.

---

### Post by rosv on 2008-10-20
Does one need the alternate CD to access the non GUI installer? I can't seem to find the correct options using the standard GUI installer.

---

### Post by sethvath on 2008-10-20
If you want to encrypt your whole system, only the alternate CD offers that option. Live cd does not have lvm support.

---

### Post by Luger01 on 2008-10-21
I used a VM to test the dm-crypt/LUKS encryption as described on the HowToForge site.  Worked great, until yesterday when I updated 58 packages including the kernel.  Now, when booting into the new kernel, there is no prompt for the encryption password, and the system won't boot.  I can still boot into the old kernel that installed when I loaded (and encrypted) the system using Ubuntu 8.04.

Has anyone else seen this happen?  When I was running Redhat AW4 and had Pointsec doing the encryption, I found that an update to initrd rendered my laptop into a boat anchor.  A total rebuild was teh only cure.  I was hoping that Ubuntu would allow me to have an encrypted laptop w/o the risk of updates hosing the system.  Maybe I just want too much.... <LOL>

Thanks for any responses in advance.

---

### Post by hyper_ch on 2008-10-21
the encryption hooks are probably not set properly in the initramfs...

---

### Post by Luger01 on 2008-10-21
So, is there any way to add these in to the new initrd file?  Or to "port" the hooks from the old file to the new?

Thanks.

---

### Post by hyper_ch on 2008-10-22
I made a howto on remote booting up an encrypted computer (with dropbear and some script). In there is info regarding the initramfs, how you (re)create it, the hook scripts... have a look there and then try to figure out what's missing on your side so that the initramfs got wrongly configured.

---

### Post by pirattrev on 2008-10-22
is lvm with the alternate worth it? wouldn't that slow down disk access and other i/o stuffs if it has to decrypt everything on the fly? I'm not really knowledgeable about fs encryption but i was interested in giving it a go, mostly just for the fun of it.

---

