---
title: "LUKS - separate root and home partitions question"
date: 2020-04-12
forum: Security
---

### Post by dammitcharlie on 2020-04-12
Hey all, relative newcomer to Linux here. I just re-installed Lubuntu so I could start fresh, but with disk encryption enabled this time. In the past I've used separate partitions for root and home, and I like the idea of it, so I repeated that in this install.

[IMG]https://i.imgur.com/WpM9nHs.jpg[/IMG]


[IMG]https://i.imgur.com/BJfc9Cl.jpg[/IMG]

As you can see, I've encrypted each of the root and home partitions. However, I have noticed something a little strange. When I first boot up the computer, I am asked to enter my password to decrypt the root partition, **but at no point am I required to input the password to decrypt the home partition.** This behavior differs from what I've seen with BitLocker on Windows: after decrypting the C drive at the beginning of startup, I still have to enter the password to my secondary drive whenever I try to access it from within Windows. On Lubuntu, it seems like the home partition is magically decrypted once I'm logged in.

What's going on here? Is the fact that /home is a subdirectory of / basically making the /home encryption redundant/irrelevant? If someone got a hold of my hard drive and was able to unlock the root partition, would they then have access to the home partition? Or, even worse: is my /home partition not encrypted at all?

When I run *cryptsetup luksDump* it seems to indicate that /home is encrypted. Am I missing something here?

Any insight into this would be appreciated.

Bonus question: when trying to install Lubuntu with the boot partition encrypted (same as above: ext4 with LUKS), I kept running into some kind of Python error (sorry, forgot to save it). Was I trying to do something impossible with this, or should I have figured out a way to encrypt the boot partition if I'm serious about security? Is having a non-encrypted boot partition defeating the purpose of the encryption of the other partitions?

Thank you!

---

### Post by EuclideanCoffee on 2020-04-12
Perhaps this is due to a script inside of Ubuntu to make decryption of multiple devices easier.

[https://packages.debian.org/search?searchon=contents&keywords=decrypt_keyctl](https://packages.debian.org/search?searchon=contents&keywords=decrypt_keyctl)

You may want to refer to the hints in the document below on how to remove keyfile. Otherwise perhaps Google will provide further troubleshooting.

```

Crypttab Entries:

    <target>    <source>    <keyfile>        <options>
    sda_crypt   /dev/sda2   main_data_raid   luks,discard,keyscript=decrypt_keyctl
    sdb_crypt   /dev/sdb2   main_data_raid   luks,discard,keyscript=decrypt_keyctl
    ...
    sde_crypt   /dev/sde2   main_data_raid   luks,discard,keyscript=decrypt_keyctl


How does it work
----------------

Crypttab Interface:

A keyscript is added to options including a keyfile definition as third
parameter in the crypttab file. The keyscript is called with the keyfile as the
first and only parameter. Additionally there are a few environment variables
set but currently are not used by this keyscript (man 5 crypttab for exact
description).

Keyscript:

`decrypt_keyctl` uses the Linux kernel keyring facility to securely cache
passphrases between multiple invocations.
The keyfile parameter from crypttab is used to find the same passphrase
between multiple invocations.  The term used to described the key in the user
keyring is `cryptsetup:$CRYPTTAB_KEY`, unless `$CRYPTTAB_KEY` is empty
or has the special value `none`, in which case the description is merely
`cryptsetup` (thus allowing compatibility with other tools like gdm and
systemd-ask-password(1).)

Currently the cache timeout is 60 seconds and not configurable (please report a
bug if it is too low for you).


Problems
--------

Passphrase is piped between processes and could end up in unsecured memory,
thus later swapped to disk! => Use of cryptoswap recommend!


Hints
-----

To remove all traces of this keyscript you may want to cleanup the keyring
completely with the following command afterwards:

    sudo keyctl clear @u


```

---

### Post by TheFu on 2020-04-12
An example of encrypted + LVM layout:
[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
That is what the installer creates by default. No extra effort needed.
There is 1 encrypted partition and LVM is used to split that encrypted container into different LVs.

Resizing the LVs post-install is pretty easy.  Just accept the defaults and fix it immediately after the install and 1st patches are done.

---

### Post by EuclideanCoffee on 2020-04-12
The default lvm configuration does not encrypt two partitions.

Generally "double encryption" does not equal better encryption.

If a user can bypass the root encryption, they can attack the home encryption the same way.

If you are seriously interested in better full disk encryption, use TPM2. This has not yet been implemented to Ubuntu, but you can build your own solution on Ubuntu.

---

### Post by TheFu on 2020-04-12
> **EuclideanCoffee said:**
> The default lvm configuration does not encrypt two partitions.

True.  That's why LVM is used to provide multple LVs inside the  PV that gets encrypted.
> **EuclideanCoffee said:**
> 
If a user can bypass the root encryption, they can attack the home encryption the same way.

There are mitigations for the evil maid attack.  Mainly, booting from a flash drive that never leaves your person, even int the shower.
> **EuclideanCoffee said:**
> 
If you are seriously interested in better full disk encryption, use TMP2. This has not yet been implemented to Ubuntu, but you can build your own solution on Ubuntu.
i suspect TMP2 is a typo.  Probably meant TPM2?  I&#8217;ve only used TPM on Chrombooks.

i haven't seen any Ubuntu that supports an encrypted /boot, but i'm running a few LTS behind.  New is NOT always better.

---

### Post by EuclideanCoffee on 2020-04-12
TMP2 was a typo. 

Boot isn't needed, as it's not part of full-disk encryption. Boot is not a security flaw. It allows you to access the other partitions.

TPM2 makes it harder to break security by n-th number of years. It also has a mechanism to stop accepting attempts after 32 tries and then allows you to fail until reset.

---

