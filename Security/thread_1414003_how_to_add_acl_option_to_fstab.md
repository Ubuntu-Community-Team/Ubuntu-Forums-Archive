---
title: "how to add acl option to fstab"
date: 2010-02-23
forum: Security
---

### Post by tanoloco on 2010-02-23
Hello,

I'm using ubuntu since a few months so I'm sorry if my question
would sound easy to the majority but I cannot solve it by myself.


I've got a partition, let's say sdb6, which is one of the partitions of my second hard disk.
On boot ubuntu only mount my boot partition, let's say sda2, which is on my first drive.
Once ubuntu started  if I want to mount a partition I usually click on it under the Places menu and an authorization is required.

As I would like to add acl to a partition following this thread

> 
[http://ubuntuforums.org/showthread.php?p=8787962](http://ubuntuforums.org/showthread.php?p=8787962)
I've tried to add acl option to my fstab, but my /etc/fstab doesn't have
any info of any of my  partitions and it originaly looks like:

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=01c0de92-a506-4615-9280-cd13e8803cd2 /               reiserfs notail          0       1
# swap was on /dev/sdb1 during installation
UUID=fa236bc3-f8c7-432d-8418-db03b06ec3d8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,defaultsnoauto,exec,utf8 0       0
so I tried to add a new line for my partition as:
```

/dev/sdb6    /media/data    ext3    defaults,acl    0    1

```but when I click on it under the places menu it shows an error window saying:
> 
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb6 on /media/data
I tried to specify other options rather then defaults as explained here

> 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
but nothing changed.


So if I mount it through terminal follow:
```

sudo mkdir /media/data
sudo mount -t ext3 /dev/sdb6 /media/data

```everything is fine and the partition is mounted but if I try to unmount  it by right-clicking
on its desktop icon and selecting unmount it again shows me a similar error

> 
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdb6 from /media/data
and on a similar way if I unmount it through a terminal by typing

```

sudo umount /media/data
sudo rm -r /media/data

```evrything is ok.

However acl support seems not to be loaded neither in this way because if I open a file on it with eiciel it gives me an error (of course when the partition is mounted with the previous code)
> 
Could not open the file "/media/dati/test" (Operation not supported)
while if I type on a terminal

```

sudo mount -o remount,acl /media/data

```acl is loaded and eiciel can open any file and folder on it.

My goal is to mount/unmount any partition with acl loaded and graphically
but I reached my limit on my linux knoweledge.

Could any guru out there help me please?
Thanks in advance

---

### Post by ajgreeny on 2010-02-23
Have a look at this site, which is actually for debian, but may also be OK for Ubuntu.
[http://www.debianhelp.co.uk/acl.htm](http://www.debianhelp.co.uk/acl.htm)

---

### Post by tanoloco on 2010-02-23
hi,

thanks for your suggestion but it didn't work.
I had a look to a lot of guides without luck.

I tried pysdm to try to write fstab correctly but it works fine only through its gui:
it requires an aauthorization whle start-up and then it has a workin mount/unmount buttom
and acl is activated too, but when you write all the modifications to fstab by pressing the apply button and try to mount from the places menu the old error mounting advice show up.

I tried googling but no solution at th moment.

BTW the string I used on my fstab following your suggestion was

```


/dev/sdb6   /media/dati     ext3   {{acl}},defaults,errors=remount-ro  0  1


```

---

### Post by adam814 on 2010-02-23
I have a line in my fstab almost identical to the first one you tried and it works fine, but it's a partition I want mounted at boot (it's on my boot hard drive so it's always there).  The only other difference is I used the UUID of the partition instead of the device to identify it.

Assuming what you want is to be able to mount the device by right-clicking it and have the ACL option work here are my recommendations:

1) Use the first line you posted, changing /dev/sdb6 to the UUID of /dev/sdb6 (you can find it out with "sudo blkid")
2) Change the options from "default,acl" to "acl,user,noauto,errors=remount-ro"

That should do what you want.

---

### Post by tanoloco on 2010-02-23
I found a partial workaround:

1. fstab was changed adding the following
```

/dev/sdb6  /media/data     ext3    user,noauto,acl  0  0 

```2. I created a mounting point under media
```

sudo mkdir /media/data 

```which on my desktop comes with 750 permission while media folder as 755 permission

Now clicking under the places menu will produce to mount the partition with acl activated but some problems still remain:


a. the  authorization is no longer required as before: the user can mount and unmount the partition freely. If I change in fstab the user option in nouser I  will get the hated 
> 
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb6 on /media/data
b. the mounting point (the data folder in my case on /media) will no longer be deleted.
If I cancel by  myself (when unmounted) with
```

sudo rm -r /media/data

```When next trying to mount it always by clicking on the menu places I receive an error

> 
Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/dati does not exist
c. if a different user mount this partition then other users cannot unmount it receiving an  error 
> 
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only other_user can unmount /dev/sdb6 from /media/data
even if the other user close his session and the only way to unmount it is by terminal
```

sudo umount /media/data

```


