---
title: "HOWTO: Mount NTFS partitions with specific ownership/permissions"
date: 2010-10-23
forum: Tutorials
---

### Post by WorMzy on 2010-10-23
Hello there. If you're reading this then you're probably trying to get around the fact that NTFS partitions don't support Linux file permissions. This tutorial will, hopefully, show you how to get around this little problem. Fortunately for you, this only involves editing a single file. Easy, eh?

The file in question is located at /etc/fstab. This file contains a list of partitions which you want mounted, one partition per line. Now, if you take a look at this file, you'll see that there are several lines already. **DO NOT EDIT THESE LINES**. They are important. Editing them, even slightly, may cause your system to stop booting.

If you take a look at this file, you'll see that there are several columns of information. Assuming that you haven't already created one, you'll need to add a new line for your NTFS partition. To know what to put as the information for the partition, we'll need to know a few things about it. Once you have all the information, you can edit fstab by running
```
gksu gedit /etc/fstab
```

[LIST]
[*]Firstly: **which partition is it**?
In this case, this needs to be a device node identifier. e.g. /dev/sda1, a partition UUID, or a partition label. Running
```
sudo blkid -c /dev/null
```
in a terminal will tell you all the relevant information about your partitions. Hopefully you can determine from this list which one is the correct partition.

If you use a UUID or Label, you need to declare it as such. e.g. "LABEL=*[COLOR="Red"]Windows[/COLOR]*", "UUID=[COLOR="Red"]*ABCDEFGHIJKLKLMNOP*[/COLOR]".

[*]Next, **where should it be mounted**?
This part is simple: where do you want the partition to be accessible from? Ubuntu mounts partitions in /media by default, so if you want the partition to be mounted there, say so. e.g. "/media/Windows". You will need to manually create this folder since fstab will complain if it's not there, so make sure that the folder isn't being used already, and run ```
sudo mkdir /media/Windows
```

[*]Next, **which filesystem should it be mounted as**?
Since we're mounting an ntfs partition, specify "ntfs-3g" for this column. Don't use "ntfs" unless you don't want to be able to write to the partition after it's mounted (by write, I mean making new files, editing files, moving  files and folders, etc.; the "ntfs" driver is outdated and only lets you read files.)

[*]Next, **what options should it be mounted with**?
This is the most important column in this case, this is where you specify permissions. How you do this isn't immediately obvious, but there's a way, and it's actually rather simple.

This is a comma separated list, so don't use spaces or tabs, or else you'll find that the mount line doesn't work as expected. To specify the permissions, you merely need to declare three things: UID, GID, and umask.
[LIST]
[*]uid=*[COLOR="Red"]####[/COLOR]* specifies which userid should own the files on the partition. e.g. "uid=1000" means that the user with the id "1000" should own the files. You can find out your UID by opening a terminal and running "echo $UID".

[*]gid=*[COLOR="Red"]####[/COLOR]* specified which groupid should own the files on the partition. e.g. "gid=1000" means that the group with the id "1000" should own the files. Finding out groupids is slightly more difficult than finding out your userid because you can belong to several groups at the same time. Now, Ubuntu normally creates a group for every user, with the same ID as the UID, so you can probably use your UID as the GID. However, you can get a list of groups by running, in a terminal, "cat /etc/group". This will display a list with upto four colon-separated fields per line. The lines will contain the following items: name, an encrypted password, the GID, and a list of users in the group. Find the group you want to use, and add it's GID to the options.

[*]umask=*[COLOR="Red"]UGO[/COLOR]* is the most important of the three options; it specifies what the permissions will be for the user, the group, and everyone else. The numbers used here need to be between 0 and 7, anything else will probably cause an error. These numbers are actually an inverse of normal permissions, so while "7" means "read, write, and execute" in normal permission setting, in fstab "7" means "no permissions". Setting "umask=000" will give EVERYONE read, write, and execute permissions. For clarification, the U is the permissions for the user, G is for group, and O is for others. See [this]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html") for more details about umask.
[/LIST]

You may also add other things to this list. Generally speaking, it's best to start with the "defaults" option. "auto" makes the partition mount automatically when you boot up. Read more here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

[*]**The final two columns should be "0" and "0"**.
These two columns are only used for Linux filesystems, so setting them to 0 stops any complications from arising.
[/LIST]
A finished fstab line may look like:
```
UUID=ABCDEFGHIJKLKLMNOP /media/Windows ntfs-3g defaults,auto,uid=1000,gid=1000,umask=002 0 0
```
another example:
```
/dev/sdb5 /mnt/Music ntfs-3g defaults,uid=1002,gid=1500,umask=227 0 0
```

The next time you boot up, or the next time you run "sudo mount -a", the partition should be mounted where you want it, with the permissions you want it to have.

Enjoy. :)

---

### Post by Channi on 2011-04-04
Nice How To friend, helped me a lot.

---

### Post by debd on 2011-05-28
Nice.

---

### Post by Rakeshvijayan on 2011-06-27
If have two more ntfs partitions how to mount all .here is my whole file.csmct is the limted user I want to give the permission for accessing those ntfs drives without credential of admin power

---

### Post by Rakeshvijayan on 2011-06-27
another file

