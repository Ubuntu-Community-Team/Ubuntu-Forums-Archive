---
title: "encrypt swap partition"
date: 2005-10-31
forum: Server Platforms
---

### Post by MindSpore on 2005-10-31
Can anyone give me a step-by-step on how to do this?  I have dm-crypt installed.  Basically I want it to generate a random key and encrypt the swap on boot, so it's encrypted for the session.

Thanks,
spore

---

### Post by niko_ on 2005-11-01
hi mindspore, i dunno about dm-crypt, but you could use jetico bestcrypt, which is a very good program and provides best encryption.
Here i wrote an easy 2 steps guide for encrypting the swap partition with powerful rijndael algorithm using random key on boot with bestcrypt:

1. download bestcrypt and install it:

> wget [www.jetico.com/linux/BestCrypt-1.6-2.tar.gz](www.jetico.com/linux/BestCrypt-1.6-2.tar.gz)
tar zfvx BestCrypt-1.6-2.tar.gz
cd bcrypt
make
sudo mkdir /usr/man/man8;make install

2. apply this patch i wrote:

> download  [ATTACH]3297[/ATTACH]
gzip -d swapenc.patch.gz
sudo mv swapenc.patch /etc/init.d
cd /etc/init.d/
sudo patch < swapenc.patch
sudo rm -rf swapenc.patch

The patch basicly modifyes /etc/init.d/bcrypt and adds swap encryption on boot. It adds activating the original swap again after bcrypt is stopped (when linux shutdowns usually), so you wont get any annoying umount errors. Also it fixes the bc modules load fatal errors problem which happens on breezy 2.6.12-9 kernel and maybe others. 
You can use any other kind of encryption algorithm, but i recommend rijndael.

have fun.

---

### Post by MindSpore on 2005-11-01
Isn't Jetico BestCryp commercial?

---

### Post by niko_ on 2005-11-01
its free for linux

---

### Post by poptones on 2005-11-01
Jeezus don't do that, there's no need for it. DM is *truly* Free, it's being supported by further development, it's part of the distribution, and it works great.

To encrypt your swap partition all you need to do is:

sudo echo "swap /dev/**your_swap_partition_goes_here** /dev/urandom swap" > /etc/crypttab
sudo sed -i "s:/dev/**your_swap_partition_goes_here**:/dev/mapper/swap:" /etc/fstab

Next time you reboot, DM and the boot scripts will handle everything.

---

### Post by Doc.Caliban on 2005-11-02
I can't seem to find any reference to "dm-crypt" for installation.

On a different note, could I disable the swap alltogether with enough RAM installed?  (I have 2 GB)  Just a though.

-Doc

---

### Post by jonzep on 2005-11-02
i would go with Doc.Caliban's suggestion of just going with no swap if security is an issue and you have enough ram... swap is slow to begin with... encrypting it won't help...

---

### Post by MindSpore on 2005-11-02
And to answer your question Doc.Caliban, do:

sudo apt-get install cryptsetup

That will install the configuration utility and of course will install dm-crypt with it.

---

### Post by humbll on 2007-02-20
> **poptones said:**
> Jeezus don't do that, there's no need for it. DM is *truly* Free, it's being supported by further development, it's part of the distribution, and it works great.

To encrypt your swap partition all you need to do is:

sudo echo "swap /dev/**your_swap_partition_goes_here** /dev/urandom swap" > /etc/crypttab
sudo sed -i "s:/dev/**your_swap_partition_goes_here**:/dev/mapper/swap:" /etc/fstab

Next time you reboot, DM and the boot scripts will handle everything.


when i entered the 1st command:
 sudo echo "swap /dev/sda7 /dev/urandom swap" > /etc/crypttab

my terminal returned the error:
bash: /etc/crypttab: Permission denied

What gives? I am using Edgy

---

