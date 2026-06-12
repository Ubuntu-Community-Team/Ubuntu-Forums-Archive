---
title: "Hard Drive Encryption in Ubuntu - How Do I Upgrade or Reinstall OS?"
date: 2008-03-20
forum: Security Discussions
---

### Post by MountainX on 2008-03-20
I set up my system as per this guide:

[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

/boot is unencrypted
everything else is in an LVM partition in the encrypted partition.

After I had it set up, an upgrade didn't go well and I could not boot up. I had to reinstall.  If this situation were to happen again, would it be possible to recover the encrypted data? 

When using an encrypted file system, how do you deal with OS disasters without losing data?

And when it comes time to upgrade to Hardy, how will I do it? When I start the install, it doesn't give me an option to use the existing encrypted partition.

---

### Post by jpkotta on 2008-03-20
> **MountainX said:**
> 
When using an encrypted file system, how do you deal with OS disasters without losing data?

And when it comes time to upgrade to Hardy, how will I do it? When I start the install, it doesn't give me an option to use the existing encrypted partition.

Make backups.  In your case, probably encrypted backups, but maybe you'll want to use a different method, like maybe truecrypt.

As for upgrades, why not just do an upgrade instead of reinstalling, which is what it sounds like you're intending to do.  In theory, it's almost the same as "sudo aptitude upgrade".  On my old machine, I originally installed Hoary and never made a fresh install, all the way up to Feisty.  Obviously, there may be some caveats for encrypted disks, but I would assume not.

BTW, my upgrade method is to download the alternative CD, and upgrade from a running system (not boot from the CD).

---

### Post by MountainX on 2008-03-21
Thank you.

Backups, of course, are necessary to recover from the worst disasters, but I was hoping there was also another option also. 

If I happen to automatically download a kernel update that doesn't go smoothly, it sure would be nice to have a recovery option besides a full restore from backup.

And in regard to upgrades, that would be my preference. However, many people say that they can be problematic. But I'm realizing that with a fully encrypted file system, there are fewer options.

Is there no way to boot up into a recovery mode (maybe using a CD even) and access the encrypted partitions with the correct password?

---

### Post by tact on 2008-03-21
Hi there..  I cannot answer all your questions but can give some insight into living with HDD encryption in ubuntu.

1.  Forget about truecrypt.  :)

2.  I installed my laptop from alternate installer and encrypted everything at install.  (except /boot of course)

3.  Then I cloned my laptop's HDD to an external USB drive so I would have a complete, bootable, disaster recovery option.  

4.  Then periodically I plug the external cloned drive into my laptop and use rsync to do incremental backups.

It works well.  Whenever I plug in the external drive (encrypted as per the internal drive) my ubuntu system recognises that there is an encrypted volume on the external drive and prompts me for the passphrase.  With that entered then I can mount the partitions (LVs) just like any unencrypted USB drive and do my incremental backups.

How to upgrade?  Well the night before last I did a "dist-upgrade" online and upgraded my system from Gutsy to the current Hardy Alpha6 release.   No problems.  The encrypted nature of the LVs was transparent to the system.

I have never had to boot from CD and do a reinstall that way.  I am not sure if/how it will work but just in case i have set up the LV's on the encrypted volume such that /home is on its own LV.  Hoping, of course, that if I need to reinstall the OS I can do so without losing the data in the separate /home partition.    Not sure if it works.... if not then I have the clone HDD as my back up... the fall back plan being to reinstall completely and then copy /home back from the cloned drive.  I know that works.

---

### Post by MountainX on 2008-03-21
> **tact said:**
> 

I have never had to boot from CD and do a reinstall that way.  I am not sure if/how it will work but just in case i have set up the LV's on the encrypted volume such that /home is on its own LV.  Hoping, of course, that if I need to reinstall the OS I can do so without losing the data in the separate /home partition.   .

Thanks for all the feedback and tips. I learned some helpful things. In regard to your point quoted above, I suspect it will not work because after installing the new OS, this new OS will not be able to decrypt your separate encrypted /home partition -- at least that's my guess based on what I've been reading. I haven't tried it yet.

---

### Post by MountainX on 2008-03-21
> **tact said:**
> . if not then I have the clone HDD as my back up... the fall back plan being to reinstall completely and then copy /home back from the cloned drive.  I know that works.

Actually, this point concerns me as well. I think the only reason you can access the encrypted data on the clone HDD is because it was made with your current installation. If you install a new OS, I have a feeling you will not be able to decrypt the clone HDD. Hopefully someone else can step in and tell us if this is correct. It certainly is one of my big concerns.

