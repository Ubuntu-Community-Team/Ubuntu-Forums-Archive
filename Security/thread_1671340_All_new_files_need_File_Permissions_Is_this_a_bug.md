---
title: "All new files need File Permissions? Is this a bug?"
date: 2011-01-19
forum: Security
---

### Post by nrundy on 2011-01-19
I have my HOME folder set to file permissions as such: 

drwx------ 
Owner:rwx, Group:---, Others--- 

I clicked "Apply permissions to enclosed files" after setting these parameters. Checking individual files and folders within the HOME folder afterwards confirmed these permission settings were active. Yet everytime I add a new file to the HOME folder, the new file contains one of two file permission settings, either: -rwxr--r-- or -rwxr-xr-x. Shouldn't new files added to the HOME folder automatically adopt the file permission settings for the parent folder (i.e., the HOME folder)?

Is there a setting I'm missing, or is this a massive bug?

---

### Post by Dave_L on 2011-01-20
> **nrundy said:**
> Shouldn't new files added to the HOME folder automatically adopt the file permission settings for the parent folder (i.e., the HOME folder)?

No. Linux file permissions don't work that way.

You need to change the file mode creation mask with the "umask" command.

But if your top-level home directory has permissions 700, then only your user (and root) will be able to access that directory's subdirectories. Forcing all the files and subdirectories to have 700 permissions too is unnecessary. (If I'm wrong about this, please correct me.)

---

### Post by bodhi.zazen on 2011-01-20
You can change the default umask value by editing ~/.bashrc ;)

---

### Post by FuturePilot on 2011-01-20
> **Dave_L said:**
> 
But if your top-level home directory has permissions 700, then only your user (and root) will be able to access that directory's subdirectories. Forcing all the files and subdirectories to have 700 permissions too is unnecessary. (If I'm wrong about this, please correct me.)

This is correct.

---

### Post by FuturePilot on 2011-01-20
> **Dave_L said:**
> 
But if your top-level home directory has permissions 700, then only your user (and root) will be able to access that directory's subdirectories. Forcing all the files and subdirectories to have 700 permissions too is unnecessary. (If I'm wrong about this, please correct me.)

This is correct.

---

### Post by nrundy on 2011-01-24
So even though a file within the username folder has permissions that allow other users to see it and write to it, is this folder private to only the user who's folder it resides in?  I don't understand the permissions 700 talk you guys engaged in. Sorry. I'm assuming there is an option to change the permissions setup but it sounds like it isn't necessary (or desirable)?

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> So even though a file within the username folder has permissions that allow other users to see it and write to it, is this folder private to only the user who's folder it resides in?  I don't understand the permissions 700 talk you guys engaged in. Sorry. I'm assuming there is an option to change the permissions setup but it sounds like it isn't necessary (or desirable)?

See : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by Morbius1 on 2011-01-24
> **nrundy said:**
> So even though a file within the username folder has permissions that allow other users to see it and write to it, is this folder private to only the user who's folder it resides in?  I don't understand the permissions 700 talk you guys engaged in. Sorry. I'm assuming there is an option to change the permissions setup but it sounds like it isn't necessary (or desirable)?
"700" is the octal representation of the permissions of a file or directory.

The first digit represents the owner.
The second digit represents the group.
The third digit represents everyone else.

