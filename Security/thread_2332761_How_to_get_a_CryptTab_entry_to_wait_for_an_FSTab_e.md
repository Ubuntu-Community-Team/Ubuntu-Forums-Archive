---
title: "How to get a CryptTab entry to wait for an FSTab entry?"
date: 2016-08-03
forum: Security
---

### Post by mikey93898 on 2016-08-03
Hello all,

Here's my problem in a nutshell: CryptTab goes first, FSTab goes second. If I mount a file system normally, and then tell CryptTab to open a container sitting on one of the FSTab partitions, my system goes into emergency/fail mode. How do I tell CryptTab to hang around and continue to try mounting a certain entry until FSTab finishes mounting it?

My reasoning is as follows - and please feel free to tell me a better way to do this. Basically I have a small SSD, and I'm hoping to speed up my system by mounting the SSD over certain folders, like "/tmp" and "~/.cache". However, I want the SSD to also be encrypted as my main home folder is, AND I want to name my SSD by UUID, to help tolerate changes to device paths.

Here's my strategy so far: In fstab, I mount the SSD by UUID. It's got an ext4 file system already on it. Inside the file system are two files: "crypt-swap.img" and "crypt-cache.img", both filled with zeros. I told crypttab to load "crypt-swap.img" as type swap, with the key set to /dev/urandom, and it seems to be working for my intended purpose: Having an encrypted swap partition that recreates with a new random encryption key with each reboot.

I then tell crypttab to utilize the other img file with basically the same parameters as the swap entry: point it to "crypt-cache.img", use /dev/urandom as the key, but specify the type as "tmp". This doesn't work at all - the system dies to emergency-mode during boot, complaining about a failed dependency for that entry. I'm guessing it has something to do with CryptTab only being run before FStab, and not after, thus failing.. but this baffles me as to why the swap entry works though.

My hope was that after "crypt-cache.img" was mounted to the /dev/mapper area, I could then run a script that would create some folders in the tmp file system (like tmp and .cache), and then bind-mount then over the folders in my home folder.

Is there any easy way to tell CryptTab to retry an entry later? Am I going about this the wrong way? Am I asking the impossible?

I welcome alternative solutions. All I really want is to have my SSD speed me up a bit, but be encrypted, but not ask for a password on boot. While I'm waiting on answers, I'll probably write a script that does all this manually, after my profile logs in... but I feel this would be a failure on my part, and I'd also have to spend extra time applying the solution to several other profiles on my machine.

Thank you all for your time!

~Mike

---

### Post by mikey93898 on 2016-08-04
I solved it (sort of) by finding an obscure entry somewhere in the archlinux wiki. Basically, what I needed to do was create two full partitions on my SSD: One for my encrypted swap, and the other for my encrypted cache files. Then I formatted each using ext2 *but specifying* the file systems to be only 1 megabyte long each and leave the remainder of each partition unused. Then in the crypttab, I specify an offset value of 2048 sectors, which means crypttab won't ever touch that 1 megabyte partition and ruin its UUID, which means I'm now free to refer to each partition by its UUID in the crypttab.

With both partitions hacked into exposing consistent UUID's for crypttab, they no longer need to wait for fstab to load anything, and all works well. I ended up then going into fstab and adding the normal swap entry for the exposed partition from crypttab, and then mounting the other entry over my /tmp with a bind mount.

Then I just wrote an entry in my "~/.profile" folder to execute a short script that makes a folder for my users inside /tmp, then does another bind mount onto my ~/.cache folder.

It seems hacky but it definitely works.... and my system seems to be a bit faster now when opening a bazillion chrome tabs and youtube videos and stuff.

Yay.

---