---

### Post by Rakeshvijayan on 2011-06-27
solved

---

### Post by dwitkin on 2011-06-27
Nice.  Very helpful tutorial.  Worked perfectly.

In a future version of this HOW TO, please consider including a brief explanation of several common UMASK value options, or include a link to more information.

---

### Post by WorMzy on 2011-06-27
Thanks for the feedback. I've added an informative link to that section which should help people who want to understand umask values.

---

### Post by geazzy on 2011-06-27
great tutorial :D

---

### Post by Bluztrvler on 2011-07-01
Excellent, exactly what I have been looking for.  Thanks

---

### Post by mue.de on 2011-07-02
Thanks for that tutorial,
but i still have a quite similar problem:
i tried to mount one partition of an external usb-drive with 'mixed' partitions by adding the line in the */etc/fstab:*
p, li { white-space: pre-wrap; }> [SIZE=1][FONT=Sans Serif]# Toshiba 2,5" USB-Sicherungsplatte, ext2-Partition, [/FONT][/SIZE]
 [SIZE=1][FONT=Sans Serif]UUID=93a2b065-1ddc-4710-8e3e-122ea4d5db7b /media/Tosh25_ext2  ext2   users[/FONT][/SIZE]
 p, li { white-space: pre-wrap; }
Now i get three times questions for the root-password when i login to the system!?
I thaught, the option *users* should allow anyone to mount the partition?
Thanks for advice
mue.de

---

### Post by WorMzy on 2011-07-02
> I thaught, the option users should allow anyone to mount the partition?
That's correct. From mount's man page:

```
              Normally, only the superuser can  mount  filesystems.   However,
              when fstab contains the **user** option on a line, anybody can mount
              the corresponding system.
...
              For  more  details,  see fstab(5).  Only the user that mounted a
              filesystem can unmount it again.  If any user should be able  to
              unmount,  then use **users** instead of **user** in the fstab line.
 

```

I suspect your problem lies elsewhere. You shouldn't *ever* be asked for your root password when using Ubuntu, as the root account is disable by default.

If you comment out that fstab entry (by adding a hash [#] to the start of the line), does the problem desist?

---

### Post by Morbius1 on 2011-07-02
The user and users mount option will be ignored at boot and only comes up after everything has been mounted or if the noauto option is also included. It's explanation in the man pages is misleading because it doesn't do what the man pages implies that it does - at least not in the way it implies. In any event there are no users at the time that fstab is executed - well except for root.

>   [SIZE=1][FONT=Sans Serif]UUID=93a2b065-1ddc-4710-8e3e-122ea4d5db7b /media/Tosh25_ext2  ext2   users[/FONT][/SIZE]                      You might start with finishing the sentence:
>   [SIZE=1][FONT=Sans Serif]UUID=93a2b065-1ddc-4710-8e3e-122ea4d5db7b /media/Tosh25_ext2  ext2   users[/FONT][/SIZE] [COLOR=Blue]**0 0**[/COLOR]                     But at the end of the day I agree with what I think is the direction WorMzy is heading. Why have a mount expression at all in fstab for an external usb drive.

---

### Post by mue.de on 2011-07-02
Thanks for the replies,

@WorMzy
> If you comment out that fstab entry (by adding a hash [#] to the start of the line), does the problem desist?     I deleted the new entry and got still the three password questions: so you're right when you say 'your problem might lies elsewhere', but it occured the first time as i added this line to the fstab.
How can i find  where the three kdesudo questions have their origion?

@Morbius1

I'll try it (finishing the sentence) and reply later.
With that entry in the fstab i wanted the external usb-drive to be mounted alltimes at the same place, so that i could run a cron-job (*rsync*) with a fixed target-name (far saving my */home*-directory).
Eventually could i have used the e2fslabel-Command for naming the usb-partition?
P.S. the origion of the kdesudo boxes:
[ATTACH]196578[/ATTACH]

Thanks a lot for your replies

---

### Post by jefelex on 2011-07-04
What I want to find out is how to get execution permissions for a thumb drive that is mounted after I have already logged in.  I don't want to add the thumb to my fstab (since it is not installed when I boot the computer)  I know there must be a way, but I am at a loss after investigating for weeks!  I'm not sure how the device is mounted in gnome - where would I change that configuration option?

The thumb drive is automatically mounted when I plug it in, and all the files are visible (although the drive mount type is msdos) 

??

Is it because msdos is an insecure partition type?

John

I think that was it!  I reformatted the thumbdrive to an ext4 partition, and now it works perfectly!!  Thanks for your patience while I figured this out!! :-)

---

### Post by Gaijin66 on 2011-12-21
Thank you. This info was exactly what i needed. It helped me.

---

### Post by aveminus on 2012-01-13
thanx WorMzy  for the tutorial that was very helpful :)

---

### Post by StrangeKid on 2012-06-11
It worked! Thank you so very much!

---

### Post by funkeba on 2012-07-02
wow, thanks man it was really helpful :)

---

### Post by joerlo on 2012-09-24
Thanks

---

### Post by dbruvers on 2013-01-16
Thank you for the detailed explanation! It made things clearer to me :)

---