It can be given different numerical values:
"0" - no access
"1" - Execute ( for a folder it represents the ability "to open" the folder to see what's inside )
"2" - Write
"4" - Read

They are additive so a 7 is full access ( 1+2+4).

When you try to access a specific file you are actually going through the entire path to get there. So if you have a file test.txt that resides in say .. /home/morbius/test.txt and you set /home/morbius to 700 then only morbius has the ability to open the "morbius" folder to access what's inside.

---

### Post by uRock on 2011-01-24
Or, you can alternate-click the folder, click **properties**, then click on the **permissions tab** and change **Group** and **Others** permissions to **None**, then click the button to **Apply Permissions to Enclosed Files**. Doing this will block others from seeing and accessing your files from another account.

Almost everything in Ubuntu has a GUI way to do things.

---

### Post by vanadium on 2011-01-24
There is no objection to set the files of your home directory to 700, if you desire this level of privacy.

---

### Post by nrundy on 2011-01-24
Thanks for all this info, guys. You've been a great help in my education :)

vanadium, do you know a situation where it would be desirable to have the file permissions extend all the way to the files? I'm just curious for my own learning. I figure each way as pluses and minuses. Anybody know why Ubuntu doesn't extend 700 to file permissions by default? What is the advantage of not doing it?

---

### Post by vanadium on 2011-01-24
It is just a choice. It is the level of privacy you choose.

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> Thanks for all this info, guys. You've been a great help in my education :)

vanadium, do you know a situation where it would be desirable to have the file permissions extend all the way to the files? I'm just curious for my own learning. I figure each way as pluses and minuses. Anybody know why Ubuntu doesn't extend 700 to file permissions by default? What is the advantage of not doing it?

Most files do not need to be executable, only scripts.

So 600 is, IMO, most appropriate for most files.

In terms of 700 / 770 / 777 600 / 660 / 640 etc up to you and how much privacy / security you feel you need. I keep most files on a web server 440 .

---

### Post by nrundy on 2011-01-24
Within my /Home/username folder, what programs **[COLOR=black]need[/COLOR]** to be exe? 

Bodhi did you change file permissions so that files inherit the parent folder permissions? Like I posted earlier some files get created by default with exe powers. Files that don't need exe. Forcing files to inherit parent folder permissions would solve this. I'm wondering if maybe I should switch the permission config afterall.

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> Within my /Home/username folder, what programs **[COLOR=black]need[/COLOR]** to be exe? 

Depends on what you do. I keep scripts in $HOME/bin, and scripts need to be marked as executable (well not really ...)

As has been pointed out, it sort of depends on what you are doing.

In general, no files in $HOME need to be marked as executable.

> Bodhi did you change file permissions so that files inherit the parent folder permissions?

Why would I do that ? Permissions on directories are not the same as permissions on files.

See the link I gave you on Linux permissions for details.

The "linux method" of setting permissions of files is to use umask.

You can temporarily set a umask value from the command line or long term from ~/.bashrc

There is not single answer to your questions, it all depends on a number of variables.

You simply need to read and learn permissions. Is there some problem with the default behavior ? The default are sufficient for most people =)

---

### Post by nrundy on 2011-01-24
No problems. It seems that it would be more secure to not have files default being executable though. For example I copied a jpg file from USB and it defaulted at rwx. If it defaulted to parent settings it would only be r--. Seems more secure to me, that's all.  I'll read the umask thing.

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> No problems. It seems that it would be more secure to not have files default being executable though. For example I copied a jpg file from USB and it defaulted at rwx. If it defaulted to parent settings it would only be r--. Seems more secure to me, that's all.  I'll read the umask thing.

That is because you are copying a file from a FAT or NTFS partition (I am guessing).

1. cp (copy) != new file (see man cp ).

2. Assuming it is a FAT / NTFS, permissions of files and directories are all 777. To change this you need to see man mount =)

---

### Post by nrundy on 2011-01-24
Hehe. Windows!

So I can change the mount behavior so that it will copy these things over automatically without exe powers? I can find the config steps in a man mount document?

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> Hehe. Windows!

So I can change the mount behavior so that it will copy these things over automatically without exe powers? I can find the config steps in a man mount document?

It is on the man mount page, but as you can see it is a long page.

See : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

use umask, or better dmask and fmask. There are examples on that thread.

See this page:

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

Under fat and ntfs partitions.

---

### Post by nrundy on 2011-01-24
none of that is making any sense to me. Just to make sure im on the right track, by studying the links and using umask I'll be able to configure the mounting fucntion to copy files over without granting exe capabilities by default in the file permissions?

---

### Post by bodhi.zazen on 2011-01-24
> **nrundy said:**
> none of that is making any sense to me. Just to make sure im on the right track, by studying the links and using umask I'll be able to configure the mounting fucntion to copy files over without granting exe capabilities by default in the file permissions?

Yes, it takes a while to understand permissions and mounting options.

Basically you need to edit /etc/fstab and add or edit your entry for your windows partition.

There are 2 examples, one for ntfs and one for fat on that thread.

---

### Post by Morbius1 on 2011-01-25
> **nrundy said:**
> none of that is making any sense to me. Just to make sure im on the right track, by studying the links and using umask I'll be able to configure the mounting fucntion to copy files over without granting exe capabilities by default in the file permissions?
Let's take an example. Let's say you want to mount an NTFS partition located at sda2. On Windows it might be your "D Drive".

First you would make a permanent home for the partition ( mount point ):
```
sudo mkdir /media/WinD
```Then you would add a line in /etc/fstab that will auto mount that partition at boot:
```
/dev/sda2 /media/WinD ntfs defaults,uid=1000,umask=077 0 0
```[COLOR=Blue]*uid=1000 is the user id and 1000 should be you so uid=1000 will make you the owner of the mount point.*[/COLOR]