When I reinstalled my OS, I could not decrypt the encrypted partitions on my HDD and this sounds like the same scenario you will face with your clone HDD. I think your backup could be worthless. Hopefully I'm wrong.

---

### Post by tact on 2008-03-21
> **MountainX said:**
> Thanks for all the feedback and tips. I learned some helpful things. In regard to your last point, I suspect it will not work because after installing the new OS, this new OS will not be able to decrypt your separate encrypted /home partition -- at least that's my guess based on what I've been reading. I haven't tried it yet.

I suspect as much myself.  I read somewhere that its in the future that the option to do full HDD encryption will be added to the LiveCD install.  I guess once thats in place then we will have the mechanism to recognise encrypted partitions at new/reinstall time.

As mentioned I am not sure if that facility is available when booting from alternate installer CD.but suspect not at this time.

---

### Post by tact on 2008-03-21
> **MountainX said:**
> Actually, this point concerns me as well. I think the only reason you can access the encrypted data on the clone HDD is because it was made with your current installation. If you install a new OS, I have a feeling you will not be able to decrypt the clone HDD. Hopefully someone else can step in and tell us if this is correct. It certainly is one of my big concerns.

When I reinstalled my OS, I could not decrypt the encrypted partitions on my HDD and this sounds like the same scenario you will face with your clone HDD. I think your backup could be worthless. Hopefully I'm wrong.

Well as I wrote I know that does work.  I have done it a few times...

i.e.  I have completely formatted and reinstalled to the internal HDD a few times now and the final step is always - plug in the encrypted clone HDD and copy /home back to the internal HDD.   

Works perfectly.

---

### Post by MountainX on 2008-03-21
> **tact said:**
> 
3.  Then I cloned my laptop's HDD to an external USB drive so I would have a complete, bootable, disaster recovery option.  


Now that I understand you have had success with this, I think I'll do the same thing. What software did you use to clone your HDD? I would love to use dd, but I'm told it won't work if source and target HDDs aren't exactly the same size...

---

### Post by tact on 2008-03-21
> **MountainX said:**
> Now that I understand you have had success with this, I think I'll do the same thing. What software did you use to clone your HDD? I would love to use dd, but I'm told it won't work if source and target HDDs aren't exactly the same size...

I used dd as I had same size drives.  You can still use dd if the destination drive is larger than source.   It takes FOREVER tho.... 120Gb drive takes about 6hrs to clone with dd.

---

### Post by tact on 2008-03-21
If you do use a sector copier such as dd to clone a HDD (and I suppose this goes for other sector copiers also) you will also clone the UUID's of any partitions.

Of course that makes the UUIDs no longer "unique".   This is not a problem if all you ever do is keep the cloned drive in a drawer until the day you want to put it in a PC and boot from it.

It is a problem if you intend to do what i like to do - and thats install the cloned drive in a USB enclosure and be able to plug in into the original system for any reason (like doing incremental backups).   Reason its a problem is that you then have more than one partition with the same (supposedly) unique ID (UUID).

Search these forums...  I wrote extensively in another thread  how to do the clone, then manually change the UUID's on the cloned partitions so that there is no duplication of UUID.

---

### Post by MountainX on 2008-03-21
> **tact said:**
> 

Search these forums...  I wrote extensively in another thread  how to do the clone, then manually change the UUID's on the cloned partitions so that there is no duplication of UUID.

