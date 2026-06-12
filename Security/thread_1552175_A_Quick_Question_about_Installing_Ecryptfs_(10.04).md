---
title: "A Quick Question about Installing Ecryptfs (10.04)"
date: 2010-08-13
forum: Security
---

### Post by StewartM on 2010-08-13
I've solved all the problems with my 10.04 system upgrade (well, in one fashion or another). 

However, I'm thinking of re-installing just to place /home on a separate partition and the fact that I can see some remnants of 8.04 on my system (I ran a Sweeper and it removed all the Hardy kernels and a few other things but I still see the modules for those kernels when browsing the filesystem). I know you can also move /home to a new partition without performing a new installation, but I lack the requisite disk space to do that.

I'm going to start using Ecryptfs. But aAccording to this dated link I was given (for 9.04 alpha)

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

says the Ecryptfs install doesn't like /home folders on separate partitions. Is that still true or has that been updated?

StewartM

---

### Post by FuturePilot on 2010-08-13
I use a separate /home partition and ecryptfs works fine.

---

### Post by bodhi.zazen on 2010-08-13
> **StewartM said:**
> I've solved all the problems with my 10.04 system upgrade (well, in one fashion or another). 

However, I'm thinking of re-installing just to place /home on a separate partition and the fact that I can see some remnants of 8.04 on my system (I ran a Sweeper and it removed all the Hardy kernels and a few other things but I still see the modules for those kernels when browsing the filesystem). I know you can also move /home to a new partition without performing a new installation, but I lack the requisite disk space to do that.

I'm going to start using Ecryptfs. But aAccording to this dated link I was given (for 9.04 alpha)

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

says the Ecryptfs install doesn't like /home folders on separate partitions. Is that still true or has that been updated?

StewartM

I will update the blog page.

If you are already using a separate /home directory from a previous install, and you want to preserve your /home , there is no way that I know of encrypting the old home (if that makes sense).

In other words, during the installation process, ecryptfs will not encrypt an existing /home partition.

---

### Post by FuturePilot on 2010-08-13
There shouldn't be a need to do anything with an existing ecryptfs /home partition. I've done reinstalls like that and as long as you don't select the encryption option and use the same password as you had, everything will still be there, unlocked automatically when you log in, as usual.

---

### Post by bodhi.zazen on 2010-08-13
> **FuturePilot said:**
> There shouldn't be a need to do anything with an existing ecryptfs /home partition. I've done reinstalls like that and as long as you don't select the encryption option and use the same password as you had, everything will still be there, unlocked automatically when you log in, as usual.

That is not what I am saying.

If you have an existing /home partition, and it is not encrypted, you can not easily use the installation CD (Desktop or alternate) to convert the old, unencrypted partition, to an ecryptfs partition. You have to back up your data, do the install, which will encrypt the new home, and then restore the data.

If you have an old ecryptfs partition you can continue to use it as an encrypted partition, so long as you keep the same password, and do not format /home during the install.

So you see, it is not so straight forward.

---

### Post by FuturePilot on 2010-08-13
Oh now I see. Sorry, I misunderstood.

---

### Post by bodhi.zazen on 2010-08-13
> **FuturePilot said:**
> Oh now I see. Sorry, I misunderstood.

Yep, how to write that onto my web page , lol.

It is trivial for someone as knowledgeable you yourself, confusing for new users, and a mistake can result in data loss :(

---

### Post by StewartM on 2010-08-15
Oh, but it's interesting to listen to this discussion. :P

I have done the re-installation. All home user directories, even the guest account, are encrypted using Ecryptfs, as well as swap space. I installed both Truecrypt and Scramdisk as well, even though the latter doesn't work with the 2.6.32-24 kernel. Looking at the development notices the developer is busy fixing things for the .34 kernel, so I assume he's going for a long-term fix rather than a short-term solution. I am going to use these tools to manage my backed up data. I am using Revelation to store my Ecryptfs passphrases (can you copy-and-paste these if you need to change passphrases? I'd hate to type all that out by hand).

I'd like to recommend that Scramdisk be included in the Ubuntu repositories. One, unlike Truecrypt, it's truly open-source and doesn't come with a weird license. Two, it's actively maintained, unlike some of the other encryption tools that *are* in the repositories, which haven't been updated since 2006. I would eventually like to see Scramdisk not only support the legacy Scramdisk and Truecrypt partitions/containers (it also does swapfile encryption, though that's less necessary with Ubuntu supporting it) but also become a frontend for LUKS encryption. Also, unlike Truecrypt, Scramdisk does not require sudo-user privileges or tweaking the sudousers file to mimic sudo-user privileges. One of the worrisome things about Truecrypt is that my day-to-day internet account is now a sudo user account, though I limit that use to just mounting Truecrypt volumes (though there are published tweaks around this problem).

But anyway--the only odd thing is how my partition table looks. I have these additional 1 mB partitions on the disk I didn't put there. I noticed when partitioning the disk the partition numbers were not sequential (I gave the filesystem the first partition, swap second, and /home the third). Here is what my file system table looks like:

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Linux%20Support/Screenshot.png[/IMG]

I backtracked a couple of time in the install when I saw this happening. Is this a feature of Grub 2, or is it a feature of using Encryptfs (I suspect the "unknown" on the swap space is because it's encrypted) or do I have bad places on the disk, or did I goof up somehow?

StewartM

---

### Post by StewartM on 2010-08-15
> I'd like to recommend that Scramdisk be included in the Ubuntu repositories. 

Where do I do this?

StewartM

---

### Post by movieman on 2010-08-15
> **StewartM said:**
> But anyway--the only odd thing is how my partition table looks. I have these additional 1 mB partitions on the disk I didn't put there. I noticed when partitioning the disk the partition numbers were not sequential (I gave the filesystem the first partition, swap second, and /home the third).

1MB gaps are probably for alignment, and the partition numbers are not sequential because you're using a DOS-era partition table where 'four partitions are enough for anyone' until they had to add extended partitions to cope with cases where they're not :).

---

