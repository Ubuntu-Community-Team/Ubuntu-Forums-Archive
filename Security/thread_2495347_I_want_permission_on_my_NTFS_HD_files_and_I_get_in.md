---
title: "I want permission on my NTFS HD files and I get input and output errors, help me"
date: 2024-02-15
forum: Security
---

### Post by mamp on 2024-02-15
I'm having a lot of difficulty accessing files on an NTFS HD with conflicting permissions


Entry and exit error
I already tried giving command:
1.
sudo cmod -R +777 /mnt/sdb1
and the Input and output error message


2. I entered root terminal and typed nautilus
Nautilus and navigated to the folder containing the files you are having problems with.
I right-clicked the folder and selected "Properties".
In the "Permissions" tab, I clicked "Change Permissions".
In the "Other Permissions" box, I checked the box next to "Create and delete files."
Click "OK" to save the changes.


but the input and output error message




How do I get back in possession of my files and written reading permissions and all files?

---

### Post by TheFu on 2024-02-15
Under Linux, NTFS doesn't support permissions.  The only method is to set permissions for the entire file system at mount time. Sorry.

chmod and chown don't work for NTFS file systems.

There is a "permissions" option for the NTFS file system driver, but it doesn't work.  A few years ago, I tested this specifically.  The permissions appeared to work for about a month - I don't use NTFS that much and seldom with multiple users, so I really didn't test more than a few days.  After about a month, it was clear that the permissions were gone.

If you need permissions to be supported, fully, use a native Linux file system like ext4 or f2fs.
[https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822](https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822) explains more and has example mount options.

---

### Post by mamp on 2024-02-15
I thought about switching to EXT4, would it be possible to convert?
HD that was used in conjunction with Windows. but Windows doesn't work.
Every version of Windows they want to dominate the permissions.


I even tried:


sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install ntfs-config


oh it did
Reading package lists... Done
Building dependency tree... Done
Reading status information... Done
E: Unable to find ntfs-config package

---

### Post by ajgreeny on 2024-02-15
To use the disk or partition as ext4 you would have to reformat it for which you can use gparted; you can not "convert" between NTFS and ext4 in any other way.

You would have to backup those files to some other disk or partition first as they will be deleted by the format operation.

---

### Post by TheFu on 2024-02-15
> **mamp said:**
> 
I even tried:


```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install ntfs-config
```



I have zero idea what programs ntfs-config may contain and I've never installed it on any of my systems the last 25+ yrs. Is it even a package?
[https://packages.ubuntu.com/search?keywords=ntfs-config](https://packages.ubuntu.com/search?keywords=ntfs-config) says, nope, confirming what my local **apt search** answered.

You've lost me completely.

---

### Post by mamp on 2024-02-15
The ntfs-3g driver allows read and write access to NTFS partitions. It should already be installed on most Linux distributions, including Ubuntu. You can check with the following command:


dpkg -l ntfs-3g


In Ubuntu Version 22.04.03 LTS it is already built-in. It works.
If you use Ubuntu it has been running since installation.


But the biggest challenge is having a data HD that Windows and Linux can read. But Windows is becoming very difficult, it is taking ownership of the files. And now on Linux they are disappearing even though they were there. And I can't change permissions.


I'm inclined to convert EXT4 to a very large operation, large HD. But will I be able to read these files later on Windows?

---

### Post by TheFu on 2024-02-15
> **mamp said:**
>  
But the biggest challenge is having a data HD that Windows and Linux can read. But Windows is becoming very difficult, it is taking ownership of the files. And now on Linux they are disappearing even though they were there. And I can't change permissions.

Permissions, owner, group for NTFS can controlled at mount time under Linux.  When you mount the file system, you must set the owner, group, and permissions you want in the mount options.  I don't know how to say it any clearer. Sorry.

For data that you want shared between Linux and Windows installed on the same computer, NTFS is, unfortunately, the best option.  The only other viable option is exFAT and it also requires mount options to be control the owner, group, and permissions.

If the file system won't mount under Linux, that's usually due to MSFT not properly closing the file system.  There are lots of how-to instructions for disabling that "feature" of MS-Windows.

---

### Post by mamp on 2024-02-15
Now you really left me with doubts.
I left the HD only with NTFS data and I always mounted the partition in Linux when mounting as you said.


But in the rare moments that I logged into Windows, it always tried to appropriate my files with permissions.


But I don't know how in the HD and partition setup you define permissions. If you have an article or link, I would appreciate it.


I'm inclined to move everything to EXT4 and leave a smaller transitional NTFS partition. I only use NTFS for what I use shared and when I return to Linux I switch to EXT4 and have more control over the files. What do you think. Laborious.


(I read something that you can try to read Windows files with EXT4 extensions only with little efficiency).

---

### Post by ajgreeny on 2024-02-16
About 20 years ago when I started using Ubuntu I did try the "driver" that was available for WinXP to read an ext# formatted disk.
It worked, but was very flaky and did not allow any writes to disk so was fairly useless for most things.

I have no idea if such things are still available though I would be surprised if there was not some way to do this, maybe even now to write to ext4 from Windows.

However be prepared for problems as Microsoft always seems to throw spanners in the works when it comes to this sort of cooperation.

---

### Post by The Cog on 2024-02-16
> Permissions, owner, group for NTFS can controlled at mount time under Linux. When you mount the file system, you must set the owner, group, and permissions you want in the mount options. I don't know how to say it any clearer. Sorry.

I would add that this is because NTFS is not able to store *nix ownership and permissions. Therefore, as part of mounting the disk, you tell the driver what owner and permissions you want to ***pretend*** that it has. But they are not real, and you can't change them. Trying to change them doesn't cause an error, but doesn't do anything either.

On top of this, if Windows doesn't to a full shutdown (i.e without "fast-start") then we know that Windows may have cached unwritten changes. In this case writing to the disk could conflict with Windows cached data, so Linux mounts the whole filesystem read-only to avoid causing disk corruption.

---

### Post by TheFu on 2024-02-16
> **mamp said:**
> But I don't know how in the HD and partition setup you define permissions. If you have an article or link, I would appreciate it.

See post #2. Link provided.

> **mamp said:**
> 
I'm inclined to move everything to EXT4 and leave a smaller transitional NTFS partition. I only use NTFS for what I use shared and when I return to Linux I switch to EXT4 and have more control over the files. What do you think. Laborious.

a) I don't dual boot.  I think it is a bad idea. Been burned badly a few times.  I have network sharing setup on Linux that Windows can access.
b) You can do whatever you like. It is your system. Heck, you ARE running MS-Windows on hardware (not inside a VM), which I wouldn't do either.