Now here's the confusing part. "umask" represents the permissions [COLOR=Blue]you want to take away[/COLOR] from the initial permissions state of the partition. At the instance of mount an NTFS partition will have permissions of 777 for both folders and files. "umask=077" will do the following:

777 inital state
077 umask
=========
700 result

700 is the permissions you want on folders but not on files since a 7 makes a file executable. So we have to use a different set of options to differentiate between folders and files: dmask ( directory umask ) and fmask ( file umask ). So we change the initial fstab entry to this:
```
/dev/sda2 /media/WinD ntfs defaults,uid=1000,dmask=077,fmask=177 0 0
```What these will do is:

** For folders:**
777 inital state
077 dmask
=========
700 result

** For files:**
777 inital state
 177 fmask
 =========
 600 result

A "6" (4+2) means that the owner ( you because of uid=1000 ) will be able to read (4) and write (2) to the file but not execute.

Unlike Linux filesystems, on Windows' filsystems all folders and files inherit the permissions defined by the fstab entry so all folders will have permissions of 700 and all files will have permissions of 600.

Lord, I hope I did all that correctly. My intent is to clarify not to confuse ;)

---

### Post by nrundy on 2011-01-25
guys, how does this solution look to you? I don't understand it because there is so much command line talk. But it sounds like I need to change the auto-mount behavior for ALL USB drives.

