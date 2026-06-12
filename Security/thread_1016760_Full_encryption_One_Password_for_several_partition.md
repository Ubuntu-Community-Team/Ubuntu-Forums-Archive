---
title: "Full encryption: One Password for several partitions?"
date: 2008-12-20
forum: Security
---

### Post by srynonick on 2008-12-20
hello,

yesterday I installed fedora 10 and encrypted 3 partitions. i only had to enter one password (during install and especially at boot - and all encrypted partitions get mounted!). this is what i'm missing on ubuntu - currently i have 3 encrypted partitions and have to enter 3 passwords at boot, that's quite annoying!

1) any chance to fix this without storing the password unencrypted in a shell script and running this after boting?
2) would using LVM help to fix this, if you add all partitions to one LVM?
3) does somebody know how fedora 10 does this?

thank you very much!

---

### Post by bodhi.zazen on 2008-12-20
I believe you are correct, the 3 partitions are on a LVM. I believe you can do this with the Ubuntu Alternate Installation CD.

---

### Post by blastus on 2008-12-20
You can have multiple partitions and set it up so that you only have to enter in a pass phrase once regardless of whether they are LVM partitions or not. 

What you need to do is create a keyfile and insert the keyfile into the 2nd LUKS slot (which is slot 1) for all the partitions except for the one where you need to enter in a pass phrase to boot (which is typically an LVM partition containing root and swap.) 

What I do is put the keyfile somewhere on root and configure crypttab to use the keyfile to unlock all the other encrypted partitions. This way I only have to enter in my pass phrase once and then the keyfile (which is also secure because it is on an encrypted partition) is used to unlock all the other partitions. 

There is no limit to the number of encrypted partitions you can have. I have five of them, four of which are unlocked with a keyfile and I only have to enter in my pass phrase once to unlock the first partition.

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Caveat: If you only have to enter one password, then potential attackers only have to *compromise* one password. This should factor into your consideration in proportion to the importance of the data you're trying to protect.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNOxwACgkQyLm4ydrABvcnXwCgxR3Kk5uat2SEMyb8NHEE9VGD
VvQAoKsrI9LpMzTev+/m5VcpWTJaXCyi
=JBcl
-----END PGP SIGNATURE-----

---

### Post by blastus on 2008-12-20
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Caveat: If you only have to enter one password, then potential attackers only have to *compromise* one password. This should factor into your consideration in proportion to the importance of the data you're trying to protect.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNOxwACgkQyLm4ydrABvcnXwCgxR3Kk5uat2SEMyb8NHEE9VGD
VvQAoKsrI9LpMzTev+/m5VcpWTJaXCyi
=JBcl
-----END PGP SIGNATURE-----

True but no-one is going to remember or use more than one long or completed pass phrase when they boot (or manually enter later by opening a text file containing the additional pass phrases.) It is better to have one good pass phrase (mine is almost 40 characters long) than five short and easy to remember passwords.

---

### Post by hyper_ch on 2008-12-20
> **blastus said:**
> 
What you need to do is create a keyfile and insert the keyfile into the 2nd LUKS slot (which is slot 1) for all the partitions except for the one where you need to enter in a pass phrase to boot (which is typically an LVM partition containing root and swap.) 

I wrote a little howto on that. It's in the tutorials section.

---

### Post by srynonick on 2008-12-20
hello,

thank you all for your replies!
i'm aware it can be done this way, but i don't like to store my keys or password directly on the hdd (even if it's encrypted). i'm wondereing how it's done on fedora, anybody knows that? i mean, if you currently login, your password is somewhere in the cache, you should also be able to use this for the other partitions (as long as they have the same passwords) instead of using a keyfile or similar.

i will try if it makes a difference if you put all partitoins in one LVM, though i have no clue how to use LVM, will just try it and let you know if it then works with only one password...

---

### Post by teddks on 2008-12-20
> **srynonick said:**
> hello,

thank you all for your replies!
i'm aware it can be done this way, but i don't like to store my keys or password directly on the hdd (even if it's encrypted). i'm wondereing how it's done on fedora, anybody knows that? i mean, if you currently login, your password is somewhere in the cache, you should also be able to use this for the other partitions (as long as they have the same passwords) instead of using a keyfile or similar.

i will try if it makes a difference if you put all partitoins in one LVM, though i have no clue how to use LVM, will just try it and let you know if it then works with only one password...

Fedora is likely done with LVM. It's easy to do LVM in the alternate installer, you just do what you normally do to set up an encrypted device, except when you would be formatting it as ext3 or another filesystem, you select "Use as physical volume for LVM". Then, you make all the filesystems on top of that LVM.

---

### Post by srynonick on 2008-12-20
thank you teddks, i meanwhile tested this. seems like LVM is the solution to my problem - make e.g. 2 partitions on your hdd (1 for /boot, rest for LVM), use the LVM partition as "partition for encryption" and when configuring this partition, choose "parition for lvm".

however, my problem now is, that i have 2 HDDs and need this layout:
HDD1:
/boot
swap
/ (root)

HDD2
/home

but using the alternate installer, i first have to choose "use volume for encryption" before creating a LVM group. and as i have two HDDs i have two partitions for encryption (=2 passwords and the installer doesn't care if you choose the same password for several partitions) before i can create a LVM group, so i still have to enter 2 passwords on boot ):
anybody can help me with this?

thank you very much!

---

### Post by teddks on 2008-12-20
> **srynonick said:**
> thank you teddks, i meanwhile tested this. seems like LVM is the solution to my problem - make e.g. 2 partitions on your hdd (1 for /boot, rest for LVM), use the LVM partition as "partition for encryption" and when configuring this partition, choose "parition for lvm".

however, my problem now is, that i have 2 HDDs and need this layout:
HDD1:
/boot
swap
/ (root)

HDD2
/home

but using the alternate installer, i first have to choose "use volume for encryption" before creating a LVM group. and as i have two HDDs i have two partitions for encryption (=2 passwords and the installer doesn't care if you choose the same password for several partitions) before i can create a LVM group, so i still have to enter 2 passwords on boot ):
anybody can help me with this?

thank you very much!

Install the full system onto one hard drive, then just expand the LVM onto the second.

---

### Post by bodhi.zazen on 2008-12-20
> **teddks said:**
> Install the full system onto one hard drive, then just expand the LVM onto the second.

You can do that with LVM, but can you also extend a crypt across physical drives ?

---

### Post by teddks on 2008-12-20
> **bodhi.zazen said:**
> You can do that with LVM, but can you also extend a crypt across physical drives ?

Crap, I didn't think of that. You're right.

You could set up a RAID and then a crypt and then an LVM... I hope.

---

### Post by bodhi.zazen on 2008-12-21
Too bad, I was hoping you knew how to do that ....

---

### Post by hyper_ch on 2008-12-21
> **teddks said:**
> You could set up a RAID and then a crypt and then an LVM... I hope.

There's a bug when doing so... it won't correctly create the initramfs... at least not up to intrepid...

---

### Post by cmcginty on 2008-12-23
The work around for that bug is:

1) exit to the shell after installation is complete
2) chroot to the new root partition
3) edit the /etc/crypttab and add an entry to the file for your crypt partitions: 'crypt_md0 /dev/md0 none luks'
4) run update-initramfs -u -k all
5) reboot

---

