---
title: "dm-crypt / LUKS on (X)ubuntu Feisty"
date: 2007-04-07
forum: Server Platforms
---

### Post by hyper_ch on 2007-04-07
Hiho

I came accross a little guide on how to encrypt a whole disk drive with a steganographic system (dm-crypt / LUKS) and I thought I could try it as *buntu and debian are so close to each other...

The URL is [http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)

Well, I started with it... skipped Step 2 (as I have no clue so far on how to do that) and now I fail at Step 6. I get following error notice:
> 
hyper@xubi:/dev$ sudo cryptsetup --verbose --verify-passphrase luksFormat /dev/hda1

WARNING!
========
This will overwrite data on /dev/hda1 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/hda1 contains at least 133 sectors.
Failed to write to key storage.
Command failed.
hyper@xubi:/dev$ 


So I guess that the (X)ubuntu Feisty 2.6.20-14-generic kernel doesn't have one of the options enabled that is being talked about in Step 2 of the howto.

So my questions are:

(1) Am I right with my assumption from that error notice?

and if so (2) how to I enable those options?

---

### Post by jfsylvain on 2007-04-07
I had the same problem in Edgy.

Try loading the encryption modules manually before running any cryptsetup commands:

sudo modprobe aes
sudo modprobe dm_mod
sudo modprobe dm_crypt

---

### Post by hyper_ch on 2007-04-08
Hiya

I meanwhile fixed it :) I'll write a little howto later :) thx for the feedback.

---

### Post by michux on 2007-05-25
There is a howto already: [Encrypted home partition in Linux with DM_Crypt](http://polishlinux.org/howtos/encrypted-home-partition-in-linux/)

---

### Post by michux on 2007-05-26
And here is another tutorial here: [TrueCrypt Tutorial: Truly Portable Data Encryption](http://polishlinux.org/howtos/truecrypt-howto/) -- it is a continuation of the tutorial for DM_Crypt explaining the steps to achieve home drive encryption with full automacy, but this time with TrueCrypt.

---

### Post by Mountaingod on 2007-07-11
Sorry to dig up an old thread, but I want to encrypt my /home partition using Truecrypt.

I'm confused by the auto-mount bit. In order to automatically mount after a reboot, you say I need to alter /home/[user]/.profile - but if it's the /home/ directory that I've encrypted using truecrypt, how would my system access such a file to prompt mounting said directory?

Those were two great tutorials you wrote, but I came away thinking I'd need to encrypt my /home/ partition using dm-crypt because truecrypt couldn't auto-mount a /home/ directory. The previous post suggests I've misunderstood.

So how would I go about getting an automounted encrypted /home/ partition (specifically) using truecrypt?

Thanks again.

---

### Post by hyper_ch on 2007-07-12
for using truecrypt use the thread belonging to truecrypt... this is about luks and dm_crypt here

---

### Post by Mountaingod on 2007-07-12
Well there isn't one exactly, just lots that touch on it. I was replying specifically to michux and his tutorials, hence why I posted here. I'll comment on his tutorials instead...

---

