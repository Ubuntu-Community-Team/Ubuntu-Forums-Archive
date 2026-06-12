---
title: "Is Whole Disk Encryption an option on the standard Hardy desktop install?"
date: 2008-04-24
forum: Security
---

### Post by kevdog on 2008-04-24
Just wanted to know if luks whole disk encryption was now an option with the Hardy desktop CD rather than only the alternate install cd??

---

### Post by hyper_ch on 2008-04-25
have you tried it?

Grab the live cd by torrent, start up vmware/vbox and test it ;)

---

### Post by Patsoe on 2008-04-25
As far as I know you still need the alternate cd. That's also what the release information suggests.

> **hyper_ch said:**
> have you tried it?

Grab the live cd by torrent, start up vmware/vbox and test it ;)

Come on... :P

---

### Post by sunbird on 2008-04-25
I've got whole-disk encryption running on my 7.10 install, but I had to install from the alternate. There's a how-to I wrote for Macbook Pros on dual boot encryption [here.]("http://ubuntuforums.org/showthread.php?p=4604645") I definitely think  this capability should be moved to the live CD ASAP.

---

### Post by Patsoe on 2008-04-25
> **sunbird said:**
> I've got whole-disk encryption running on my 7.10 install, but I had to install from the alternate. There's a how-to I wrote for Macbook Pros on dual boot encryption [here.]("http://ubuntuforums.org/showthread.php?p=4604645") I definitely think  this capability should be moved to the live CD ASAP.

Agreed. Encryption is a hot topic and it would be a great "selling point" if Ubuntu would make it easy to set up. I think it's quite some work to put that into the installer though.

---

### Post by kevdog on 2008-04-25
Haven't had time to grab the new distro.  I guess I was relying on others who had to tell me in an effort of saving time.

---

### Post by Stochastic on 2008-04-25
Hi I just stumbled into this thread, and would like to know a little more.  I'm an UbuntuStudio user (which uses the alternate installation method by default).  Is it possible to do encryption with UbieStudio?  Will it slow the disk access speed down for audio programs etc..?

---

### Post by hyper_ch on 2008-04-25
yes, encryption will slow down i/o of the disk....

---

### Post by kevdog on 2008-04-25
I wish I knew how much it would slow down I/O -- of course depending on HW, however it would be good if someone provided some benchmarks for this.

---

### Post by Patsoe on 2008-04-25
> **kevdog said:**
> I wish I knew how much it would slow down I/O -- of course depending on HW, however it would be good if someone provided some benchmarks for this.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_hdd_encrypt&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_hdd_encrypt&num=1)

---

### Post by kevdog on 2008-04-25
Thanks for the link -- would have been nice to see a few more benchmarks, but the performance hit wasn't as much as would have thought.  Looks like the liveCD may include this by default according to the article.

Good to know.

---

### Post by AnotherDave on 2008-04-25
As long as we're wishing, let's hope for selective encrypting of directories. An encrypted /home, /swap, and /var might be a good idea, but why have an encrypted /etc, or /lib? 

Also, let's put /home on its own partition in the default install.

---

### Post by Patsoe on 2008-04-26
> **AnotherDave said:**
> As long as we're wishing, let's hope for selective encrypting of directories. An encrypted /home, /swap, and /var might be a good idea, but why have an encrypted /etc, or /lib? 

Also, let's put /home on its own partition in the default install.

Yes, so by default the installer now creates an LVM physical volume that's encrypted, but you could turn it around: set up LVM, and encrypt some of the logical volumes only. (shameless plug: I just [wrote up]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/") how I configured this stuff - though have not been as smart as to encrypt only some parts...)

---

### Post by hyper_ch on 2008-04-26
> **AnotherDave said:**
> As long as we're wishing, let's hope for selective encrypting of directories. An encrypted /home, /swap, and /var might be a good idea, but why have an encrypted /etc, or /lib? 

Also, let's put /home on its own partition in the default install.

well, it is much simpler to encrypt it all than to worry where you all may have sensitive data.... e.g. /etc contains users, groups and passwoords.... that might be helpful....

---

