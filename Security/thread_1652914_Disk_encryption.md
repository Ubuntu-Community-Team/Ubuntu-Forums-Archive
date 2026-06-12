---
title: "Disk encryption?"
date: 2010-12-25
forum: Security
---

### Post by PDA1 on 2010-12-25
What is the best or recommended or typical encryption method and scheme  in Ubuntu?  Yes, yes, yes I know only I can answer that question  depending upon many variables but certainly there has to be a general  encryption plan people use in Ubuntu. 
 
I use TC for certain data files and have never had a problem with it. 
 
I've heard of just encrypting a partition or making a huge volume and  stuffing all data files into it.  I've also heard the Ubuntu offers some  disk encryption at installation (too late for that now for me). 
 
For very good encryption what should I encrypt?  I've heard something  about a swap file (or something with the name swap in it) and Tmp folder  or something. 
 
Plans and methods are what I need to hear about. 
 
What's your recommendation?

---

### Post by aeronutt on 2010-12-25
I use Truecrypt also...it can fully encrypt disk. I like the fact that the disk is encrypted indendant of the OS type or version I'm using.

---

### Post by PDA1 on 2010-12-25
Are you sure you can use TC to encrypt an entire disk in Ubuntu?

I thought that could only be done in Windoz?

---

### Post by Megaptera on 2010-12-26
I find TrueCrypt more than adequate but some interesting encryption projects and methods here:

[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

and here [http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)

---

### Post by rookcifer on 2010-12-26
If you want whole disk encryption on Linux you're only choice is dm-crypt/LUKS.  If using Ubuntu, you can use the "alternate install CD" for this.

Using TC is perfectly fine for encrypted containers (but it wont do whole disk encryption on Linux).  However, if you want to use a native Linux tool to make encrypted containers, it is fairly simple:

**Step 1:**

First decide how big you want the container to be.  Let's say you wanted it to be 10GB in size.  Now run:

```
dd if=/dev/urandom of=my_container bs=1M count=10000
```

Now let me explain the count and bs variables because you need to understand them in order to make sure your container is the size you want.  The "bs" variable stands for block size, and here it's defined at 1MB. Therefore, "count" is contingent on what you enter for bs (I recommend just sticking with 1MB).  I will let you do the math for the rest of it (hint: 1GB = 1000MB).  However, be warned that the bigger the container, the longer this operation will take.  Writing random data to the area you want to encrypt is perhaps the most important step for making sure the container is secure against cryptanalysis. 


**Step 2:**

Once you have created the container (of nothing but random data so far), you need to mount it to a loopback device, like so:

```
sudo losetup /dev/loop0 my_container
```


**Step 3:**

Now we have to decide what encryption scheme we want to use.  You can use any algorithm/hash combination that the kernel offers.  The overall best choice is probably AES-256 with SHA-512 in XTS mode (same scheme Truecrypt uses).  If you're overly paranoid you can use Serpent-256 with SHA-512 in XTS mode.  Serpent will be a little slower than AES, but it is stronger.  (However, saying Serpent is stronger than AES is like saying which is easier, jumping across the Atlantic or jumping to Mars -- neither are possible and thus neither algorithm is in any danger of being broken).  The fastest two algorithms are probably going to be AES and Twofish (and both are very secure).  You can use other algorithms too, like  3DES, CAST5/6, CAMELLIA, etc.  Here, I will use AES-256. 

In any case, once you have figured out what scheme to use, now it's time to encrypt the container:

```
sudo cryptsetup -c aes-xts-plain -s 256 -h sha512 luksFormat /dev/loop0
```

It will ask you to enter your passphrase and confirm it.  You should probably use an unpredictable passphrase of 20 characters or more (the longer the better).  Make a passphrase with letters, numbers and symbols if possible.


**Step 4:**


Now let's test it by opening it:

```
sudo cryptsetup luksOpen /dev/loop0 my_secret_filesystem
```

Notice: above I entered "my_secret_filesystem" since the name you enter here will be *different* than what we entered previously (my_container).  You can name both of them whatever you want, but just remember they need to be *different*.  Trust me, I have made this mistake of naming them the same thing and it caused me a lot of confusion.

If you get a "successful" message after entering the above command, then you're good.  You were able to unlock the encryption.  


**Step 5:**

The next thing to do is format it with a filesystem of your choice.  I will use ext4 in this example:

```
sudo mkfs.ext4 /dev/mapper/my_secret_filesystem
```

It will take it a couple of minutes, but you will be alerted when done.


**Step 6:**

Now figure out where on your filesystem you want this container to be mounted.  A standard place is /mnt, but you can choose wherever you want (just make sure where you mount it already exists!).  For simplicity, I will use /mnt in this example.

```

sudo mount /dev/mapper/my_new_filesystem /mnt/my_container
```

Here you're essentially "connecting" the new filesystem and the random blob (my_container) together at the /mnt mount point.  Now enter your password and see if it unlocks it and mounts it. If so, you are ready to begin putting files in it. 


**Step 7:**

Now all you have left to do is create two automated scripts to handle mounting and unmounting for you.

Copy and paste these scripts to two different empty text files (of course changing the names of the files accordingly).

First the mounting script:

```
#!/bin/bash

sudo losetup /dev/loop0 /path/to/my_container
sudo cryptsetup luksOpen /dev/loop0 my_secret_filesystem
sudo mount /dev/mapper/my_secret_filesystem /mnt/my_secret_filesystem
```

Name this file something like "mount.sh" and put it in your /home/username directory.

Now the unmounting script:

```
#!/bin/bash

sudo umount /mnt/my_secret_filesystem
sudo cryptsetup luksClose /dev/mapper/my_secret_filesystem
sudo losetup -d /dev/loop0
```

Now save it and name it something like "unmount.sh"  And, BTW, be sure to *make both scripts executable!*

Now all you have to do to mount the container is type "mount" at the terminal and enter your password.  After that, it will be mounted and ready to use.  When you're done with it, just type "unmount" at the terminal and it will close it.

**Now a final recommendation:** you should create a test container before you create a "real" container for everyday use, just to make sure it works properly.  There's nothing worse than putting important stuff in a container that you can't unlock.

---

### Post by Razor338 on 2010-12-27
use truecrypt!!!it has many features and very easy to customize!!

---

### Post by PDA1 on 2010-12-27
> **rookcifer said:**
> If you want whole disk encryption on Linux you're only choice is dm-crypt/LUKS.  If using Ubuntu, you can use the "alternate install CD" for this.

Using TC is perfectly fine for encrypted containers (but it wont do whole disk encryption on Linux).  However, if you want to use a native Linux tool to make encrypted containers, it is fairly simple:

**Step 1:**

First decide how big you want the container to be.  Let's say you wanted it to be 10GB in size.  Now run:

```
dd if=/dev/urandom of=my_container bs=1M count=10000
```Now let me explain the count and bs variables because you need to understand them in order to make sure your container is the size you want.  The "bs" variable stands for block size, and here it's defined at 1MB. Therefore, "count" is contingent on what you enter for bs (I recommend just sticking with 1MB).  I will let you do the math for the rest of it (hint: 1GB = 1000MB).  However, be warned that the bigger the container, the longer this operation will take.  Writing random data to the area you want to encrypt is perhaps the most important step for making sure the container is secure against cryptanalysis. 


**Step 2:**

Once you have created the container (of nothing but random data so far), you need to mount it to a loopback device, like so:

```
sudo losetup /dev/loop0 my_container
```**Step 3:**

Now we have to decide what encryption scheme we want to use.  You can use any algorithm/hash combination that the kernel offers.  The overall best choice is probably AES-256 with SHA-512 in XTS mode (same scheme Truecrypt uses).  If you're overly paranoid you can use Serpent-256 with SHA-512 in XTS mode.  Serpent will be a little slower than AES, but it is stronger.  (However, saying Serpent is stronger than AES is like saying which is easier, jumping across the Atlantic or jumping to Mars -- neither are possible and thus neither algorithm is in any danger of being broken).  The fastest two algorithms are probably going to be AES and Twofish (and both are very secure).  You can use other algorithms too, like  3DES, CAST5/6, CAMELLIA, etc.  Here, I will use AES-256. 

In any case, once you have figured out what scheme to use, now it's time to encrypt the container:

```
sudo cryptsetup -c aes-xts-plain -s 256 -h sha512 luksFormat /dev/loop0
```It will ask you to enter your passphrase and confirm it.  You should probably use an unpredictable passphrase of 20 characters or more (the longer the better).  Make a passphrase with letters, numbers and symbols if possible.


**Step 4:**


Now let's test it by opening it:

```
sudo cryptsetup luksOpen /dev/loop0 my_secret_filesystem
```Notice: above I entered "my_secret_filesystem" since the name you enter here will be *different* than what we entered previously (my_container).  You can name both of them whatever you want, but just remember they need to be *different*.  Trust me, I have made this mistake of naming them the same thing and it caused me a lot of confusion.

If you get a "successful" message after entering the above command, then you're good.  You were able to unlock the encryption.  


**Step 5:**

The next thing to do is format it with a filesystem of your choice.  I will use ext4 in this example:

```
sudo mkfs.ext4 /dev/mapper/my_secret_filesystem
```It will take it a couple of minutes, but you will be alerted when done.


**Step 6:**

Now figure out where on your filesystem you want this container to be mounted.  A standard place is /mnt, but you can choose wherever you want (just make sure where you mount it already exists!).  For simplicity, I will use /mnt in this example.

```

sudo mount /dev/mapper/my_new_filesystem /mnt/my_container
```Here you're essentially "connecting" the new filesystem and the random blob (my_container) together at the /mnt mount point.  Now enter your password and see if it unlocks it and mounts it. If so, you are ready to begin putting files in it. 


**Step 7:**

Now all you have left to do is create two automated scripts to handle mounting and unmounting for you.

Copy and paste these scripts to two different empty text files (of course changing the names of the files accordingly).

First the mounting script:

```
#!/bin/bash

sudo losetup /dev/loop0 /path/to/my_container
sudo cryptsetup luksOpen /dev/loop0 my_secret_filesystem
sudo mount /dev/mapper/my_secret_filesystem /mnt/my_secret_filesystem
```Name this file something like "mount.sh" and put it in your /home/username directory.

Now the unmounting script:

```
#!/bin/bash

sudo umount /mnt/my_secret_filesystem
sudo cryptsetup luksClose /dev/mapper/my_secret_filesystem
sudo losetup -d /dev/loop0
```Now save it and name it something like "unmount.sh"  And, BTW, be sure to *make both scripts executable!*

Now all you have to do to mount the container is type "mount" at the terminal and enter your password.  After that, it will be mounted and ready to use.  When you're done with it, just type "unmount" at the terminal and it will close it.

**Now a final recommendation:** you should create a test container before you create a "real" container for everyday use, just to make sure it works properly.  There's nothing worse than putting important stuff in a container that you can't unlock.


Thank you for the very thorough explanation.

My problem is that I already have 10.04 installed on my computer.  Can I use your method to encrypt the disk even though data is already on it?   Does the data and files have to be backed up first and then copied back to the newly created encrypted drive?

Oh....tell me if I'm correct as I just re-read your post-  what you're describing in detail is creating a Container that gets mounted and you were not providing detailed instructions on how to encrypt and existing drive.  Is that correct?

On the other hand......to encrypt the entire drive using dm-crypt/LUKS I would have to first backup my Home Folder (only that Home Folder and no other) and then do a fresh Ubuntu installation using the Alternate Install CD and then move the entire Home Folder back over to the new installation.  Is that right?

---

### Post by PDA1 on 2010-12-27
> **Razor338 said:**
> use truecrypt!!!it has many features and very easy to customize!!


TC is great.  I love it....BUT.........my computer is already in use, unencrypted.  

Using TC what would I do to create an encrypted drive?  I'm not that Ubuntu savy so a lot of this stuff is strange to me.  From what I can tell there are 2 parts to my system;

1.  The Home Folder

2.  The File System folder

Now, in what way would I use Truecrypt to create an encrypted drive?  Do I create some HUGE Volume that contains both Home Folder and File System and then, using Truecrypt alone, Mount them?

---

