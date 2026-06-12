---
title: "Encrypted 7.10 Gusty install - 3 questions"
date: 2008-04-19
forum: Security Discussions
---

### Post by sparklyprgs on 2008-04-19
i installed gusty on a machine using the "use full hard drive" default encrypted LVM install process which worked great.

**q1)** which encryption algorithm does the default install use? i'm 99% sure it was aes but is there a way to check on an already installed machine?

then i installed gutsy on another machine for _dual windows booting_, so this time went through this guys [COLOR="RoyalBlue"]**COOL **[/COLOR]guide: [HERE]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html")
which lets you have more control, so i could pick an algo, more choice on the partitioning etc.

**q2)** is there any windows program that i can use to "mount" the encrypted gutsy partions *within* windows?

**q3a)** (especially if the answer to 2 is no) could i do a non-encrypted install of gutsy for the dual boot machine, and then do full system encryption using truecrypt 5?

**q3b)** if so, can you then access THAT partition from within windows since truecrypt is cross platform?

thanks... just starting out still - a lot to learn.

---

### Post by Macchi on 2008-04-19
Hi,

The answer to your second question is No and Yes. 
Most probably there is NO easy solution to access your data from a Windows partition on the same machine because the encrypted partition has a Logical Volume Management on top of the encryption and a Linux file system such as ext3 on top of all that. To access it from Windows you would need a driver that decrypts the disk partition, interpretes the lvm and furthermore handles the filesystem (for instance ext3).
I haven't seen nor heard yet about such a driver on Windows. Actually even reading ext3 file systems from windows can be quite unstable. That was my impression of previous experiments with ext2/etx3 drivers for Windows.
 
But the answer to your second question could also be YES if you mean accessing a shared area on your encrypted Linux machine through the network from another machine running Windows. That can be accomplished quite easily by installing a samba-server with a suitable configuration. Search the forums for examples and hints on the art of configuring samba servers.

I do not have time to try to understand your third question but certainly it would be easier to have a non-encrypted FAT32 partition that can be accessed both from Windows and from your encrypted Linux system. Then have all data on that partition encrypted through some cross-platform solution for win and linux.

Before attempting all this you should consider deleting your windows partitions and simply accessing your sensitive and confidential information exclusively from Linux!

---

### Post by hyper_ch on 2008-04-20
I duno yet a way to mount the luks/dm_crypt encrypted drives in windows.

Another thing you must DO is backup your data. Either also encrypted or not. If you harddisk will ever get a failure at the initializing vector of the encrypted partition, then you will not be able to access any data on it at all. Hence you DO need a backup.

---

### Post by Macchi on 2008-04-20
> **hyper_ch said:**
>  Another thing you must DO is backup your data. 
...If you harddisk..ever fails... then you will not be able to access any data on it at all.

Thanks Hyper_ch, It is great that you mention this because recovering data from an encrypted partition is not impossible but can be really very very difficult, even if you have qualified hints on the encryption keys. 

These high security environments are fantastic but eventually the complexity for maintenance and support may become too difficult to handle.Thats what happened to me. 
Unfortunately I had to give up using a completely encoded environment for my production laptop because the risk for loosing important information became bigger that the risk for such information to end up in the wrong hands. It depends completely on your application area.
For instance I configured a totally encrypted environment for a friend that stores medical research data in his (Ubuntu) laptop. I have to keep reminding him on the importance of regular backups.

---

### Post by hyper_ch on 2008-04-20
no, I don't mean if you have the key forgotten but if the initializing vector gets damaged....I dunno if data still can be restored then...

---

### Post by Meson on 2008-04-20
FreeOTFE supports LUKS partitions.  So you can mount them in windows.

I'm almost positive that it uses AES as a default.  Your best bet though is to set up your partitions manually, so that you can choose which algorithm, and the strength.

I use AES-128 for my root/swap logical container and AES-256 for my data partition.

---

### Post by Meson on 2008-04-20
> **hyper_ch said:**
> no, I don't mean if you have the key forgotten but if the initializing vector gets damaged....I dunno if data still can be restored then...

You can backup your LUKS header but the LUKS people actually recommend against it.  Here is the reasoning, it explains how to back it up "if you must:"

Read the second FAQ [http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq](http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq)

---

### Post by hyper_ch on 2008-04-21
well, I backup the encrypted data... on my encypted drive I have a key for my backup machine... with that key I unlock that one and then I backup with rsync.

---

### Post by sparklyprgs on 2008-04-22
thanks for all the info Macchi and others. when i saw your answer about the possible problems mounting the linux partition, i went back and rethought it out.
(and i just re-read my 3rd question - yes it was confusing!  i rushed the post....  O.o)

> 
...but certainly it would be easier to have a non-encrypted FAT32 partition that can be accessed both from Windows and from your encrypted Linux system. Then have all data on that partition encrypted through some cross-platform solution for win and linux.

yes, that sounded _exactly _like what i need! so here's what i came up with in the end.

_**AIM**_: have ubuntu installed with full encryption and as it's the main system, have ALL data in ubuntu by default.
BUT also to be able to boot an encrypted windows on occasion but be able to access the same data as used in ubuntu.

what i'd been trying to do was: ("map" of the 1 hard drive and |--partitions--|)
[INDENT]**|---grub---||---encrypted_ubuntu+DATA---||---encrypted_windows_nodata---|**[/INDENT]
so that when i boot window, i could "mount" the ubuntu partition to access the data.


as it sounded way too hard i did this instead (after a lot of fiddling):

**|---true_crypt_booter---||---encrypted_windows_nodata---||---grub---||---encrypted_ubuntu_nodata---||---truecrypt_data_container (fat32)---|**

now when i boot either OS, i scripted it so that the truecrypt container is opened automatically and in ubuntu, it maps under the home folder (i didn't how this could be done before) and in windows, i use "junction.exe" to make a link to it under "my documents".

this way it's still only one password to get in to either secured OS and have data available to both.

It worked out really well too because as others pointed out backups are a must (i do do backups!) so it's now easy to just backup the container file to some drive since it's just one fat 40gb file.

maybe the above might help someone else who wants a dual boot secure laptop....  \\:D/

---