[http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive/17550#17550](http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive/17550#17550)

---

### Post by Morbius1 on 2011-01-25
Now you've confused me - which really isn't all that hard to do.

If you are using the latest Ubuntu all ntfs external usb drives are already mounted with the permissions you want: Folders = 0700 and Files = 0600. In fact there are a lot of posts here from people who are very upset at this development and want to revert back to the way it was done before where it would mount with every file executable.

Are you saying you want files not executable by default on your internal drives but executable on your external drives?

And remember that with usb ntfs drives the drive "dances with whoever brung her". When you mount it it will mount with you as owner and with the execute bit turned off. If you hand it to me and I'm using a older version of Ubuntu then it will mount with me as owner and the execute bit turned on.

---

### Post by nrundy on 2011-01-26
I'm not following you morbius,

if i plug in a usb drive and copy from the usb drive an image that was created on a WinXP system, the image is showing -rwx r-x r-x permissions.

I just changed my /etc/profile umask to 077. I don't know if this will correct the usb issue or not. I also just learned that IF i manually mount a usb drive i can specify what umask i want in the mount command. Not sure how to specify it yet for auto-mounts. I got to study the fstab file.

---

### Post by vanadium on 2011-01-27
USB drives are by default mounted with read/write permissions for the current user.

Check, in Synaptic Pachage Manager, whether "usbmount" is installed. If it is, then *remove* it. usbmount should *not* be installed. I have seen one case where usbmount was the cause of an issue similar to yours.

---

### Post by nrundy on 2011-01-27
> **vanadium said:**
> USB drives are by default mounted with read/write permissions for the current user.

Check, in Synaptic Pachage Manager, whether "usbmount" is installed. If it is, then *remove* it. usbmount should *not* be installed. I have seen one case where usbmount was the cause of an issue similar to yours.

Will USBs still mount if I remove this? Are you saying that usbmount doesn't affect mounting just the "excessive" permissions being put on copied files?

---

### Post by nrundy on 2011-01-27
I just copied a file from my mounted WindowsXP partition, the bmp image i copied arrived on my Ubuntu desktop with -rwx rwx rwx permissions (yikes!).  This is a default ubuntu setting, i have not messed with mount settings at all.

---

### Post by nrundy on 2011-01-28
Bodhi, fmask and dmask don't work in the /etc/profile setup (I do not have a .bashrc file on my computer). Only umask works. Is this your experience too? fmask and dmask will work in /etc/fstab setup though right?

---

### Post by bodhi.zazen on 2011-01-28
> **nrundy said:**
> Bodhi, fmask and dmask don't work in the /etc/profile setup (I do not have a .bashrc file on my computer). Only umask works. Is this your experience too? fmask and dmask will work in /etc/fstab setup though right?

correct. umask works in .bashrc , the other options are file system specific, again read man mount (I know it is long, but it explains the options per file system and it really is the best referance).

---

### Post by nrundy on 2011-01-28
I did read the man mount bodhi. 

I do not have .bashrc on my comp. It is correct that fmask and dmask do not work in /etc/profile? I can only get umask to work to configure permissions settings in profile.

---

### Post by uRock on 2011-01-28
> **nrundy said:**
> I do not have .bashrc on my comp.
It is in your home folder.

---

### Post by bodhi.zazen on 2011-01-28
> **uRock said:**
> It is in your home folder.

~/.bashrc 

Or in nautilus, show hidden files.

---

### Post by nrundy on 2011-01-30
Hmm, I found .bashrc. Not sure why I couldn't find it before. Regardless

my reading indicated /etc/profile affects system wide (which is what I want). .bashrc only affects user.

Can you guys **please** check, does fmask and dmask work in /etc/profile on you systems? I can only get umask to work in /etc/profile.

From my reading there does not appear to be a system-wide automatic way to configure permissions for auto-mounts. The only option is to have to manually mount every time. Too much trouble.

---

### Post by Morbius1 on 2011-01-30
> Can you guys **please** check, does fmask and dmask work in /etc/profile on you systems? I can only get umask to work in /etc/profile.Already been answered by bodhi.zazen 2 days ago and as it turns out it's still No. 
> From my reading there does not appear to be a system-wide automatic way  to configure permissions for auto-mounts. The only option is to have to  manually mount every time. Too much trouble.     That's why the Linux / Unix gods created fstab. Again this has already been answered. Creating an fstab entry for an NTFS internal partition is easy and fun and has been explained in this very topic. You can also create the same type of entry for an external drive but that gets messy depending on how many different external usb devices you have. 

There is another way to change the way an external ntfs usb device mounts and that's to create your own udev rule:
[https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g](https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g)

---

### Post by nrundy on 2011-01-31
> **Morbius1 said:**
> Already been answered by bodhi.zazen 2 days ago and as it turns out it's still No. 
That's why the Linux / Unix gods created fstab. Again this has already been answered. Creating an fstab entry for an NTFS internal partition is easy and fun and has been explained in this very topic. You can also create the same type of entry for an external drive but that gets messy depending on how many different external usb devices you have. 

There is another way to change the way an external ntfs usb device mounts and that's to create your own udev rule:
[https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g](https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g)

> **bodhi.zazen said:**
> correct. umask works in .bashrc , the other  options are file system specific, again read man mount (I know it is  long, but it explains the options per file system and it really is the  best referance).

I'm assuming Morbius that the above quote by bodhi is the answer to the fmask/dmask question you are referring to? This is hardly clear as it is referring to .bashrc and file systems---not /etc/profile. Thanks for making it clear that fmask and dmask do NOT work in /etc/profile. I appreciate it.

I have read fstab by bodhi and the man mount. And do not see how to accomplish this:
1. friend has an image on his Window 7 NTFS hdd computer.
2. friend copies image onto a FAT32 USB drive.
3. I plug USB into Ubuntu ext3 hdd computer and copy image onto ext3 hdd.
4. image lands on my desktop with -rwx rwx rwx (instead of my desired -rw- --- ---)

It appears I would have to manually mount each time I want to accomplish this as there does not appear to be a default setting that can accomplish this. You guys are insinuating there is a way, but it's not clear from reading the documents.

---

### Post by uRock on 2011-01-31
> **bodhi.zazen said:**
> You can temporarily set a umask value from the command line **_or long term from ~/.bashrc_**

There is not single answer to your questions, it all depends on a number of variables.

You simply need to read and learn permissions. Is there some problem with the default behavior ? The default are sufficient for most people =)
I think bodhi.zazen answered the question here.

Honestly, I would set the Home permissions to 600 and forget about it, because nobody will be able to see the files in the home's subdirectories.

---

### Post by nrundy on 2011-01-31
bodhi did not answer the question. he directed me to a couple documents to read (which do not clearly address the issue I describe in my previous post). I'm not complaining. Just clarifying.

I'm kinda surprised that the developers didn't configure Ubuntu to disable executable permissions by default for items being copied to the harddrive from USB drives. It's one of the most common ways for infection to occur on Windows PCs and Ubuntu has a simple fix (remove executable permission) but it doesn't do it by default. Seems like a big security hole.

---

### Post by Morbius1 on 2011-01-31
It seems to me that you've got 4 options:

(1) Mount the usb device from the command line with the permissions you want which will be a little after the fact.

(2) Set up a entry in fstab that will mount the usb device with the permissions you want. This is going to get tricky on a randomly selected usb storage device.

(3) Explore creating your own udev rule for external usb devices. It seems simple enough but I've never done it myself so let us know how it works out.

(4) Install Ubuntu 10.10

As for the "why didn't the developers..." and the "common way to infect a Windows PC" stuff, I'll let others debate the issue with you.