Is this the post you are referring to?
[http://ubuntuforums.org/showthread.php?t=679144](http://ubuntuforums.org/showthread.php?t=679144)

UPDATE: I found another related post:
[http://ubuntuforums.org/showthread.php?t=678629](http://ubuntuforums.org/showthread.php?t=678629)

---

### Post by tact on 2008-03-21
> **MountainX said:**
> Is this the post you are referring to?
[http://ubuntuforums.org/showthread.php?t=679144](http://ubuntuforums.org/showthread.php?t=679144)

UPDATE: I found another related post:
[http://ubuntuforums.org/showthread.php?t=678629](http://ubuntuforums.org/showthread.php?t=678629)

Ya either of those will do.

---

### Post by tact on 2008-03-21
> **MountainX said:**
> Actually, this point concerns me as well. I think the only reason you can access the encrypted data on the clone HDD is because it was made with your current installation. If you install a new OS, I have a feeling you will not be able to decrypt the clone HDD. Hopefully someone else can step in and tell us if this is correct. It certainly is one of my big concerns.

When I reinstalled my OS, I could not decrypt the encrypted partitions on my HDD and this sounds like the same scenario you will face with your clone HDD. I think your backup could be worthless. Hopefully I'm wrong.

Oh btw...  I installed hardy heron alpha 6 last week, and it has now autoupdated to the Hardy beta...  so the system on the internal (encrypted)  HDD is different to the gutsy system installed on the (encrypted) backup drive (which was a clone of the original).

I just plugged the external drive in to test i can still access it - and no problems.  I was prompted for the disk encryption passphrase as soon as I plugged in the USB cable and could mount the encrypted LVs

So now I am running the Hardy beta on my internal (working) laptop drive but have the security of a full back up drive (also bootable if the worst should happen to the working drive) installed with a snapshot of my Gutsy installation just before Hardy install.

I will do as I did last time when migrating from Edgy to Feisty and Feisty to Gutsy:
- incremental backups of just my data files from the internal Hardy drive to external Gutsy  (both encrypted and accessed as above)

- once the Hardy beta runs it course and in time becomes the release version of Hardy Heron (through daily updates)...  and once i am satisfied it is stable etc then I will clone that drive.  Move to Hardy complete.  :)

Using this methodology I only go thru the "pain" of a 6hr cloning exercise twice a year (after each new ubuntu release).

---

### Post by MountainX on 2008-03-26
> **tact said:**
> 
As mentioned I am not sure if that facility is available when booting from alternate installer CD.but suspect not at this time.

I just tested this. I had a fully encrypted Gutsy system and I used the Hardy alternate CD to install Ubuntu Hardy beta. The installer did not recognize the existing encrypted partition. I was forced to blow everything away and make new encrypted partitions.

---

### Post by MountainX on 2008-03-26
> **tact said:**
> e i have set up the LV's on the encrypted volume such that /home is on its own LV.  Hoping, of course, that if I need to reinstall the OS I can do so without losing the data in the separate /home partition.    Not sure if it works....

I'm curious about your setup. It sounds different from mine. I create on physical partition and encrypt the entire partition. Then inside that encrypted partition  I create one LV Group. In that I create multiple partitions (root, swap and home). In this way only one password is required.

However, I do not believe it is possible to salvage /home while reinstalling an OS to root (from a CD install) with this setup.

The alternative would be to start by creating two physical partitions and encrypting them both separately. This should work in a very similar manner to the way your external USB drive works with regard to a new OS being able to decrypt data on the pre-existing /home partition. The drawback is that one must enter two passwords to decrypt the HDD every time the computer boots up.

There is a way to use keyfiles instread of passwords, but it may introduce a security risk. Here is where I learned about it:
[http://ubuntuforums.org/showthread.php?t=732069](http://ubuntuforums.org/showthread.php?t=732069)

tact, do you have another approach to separating the /home partition without requiring two HDD encryption passwords at boot up?

---

### Post by hyper_ch on 2008-03-26
I had my system already encrypted in feisty and running the update manager to gutsy did work well... had no problems with my dm_crypt/luks partitions - but I did not use lvm - meanwhile I'm also on gutsy for quite some time...

---

### Post by tact on 2008-03-26
> **MountainX said:**
> I'm curious about your setup. It sounds different from mine. I create on physical partition and encrypt the entire partition. Then inside that encrypted partition  I create one LV Group. In that I create multiple partitions (root, swap and home). In this way only one password is required.

However, I do not believe it is possible to salvage /home while reinstalling an OS to root (from a CD install) with this setup.

The alternative would be to start by creating two physical partitions and encrypting them both separately. This should work in a very similar manner to the way your external USB drive works with regard to a new OS being able to decrypt data on the pre-existing /home partition. The drawback is that one must enter two passwords to decrypt the HDD every time the computer boots up.

There is a way to use keyfiles instread of passwords, but it may introduce a security risk. Here is where I learned about it:
[http://ubuntuforums.org/showthread.php?t=732069](http://ubuntuforums.org/showthread.php?t=732069)

tact, do you have another approach to separating the /home partition without requiring two HDD encryption passwords at boot up?

Nah nothing different in my setup.  It is as you describe.  Physical container encrypted, use LVM to set up a group and inside that separate LVs for /, /home, and swap.

I configured the separate /home because with an unencrypted HDD you can then reinstall without disturbing /home and purely,  optimistically, and perhaps foolishly hoped that perhaps the same thing can be done with encrypted HDD.   :)

I have heard that support for HDD encryption is planned at some time for the LiveCD installation method.  Perhaps then....

---

### Post by MountainX on 2008-03-26
I reinstalled again and went with a different setup.

Here are the details:

First, set up 2 encrypted partitions and 1 boot partition. All are primary.
Then, in 1 encrypted partition, use LVM and set up two partitions: root and swap
Finally, in other encrypted partition set up /home.

There are 4 total Linux partitions, one of which is /boot. The boot partition will not be encrypted, but the other 3 will. 

There are ways to set up all these partitions so that only 1 HDD encryption password is required. A good guide is here: [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html). The problem with that method is discussed in this thread. To summarize the problem, reinstalling the operating system from a CD requires wiping out all the data on the encrypted partition. You cannot, afaik, take advantage of the separation of data into the /home partition. A requirement for me is to be able to utilize the separate home partition so that I could reinstall the OS without touching my data if needed.

Without using the method just described, one might end up having to enter 3 HDD encryption passwords to boot up. That would be way too inconvenient for me. A compromise of using two HDD encryption passwords is something I can live with. (And I will probably use keyfiles and an automated script so I don't actually have to enter the passwords. But given that I might have to manually enter the passwords at times, I felt that two passwords was still the limit for HDD encryption. Of course, the normal login password is also required in all scenarios I'm discussing.)

I used 2 encrypted partitions and I set one of those up to use LVM and then I created to logical volumes. That gives me 3 encrypted partitions (root, swap and home) with only 2 passwords. Not only is this the best compromise for me, it is also about the only choice I had because I have one NTFS partition on the HDD already. That means I could not have done this without LVM or logical partitions.

---

### Post by tact on 2008-03-26
Very interesting....  I am not going to look hard into it at the moment because with a totally separate HDD as backup I have the option to just reinstall and then copy over /home from the spare HDD

It would be nice to be able to just reinstall and not touch /home on an encrypted system.

On a purely theoretical tack - My first hand experience with having an fully encrypted (DM-crypt/LUKS, LVM) external HDD is that when I connect it to my system it is detected as encrypted (LVM and all) and I am prompted for the passphrase and it can then be mounted.

If all that works (hypothesising here) then...  Surely we can have the same work when booted from LiveCD (if the right modules like fuse etc are in the live kernel)/

If that works then the install process should also be able to identify, mount and work with (or leave alone) selected encrypted partitions/

---

### Post by hyper_ch on 2008-03-27
> **tact said:**
> It would be nice to be able to just reinstall and not touch /home on an encrypted system.

You can do that... just select manual partitioning.. make an encrypted / partition... once that's setup auto-mount with a key-file the /home partition later on...

---

### Post by tact on 2008-03-27
Actually when I installed my present setup I used the alternate installer and elected to use the manual setup....

I set it up very similar to the way it is done if you select auto and use whole disk - except for the separate /home.

So I know its possible to set up two separate partitions and encrypt separately.  But its added hoops to jump thru, need to enter two keys or play around with using usb keys etc.   Not where I want to go.

As I mentioned the system has pretty much all the functionality to recognise an encrypted disk, and the volume groups, and logical volumes etc that are on it.  (refer - that spare external drive I have that is a fully encrypted clone of the fully encrypted working drive and how whenever I plug the external drive in, it is recognised for what it is, I am prompted for the passphrase, and it is then mountable and useable).

If a running whole disk encrypted system can recognise another of the same when its connected via USB drive - then all the "bits" are there already.

All thats needed is for the LiveCD kernel and installer to be brought up to speed.  When/if that happens then I will use it and appreciate it for sure.

Until then - no sweat..   can live without it.  And while I agree with you it is possible to do a custom setup as a work around I dont need that enough to bother jumping thru the hoops.  :)

---

### Post by hyper_ch on 2008-03-27
> **tact said:**
> need to enter two keys or play around with using usb keys etc.   Not where I want to go.
Not really.. two passwords yet, but later on you can put the keyfile on your root partition and auto-load it from there... no need to enter twice a password or use usb stick..

---

### Post by MountainX on 2008-03-27
> **hyper_ch said:**
> Not really.. two passwords yet, but later on you can put the keyfile on your root partition and auto-load it from there... no need to enter twice a password or use usb stick..

Here is the method I used for putting a keyfile on the USB stick: [http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

What steps do you use for putting one keyfile on the root partition? Do you have a script?

---

### Post by hyper_ch on 2008-03-27
[http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)

Step 4-6 are the essential ones there... but have a read through all of it

---