> **mamp said:**
> 
(I read something that you can try to read Windows files with EXT4 extensions only with little efficiency).

You can try lots of things.  That doesn't mean they work well.  I've never bothered.

---

### Post by mamp on 2024-02-16
I have had the same impression.
Microsoft has a package of evil things for users and no one notices.


MS has forced cloud packages to increase profitability but has access to all content made by users.
Using artificial intelligence, no one makes me suspect that it takes advantage of having access to such files.
(I discovered Windows logs, that MS was sending my entire files to her with telemetry support).


I feel like I used NTFS data HD well now it has prevented Linux from using it freely.


I'm inclined to go to EXT4 and not share it with Windows anymore. what a shame. And only use what I need, but it was great when I could use the same files on both operating systems, but MS is very aggressive with permissions.

---

### Post by mamp on 2024-02-16
Yeah, I've been feeling this. I thought about turning off Windows indexing.


but do you prefer EXT4 for your data? How do you share with Windows?

---

### Post by TheFu on 2024-02-16
>  but do you prefer EXT4 for your data? How do you share with Windows? 
I don't store data on MS-Windows.  I have 1 virtual machine used for taxes, stock investing, and business finances, nothing else. The data used by those programs is copied off ASAP.

I haven't read about any reports that MS and NTFS have changed storage stuff recently.  I watch that sort of stuff.  Most people would say that Unix is too picky about permissions, not NTFS.

---

### Post by mamp on 2024-02-18
ok I made changes to the HD after reading the comments from the links above.
I left a 10% HD common NTFS partition created from scratch and owned by me.
I believe rest EXT4 partition


In this partition, when auditing some files that were NTFS, I found traces of a virus or Windows itself trying to take ownership of my files.


When clicking on a file, properties and then calculations, I found files with encryption enabled HASH function (HMAC key). Some options activated. It was only possible when I left these files that were in NTFS on EXT4.


I'm thinking about using the command to remove all HMAC keys in all files when they have EXT4 and perhaps opting for Ubuntu Linux encryption.
This way I will no longer run the risk of anyone trying to take my files.
What do you think?

---

### Post by mamp on 2024-02-18
ok I made changes to the HD after reading the comments from the links above.
I left a 10% HD common NTFS partition created from scratch and owned by me.
I believe rest EXT4 partition


In this partition, when auditing some files that were NTFS, I found traces of a virus or Windows itself trying to take ownership of my files.


When clicking on a file, properties and then calculations, I found files with encryption enabled HASH function (HMAC key). Some options activated. It was only possible when I left these files that were in NTFS on EXT4.


I'm thinking about using the command to remove all HMAC keys in all files when they have EXT4 and perhaps opting for Ubuntu Linux encryption.
This way I will no longer run the risk of anyone trying to take my files.
What do you think?

---

### Post by TheFu on 2024-02-18
Encryption only works when the encryption container is closed and the computer is powered off. 

When the computer is on and the encrypted container is opened, normal file system risks to the data exist.  So, in reality, encrypted data really only works when the computer is off, but it is up to us to ensure it is truly off, like during transport.   

