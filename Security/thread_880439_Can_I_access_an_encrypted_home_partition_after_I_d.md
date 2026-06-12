---
title: "Can I access an encrypted /home partition after I do a clean install of Ubuntu?"
date: 2008-08-05
forum: Security
---

### Post by MountainX on 2008-08-05
I just want to be sure about this before I proceed. I know there has been some discussion on this topic, but I have to clarify it further.

**Can I access an encrypted /home partition after I do a clean install of Ubuntu?**

Scenario:
I have /home on a separate partition. It was encryted using the tools provided at install time from the alternate CD (server, actually). I also have / encrypted. 

Say I am forced to reinstall the OS. Once I complete that reinstall, can I access the encrypted /home? If so, is it simply a matter of providing the password for the encrypted volume?

Thanks

---

### Post by AusIV4 on 2008-08-05
Assuming you make sure not to write over the encrypted partition, it should still be accessible after a reinstall.

Note that the default installation doesn't come with cryptsetup, so you'll have to install it from the repositories, and modprobe dm-crypt before you'll be able to mount the disk.

---

### Post by MountainX on 2008-08-05
> **AusIV4 said:**
> it **should** still be accessible after a reinstall.


Thank you, but just to clarify. Are you **guessing** that it ***should*** be accessible...

 **or** are you saying that it ***will*** be accessible provided I don't overwrite anything?

---

### Post by hyper_ch on 2008-08-05
if you don't overwrite it you can access it later. You'll have to manually set it up in crypttab and fstab.

---

### Post by tact on 2008-08-05
I wrote a reply to the OP's other question/thread here:
[http://ubuntuforums.org/showthread.php?p=5532104#post5532104](http://ubuntuforums.org/showthread.php?p=5532104#post5532104)

...which discussed some limitation in using cloned encrypted HDD's (duplicated VG names on cloned drive (or img) causing problems connecting the clone drive to the original system).   There are possibly ways to overcome this but i have not explored there much yet - and thats a different thread.

In that post I mentioned that my laptop drive did have a bit of a disaster last week.  It was unbootable.  But i was able to swap drives (put the clone into the laptop and take the original drive and slot it into an external USB drive)...eventually copying back all my data, thus not losing anything, but had to jump thru some hoops to avoid the duplicated VG name problem.

Now to the current topic -  Last night I spent a few hours trying to see if I could resuscitate the crashed drive by reinstalling /boot and /root but keep /home as it is.

(Yes - I have "/home" on its own LV - hoping that one day I would learn whether I can reinstall my system and not lose whats in /home)

So attempt 1:
-  put the unbootable drive back into the laptop drive bay.
-  booted up alternate installer
-  selected install ubuntu... go thru all the initial steps.  get to the partitioner.  No options there that would preserve /home.  Basically can only start clean.

Attempt 2
-  boot up alternate installer again
-  select "rescue a broken system"
-  after choosing language, tz, hostname, etc guess what!?
-  was prompted for the passphrase of the encrypted partition /dev/sda5
-  after entering passphrase had options to open up root terminal.  Press "esc" a few times and you are at the installation menu...  Try to do anything past "partition disks" (e.g. reinstall grub) and you are bounced back to the disk partitioner.  So have to do that first.
-  in the disk partitioner all the LVM partitions are recognised.  Just need to go thru each one to set the file system (ext3) and mount point.  Chose to format /boot and / but NOT format /home.

It seemed to all go well...  installation proceeded as normal.  Right to the point of ejecting the CD and rebooting.  Excellent... (I thought).

When booting the system goes thru GRUB just fine and the splash screen comes up but hangs there...  no prompt to enter passphrase for the encrypted volume.

I reinstalled a few times but stuck at the same point each time.  I did a clean new install to be sure there is no problem with the HDD and that worked fine.  Attempting to just reinstall the OS (even on the fresh clean install) also sticks at the same point - no prompt for passphrase for encrypted volume.

I guess what hyper_ch suggests is required...  manually changing crypttab etc.  But I have no idea how to do that at this stage.   Maybe in the next week I will contimue the experiment on the spare drive.

Cheers

---

### Post by MountainX on 2008-08-05
> **tact said:**
> 

I guess what hyper_ch suggests is required...  manually changing crypttab etc.  But I have no idea how to do that at this stage.   

look at /etc/crypttab
```
/etc$ sudo cat crypttab
```

You'll see rows like this:

sdd2_crypt /dev/disk/by-uuid/xxxxxx keyfile.key luks,keyscript=/usr/local/sbin/keyscript.sh

My plan is to keep a backup copy of /etc/crypttab so I can restore the uuid for my encrypted volumes. It sounds like you may know your existing uuid's. Just give your device the proper mapper name (e.g. sdd2_crypt), put in the uuid, use "none" for keyfile (without quotes) and leave off the shell script if you don't have one.

Here's an example:
```
sd*X*_crypt /dev/disk/by-uuid/*YOUR-UUID-HERE* none luks

```

---

### Post by hyper_ch on 2008-08-06
Have a look at my howtos:

Here step IX: [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

and if you ahve encrypted your system fully and only want to enter the password once:
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by MountainX on 2008-08-06
> **hyper_ch said:**
> Have a look at my howtos:
Here step IX: [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)


Your "legal considerations" section is excellent! Thanks for that.

Do you know how much of your Feisty technical details still apply to Hardy? Not much of it matches for me. For example, in my install of 8.4.1 the modules are completely different from those that you mention.


> **hyper_ch said:**
> 
and if you ahve encrypted your system fully and only want to enter the password once:
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

Have you seen this guide? 
[http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM](http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM)
It is very up to date for Hardy and it has a lot of details.

---

### Post by hyper_ch on 2008-08-06
it all applies except you don't have to load the modules anymore.

---

