---
title: "auto mount encrypted partition using  cryptsetup luksformat"
date: 2010-02-13
forum: Security
---

### Post by tucemiux on 2010-02-13
I'm using karmic and I encrypted a partition located in a secondary hard drive, the partition is /dev/sdb1.  I can mount manually by clicking on the icon in "places" but I can't auto mount it by placing an entry in /etc/fstab, I followed this guide:

[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

This is how I encrypted the hard drive:

sudo cryptsetup luksFormat /dev/sdb1 -c aes -s 256 -h sha256
sudo cryptsetup luksOpen /dev/sdb1 minux_files
sudo mke2fs -t ext4 -j /dev/mapper/minux_files -L minux_files

I was then supposed to add a line in my /etc/fstab, this is what I added:

#encrypted drive
/dev/mapper/minux_files /media/archivos_local ext4 defaults 1

Here are the permissions on "/media/archivos_local" 

drwxr-sr-x  2 tucemiux tucemiux 4096 2010-02-09 01:51 archivos_local

---

### Post by tucemiux on 2010-02-18
Anyone experienced with setting this up can provide some insight?

My partition is already encrypted using LUKS. The partition is on a secondary hard drive which has 2 partitions.

I am trying to auto mount the partition, I'm supposed to get prompted by a password but this doesn't happen.  My partition is listed as "places->59 GB Encrypted" but is not auto mounted, I have to mount it manually by clicking on the hard drive and then I am prompted for my user password. 

Once it is mounted, it is mounted at this point on its own:

ls -la /media/
drwxr-xr-x  6 tucemiux tucemiux 4096 2010-02-09 14:06 minux_files

ls -la /dev/mapper/
brw-rw----  1 root disk 252,  1 2010-02-18 14:53 devkit-disks-luks-uuid-3f0ecbe5-5fe3-4504-b0a9-5736c48defa4-uid1000


The mount point on "/media/minux_files" is created on its own.

I have attempted to add an entry in /etc/fstab but it doesn't work, I tried adding this line but it didnt work.

--->/dev/mapper/minux_files /media/archivos_local ext4 defaults 1

---

### Post by bodhi.zazen on 2010-02-18
See if this helps:

[http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

specifically, did you update your initrd ?

---

### Post by tucemiux on 2010-02-20
> **bodhi.zazen said:**
> See if this helps:

[http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

specifically, did you update your initrd ?


How do I update initrd?  I followed the thread and did this: update-initramfs -u -k all

This is what my /etc/modules file looks like:

# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
dm-crypt
aes-i586
dm-mod
sha256_generic
loop
lp

I think the problem has to do with the fact that my partition is not being mapped as an encrypted partition once I boot up my machine. My partition is not showing up in /dev/mapper after reboot.  

What module am I missing that it wont map my encrypted partition at boot up?

I can map the partition manually by doing the following: 

-->sudo cryptsetup luksOpen /dev/sdb1 minux_files

I add the following line to my fstab:

-->/dev/mapper/minux_files /media/archivos_local ext4 defaults 0 

Then remount everything in fstab: 
 
-->sudo mount -a

And the partition gets mounted.

My problem is that the device is not getting mapped as an encrypted partition.  The entry in "/etc/fstab" does not get mounted because the entry in "/etc/crypttab" doesnt get mapped as an encrypted partition.

---

### Post by bodhi.zazen on 2010-02-21
Hard to tell from what you posted.

Can you post /etc/crypttab and /etc/fstab ?

---

### Post by tucemiux on 2010-02-21
> **bodhi.zazen said:**
> Hard to tell from what you posted.

Can you post /etc/crypttab and /etc/fstab ?


It doesn't really matter because it doesn't work.

The setting I use in "crypttab" is not mapped as an encrypted drive and that is why it fails to get mounted at boot time.   I already showed you how I map it manually and then I remount everything in my "fstab" file and that works when I do it manually - the problem is it doesn't get mounted at boot time.

You could post what settings I could use in "/etc/crypttab" and then what line I should put in my "/etc/fstab", I am using an ext4 on sdb1.  The settings I have tried don't really work automatically because the setting in "crypttab" is not mapped, I have to map it manually.

I am trying to figure out why my encrypted partition doesn't get mapped as an encrypted partition at boot time.

Basically I want to do the following without failure after I boot up my machine:

sudo cryptsetup status minux_files

The current status is --> /dev/mapper/minux_files is inactive.

---

### Post by tucemiux on 2010-02-27
bumpity

---

### Post by bodhi.zazen on 2010-02-28
> **tucemiux said:**
> It doesn't really matter because it doesn't work.

If you will not post your configuration it is almost impossible to offer more then general assistance.

I did a fresh install of Ubuntu, and this is how it is done :

[http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

---

### Post by tucemiux on 2010-02-28
> **bodhi.zazen said:**
> If you will not post your configuration it is almost impossible to offer more then general assistance.

I did a fresh install of Ubuntu, and this is how it is done :

[http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)


You keep sending me to where I started.

Which is why I made my point so that you know what the problem is.

I have tried everything in the guides I am seeing -- nothing works, I already explained the problem.  

I tried your guide and I have the same problem. 

If you want to see what my "/etc/crypttab" and "/etc/fstab" looks like then please  go take a lok at your guide. I went one step further - I asked you to provide the lines that I should use in my files, the only thing you provided is the guide so that is what I used.  

Last but not least, I posted my /etc/fstab in the first post, I then tried configuring my /etc/crypttab - all the settings I tried dont work.   I changed the settings in both my "fstab" and "crypttab" so many times it doesnt matter anymore because I commented them in my fstab and deleted them off my crypttab.

I began using your guide from Step 3 -- all my data was erased, good thing I have a back up, hopefully newbies wont be using your guide.

Let me restate the problem yet again, this time using your guide.   I used your guide starting from Step 3.

I want to reboot my machine and want to  execute the following command and get a success:

---->sudo cryptsetup status test

Right now, the status is "inactive".

OK let me take you back to my previous post.

I can manually open the  partition:

-->cryptsetup luksOpen /dev/sdb1 test 
Enter LUKS passphrase: 
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful

I can manually open the partition fine, I enter my passphrase and test is now mapped:

tucemiux@minux:~$ ls -la /dev/mapper/

crw-rw----  1 root root  10, 60 2010-02-28 06:26 control
brw-rw----  1 root disk 252,  0 2010-02-28 11:26 cryptswap1
brw-rw----  1 root disk 252,  0 2010-02-28 11:26 cryptswap1_unformatted
brw-rw----  1 root disk 252,  1 2010-02-28 11:43 test

The problem - here goes again - how I can map "test" in /dev/mapper automatically???  I think I'm supposed to get prompted for my passphrase when the machine is booting up?  I am not seeing a prompt, maybe that is why "test" is not getting mapped?  

If anyone knows why my encrypted partition is not getting mapped automatically please let me know.  I'm going to  use bodhi.zazen's guide from Step 1 if I dont see any replies within a day or so.

This is what "/etc/initramfs-tools/modules looks like:

aes-i586
dm-crypt
dm-mod
sha256

I also updated my initrd:

sudo update-initramfs -k all -c

---

### Post by bodhi.zazen on 2010-02-28
You need an entry in /etc/ctrypttab

Your fstab entry is incorrect.

/dev/mapper/minux_files /media/archivos_local ext4 defaults 1

I do not see minux_files listed in 

> tucemiux@minux:~$ ls -la /dev/mapper/

crw-rw----  1 root root  10, 60 2010-02-28 06:26 control
brw-rw----  1 root disk 252,  0 2010-02-28 11:26 cryptswap1
brw-rw----  1 root disk 252,  0 2010-02-28 11:26 cryptswap1_unformatted
brw-rw----  1 root disk 252,  1 2010-02-28 11:43 test

Also an fstab entry has 2 numbers at the end, do you mean

/dev/mapper/minux_files /media/archivos_local ext4 defaults 0 1

???

Also the only entries you have listed in /dev/mapper are for test and swap, neither is listed in fstab.

I have no idea of what you are trying to mount where.

You can either emulate what I did (I posted very specific information),or post your config files for review. Be sure to tell us what you want to mount where.

From what I can see your configuration is way off, not surprised it does not work from what you posted. I know you are frustrated, but if you want assistance beyond a general how to you need to give us complete information as requested:

1. What are you wanting to mount where ?

2. Contents of /etc/fstab and /etc/crypttab and /etc/initramfs-tools/modules

3. Are you using LVM ? If so, I do not see it listed. If now you do not need dm-mod

---

### Post by tucemiux on 2010-02-28
I think the problem might be the fact I am using ubuntu studio.

You are clearly not following my thread since you repeat the same question.

The problem: my encrypted partition is not getting mapped.

My encrypted partition is not getting mapped at boot time.

I am trying to figure out why this is happening.

Do this manually on your machine, reboot your machine, then:
**-->**ls /dev/mapper

On my machine "test" is not mapped. OK, lets map it manually then.

**-->** map it manually, I already showed you how I did it and yes, it works!

Lets test to see if it's mapped.
**-->**Test: #1. ls -la /dev/mapper #2. sudo cryptsetup status test
Sure enough, "test" is now mapped!

Now lets mount "test".
**-->**sudo mount -a

t works!!!! Whatever setting you use in your fstab, "test" will be mounted.

This works on my machine -- manually!

Meaning whatever entry I have in my /etc/fstab works!

==>This is ***crucial** this means my "fstab" is configured correctly.

This is the point that I am trying to get across, I know it might be difficult to see unless youre  in front of my machine but I am comfirming that it works.

Executing "sudo mount -a" will mount everything that is in your fstab.

CRUCIAL:  After I manually map my encrypted partition I can then mount all items in my "fstab" file.  However I have to do this manually.  I can also click on "Places-->"then the hard drive, I enter my password and the partition is mapped and mounted automatically.

Problem: every time I reboot the encrypted partition is not mounted automatically.
Reason: "test" is not mapped.
Cause: Unknown. If you can help me figure it out, I will greatly appreciate it.
Maybe something about my configuration on my machine that my encrypted partition wont get mapped automatically at boot time? 

Here are the details on my machine, I hope I dont confuse you or anyone else:

I installed a fresh karmic from an ISO on my first hard drive and encrypted my "/home" partition. I am dual booting with XP.

My installation consists of "/" and "/home", only "/home" is encrypted.

The dual boot with encrypted "/home" works just fine.  I installed a second hard drive into my laptop and want to encrypt the first partition on the secondary hard drive.

Encrypted Hard drive:  Secondary hard drive on a laptop, first partition, /dev/sdb1

fstab:

> # / was on /dev/sda6 during installation
UUID=ad09608b-b787-4408-a6cf-d499009bc971 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=041a1fa3-ad0d-4abe-8e63-5686a1c50a13 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=0d0f458d-7c0c-44be-8a1d-2a373814a790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

#encrypted drive
#/dev/mapper/minux_files /media/archivos_local ext4 defaults 0 2
/dev/mapper/test /mnt/tmp ext4 defaults 0 2
/etc/crypttab:

> # <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
test /dev/sdb1 none luks,retry=1


Rather long post but I guess I had to since you insist on look at those config files.  I'm only wondering if having 2 encrypt partitions might affect my distro? The only thing I can think of is that it's not getting mapped because i'm not getting prompted for my key phrase at boot time.

---

### Post by MJBoa on 2010-02-28
I've been having a very similar problem myself. I was following this guide:
[http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/](http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/)

Now the only difference there seems to be that he's got the libpam-mount package installed. You might try installing that.

Take a look at my equally frustrating topic.
[http://ubuntuforums.org/showthread.php?t=1413808](http://ubuntuforums.org/showthread.php?t=1413808)

---

### Post by bodhi.zazen on 2010-02-28
fstab :

change

/dev/mapper/cryptswap1 none swap sw 0 0

to 
```
/dev/mapper/cryptswap1 swap  swap  defaults  0 0
```

Your lines in crypttab also appear off.

change 

cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
test /dev/sdb1 none luks,retry=1

should read

```
cryptswap1 /dev/sda5 none luks,retry=1
test /dev/sdb1 none luks,retry=1
```

Then update initrd again (I assume you know that command)

---

### Post by tucemiux on 2010-03-01
> **bodhi.zazen said:**
> fstab :

change

/dev/mapper/cryptswap1 none swap sw 0 0

to 
```
/dev/mapper/cryptswap1 swap  swap  defaults  0 0
```Your lines in crypttab also appear off.

change 

cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
test /dev/sdb1 none luks,retry=1

should read

```
cryptswap1 /dev/sda5 none luks,retry=1
test /dev/sdb1 none luks,retry=1
```Then update initrd again (I assume you know that command)


Thank you for all the help, at least I have an idea of what is going on, my partition is not getting mapped at boot time.

Do you have an encrypted "/home" partition?  My home partition is in the first hard drive, /dev/sda5.  I first formatted my hard drive then I did the install, when I installed ubuntu studio I chose the option to encrypt my "/home" directory and everything works.  When I boot up into my laptop using a USB thumb drive I cannot access my "/home" partition because it is encrypted.  The install works fine.  

I'm just wondering why I would need to change those settings that you asked me to change since they're working fine.  I would have to back up my settings first before I try that.

---

### Post by bodhi.zazen on 2010-03-01
> **tucemiux said:**
> Thank you for all the help, at least I have an idea of what is going on, my partition is not getting mapped at boot time.

Do you have an encrypted "/home" partition?  My home partition is in the first hard drive, /dev/sda5.  I first formatted my hard drive then I did the install, when I installed ubuntu studio I chose the option to encrypt my "/home" directory and everything works.  When I boot up into my laptop using a USB thumb drive I cannot access my "/home" partition because it is encrypted.  The install works fine.  

I'm just wondering why I would need to change those settings that you asked me to change since they're working fine.  I would have to back up my settings first before I try that.


In your first post you are talking about using LUKS.

however, when you perform an installation, and use the "encrypt home" option, you are not using LUKS to mount home. When using this option at the time of installation you are using ecryptfs.

See:

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by tucemiux on 2010-03-01
> **bodhi.zazen said:**
> In your first post you are talking about using LUKS.

however, when you perform an installation, and use the "encrypt home" option, you are not using LUKS to mount home. When using this option at the time of installation you are using ecryptfs.

See:

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)


My home directory works just fine please do not go off tangent here.

That is why I didn't want to post my "fstab" and "crypttab" file, because it contains settings that were configured automatically when I installed ubuntu studio.  This post has nothing to do with my encryption on my "/home" directory.

As I mentioned, my installation works just fine, I have a dual boot,  a "/" partition, and a "/home" partition.  "/home" is encrypted and I did this when I installed ubuntu studio - it works fine! That is my original set up.

I recently installed a second hard drive and created 2 partitions.  I want to use this hard drive to store all my data but I want to encrypt the first partition, which is /dev/sdb1.

Now, from what youre telling me, I can't use ecryptfs and LUKS on the same installation?  Do they conflict with each other? Or why would you want to mention the encryption on my "/home" partition, I hope I'm being clear and not confusing you.

My goal here is to encrypt the first partition on my second hard drive which is /dev/sdb1.  I want to be able to just boot up into my machine, I think I have to type my passphrase and then when I login I want to be able to use the encrypted partition without having to manually mount it.  Is this possible?  It seems I have to manually mount it all the time either through the command line or through the GUI by clicking on "places->59 GB Encrypted" and typing my user password.

---

### Post by bodhi.zazen on 2010-03-01
I guess I am not understanding what you want to do exactly.

You may of course use LUKS and  ecryptfs at the same time.

I think I am getting confused because you keep mentioning your home partition.

In terms of LUKS and /dev/sdb1 you have several options. You can use a key file or you can configure LUKS to ask for a password as you boot or you can manually mount it.

I gave you instructions for how to configure your system to use /dev/sdb1 with LUKS to ask for a password as you boot.

What step did not work ?

If you are not getting asked a password as you boot, it will help if you post your configuration for LUKS. If you do not want to post the information for your home partition, do not post it, lol.

In order to provide specific assistance you need to give specific information.

What are you trying to do ?

In the instructions I gave you, is there something or some step you do not understand ?

Are you using LVM ?

What partition are you tryign to mount how, and what are the configuration files for such a partition ?

Did you update initrd ? 

What are the configuration options for initrd ?

As I said, it is working as expected here and I suspect there is a problem with your syntax.

---

### Post by tucemiux on 2010-03-02
We are getting somewhere with the pieces of information here and there.

I want to state the problem again:

-->My encrypted partition is not getting mapped at boot time.

You mentioned if I'm not getting prompted for a password.

-->My partition is encrypted, at boot time I am not being asked for a password, as a result my encrypted partition is not getting mapped.

It looks like this is a bug, I might have to file a bug report but I would like to get your input before I do that.  I was able to figure out my partition wasn't getting mapped with all the directions that you gave me.

But if you would like for me to clarify my problem here it is again.  Before I do here are a few givens:

-->
My goal here is to encrypt the first partition on my second hard drive which is /dev/sdb1

-->followed this guide: [http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

I already posted my "/etc/fstab" and "/etc/crypttab", what other config file would you like to look at?  

I told you about my "/home" partition because you asked me to make config changes that would affect my "/home" partition, you mentioned the settings were a bit off.  
-->ican please tell me why I need to make config changes that will affect my "/home" partition"?

You told me LUKS and ecryptfs can be used at the same time.

My "/home" directory is encrypted using ecryptfs, it was done automatically when I installed ubuntustudio. I dont want to change the settings on it but if I need to make the changes I will, I just want to make sure that you know why the configuration is there in the first place.  Since it's already working I dont want to change it but if will cause a conflict I will change it, I dont want to hose my distro again though, I already hosed it once while making a change to my "fstab", when I booted up I would wait for the encrypted partition to get mounted endlessly, good thing "/" is not encrypted otherwise I wouldve been a pain to fix it.

Last but not least.

I followed your guide: 

[http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

I am able to encrypt the drive.  The problem is when I shutdown my laptop and then I boot it up-- the partition  is not mounted automatically.  When I boot up my machine I am not being prompted for a password.  Like I told you before, I can manually mount the partition using the command prompt or by using the GUI, by clicking on "places-->[encrypted_harddrive].  

What I want to do is to boot up my laptop and I want the partition to be mounted already.

---

### Post by MJBoa on 2010-03-02
So you have a luks encrypted drive you want mounted at start up? There are basically two things you need to do.
Say you have a luks partition at /dev/sde1

Create a line in crypttab such as
```
crypted /dev/sde1 none luks
```

Create a line in fstab
```
/dev/mapper/crypted /mnt/crpyted ext4 defaults 0 0
```

Do you have such lines? You made it seem as if you already had these lines entered in and they just weren't working...

Also, you might need libpam-mount, but it seems like if you can mount the drive inside X, like from GNOME, it doesn't matter.

---

### Post by tucemiux on 2010-03-03
> **MJBoa said:**
> So you have a luks encrypted drive you want mounted at start up? There are basically two things you need to do.
Say you have a luks partition at /dev/sde1

Create a line in crypttab such as
```
crypted /dev/sde1 none luks
```Create a line in fstab
```
/dev/mapper/crypted /mnt/crpyted ext4 defaults 0 0
```Do you have such lines? You made it seem as if you already had these lines entered in and they just weren't working...

Also, you might need libpam-mount, but it seems like if you can mount the drive inside X, like from GNOME, it doesn't matter.

Again, I followed this guide: [http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

If you have any further questions you can look at the guide and my post #11.

Again, the problem is the encrypted partition is not getting mapped.

Meaning:

--->My encrypted partition does not show up in /dev/mapper 
      after I boot up my machine.

And yes, I have the lines that you are continously asking me to configure on my machine and kept asking me to post.  I know youre having a hard time believing that it's not working and whether I have the lines or not, you need to take a look at post #11 and your own guide.  For some reason it is not working on my machine.

Also, the lines you are asking me to enter in my "fstab" and "crypttab" file differ slightly from the ones in the guide.  The settings in the guideline seem more accurate and I used those, as you can verify from post #11.

What I am trying to figure out is:

  > Why is it my encrypted partition is not getting mapped at boot time?!?I followed your guide to the letter yet it's still not working, believe it or not.  The guide most likely is correct - I have seen other guides that are twice as long as yours and very difficult to read but your guide is clear, concise, and to the point - exactly what I want!  Unfortunately, it's not working on my machine.  

I installed libpam-mount, still no dice.

I am not getting prompted for my passphrase when I boot into my machine, you think that could be the reason my partition is not getting mapped a boot time?  How can I look at those logs that show when youre booting up your machine?

---

### Post by diHitoki on 2010-07-19
> **tucemiux said:**
> Again, I followed this guide: [http://ubuntuforums.org/showpost.php?p=8893525&postcount=5](http://ubuntuforums.org/showpost.php?p=8893525&postcount=5)

People are asking you to post your configurations because there may be an error in them. It has happened to me (even recently), and I've been administering Unix/Linux since 1991. It is not meant as an insult to your ability for following a written recipe. All information requested helps diagnose the problem. Once obvious errors are eliminated, we can look for deeper issues.

Regardless, while not Ubuntu, I've spent the last couple of days figuring out the way to get an encrypted RAID volume to mount at boot time on Fedora 13. I've written it up in a short blog post. You may or may not find it helpful:

[http://linuxfollies.blogspot.com/2010/07/software-raid-encrypted-volumes-and.html](http://linuxfollies.blogspot.com/2010/07/software-raid-encrypted-volumes-and.html)

---