My rule is this.  I use whole drive encryption on my laptops and when I leave the house or take the laptop with me outside the building it is currently in, I shut it down completely.  No hibernation. No standby mode.  100% shutdown.  Carrying a laptop between classrooms inside the same building, I would just put it into standby mode.  It's all about risk mitigation.  In my mind, the chances of the laptop being stolen between rooms in the same building aren't sufficient to require shutting it down, but leaving a building adds many more risks, hence the need, in my mind, to shutdown the computer.  Since I lecture in only 1 building, it is even easier.  If I'm headed to the car, shutdown the computer.

YMMV.

BTW, use LUKS encryption on Linux, nothing else.  Pretty much all the others have data leak flaws in them or they aren't native to Linux and leave keys in RAM after the encryption container is opened.  If you open, use, then close an encryption container, are you 100% certain that the keys to unlock it aren't still in RAM somewhere?  I'm not.

---

### Post by mamp on 2024-02-18
Thanks. I will follow your suggestion.
I also prefer to turn it off now it will be routine.


What do you think of what I intend:
1. I'm removing my NTFS bakcup and switching to the EXT4 drive
2. remove all hmac keys first
3. 10% of NTFS share for common use Windows/Linux
4. 90% EXT4 with LUKS encryption on Linux.


If you have any links or articles to guide how to use LUKS encryption, I would be grateful.

---

### Post by mamp on 2024-02-18
Unfortunately I detected a virus in Windows.
I managed to isolate some .bat .ini files and text files that generated code.
I saw that this files had a pattern of trying to get permissions from my files.
I subscribed to Kaspersky antivirus, I sent at least 5 systematically detailed reports with contaminated files and my findings.
I sent an antivirus scan to Kaspersky support that I ran on Linux, proving that there were viruses on Windows.
Kaskpesky reduced it to saying that there was no virus and 6 months later he announced the discovery of a new virus that did exactly what he had described. Unfortunate..
Now Windows only reduces applications that cannot be run on Linux, but nothing but on Windows. Vulnerable, fragile system. To make matters worse, I discovered that MS telemetry sent my files to MS even though I opted for privacy and did not send any type of information to MS.
Okay, Linux is champion. Windows never again.

---

### Post by TheFu on 2024-02-19
> **mamp said:**
> Thanks. I will follow your suggestion.
I also prefer to turn it off now it will be routine.


What do you think of what I intend:
1. I'm removing my NTFS bakcup and switching to the EXT4 drive
2. remove all hmac keys first
3. 10% of NTFS share for common use Windows/Linux
4. 90% EXT4 with LUKS encryption on Linux.

I have no opinion on this and certainly no expertise.

> **mamp said:**
> 
If you have any links or articles to guide how to use LUKS encryption, I would be grateful.
During the install, there's a check box to enable encryption.  check it.  However, this will wipe the entire drive, so if you have only one HDD installed, anything on it will be wiped.  I don't dual boot.  I put other OSes inside virtual machines and have since around 2008 as a standard practice.  At work, we were required to use VMs for all systems beginning around 2002, unless there were specific requirements AND proof that those requirements couldn't be met from a VM.  I first started using VMs at work in 1998-ish, to run different versions of MS-Windows, usually with different native languages, as part of our testing setups.  The first time I saw MS-Windows in Mandarin and Japanese was a bit odd.  Latin-based languages wasn't too bad.

---

### Post by mamp on 2024-02-19
But the debate was great, I was now able to run successive commands in the folders and I regained ownership of my files in the EXT4 partition:


1. I had to remove read-only some folder
2. clear HMAC (encryption) on all files.


Yes, it is possible with the terminal command line to perform encryption without having to do it only during installation and without losing files. I remember the commands, I just have to search again.


Unfortunately, my work does not allow using VMs, because I need digital certification with a chain of certificates to meet deadlines using MS's proprietary encryption (MSCAPI).


Official bodies require this. But when I have time I will buy a bigger hard drive and test digital certificates and hierarchy chains on the VM. But I really can't help but meet government deadlines. I am forced to maintain dual boot.

---

### Post by ajgreeny on 2024-02-20
Great!

If you're now happy that this is solved for you please use Thread-Tools menu at the top to mark the thread as SOLVED.

It is a great help to other users searching the forum.

---

### Post by mamp on 2024-02-20
But the debate was great, I was now able to run successive commands in the folders and I regained ownership of my files in the EXT4 partition:


1. I had to remove read-only some folder
2. clear HMAC (encryption) on all files.


Yes, it is possible with the terminal command line to perform encryption without having to do it only during installation and without losing files. I remember the commands, I just have to search again.


Unfortunately, my work does not allow using VMs, because I need digital certification with a chain of certificates to meet deadlines using MS's proprietary encryption (MSCAPI).


Official bodies require this. But when I have time I will buy a bigger hard drive and test digital certificates and hierarchy chains on the VM. But I really can't help but meet government deadlines. I am forced to maintain dual boot.

---

### Post by mamp on 2024-02-21
I always wanted to use the official canonical forum a lot.
but I find navigation extremely difficult.


I already looked for the resolved button, I didn't find it, just "not resolved".


Site needed to simplify navigation. Very difficult.

---