I would like to have anything as before (default behavior  of ubuntu), which is the ability to mount a partition through the menu places and unmount it by right-click on its desktop icon and it asks me an authorization to mount while any user can unmount it  with the same authorization.

All this working default behavior only with acl activated.

I didn't thought it was so complicated ... :confused:

---

### Post by tanoloco on 2010-02-23
hi [adam814]("http://ubuntuforums.org/member.php?u=982022") thanks for your  reply,

I tried your suggestion by adding

```

UUID=580214b3-c7b1-4d3e-bc91-acb1c08d4793    /media/data    ext3    acl,user,noauto,errors=remount-ro    0    1

```

to my fstab and the behavior is the same as described with my previous post.

Anyhow this is a good compromise but I was wondering if it was possible the have the default behavior with acl activated.

Thanks again for your support :D

---

### Post by bodhi.zazen on 2010-02-23
Change the option in fstab from user to users

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by tanoloco on 2010-02-24
Hi  [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") and thank you for your help,

your suggestion solved my third problem in the list of my previous post which was the prohibition to unmount a device mounted by another user.

Talking about this I made some test I want to share with you: in my experience the fstab option  *users* will allow to **mount/unmount this device** not only the users within the group users but **any user**!
In fact I created an unpriviliged user and left him standalone without adding it to any group and he can mount this device which could be unmounted by other users included in the group users and viceversa it can unmount the same device mounted by those users.[I]

Anyhow always remain the first two problems:
1. The authentication to mount the device is no longer required
2. It's needed to have a mounting point under the media folder to mount which will not be deleted after be unmounted.

While the default behavior of ubuntu is to require an authentication to mount not-removable devices and to create/delete the mounting point under the media folder by itself. (I'm talking about mounting a device through he menu places and unmounting it by right-clicking on its desktop icon)

I read a lot of guides but I cannot see a solution to fix this behavior all my tests end with the errors reported on my previous post.

I had a look at your link too  but I haven't found anything about that or am I wrong?

I was thinking that maybe the mount command called by clicking under the menu places could be configure out in order to always activate acl  for example changing it in

mount -o acl 
or
mount -o remount,acl[/I]

is there an easy way to do so?
Maybe there is a conf text somewhere to specify some option for this command

That problably would leave any behavior as is plus would activate acl anytime a device would be mounted ... :confused:


Any suggestion?

---

### Post by bodhi.zazen on 2010-02-24
To make a directory, use mkdir

```
sudo mkdir /media/foo
```

In terms of users mounting a partition, the option user allows a user to mount the  partition, users allows all users, if you need finer grain of control take away both options and configure sudo.

The problem you are having is that there are two ways of mounting a partition. One is via fstab and the other is via gnome or more specifically nautilus.

If there is an entry in fstab it overrides the gnome settings.

I really do not understand what you are wanting. Some users can mount the partition, but not others ? use sudo.

Sometimes you want it mounted with acl and sometimes not ? what then is the point of using acl ?

In terms of setting options, fstab is IMO easiest. If you are trying to configure how gnome mounts partitions you are going to start digging into gnome, the config files, and HAL.

[http://linux.die.net/man/1/gnome-mount](http://linux.die.net/man/1/gnome-mount)

[http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-storage-policy](http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-storage-policy)

Sorry, but I am not familiar enough with the specific details to know if you can configure the behavior per user.

Personally I would use fstab and sudo.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

See the sections on allowing some users to run some commands. Perhaps you want some users to mount, but not unmount ?

---

### Post by tanoloco on 2010-03-02
Hi [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") sorry if I  haven't replied to you sooner but I was deep inside another problem to solve (see another post from me asking for encfs).

Sorry if I confused you somehow: maybe I've been too prolix or maybe I'm confusing because I'm a newbie and I have my ideas not so clear ;)

My scenario is to boot from a partition with no other devices mounted.
Normally if I want to mount a partition on a not-removable device, such as a second hard disk, I use the Places menu and click on that partition and ubuntu ask me for an authorization to mount it.
On the same way if I want to unmount it I right-click on its desktop-icon and select unmount.
No folder is required on media folder to mount and no folder remains after having unmonted it.


Now: **what I want to do is to add acl support everytime this partition is mounted by  any user** without changing the behavior described now.

I thought to add acl option in fstab and I finally used (thanks to the help of the forum)
```
UUID=580214b3-c7b1-4d3e-bc91-acb1c08d4793    /media/data    ext3    acl,users,noauto,errors=remount-ro    0    1
```but this changes the behavior of ubuntu as described in my previous post in a way that:
1. The authentication to mount the partition is no longer required
2. I need to create a folder as a mounting point under the media folder which will not be deleted after be unmounted.

So again: how do I add acl support to a partition everytime is mounted by anyone without changing the default behavior of ubuntu? Or how do I  fix those changed behaviors after having added that string to my fstab?

Hope I've been more clear :P

PD: I will have a look to the links you povided me but at first look they don't seem to help me ...

---

### Post by bodhi.zazen on 2010-03-02
Well, when you are using the gui, you are using gnome, or more specifically nautilus, to mount the partition.

I do not know enough about gnome to know how to change the behavior to add in acl.

You will have to look through the gnome and hal documentation.

[http://linux.die.net/man/1/gnome-mount](http://linux.die.net/man/1/gnome-mount)

[http://felipec.wordpress.com/2006/12/28/automounting-a-storage-device-with-gnome/](http://felipec.wordpress.com/2006/12/28/automounting-a-storage-device-with-gnome/)

---

### Post by klatham on 2010-03-09
I was curious about this, since I have started using ACL on a regular basis ... so I have a vested interest ;)

gnome-mount *appears to be* what does it.

(1) according to the Nautilus information that I can find, it uses compiled extensions to handle the "Mount" option in computer:/// (which is also the default action).

Side-note: nautilus actions can not, as far as I can tell, override compiled extensions

(2) There is, in fact, "libgnome-mount.so" in /usr/lib/nautilus/extensions-2.0

(3) gnome-mount documentation states that it uses gconf for mount options.  So, below, when it says it reads from "/system/storage/defaults/FS_TYPE/" it means that path within gconf.

===========================================
The following is from [http://linux.die.net/man/1/gnome-mount](http://linux.die.net/man/1/gnome-mount)
and therefore all applicable copyrights apply (if any).
===========================================
*FILE* SYSTEM DEFAULTS[INDENT]First, default mount options are read from **/system/storage/defaults/FS_TYPE/** for the probed file system type of the volume. The option **uid=,** is treated specially by **gnome-mount** and will be replaced by **uid=UID_OF_USER** to cope with the fact that the **uid** is a function of the user calling it.
[/INDENT]*PER* DRIVE[INDENT]Second, the gconf tree at **/system/storage/drives/UDI_OF_DRIVE/** is consulted for options that depend on what drive the volume belongs to. For example, this is useful for configuring that volumes inserted into a given drive is always mounted at the same location. For example, this can be used to emulate **/etc/fstab** behaviour by where CD media is always mounted at e.g. **/media/cdrom**
[/INDENT]*PER* VOLUME[INDENT]Third, the gconf tree at **/system/storage/drives/UDI_OF_VOLUME/** is consulted for options that are specific to a particular piece of media and as such depends on either the file system label (e.g. **EOS_DIGITAL** ) or the file system UUID (e.g. **E18B_10EC** ) or both.
[/INDENT]===========================================

I just read all of this, so I have not tried it yet ...
... but my gconf entries do exist as outlined by this documentation, so I guess its just a matter of adding a new one for ext3 (in my case).

Thought it might help.  I will repost after some experimentation.

Ken
[LEFT]
[/LEFT]

---

### Post by tanoloco on 2010-03-11
hello, thanks for your reply. Unluckly my skills on ubuntu are still limited and I cannot go on through your suggestions. While waiting for your tests or for other people more skilled than me to help us in that, I was wondering if it is possible to execute a script anytime that a device is mounted.
If yes we could create a script with the command```
sudo mount -o remount,acl /media/data
```which is execute on mounting /media/data for example.

I've simulated it in this way:
- click on Places > data and it asks for the authorization.
- once authorized and mounted I give the above code through a terminal.
- the devie shows acl controls correctly
- I can click on its desktop icon and it's unmounted without living the mount point on the media folder.

In other words: same behavior as before but with acl controls! :)

is there someone knowing how to flash such a script each time a device is mounted?  :confused:

---

### Post by tanoloco on 2010-05-13
Hello,
I answer to myself :) hoping this could help someone else searching the same.

Lucid won't ask you anymore an authentication to mount partition on local disks and I've found there's a bug in gvfs which causes duplicate entries in Places when fstab is customized
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

So, in lucid, to add acl when mounting a local partition is like without changing the lucid behavior is to:

1 . create a mounting point under media
```
cd /media
sudo mkdir data
sudo chown root:users data
sudo chmod 770 data
```2. edit fstab:
```
gksudo gedit /etc/fstab
```and add
```
/dev/sdb6    /media/data ext3    users,exec,acl,noauto,errors=remount-ro 0 1
```specify he partition with /dev/xx instead of using UUID will prevent duplicates of the partition name under place

Thanks to all!
:guitar:

---

### Post by tanoloco on 2010-08-15
Hello! :)

a new question about this thread. I recently noticed that I cannot activate acl support on drive mounted on /mnt !?

If I add the string I previously posted on my /etc/fstab```
/dev/sdb6    /media/data ext3    users,exec,acl,noauto,errors=remount-ro 0 1 
``` acl support is correctly added for sdb6 drive

but if I use the same string only changing the mounting point as:
```
/dev/sdb6    /mnt/data ext3    users,exec,acl,noauto,errors=remount-ro 0 1 
```
acl support is not activated !!!

This sounds very strange to me. Does anyone know why and if there's something I can do?
I'm interested in the second string just to hide the drive from the "places" menu.

Thanks for any help
Cheers

---