---

### Post by uRock on 2011-01-31
> **nrundy said:**
> bodhi did not answer the question.

> **bodhi.zazen said:**
> You can change the default umask value by editing ~/.bashrc ;)
It may require some more reading to get it done, but it can be done. 

I have had no problems with permissions, as I am the one who puts the files on the thumb drives and I am the one who copies them from the drive. Don't put anything on your thumb drive that you don't trust or, more importantly, don't copy anything from the drive that you don't trust.

Windows and Ubuntu ask me first before auto-running an executable, then Windows asks permission to allow said executable to make changes, as Ubuntu asks for the root password.

Windows XP is different, but that is why Microsoft is trying to get people to ditch the out of date OS.

---

### Post by nrundy on 2011-01-31
> **Morbius1 said:**
> It seems to me that you've got 4 options:

(1) Mount the usb device from the command line with the permissions you want which will be a little after the fact.

(2) Set up a entry in fstab that will mount the usb device with the permissions you want. This is going to get tricky on a randomly selected usb storage device.

(3) Explore creating your own udev rule for external usb devices. It seems simple enough but I've never done it myself so let us know how it works out.

(4) Install Ubuntu 10.10

As for the "why didn't the developers..." and the "common way to infect a Windows PC" stuff, I'll let others debate the issue with you.

Hey Morbius why is 10.10 a solution?

---

### Post by nrundy on 2011-01-31
> **uRock said:**
> It may require some more reading to get it done, but it can be done. 

I have had no problems with permissions, as I am the one who puts the files on the thumb drives and I am the one who copies them from the drive. Don't put anything on your thumb drive that you don't trust or, more importantly, don't copy anything from the drive that you don't trust.

Windows and Ubuntu ask me first before auto-running an executable, then Windows asks permission to allow said executable to make changes, as Ubuntu asks for the root password.

Windows XP is different, but that is why Microsoft is trying to get people to ditch the out of date OS.

Okay, so if a file is copied to my desktop and tries to run as executable (ie, it has executable permission enabled), ubuntu will ask for my password? this is a great security feature. I didn't know it would do this. I want to make sure I understand your post accurately.

---

### Post by uRock on 2011-02-01
> **nrundy said:**
> Okay, so if a file is copied to my desktop and tries to run as executable (ie, it has executable permission enabled), ubuntu will ask for my password? this is a great security feature. I didn't know it would do this. I want to make sure I understand your post accurately.

The file will require your intervention in order to run. Files dropped on the desktop, even with the executable, will not autorun without asking if you want it to and if the binary needs to access a root file, then it will ask for root permissions.

There are way too many hurdles to be jumped for a binary to infect your system.

I do agree that it would be nice if an update were to fix the permission issue we are discussing, but I do not think of it as a security threat.:p

Cheers,
uRock

---

### Post by Morbius1 on 2011-02-01
> **nrundy said:**
> Hey Morbius why is 10.10 a solution?
This way Windows formatted external USB storage devices automount is an ever evolving thing with Ubuntu ( actually I think it's driven by Debian itself ).

_Ubuntu 10.04 behavior:_
NTFS:  directories = 0700, files = 777
FAT32: directories = 0700, files = 755
In both cases the "execute bit" on files is turned on.

_Ubuntu 10.10 behavior:_
NTFS:  directories = 0700, files = 600
FAT32: directories = 0700, files = 644
In both cases the "execute bit" on files has been turned off.

This change has actually angered more people than pleased them but it seems right up your alley.

---

### Post by uRock on 2011-02-01
> **Morbius1 said:**
> This way Windows formatted external USB storage devices automount is an ever evolving thing with Ubuntu ( actually I think it's driven by Debian itself ).

_Ubuntu 10.04 behavior:_
NTFS:  directories = 0700, files = 777
FAT32: directories = 0700, files = 755
In both cases the "execute bit" on files is turned on.

_Ubuntu 10.10 behavior:_
NTFS:  directories = 0700, files = 600
FAT32: directories = 0700, files = 644
In both cases the "execute bit" on files has been turned off.

This change has actually angered more people than pleased them but it seems right up your alley.

+1 This is what I was seeing when I first noticed this thread. I had to run to the wife's machine to see how 10.04 was handling files.

---

### Post by nrundy on 2011-02-02
Thanks so much for the info guys :)

---

### Post by nrundy on 2011-02-02
> **Morbius1 said:**
> 
This change has actually angered more people than pleased them but it seems right up your alley.

Morbius, why are people angered about this change? They're losing a capability?

---

