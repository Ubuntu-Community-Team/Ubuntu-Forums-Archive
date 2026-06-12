---
title: "Server 14.04 for backups, file share in mixed OS environment"
date: 2016-02-10
forum: Server Platforms
---

### Post by andrew283 on 2016-02-10
I suspect this is far simpler than I am finding it, which makes me feel a bit foolish really, but here goes.

My home network was comprised of an ISP-provided modem / router (Hitron), 2 linux-based Minix media boxes connected via wifi, an android tablet, an iPad, numerous phones of all flavours (BB10, iOS, android), a (current) Macbook, 3 Win 7 machines, an XP desktop box and a 1 TB LACIE Neil Poulton NAS.  The NAS held all the media (iTunes, movies), outlook backups and acted as my file server depending on which Windows machine I was on. All the Windows machines used the NAS as their iTunes storage (great until you hit the road).  

The first NAS was replaced under warranty a few years ago, but we lost all the data. The replacement unit died the other day. I tore the unit down, plugged the drive into a SATA/USB adapter, installed Ubuntu in a VM and pulled up the drive. The disk is perfectly fine - can access all the files without issue. But I don't need a USB drive, I need something on the network. I don't want another LACIE.

I re-deployed an old Dell Inspiron 530 box, added memory (5 gb), installed a new WD NAS 1 TB drive and installed Ubuntu Server 14.04 with a full-disk LVM partition. The install included basic server, openSSH and SAMBA options. I installed Unity desktop because I'm a command line newb, but have found I'm quite happy to use Putty from Windows, I just don't know any commands.

I shut the server down, installed the old LACIE drive in a 2nd slot, fired it all back up, and the primary storage partition appeared as a drive in Unity. However, when I try to open any of the folders, it tells me I'm not the owner and all the folders disappear. Not handy. Using the terminal, I changed permission -R 777 which now gets me access, but I suspect it's not quite what I'm after from a security standpoint.

What I'd like:
[LIST]
[*]A network drive for each individual, that they can access from their respective device, that can be mapped as another drive on the Windows and MAC machines 
[*]A common network drive so we can share files between us.
[LIST]
[*]It would be amazing if these were available over the internet but the security aspect terrifies me. 
[/LIST]
  
[*]Backup space for each computer 
[*]A shared iTunes repository (because once they have their claws in you, you can't get out) 
[*]Movies / Television media are currently stored in 2 different folders depending on whether they're appropriate for kids or not. Access for the Minix boxes is only controlled through XBMC by mapping the folders to the different user accounts. I'd like that control moved to the server. 
[/LIST]

I tried to follow a couple of different online tutorials, but several used webmin, which I understand is no longer supported, or they included email servers and LAMP stacks which gave me no end of grief trying to configure (starting with a lack of domain name), or both.

I'm still struggling to get my head around the difference in layout between Ubuntu/Unix and Windows. What I had previously was a C drive with just the OS, a D drive with everything else, a folder in the NAS that was mapped to my machine as a Z drive, which was really only a subfolder of the folder holding all of the iTunes and other media folders. I don't know how to put all this together. 

If I create a user for each person that needs a network drive space, that seems fairly straight forward, but who or how or where does the shared network space get created? 
How do I incorporate the old NAS drive into the new environment without erasing everything on it?
Where do I begin?

---

### Post by yancek on 2016-02-10
> However, when I try to open any of the folders, it tells me I'm not the owner and all the folders disappear

An ordinary user is the owner with permissions only to his/her /home/user folder.  Some minor exceptions.  You need to either access the partition as root using sudo or change the permissions.

> Using the terminal, I changed permission -R 777 which now gets me access

Additionally, that will give any user who has access, permission to completely modify/delete anything and everything on that partition.  So what is the filesystem type on the drive/partition you are referring to?  If this is a Linux filesystem, you can create a group and add your users to the group and give the group permissions you want.  If it is a windows filesystem, Linux permissions don't work so you will have to use something like umask.

---

### Post by andrew283 on 2016-02-10
It's a Linux filesystem thankfully - that's one of the things that prompted this venture was the (theoretical) ease of saving the data.

I'm just reading *man adduser *but I'm foggy on groups. How do I connect the group permissions to that folder (/dev/sdb2)?

edit to add: if I'm using the Unity gui, how do I *sudo*?

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> It's a Linux filesystem thankfully - that's one of the things that prompted this venture was the (theoretical) ease of saving the data.

I'm just reading *man adduser *but I'm foggy on groups. How do I connect the group permissions to that folder (/dev/sdb2)?

edit to add: if I'm using the Unity gui, how do I *sudo*?
Do not use the GUI to invoke sudo.  Learn to use the terminal to set up the data store.  Most of what you want to achieve is fairly simple to do, but not very intuitive if you've never done it before. 

You will need to [LIST]
[*]Add users + configure groups
[*]Create the file system for the data (/srv/share)
[*]Install and configure Samba for the network
[*]
[/LIST]

The only problem will be the iTunes share.  There can be problems if users can delete other users music.

Samba can easily handle all the users private data with one simple [homes] share.  The Public share can created with several variations.

Do you expect each user to backup their data or are you going to manage that?

I have a single server that serves both NFS exports and Samba shares (/srv/nas) along with partition that I use to backup all the NAS data along with each of the client machines (srv/backup).  It has been running with no problems for that last 6 years.

Are you willing to do this using the terminal (CLI)?

---

### Post by andrew283 on 2016-02-10
100%! Absolutely. I'd be happy to remove the Unity GUI all together.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> 100%! Absolutely. I'd be happy to remove the Unity GUI all together.
There is no reason to remove the GUI.  You are just better off creating and managing the data with the terminal.

Have you added the users yet?  All you need to do to add a Ubuntu user is this```
sudo adduser <user_name>
```...where <user_name> is the login name you want to assign to that person.  Be prepared to the add the users first and last name and provide a password for that person.

We can add the users to the user groups you need next.  First you need to think about haw many user groups you will need (kids, parents, admin. etc).

---

### Post by andrew283 on 2016-02-10
Users added.  

I think the groups you listed reflect how I was imagining them. So let's go with exactly that - admin, parents, kids

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Users added.  

I think the groups you listed reflect how I was imagining them. So let's go with exactly that - admin, parents, kids
I can see the parents and kids groups, but not the admin group.  With Linux there is only one administrator.  That would be the root user (uid=0).  The administrative accounts for Ubuntu are all in the group sudo.  Using sudo (Switch User and DO) allows the sudo user to become root and execute the command.

In your case I imagine that you installed Ubuntu so you are the only sudo user at the present time.  You can check that with this command```
getent group sudo
```

That gives you the 3 groups (sudo kids parents).  Have you created the users?  Post the output of this command```
getent passwd | grep 100
```

---

### Post by andrew283 on 2016-02-10
```
andrew@media-srv:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:
andrew:x:1000:1000:andrew,,,:/home/andrew:/bin/bash
wife:x:1001:1001:,,,:/home/wife:/bin/bash
kid1:x:1002:1002:,,,:/home/kid1:/bin/bash
kid2:x:1003:1003:,,,:/home/kid2:/bin/bash
kid3:x:1004:1004:,,,:/home/kid3:/bin/bash


```

I didn't answer your question about backups earlier. Ideally they'd be scheduled to happen on their own and the server would look after that, but I'm not sure how that works. My wife is an Apple user because of it's simplicity - pick it up and it operates intuitively, she won't (generally) break anything and she doesn't need to tech savvy. As long as you stay within the confines of Apple, it tends to work flawlessly so this is her choice. We tried getting her into Android but it lacked the same ability and made her very frustrated. Happy wife, happy life.  Which is to say, if the server can automatically back up her Mac without her doing anything, that's perfect.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> ```
andrew@media-srv:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:
andrew:x:1000:1000:andrew,,,:/home/andrew:/bin/bash
wife:x:1001:1001:,,,:/home/wife:/bin/bash
kid1:x:1002:1002:,,,:/home/kid1:/bin/bash
kid2:x:1003:1003:,,,:/home/kid2:/bin/bash
kid3:x:1004:1004:,,,:/home/kid3:/bin/bash


```

I didn't answer your question about backups earlier. Ideally they'd be scheduled to happen on their own and the server would look after that, but I'm not sure how that works. My wife is an Apple user because of it's simplicity - pick it up and it operates intuitively, she won't (generally) break anything and she doesn't need to tech savvy. As long as you stay within the confines of Apple, it tends to work flawlessly so this is her choice. We tried getting her into Android but it lacked the same ability and made her very frustrated. Happy wife, happy life.  Which is to say, if the server can automatically back up her Mac without her doing anything, that's perfect.

So lets add a group for the kids with this command```
sudo addgroup --gid 200 kids
```...and then one for the parents```
sudo addgroup --gid 201 parents
```

See if you can see them with ```
getent group
```

---

### Post by yancek on 2016-02-10
There are any number of ways to do backups.  I believe if you look in System Settings on your Ubuntu, you will see a backup program.  You can use simple scripts to do this also and put an entry in a cron entry to do it on a regular basis.  Lots of examples of cron entries available from Mr Google.

---

### Post by andrew283 on 2016-02-10
Done and success.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Done and success.
Now we need to add the users to the 2 groups.  I think the parents should be in the kids group as well their own parents group.  So add all users to the kids group with  this command```
sudo addgroup <user_name> kids
```

Add the parents only to the parents group with this command```
sudo addgroup <user_name> parents
```

Check this (again) with this command```
getent group
```

---

### Post by andrew283 on 2016-02-10
Done and Success. Is there a method to append all the usernames to move multiple users to a group at once? Also, why the manual gid entry in the group creation?

```
kids:x:200:andrew,wife,kid1,kid2,kid3
parents:x:201:andrew,wife


```

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Done and Success. Is there a method to append all the usernames to move multiple users to a group at once? 

No, I checked it again just before telling you what to do.  I would script it for larger applications.
> 
Also, why the manual gid entry in the group creation?

Habit and neatness.  All the mortal (humans) users and groups start at 1000 and the system users and group are less than 200 in your install.  So 200 and 201 are sort of by themselves.  In the logs if you see gid=200 or 201 you will know that they are your groups (kids or parents). 
> 

```
kids:x:200:andrew,wife,kid1,kid2,kid3
parents:x:201:andrew,wife

```
We can now create a structure for the data.  Since all multi-user data should be outside of /home and this will be data served by Samba we should use the /srv branch of the file system.

What **separate ** directories do you think you will need?  How do we arrange the kids data (not including their private homes directories)?  The same for the parents data.  How do you want to arrange the iTunes data; and  the Movies data?

I would like to see what you have done with the default partitions.  Post the output of these 2 commands```
df -h

sudo blkid -c /dev/null -o list

```

---

### Post by andrew283 on 2016-02-10
> In the logs if you see gid=200 or 201 you will know that they are your groups (kids or parents).
Ah - makes perfect sense.
> I would like to see what you have done with the default partitions.  Post the output of these 2 commands
```
andrew@media-srv:~$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
udev                             2.5G  4.0K  2.5G   1% /dev
tmpfs                            495M  2.0M  494M   1% /run
/dev/mapper/media--srv--vg-root  912G  3.8G  862G   1% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
none                             5.0M     0  5.0M   0% /run/lock
none                             2.5G  304K  2.5G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sda1                        236M   38M  186M  17% /boot
/dev/sdb2                        931G  652G  280G  70% /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e
/dev/sdb9                        633M   49M  551M   9% /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e

andrew@media-srv:~$ sudo blkid -c /dev/null -o list
[sudo] password for andrew:
device     fs_type label    mount point    UUID
--------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          0bb64c4b-c7c6-4181-9ffd-7d515aeabf41
/dev/sda5  LVM2_member      (in use)       hKgCHK-fZA4-ySjX-vbCM-RWLS-YO7q-edGxjD
/dev/sdb2  xfs              /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e 9b29bf55-8c05-4be6-a32f-6137cecc3d8e
/dev/sdb5  swap             (not mounted)
/dev/sdb7  linux_raid_member  (not mounted) 46a316ea-054c-5468-4a1c-d8090613fe8d
/dev/sdb8  linux_raid_member  (not mounted) fd1ccfdb-9208-47dd-3ff0-84c4dea81dfe
/dev/sdb9  ext3             /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e 759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e
/dev/mapper/media--srv--vg-root           ext4             /              69887c81-8dd7-454b-ac53-75f9057bb708
/dev/mapper/media--srv--vg-swap_1           swap             <swap>         5f473229-e5da-4801-b399-5305e3f1ebed

```

The server's name is *media-srv.* /dev/sdb has numerous small partitions that, I assume, contain the original LACIE OS, the swap files, the UPnP server and whatever else was in there. I'm not sure why it's mounting both sdb2 and sdb9, as sdb9 is both the bulk of the 1TB drive and contains all of the files in question but they both seem to mount automatically.
> What **separate ** directories do you think you will need?  How do we  arrange the kids data (not including their private homes directories)?   The same for the parents data.  How do you want to arrange the iTunes  data; and  the Movies data?
[LIST]
[*]andrew storage
[*]wife storage
[LIST]
[*]can the /home/user  directory serve the function?
[/LIST]

[*]family shared files
[*]single directory for everyone's backups
[/LIST]
The original NAS was fairly disorganized. Movies were in folders *Kids *or *Parents *with the files being within their own sub-folders (mostly...or directly in the *Kids* folder). With some cleaning up, this still seems to make sense.
iTunes is a typical iTunes-built folder structure with each artist directory and album sub-directory.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Ah - makes perfect sense.

```
andrew@media-srv:~$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
udev                             2.5G  4.0K  2.5G   1% /dev
tmpfs                            495M  2.0M  494M   1% /run
/dev/mapper/media--srv--vg-root  912G  3.8G  862G   1% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
none                             5.0M     0  5.0M   0% /run/lock
none                             2.5G  304K  2.5G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sda1                        236M   38M  186M  17% /boot
/dev/sdb2                        931G  652G  280G  70% /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e
/dev/sdb9                        633M   49M  551M   9% /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e

andrew@media-srv:~$ sudo blkid -c /dev/null -o list
[sudo] password for andrew:
device     fs_type label    mount point    UUID
--------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          0bb64c4b-c7c6-4181-9ffd-7d515aeabf41
/dev/sda5  LVM2_member      (in use)       hKgCHK-fZA4-ySjX-vbCM-RWLS-YO7q-edGxjD
/dev/sdb2  xfs              /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e 9b29bf55-8c05-4be6-a32f-6137cecc3d8e
/dev/sdb5  swap             (not mounted)
/dev/sdb7  linux_raid_member  (not mounted) 46a316ea-054c-5468-4a1c-d8090613fe8d
/dev/sdb8  linux_raid_member  (not mounted) fd1ccfdb-9208-47dd-3ff0-84c4dea81dfe
/dev/sdb9  ext3             /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e 759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e
/dev/mapper/media--srv--vg-root           ext4             /              69887c81-8dd7-454b-ac53-75f9057bb708
/dev/mapper/media--srv--vg-swap_1           swap             <swap>         5f473229-e5da-4801-b399-5305e3f1ebed

```

The server's name is *media-srv.* /dev/sdb has numerous small partitions that, I assume, contain the original LACIE OS, the swap files, the UPnP server and whatever else was in there. I'm not sure why it's mounting both sdb2 and sdb9, as sdb9 is both the bulk of the 1TB drive and contains all of the files in question but they both seem to mount automatically.


Mind boggling.  :D  I need to spend a bit of time pondering the possibilities.  ;-)  It will help if you post the output of this ```
cat /etc/fstab
```...and let me have a few minutes to think. 
> 

[LIST]
[*]andrew storage
[*]wife storage
[LIST]
[*]can the /home/user  directory serve the function?
[/LIST]
Sure you can use the /home directory for personal stuff.  The Samba [homes] share defaults to this arrangement.
[*]family shared files
[*]single directory for everyone's backups
[/LIST]
The original NAS was fairly disorganized. Movies were in folders *Kids *or *Parents *with the files being within their own sub-folders (mostly...or directly in the *Kids* folder). With some cleaning up, this still seems to make sense.
iTunes is a typical iTunes-built folder structure with each artist directory and album sub-directory.
I understand.  Let me see the /etc/fstab file and I will make sense of it all.

---

### Post by andrew283 on 2016-02-10
```
andrew@media-srv:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/media--srv--vg-root /               ext4    errors=remount-ro           0     1

# /boot was on /dev/sda1 during installation
UUID=0bb64c4b-c7c6-4181-9ffd-7d515aeabf41 /boot           ext2    defaults    0      2
/dev/mapper/media--srv--vg-swap_1 none            swap    sw                        0     0


```

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> 
```
andrew@media-srv:~$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/media--srv--vg-root  912G  3.8G  862G   1%[COLOR="#008000"]** /   <--fstab mounted main partition**[/COLOR]
/dev/sda1                        236M   38M  186M  17% /boot    <-- fstab mounted boot partition

/dev/sdb2                        931G  652G  280G  70% [COLOR="#0000FF"] /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e  **<-- udev mounted data partition**[/COLOR]
/dev/sdb9                        633M   49M  551M   9% [COLOR="#FF0000"] /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e <-- what is in this directory
[/COLOR]


```

Does the above sdb2 partition (noted in blue) have all the data?  What does the above sdb9 partition (noted in red) have in it?  Ca we move all the data to the main partition (noted in green)?
> 

```


andrew@media-srv:~$ sudo blkid -c /dev/null -o list
[sudo] password for andrew:
device     fs_type label    mount point    UUID
--------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          0bb64c4b-c7c6-4181-9ffd-7d515aeabf41
/dev/sda5  LVM2_member      (in use)       hKgCHK-fZA4-ySjX-vbCM-RWLS-YO7q-edGxjD
/dev/sdb2  xfs              /mnt/9b29bf55-8c05-4be6-a32f-6137cecc3d8e 9b29bf55-8c05-4be6-a32f-6137cecc3d8e
/dev/sdb5  swap             (not mounted)
/dev/sdb7  linux_raid_member  (not mounted) 46a316ea-054c-5468-4a1c-d8090613fe8d
/dev/sdb8  linux_raid_member  (not mounted) fd1ccfdb-9208-47dd-3ff0-84c4dea81dfe
/dev/sdb9  ext3             /media/andrew/759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e 759f063a-ee7c-43dc-b5f1-d1d5d63b9c0e
/dev/mapper/media--srv--vg-root           ext4             /              69887c81-8dd7-454b-ac53-75f9057bb708
/dev/mapper/media--srv--vg-swap_1           swap             <swap>         5f473229-e5da-4801-b399-5305e3f1ebed

```

The server's name is *media-srv.* /dev/sdb has numerous small partitions that, I assume, contain the original LACIE OS, the swap files, the UPnP server and whatever else was in there. I'm not sure why it's mounting both sdb2 and sdb9, as sdb9 is both the bulk of the 1TB drive and contains all of the files in question but they both seem to mount automatically.

We don't have to worry about anything but the data.  If we can move it to a directory on the root (/) partition we can reformat the /dev/sdb device as a single ext4 partition.
> 

[LIST]
[*]andrew storage
[*]wife storage
[LIST]
[*]can the /home/user  directory serve the function?
[/LIST]
Yes.  This is what you want to do.  Use the /home directories for your personal data.  The kids would also have their own personal space. 

[*]family shared files
[*]single directory for everyone's backups
[/LIST]
The original NAS was fairly disorganized. Movies were in folders *Kids *or *Parents *with the files being within their own sub-folders (mostly...or directly in the *Kids* folder). With some cleaning up, this still seems to make sense.
iTunes is a typical iTunes-built folder structure with each artist directory and album sub-directory.
You will have to share these things via Samba (for the MAC and Windows clients), so I would think we should have something like this: 
//Server/kids_movies
//Server/parents_movies
//Server/public

//Server/andrew
//Server/wife

//Server/itunes 

This means we need to create some file system structure like this:
/srv/nas/movies/kids
/srv/nas/movies/parents
/srv/nas/public
/srv/nas/itunes

/srv/backup

I have separated the /srv/backup from the /srv/nas  so you can expand data storage by adding the other HDD id you want.  Think of the 2 as separate (/srv/nas vs /srv/backup).

The big thing right now is; can we move the data off of sdb2?

---

### Post by andrew283 on 2016-02-10
> **bab1 said:**
> Does the above sdb2 partition (noted in blue) have all the data?  What does the above sdb9 partition (noted in red) have in it?  Ca we move all the data to the main partition (noted in green)?
We don't have to worry about anything but the data.  If we can move it  to a directory on the root (/) partition we can reformat the /dev/sdb  device as a single ext4 partition.
Blue - all the data
sdb9 red - appear to be OS files from the LACIE NAS (including Twonky Vision UPnP)
Yes - all data can be moved.  Currently using fslint to find duplicates before doing so.


> 
You will have to share these things via Samba (for the MAC and Windows clients), so I would think we should have something like this: 
//Server/kids_movies
//Server/parents_movies
//Server/public

//Server/andrew
//Server/wife

//Server/itunes 

This means we need to create some file system structure like this:
/srv/nas/movies/kids
/srv/nas/movies/parents
/srv/nas/public
/srv/nas/itunes

/srv/backup

I have separated the /srv/backup from the /srv/nas  so you can expand data storage by adding the other HDD id you want.  Think of the 2 as separate (/srv/nas vs /srv/backup).

The big thing right now is; can we move the data off of sdb2?
I do want to use both HDDs - that only makes sense. Layout I think makes sense.
750 gb is a lot of data to move from one drive to the other so will sort out the duplicates issue first, then charge away.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> 
I do want to use both HDDs - that only makes sense. Layout I think makes sense.
750 gb is a lot of data to move from one drive to the other so will sort out the duplicates issue first, then charge away.
If some of the data makes sense to you we can put it where it will end up later such as /srv/nas/movies/parents or /srv/nas/movies/kids or ...

Let me know if you need help with that.

---

### Post by andrew283 on 2016-02-10
Perhaps some clarity on how to create the directory in the correct location. At the moment, won't everything I create end up in /home/andrew?  I'm familiar with ```
mkdir /mnt/newdrive
``` for example, but I don't actually know where mnt is - which goes back to my earlier statement that I'm struggling with the *C:\ *Windows structure vs. the Linux layout. I haven't conceptualized it quite yet.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Perhaps some clarity on how to create the directory in the correct location. At the moment, won't everything I create end up in /home/andrew?  I'm familiar with ```
mkdir /mnt/newdrive
``` for example, but I don't actually know where mnt is - which goes back to my earlier statement that I'm struggling with the *C:\ *Windows structure vs. the Linux layout. I haven't conceptualized it quite yet.

Everything in the Linux file system starts at /.  So mnt is a subdirectory of / (i.e. /mnt) and newdrive is a subdirectory of /mnt.  You can see all the subdirectories below / with this command```
ls -l /
```

The only subdirectories a mortal user can make are in that users /home directory.  A directory such as /home/<user>/newdirectory is possible.  You can use sudo to become root to make a directory outside of your home directory.

The command cd (change directory) will allow you do change to a different working directory (the dir that you are "in").  If you wanted to make a directory that is several levels deep (/srv/nas/kids/movies you can use the -p switch.  This automatically makes all the subdirectories in the path; such as```
sudo mkdir -p /srv/nas/kids/movies 
``` will make below /srv these subdirs nas kids movies.

Speaking of paths.  Think of the subdirectories as stepping stones on a path to the directory you want the data to be in.  The absolute path always starts at the beginning ( / ).  The relative path is relative to the working directory you are in.

Where do you want the data to end up?

---

### Post by andrew283 on 2016-02-10
That makes sense - thank you.  I assume, based on your recommendations and the existing presence of /srv that it's traditional use is for file serving?

> **yancek said:**
> There are any number of ways to do backups.  I believe if you look in System Settings on your Ubuntu, you will see a backup program.  You can use simple scripts to do this also and put an entry in a cron entry to do it on a regular basis.  Lots of examples of cron entries available from Mr Google.
Thanks for that yancek - I'll search it out.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> That makes sense - thank you.  I assume, based on your recommendations and the existing presence of /srv that it's traditional use is for file serving?

/srv is the traditional location of that kind of data.

```
/srv  --  Site specific data for services provided by the system (i.e. servers)
```

See [here]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for the rest of the hierarchy

---

### Post by andrew283 on 2016-02-10
So, I was going to go with ```
mv /mnt/oldnas/openshare/movies_kids /srv/nas/movies/kids
``` but I suspect that will give me a folder called movies_kids in the new nas folder. How do I copy the contents (recursively) instead?

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> So, I was going to go with ```
mv /mnt/oldnas/openshare/movies_kids /srv/nas/movies/kids
``` but I suspect that will give me a folder called movies_kids in the new nas folder. How do I copy the contents (recursively) instead?

I recommend you copy the data rather than move it.  Just in case it all goes terribly wrong.

If you want to copy data to a root owned directory you need to use sudo.  You also need to make it recursive with the -R switch.

The command is ```
sudo cp -R /mnt/oldnas/openshare/movies_kids/*   /srv/nas/movies/kids/
```
The * says add the data but not the folder.  The rest of the subdirectories and their contents will be copied over too.

[COLOR="#0000FF"]Edit:  I assume you have made the /srv/nas/movies/kids/  directories.
Edit2: Do not worry about the ownership or permissions at this stage.  We take care of that later.  [/COLOR]

---

### Post by andrew283 on 2016-02-10
Thanks BAB1. I understand sudo / root vs. user - that's fairly straight forward. The directories have been created and I'll move the non-duplicate contents. The only hitch will be in the iTunes folder - that's where the dupes are lurking.

---

### Post by bab1 on 2016-02-10
> **andrew283 said:**
> Thanks BAB1. I understand sudo / root vs. user - that's fairly straight forward. The directories have been created and I'll move the non-duplicate contents. The only hitch will be in the iTunes folder - that's where the dupes are lurking.
Let me know when you have all the data copied over.  Then we can move on to the next step of creating a new partition and formatting it on the old HDD.

---

### Post by andrew283 on 2016-02-10
It's slowly grinding away. I appear to have logged off or otherwise interrupted fslint before it was finished with the iTunes work I'm afraid.  The terminal window is not very communicative with the time to go with file transfers is it :D Not that Windows was accurate...

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> It's slowly grinding away. I appear to have logged off or otherwise interrupted fslint before it was finished with the iTunes work I'm afraid.  The terminal window is not very communicative with the time to go with file transfers is it :D Not that Windows was accurate...

I'm getting tired anyway. There is always tomorrow.  I'll be here.

---

### Post by andrew283 on 2016-02-11
Thanks for all your help today. Much appreciated.

Hokay...  All files moved to their new homes now. Stayed up into the wee hours trying to find a way to shorten the process but in the end it was more expedient to just move everything. 

I used sudo su to enable me to move my wife's files off the old drive into /home/wife/, moved the family files to /srv /nas/public/, moved iTunes and so on. Following the official doc, I tried to create a samba share to the old /mnt /oldnas/openshare/iTunes but met with only partial success.  I could see the share on the windows machine, but it kept reporting that my credentials were incorrect. I deleted the share and that's where I am now.

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> Hokay...  All files moved to their new homes now. Stayed up into the wee hours trying to find a way to shorten the process but in the end it was more expedient to just move everything. 

I used sudo su to enable me to move my wife's files off the old drive into /home/wife/, moved the family files to /srv /nas/public/, moved iTunes and so on. Following the official doc, I tried to create a samba share to the old /mnt /oldnas/openshare/iTunes but met with only partial success.  I could see the share on the windows machine, but it kept reporting that my credentials were incorrect. I deleted the share and that's where I am now.

Just to be sure.  All the files that you want have been copied to where you want them to be under /srv/nas.  Is that correct?

[COLOR="#0000FF"]Edit:  Let's list them with this command[/COLOR]```
ls -l /srv/nas
```

---

### Post by andrew283 on 2016-02-11
Yes. The original drive can be reformatted / partitioned entirely.

```
andrew@media-srv:/$ ls -l /srv/nas
total 96
drwxr-xr-x 2030 root root 86016 Feb 11 17:27 itunes
drwxr-xr-x    4 root root  4096 Feb 10 19:29 movies
drwxr-xr-x    5 root root  4096 Feb 11 17:34 public
drwxr-xr-x    7 root root  4096 Feb 11 18:18 tv
```
edited for formatting

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> ```
andrew@media-srv:/$ ls -l /srv/nastotal 96
drwxr-xr-x 2030 root root 86016 Feb 11 17:27 itunes
drwxr-xr-x    4 root root  4096 Feb 10 19:29 movies
drwxr-xr-x    5 root root  4096 Feb 11 17:34 public
drwxr-xr-x    7 root root  4096 Feb 11 18:18 tv
```

Here is what I think we should do.  First thing we do is to set the ownership and permissions on the subdirectories of /srv/nas.  Then we will share these with Samba   The last task is to partition and format the old HDD.  It will become the backup HDD.  We can mount it at /srv/backup as the final part of our configuration of the server.

If this sounds good to you, let's set the permissions and ownership on /srv/nas/public.  Under most conditions, I would put all the users involved in sharing in a group called ***users***.  But in your case all the users are part of the kids group (the lowest common denominator) and we could use that group.  But my neat mind would say add the individual kids to the ***users*** group and use the ***users*** group as the group-owner of /srv/nas/public.  In that way if you wanted to add another user to allow access to/srv/nas/public you can  A short digression but worthwhile in the long run.

To add the users to the ***users***  group we should use this command```

sudo addgroup <user_name> users

```... for andrew, wife, kid1, kid2 and kid3

Check your work with ```
getent group users
```

In the long run this will be more flexible and understandable when administrating the system.

If that works you can then change the ownership of the /srv/nas/public branch with this command```
sudo chown -R root:users /srv/nas/public 
```
Post the output of this command to see your work```
ls -l /srv/nas/public
```

---

### Post by andrew283 on 2016-02-11
getent returns *```
ser:x:100:andrew, wife, kid1, kid2, kid3
``` *as expected.
```
andrew@media-srv:~$ ls -l /srv/nas/public
total 4492
-rwxrwxrwx 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxrwx 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxrwx 3 root users    4096 Feb 10 12:23 Annie
drwxrwxrwx 3 root users    4096 Dec 29  2011 Novel
-rwxrwxrwx 1 root users 1937534 Dec 30  2003 cover.jpg
drwxrwxrwx 4 root users    4096 Dec 29  2011 Pics


```

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> getent returns *```
ser:x:100:andrew, wife, kid1, kid2, kid3
``` *as expected.
```
andrew@media-srv:~$ ls -l /srv/nas/public
total 4492
-rwxrwxrwx 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxrwx 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxrwx 3 root users    4096 Feb 10 12:23 Annie
drwxrwxrwx 3 root users    4096 Dec 29  2011 Novel
-rwxrwxrwx 1 root users 1937534 Dec 30  2003 cover.jpg
drwxrwxrwx 4 root users    4096 Dec 29  2011 Pics


```

Now we need to change the permissions with this command```
sudo chmod -R ug=rwX,o=rX /srv/nas/public
```

Post the output of this command ```
ls -l /srv/nas/public
```

---

### Post by andrew283 on 2016-02-11
```
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rwxrwxr-x 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxr-x 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rwxrwxr-x 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics


```
If I understand permissions correctly, this means that root and owners (which were assigned with previous chown command) have read/write/execute permissions, but others have only read and execute.  In this scenario, who (or what) would comprise members of "other"? 

Edited to add: What does execute permission provide that a combination of read and write do not?

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> ```
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rwxrwxr-x 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxr-x 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rwxrwxr-x 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics


```
If I understand permissions correctly, this means that root and owners (which were assigned with previous chown command) have read/write/execute permissions, but others have only read and execute.  In this scenario, who (or what) would comprise members of "other"? 

Edited to add: What does execute permission provide that a combination of read and write do not?

In this case root is the owner and the user group is users.  The have read and write permissions and the ability to read directories (traverse).  The 3rd group is all other users on the system.  Under this system all the others (guests and system users) can read directories (traverse) and read files.

I want to see the exact command you used.  The jpg files should not be eXecutable.

[COLOR="#0000FF"]Edit:  I guess this problem is due to setting the permissions to 777 earlier.  No problem.  We just need 2 steps to cure it.  I'll wait to see your response.[/COLOR]

---

### Post by andrew283 on 2016-02-11
```

andrew@media-srv:/srv/nas$ sudo chmod -R ug=rwX,o=rX /srv/nas/public
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rwxrwxr-x 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxr-x 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rwxrwxr-x 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics

```

[IMG]https://dl.dropboxusercontent.com/u/44764511/uf_chmod.jpg[/IMG]

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> ```

andrew@media-srv:/srv/nas$ sudo chmod -R ug=rwX,o=rX /srv/nas/public
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rwxrwxr-x 1 root users  126402 Sep 17  2012 317.JPG
-rwxrwxr-x 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rwxrwxr-x 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics

```

We need to first remove all executable bits with this```
sudo chmod -R 600 /srv/nas/public
```...this strips the executable bits off of all files and directories.

Then we add back what we want with ```
sudo chmod -R ug=rwX,o=rX /srv/nas/public
```... the UPPER CASE X adds executable only on existing eXecutable file bits.  ;-)

Post the output again of ```
ls -l /srv/nas/public
```

---

### Post by andrew283 on 2016-02-11
```

andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rw-rw-r-- 1 root users  126402 Sep 17  2012 317.JPG
-rw-rw-r-- 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rw-rw-r-- 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics


```
[SIZE=1]*goes to man chmod...*[/SIZE]

> [COLOR=#0000FF]  I guess this problem is due to setting the  permissions to 777 earlier.  No problem.  We just need 2 steps to cure  it. [/COLOR]
Something tells me we might see more of this...8-[

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> [IMG]https://dl.dropboxusercontent.com/u/44764511/uf_chmod.jpg[/IMG]
Yes, I know they are color coded.  I only need to look at the perms (on the left) to see the problem.  Some of this stuff I check out on my machine before I give you the command.  :D

> **andrew283 said:**
> Something tells me we might see more of this...8-[

Yes.  Each one of the subdirectories will require a 2 step process.

> **andrew283 said:**
> 
Edited to add: What does execute permission provide that a combination of read and write do not?

You are adding it only to the directories.  It allows you to traverse (descend into) and read the contents of the directories.

---

### Post by Bucky Ball on 2016-02-11
*Thread moved to **Server Platforms**.*

---

### Post by andrew283 on 2016-02-11
> **bab1 said:**
> Yes.  Each one of the subdirectories will require a 2 step process.
Okay - that seems fairly straight forward without any gotchas. I've assigned owners to /srv/nas/movies/kids, /parents, /nas/tv/kids, /parents (kids and parents groups as owners obviously), but not changed the permissions. At the present time, the /tv and /movies are root root with the subs being divided up between kids and parents. Should they be root parents instead?

I suspect we'll come across all sorts of remnants of my messing around in the late hours last night.

---

### Post by bab1 on 2016-02-11
> **andrew283 said:**
> ```

andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rw-rw-r-- 1 root users  126402 Sep 17  2012 317.JPG
-rw-rw-r-- 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwxr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwxr-x 3 root users    4096 Dec 29  2011 Crayola
-rw-rw-r-- 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwxr-x 4 root users    4096 Dec 29  2011 Pics


```
[SIZE=1]*goes to man chmod...*[/SIZE]

Now comes the magic.  We need to configure the user-group to inherit the group ownership of the root directory (in this case /srv/nas/public).  In other words when a user creates a file or directory below /srv/nas/public we want the user-group to be ***users***.  To do that we set the SGID bit on the /srv/nas/public directory.  Use this command to do that```
sudo chmod -R g+s /srv/nas/public
```

Post the output of this command```
ls -l /srv/nas/public
```...note the s in the user-group permissions.

---

### Post by andrew283 on 2016-02-11
```
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rw-rwSr-- 1 root users  126402 Sep 17  2012 317.JPG
-rw-rwSr-- 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwsr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwsr-x 3 root users    4096 Dec 29  2011 Crayola
-rw-rwSr-- 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwsr-x 4 root users    4096 Dec 29  2011 Pics

```
There's s and S permissions now. This means that any new content created within /public will have the same permissions as the existing /public folder?

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Okay - that seems fairly straight forward without any gotchas. I've assigned owners to /srv/nas/movies/kids, /parents, /nas/tv/kids, /parents (kids and parents groups as owners obviously), but not changed the permissions. At the present time, the /tv and /movies are root root with the subs being divided up between kids and parents. Should they be root parents instead?

I suspect we'll come across all sorts of remnants of my messing around in the late hours last night.

Did you see the part about setting inheritance?

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> ```
andrew@media-srv:/srv/nas$ ls -l /srv/nas/public
total 4492
-rw-rwSr-- 1 root users  126402 Sep 17  2012 317.JPG
-rw-rwSr-- 1 root users 2518749 Sep 19  2012 323.JPG
drwxrwsr-x 3 root users    4096 Feb 10 12:23 Annie
drwxrwsr-x 3 root users    4096 Dec 29  2011 Crayola
-rw-rwSr-- 1 root users 1937534 Dec 30  2003 IMG_0090.jpg
drwxrwsr-x 4 root users    4096 Dec 29  2011 Pics

```
There's s and S permissions now. This means that any new content created within /public will have the same permissions as the existing /public folder?
Use parent for relative addressing /parent is not the same as parent or ../parent.

Yes, you can create a zero byte file like this ```
touch /srv/nas/public/testfile
```...see if you can see the testfile.

[COLOR="#0000FF"]Edit:  I'm going to pause here for a minute so we can both be at the same place.  We are overrunning each other here.[/COLOR]

---

### Post by andrew283 on 2016-02-12
> [COLOR=#0000FF] I'm going to pause here for a minute so we can both be at the same place.  We are overrunning each other here.[/COLOR]
Aye - agreed. I'll start here...
> **bab1 said:**
> Did you see the part about setting inheritance?
I did, but I'm not sure I fully understand.

I have 
[LIST]
[*]/srv/nas/movies (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/tv       (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/public  (root users)
[/LIST]

Within public (duly noted diff between *public* and */public*), ```
sudo chmod -R g+s /srv/nas/public
``` will assign all newly created content the same permissions as the existing content, which is inherited from the owner group *users*. (Correct?)

Extrapolating to the various *kids* and *parents* sub-directories, I understand that. However, I'm unclear (and perhaps unnecessarily focusing on) the higher level */srv/nas/movies *and */srv/nas/tv* "top level" directory owners. Having said that, /srv and /srv/nas are unchanged from root root, which as I type makes me think I'm making much ado about nothing.

For clarity then: the correct command for the various kids and parents group owned sub-directories (oh...that's a poorly formed sentence...) would have inheritance assigned with 
```
sudo chmod -R g+s /srv/nas/movies/kids
sudo chmod -R g+s /srv/nas/movies/parents
```
and so forth?

---

### Post by bab1 on 2016-02-12
If I understand correctly you have split the branch of ../movies and ../tv along the kids and parents group-ownership.  I think you are doing great!  Show me your work with with these commands ```
ls -l /srv.nas/movies/kids

ls -l /srv/nas/movies/parents

ls -l /srv/nas/tv/kids

ls -l /srv/nas/tv/parents
```

We don't have to differentiate with the permissions as they are the same on all the subdirectories.  The access control is by usr-group (**authentication**).  The *authorization* is then passed by the permissions.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Aye - agreed. I'll start here...

I did, but I'm not sure I fully understand.

I have 
[LIST]
[*]/srv/nas/movies (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/tv       (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/public  (root users)
[/LIST]

Within public (duly noted diff between *public* and */public*), ```
sudo chmod -R g+s /srv/nas/public
``` will assign all newly created content the same permissions as the existing content, which is inherited from the owner group *users*. (Correct?)

Extrapolating to the various *kids* and *parents* sub-directories, I understand that. However, I'm unclear (and perhaps unnecessarily focusing on) the higher level */srv/nas/movies *and */srv/nas/tv* "top level" directory owners. Having said that, /srv and /srv/nas are unchanged from root root, which as I type makes me think I'm making much ado about nothing.

For clarity then: the correct command for the various kids and parents group owned sub-directories (oh...that's a poorly formed sentence...) would have inheritance assigned with 
```
sudo chmod -R g+s /srv/nas/movies/kids
sudo chmod -R g+s /srv/nas/movies/parents
```
and so forth?

We do the SGID bit after we set the normal permissions .

---

### Post by andrew283 on 2016-02-12
> **bab1 said:**
> If I understand correctly you have split the branch of ../movies and ../tv along the kids and parents group-ownership.  I think you are doing great!  Show me your work with with these commands ```
ls -l /srv.nas/movies/kids

ls -l /srv/nas/movies/parents

ls -l /srv/nas/tv/kids

ls -l /srv/nas/tv/parents
```
I have, but I haven't two-step corrected the *permissions *as you outlined on ../public.
```
andrew@media-srv:/srv/nas$ ls -l /srv/nas/movies/parents
total 14265572
-rwxr-xr-x 1 root parents  733054976 Feb 10 20:26 12 Angry Men(1957)
drwxr-xr-x 3 root parents       4096 Feb 10 20:27 13 (2010)
drwxr-xr-x 3 root parents       4096 Feb 10 20:30 300 (2006)
-rwxr-xr-x 1 root parents 1769418330 Feb 10 21:39 Louis_CK_OhMyGod_EXT_HD1280.mp4

```
```

andrew@media-srv:/srv/nas$ ls -l /srv/nas/movies/kids
total 19354832
drwxr-xr-x 3 root kids       4096 Feb 10 20:20 1984
drwxr-xr-x 2 root kids       4096 Feb 10 20:20 A Charlie Brown Christmas (1965)
-rwxr-xr-x 1 root kids    8616830 Feb 10 20:20 BOOGIEWOOGIE.wmv

```
note to self - move 1984...#-o
```

andrew@media-srv:/srv/nas$ ls -l /srv/nas/tv/kids
total 12
drwxrwxrwx  2 root kids 4096 Apr  7  2011 FG-S18
drwxrwxrwx 29 root kids 4096 Jan 30  2015 Top Gear

```
```

andrew@media-srv:/srv/nas$ ls -l /srv/nas/tv/parents
total 8
drwxrwxrwx  6 root parents 4096 Apr 24  2000 AIA
drwxrwxrwx 12 root parents 4096 Jan 28  2014 Breaking Bad

```



> 
We don't have to differentiate with the permissions as they are the same on all the subdirectories.  The access control is by usr-group (**authentication**).  The *authorization* is then passed by the permissions.
Aaaand I'm lost now :|

> We do the SGID bit after we set the normal permissions .
Understood.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Aye - agreed. I'll start here...

I did, but I'm not sure I fully understand.

I have 
[LIST]
[*]/srv/nas/movies (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/tv       (root root)
[LIST]
[*]/kids        (root kids)
[*]/parents   (root parents)
[/LIST]

[*]/srv/nas/public  (root users)
[/LIST]

Within public (duly noted diff between *public* and */public*), ```
sudo chmod -R g+s /srv/nas/public
``` will assign all newly created content the same permissions as the existing content, which is inherited from the owner group *users*. (Correct?)

In a sense, yes.  The + adds the sgid bit to the already assigned permissions.  But you have not yet set the correct permissions, which in out case we need to do in 2 steps (striping the extant permissions and then adding back the correct permissions).
> 

Extrapolating to the various *kids* and *parents* sub-directories, I understand that. However, I'm unclear (and perhaps unnecessarily focusing on) the higher level */srv/nas/movies *and */srv/nas/tv* "top level" directory owners. Having said that, /srv and /srv/nas are unchanged from root root, which as I type makes me think I'm making much ado about nothing.

All users can traverse the tree to the directory needed so the ownership is irrelevant until we get to the directory in question (e.g. public or ../tv/kids or ../tv/parents or some such).

---

### Post by andrew283 on 2016-02-12
2-step permission changes done to both ../movies/kids, /tv/kids and the respective parents directories.
Still needs the SGID update.

```
andrew@media-srv:/srv/nas/movies$ ls -l /srv/nas/movies/kids
drwxrwxr-x 3 root kids       4096 Feb 10 20:20 1984
drwxrwxr-x 2 root kids       4096 Feb 10 20:20 A Charlie Brown Christmas (1965)
-rw-rw-r-- 1 root kids    8616830 Feb 10 20:20 BOOGIEWOOGIE.wmv


```
```
andrew@media-srv:/srv/nas/movies/kids$ ls -l /srv/nas/tv/kids
total 12
drwxrwxr-x  2 root kids 4096 Apr  7  2011 FG-S18
drwxrwxr-x 29 root kids 4096 Jan 30  2015 Top Gear


```

---

### Post by bab1 on 2016-02-12
Let me lead the dance for a bit.  :-)

> **andrew283 said:**
> ...I haven't two-step corrected the *permissions *as you outlined on ../public.
To set the permissions we do this on the various branches (in 2 steps)
```
sudo chmod -r 600 /srv/nas/dir/subdir 

sudo chmod ug=rwX,o=rX /srv/nas/dir/subdir
```
You will need to know whether you use ../dir or ../dir/subdir (tv or movies).

If you don't understand, I will provide the proper invocation for each step.

[QUOTE=BAB1]We don't have to differentiate with the permissions as they are the same on all the subdirectories. The access control is by user-group (authentication). The authorization is then passed by the permissions. [/QUOTE]
> 
Aaaand I'm lost now :|

There is a difference between authentication (who are you?) and authorization (you can do that).  In this case if you are the proper group then the authorization is read write and execute.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> 2-step permission changes done to both ../movies/kids, /tv/kids and the respective parents directories.
Still needs the SGID update.

```
andrew@media-srv:/srv/nas/movies$ ls -l /srv/nas/movies/kids
drwxrwxr-x 3 root kids       4096 Feb 10 20:20 1984
drwxrwxr-x 2 root kids       4096 Feb 10 20:20 A Charlie Brown Christmas (1965)
-rw-rw-r-- 1 root kids    8616830 Feb 10 20:20 BOOGIEWOOGIE.wmv


```
```
andrew@media-srv:/srv/nas/movies/kids$ ls -l /srv/nas/tv/kids
total 12
drwxrwxr-x  2 root kids 4096 Apr  7  2011 FG-S18
drwxrwxr-x 29 root kids 4096 Jan 30  2015 Top Gear


```
So now you need to add the sgid bit just as you described before.  That can be from the top ( the root) of each branch (..tv or ../movies).

Have you set up the others (itunes or ???)

---

### Post by andrew283 on 2016-02-12
I haven't addressed iTunes as of yet. I think for the moment I'll assign ownership to users right at the top as there's no separation in place. That could well change later, but will do for the immediate moment.

A moment or two and I'll get caught up and have the sgid bit assignments completed.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> I haven't addressed iTunes as of yet. I think for the moment I'll assign ownership to users right at the top as there's no separation in place. That could well change later, but will do for the immediate moment.

A moment or two and I'll get caught up and have the sgid bit assignments completed.
Standing by.

---

### Post by andrew283 on 2016-02-12
Apologies - completed. Assigned ownership, updated permissions and assigned inheritance to all directories, at the relevant levels, within /srv/nas

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Apologies - completed. Assigned ownership, updated permissions and assigned inheritance to all directories, at the relevant levels, within /srv/nas

Since both you and your wife can go anywhere and create objects in this structure, the test will be to see if a kid is restricted.  You can switch to one of the kids easily with ```
sudo kid1
```...and use kid1 password.  Then try and access a directory that is group owned by parents.  You should be denied access.

---

### Post by andrew283 on 2016-02-12
```
 andrew@media-srv:/$ su kid1
Password:
Added user kid1.
 
kid1@media-srv:/$ cd /srv/nas/movies/kids
kid1@media-srv:/srv/nas/movies/kids$ cd ..
kid1@media-srv:/srv/nas/movies$ cd parents
kid1@media-srv:/srv/nas/movies/parents$ ls -l
-rw-rwSr-- 1 root parents  733054976 Feb 10 20:26 12 Angry Men

```
Hmmmm...kid1 is definitely not in the parents group according to getent - just andrew and wife.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> ```
 andrew@media-srv:/$ su kid1
Password:
Added user kid1.
 
kid1@media-srv:/$ cd /srv/nas/movies/kids
kid1@media-srv:/srv/nas/movies/kids$ cd ..
kid1@media-srv:/srv/nas/movies$ cd parents
kid1@media-srv:/srv/nas/movies/parents$ ls -l
-rw-rwSr-- 1 root parents  733054976 Feb 10 20:26 12 Angry Men

```
Hmmmm...kid1 is definitely not in the parents group according to getent - just andrew and wife.
Can kid1 read the file "Angry Men"?

---

### Post by andrew283 on 2016-02-12
Stupid question...how do I read a non-text file (or open a jpg) from the terminal?

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Stupid question...how do I read a non-text file (or open a jpg) from the terminal?

It won't read it correctly but you can use this command> less <file_name>  or this ```
cat <file_name>
```

In any event we need to restrict the others (world readable) by setting the permissions a little more restrictive on ../tv/parents and below.  You need to exit the kid1 shell.  Type exit at the shell prompt.  Now we can do this by removing the others r-X from that directory branch.  This will stop access (akin to a locked door).  Lets do this```
sudo chmod -R o-rX /srv/nas/tv/parents
``` 

See what you get now.

---

### Post by andrew283 on 2016-02-12
Well...as andrew, I can no longer CD into the directory /srv/nas/tv/parents :)

Well...as andrew, I can no longer CD into the directory /srv/nas/tv/parents :)
Using sudo su, I can see the file permissions in that directory are drwxrws---  6 root parents

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Well...as andrew, I can no longer CD into the directory /srv/nas/tv/parents :)
So we walk the path.  Post the output of these comands```

ls -l /srv/nas

ls -l /srv/nas/tv

ls -l /srv/nas/tv/parents

```

In addition post the output of this```
getent group parents
```

---

### Post by andrew283 on 2016-02-12
```
andrew@media-srv:/$ ls -l /srv
total 8
drwxr-xr-x 2 root root 4096 Feb 10 19:31 backup
drwxr-xr-x 6 root root 4096 Feb 10 19:31 nas


```

```
andrew@media-srv:/$ ls -l /srv/nas
total 96
drwxrwxr-x 2030 root users   86016 Feb 11 23:18 itunes
drwxr-xr-x    4 root root     4096 Feb 10 19:29 movies
drwxrwsr-x    5 root users    4096 Feb 11 17:34 public
drwxr-xr-x    4 root parents  4096 Feb 11 20:58 tv


```
```
andrew@media-srv:/$ ls -l /srv/nas/tv
total 8
drwxrwsr-x 5 root kids 4096 Feb 11 20:57 kids
drwxrws--- 4 root root 4096 Feb 11 20:58 parents


```
Aha he says...It appears I dropped the ball on the ownership here.

```
andrew@media-srv:/$ getent group parents
parents:x:201:andrew,wife


```

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> ```
andrew@media-srv:/$ ls -l /srv
total 8
drwxr-xr-x 2 root root 4096 Feb 10 19:31 backup
drwxr-xr-x 6 root root 4096 Feb 10 19:31 nas


```

```
andrew@media-srv:/$ ls -l /srv/nas
total 96
drwxrwxr-x 2030 root users   86016 Feb 11 23:18 itunes
drwxr-xr-x    4 root root     4096 Feb 10 19:29 movies
drwxrwsr-x    5 root users    4096 Feb 11 17:34 public
drwxr-xr-x    4 root parents  4096 Feb 11 20:58 tv


```
```
andrew@media-srv:/$ ls -l /srv/nas/tv
total 8
drwxrwsr-x 5 root kids 4096 Feb 11 20:57 kids
drwxrws--- 4 root root 4096 Feb 11 20:58 parents


```
Aha he says...It appears I dropped the ball on the ownership here.
Yes indeed.  But you know how to find and correct it I suppose.

---

### Post by andrew283 on 2016-02-12
```
andrew@media-srv:/$ sudo chown root:parents /srv/nas/tv/parents
andrew@media-srv:/$ cd /srv/nas/tv/parents
andrew@media-srv:/srv/nas/tv/parents$ ls -l
total 8
drwxrws---  6 root parents 4096 Apr 24  2000 AIA
drwxrws--- 12 root parents 4096 Jan 28  2014 Breaking Bad


```
That did the trick to fix the access for me, and a quick su kid1 trip shows that it halt access to ../tv/parents while leaving access to ../tv/kids. So your permission tweak did the trick.

Will apply the new permissions across the directories. 

Looking at the above output of ls -l /srv/nas, it shows root parents for tv, rather than root root as it does for movies. Given that the only items in tv are two sub-directories with their own permissions, does that need to be addressed and corrected back to root root?

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> ```
andrew@media-srv:/$ sudo chown root:parents /srv/nas/tv/parents
andrew@media-srv:/$ cd /srv/nas/tv/parents
andrew@media-srv:/srv/nas/tv/parents$ ls -l
total 8
drwxrws---  6 root parents 4096 Apr 24  2000 AIA
drwxrws--- 12 root parents 4096 Jan 28  2014 Breaking Bad


```
That did the trick to fix the access for me, and a quick su kid1 trip shows that it halt access to ../tv/parents while leaving access to ../tv/kids. So your permission tweak did the trick.

At this point the only thing left to do is install and configure Samba to share the directories over the LAN.

I think we will do that tomorrow.  If you installed Samba that is fine.  Do not mess with the /etc/samba/smb.conf file before making a copy of it.

If you want we can make a copy of it tonight. Then I need some sleep.  Do you have time (a specific time) tomorrow?

> **andrew283 said:**
> Will apply the new permissions across the directories. 

Looking at the above output of ls -l /srv/nas, it shows root parents for tv, rather than root root as it does for movies. Given that the only items in tv are two sub-directories with their own permissions, does that need to be addressed and corrected back to root root?
I do better if I can see the output.

---

### Post by andrew283 on 2016-02-12
I'm pretty cross-eyed myself at this point :)  Thank you for all of your help yet again this evening. Monsters are off school tomorrow so my schedule is fairly wide open. How does 10 AM Pacific sound?
> I do better if I can see the output.
```
andrew@media-srv:/srv/nas/public$ ls -l /srv/nas/
total 96
drwxrwx--- 2030 root users   86016 Feb 11 23:18 itunes
drwxr-xr-x    4 root root     4096 Feb 10 19:29 movies
drwxrws---    5 root users    4096 Feb 12 00:18 public
drwxr-xr-x    4 root parents  4096 Feb 11 20:58 tv
```

I tried entering various directories as kid1 and kid2, as well as trying to create and delete files (touch testfile). Everything, in all directories, for all users including myself, worked as expected now.  Many thanks.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> I'm pretty cross-eyed myself at this point :)  Thank you for all of your help yet again this evening. Monsters are off school tomorrow so my schedule is fairly wide open. How does 10 AM Pacific sound?

```
andrew@media-srv:/srv/nas/public$ ls -l /srv/nas/
total 96
drwxrwx--- 2030 root users   86016 Feb 11 23:18 itunes
drwxr-xr-x    4 root root     4096 Feb 10 19:29 movies
drwxrws---    5 root users    4096 Feb 12 00:18 public
drwxr-xr-x    4 root parents  4096 Feb 11 20:58 tv
```

I tried entering various directories as kid1 and kid2, as well as trying to create and delete files (touch testfile). Everything, in all directories, for all users including myself, worked as expected now.  Many thanks.

I think 10 AM PST is fine for me.My kids are grown and gone.

The correction of ```
drwxr-xr-x    4 root parents  4096 Feb 11 20:58 tv
``` 
... to this ```
drwxr-xr-x    4 root root  4096 Feb 11 20:58 tv
```
... is cosmetic at this point as all users (via others have traversal and read rights to the tv directory.  Neither movies and tv are going to be the root of the Samba share anyway, whereas public and itunes are the root of their shares.

---

### Post by andrew283 on 2016-02-12
Thanks BAB1 - have a good evening...well, night :D

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Thanks BAB1 - have a good evening...well, night :D
You're welcome.  We should finish this tomorrow for sure.

---

### Post by mikodo on 2016-02-12
I apologize for butting in but, this has been a joy to follow. It's ~4 hrs past my bedtime in Saskatoon. Usually up at 05:00 CST. Oh well.

- Waiting for Samba and hopefully the backup scenario BAB1 suggests.

- When it's all said & done, you could consider making this thread a [Tutorial Post]("http://ubuntuforums.org/forumdisplay.php?f=100") Andrew283. (That was one of best small block GM V-8 motors ever made).

---

### Post by bab1 on 2016-02-12
> **mikodo said:**
> I apologize for butting in but, this has been a joy to follow. It's ~4 hrs past my bedtime in Saskatoon. Usually up at 05:00 CST. Oh well.

- Waiting for Samba and hopefully the backup scenario BAB1 suggests.

- When it's all said & done, you could consider making this thread a [Tutorial Post]("http://ubuntuforums.org/forumdisplay.php?f=100") Andrew283. (That was one of best small block GM V-8 motors ever made).
Hi @mikodo,

I wrote it so that it could become notes on how to configure multiple user directories with Samba shares properly.  It will also work for NFS exports.  In essence it is the same configuration as an off the shelf NAS appliance, only much better, as it can use current Samba and NFS packages.  I'm well aware that others later on will read this stuff

I'm not going to clean it up but all the steps are laid out nicely.

I use rsnapshot with my own wrapper script for backups.  Rsnapshot is a perl wrapper of rsync to begin with.  I could easily use cron (and anacron) to automate the backups.  At the present time I just run the scripts manually in the afternoon and manually update my own logs.  I'm to lazy to automate it these days.  I have the last 10 years of data archived annually in zip files.  I'm well past managing a tape backup silo these days.  I just manage my home network now.

Having an entire disk to mount at /srv/backup makes it easy to separate the backups from the live data.  When mounted it's just local Linux to local Linux.

---

### Post by andrew283 on 2016-02-12
> **mikodo said:**
> I apologize for butting in but, this has been a joy to follow. It's ~4 hrs past my bedtime in Saskatoon. Usually up at 05:00 CST. Oh well.

- Waiting for Samba and hopefully the backup scenario BAB1 suggests.

- When it's all said & done, you could consider making this thread a [Tutorial Post]("http://ubuntuforums.org/forumdisplay.php?f=100") Andrew283. (That was one of best small block GM V-8 motors ever made).

Hardly butting in! I'm glad to see it's of interest to someone besides me :D I'm enjoying this trip rather a lot. (283 was appended by the forum automatically - I tend to favour the ultra-rare ZZ302 from the '69 Z myself, or unobtanium ZL1 of the same era ;) )

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Hardly butting in! I'm glad to see it's of interest to someone besides me :D I'm enjoying this trip rather a lot. (283 was appended by the forum automatically - I tend to favour the ultra-rare ZZ302 from the '69 Z myself, or unobtanium ZL1 of the same era ;) )
I've moved on; how about a LS7 in a '69 Camaro resto.  Easy to do here in So Cal.

Do you have Samba installed?  If so how did you install it?  Via tasksel or apt?

---

### Post by andrew283 on 2016-02-12
Samba installed during initialization so I assume that's taskel. 

I could get with an LS7...

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Samba installed during initialization so I assume that's taskel. 

I could get with an LS7...

There are 2 parts to the Samba configuration.  First is making the server browsable on the LAN.  This part is done in the [global] section of the smb.conf file.  The second part is configuring the [homes] share for the users private shares and adding the genreal shares at the bottom of the smb.conf file.  Did you mess with the smb.conf file?  Can you see the Samba server at all from the clients?

How about a LS7 stroker?  That would be a custom tall block and crank for 502 CID and 700+ HP.

---

### Post by andrew283 on 2016-02-12
Before I first messed around with it, I made a copy

```
 sudo cp smb.conf smb.conf.old
```

Before last night's ownership and permissions lesson, I tried to create a share but was only partially successful. I deleted the share and have left it alone.

> **bab1 said:**
> 
How about a LS7 stroker?  That would be a custom tall block and crank for 502 CID and 700+ HP.
Can we get 502 out of a late LS? Yowza.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Before I first messed around with it, I made a copy

```
 sudo cp smb.conf smb.conf.old[/conf]  <-- This is better accomplished by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the editor and pasting the data between the [noparse][CODE]
```[/noparse] blocks.  Note the ending block uses a leading / ; not a \.

Before last night's ownership and permissions lesson, I tried to create a share but was only partially successful. I deleted the share and have left it alone.You can see the server I assume.  By default the smbd deamon (Samba) relies on a correctly configured /etc/hosts file and the proper running of the nmbd daemon for name resolution.  I usually eliminate all of that by declaring the NetBIOS name explicitly.  I also set the name resolve order to bcast as that is what it always ends up using on a small single segment home LAN.

Do you want the sever name to be something other than its hostname of media-srv?  This can be changed at any time.  We can come back to it as a last task.

Lets set up the public share as it is the easiest.  Although the share will be available to all, it can be setup so that no password is needed.  Or it can be setup so that all users use their password to access.  The difference is that with the "no password" option, all users become the user **nobody** and the user-group is **nogroup**.  Of course we convert the user-group to users, but we won't have a true user name (creator of the file).  Any preferences?

Either way any user will be able to modify or delete other users file in this share.  Is that okay?

This is the configuration you can user for your public share```
[Public]
        comment = Shared Data
        path = /srv/nas/public
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = .smb-trash
        recycle:keeptree = yes
        recycle:versions = yes

```

An annotated (in red) version is below  ```

[Public]  [COLOR="#FF0000"]<--Tthe name of the share[/COLOR]
        comment = Shared Data [COLOR="#FF0000"]<-- Comment used in some test scripts[/COLOR]
        path = /srv/nas/public [COLOR="#FF0000"]<-- Location of the data[/COLOR]
        browseable = yes  [COLOR="#FF0000"]<-- Visible to all users when browsing[/COLOR]
        guest ok = yes  [COLOR="#FF0000"]<-- No login needed (all users are nobody:nogroup)[/COLOR]
        force group = users  [COLOR="#FF0000"]<-- Forces the user-group of your choice [/COLOR]
        writeable = yes  [COLOR="#FF0000"]<-- Allows writing to the share[/COLOR]
        create mask = 0664  [COLOR="#FF0000"]<-- Sets the created file permissions [/COLOR]
        force directory mode = 2775  [COLOR="#FF0000"]Sets the created directory permissions[/COLOR]
        vfs objects = recycle  [COLOR="#FF0000"]The following sets up a recycle bin that is a hidden directory[/COLOR]
        recycle:repository = .smb-trash [COLOR="#FF0000"]<-- the hidden directory[/COLOR]
        recycle:keeptree = yes
        recycle:versions = yes

```

I have this setup on my Samba server so I know it works.

[COLOR="#0000FF"]Edit: Or we can alter it to force login and preserve the actual usernames[/COLOR]

[COLOR="#800080"]Edit2: I forgot to mention that you need to restart the Samba server (smbd) after adding the share.  The incantation is [/COLOR]```
sudo service smbd restart
```

> **andrew283 said:**
> Can we get 502 out of a late LS? Yowza.

See [**here**]("http://www.chevyhardcore.com/tech-stories/engine/engine-build-rhs-backed-700hp-ls-big-block/").

---

### Post by andrew283 on 2016-02-12
> his is better accomplished by clicking on the [SIZE=5]**#**[/SIZE]  icon at the top of the editor and pasting the data between the   blocks.  Note the ending block uses a leading / ; not a \.

Full agreement - but my quick reply window doesn't have that, only the advanced, which for two or three lines seemed an unnecessary step.


[LIST]
[*]Yes, when I open my Windows network tab, \\media-srv\ shows up.
[/LIST]
 
[LIST]
[*]Name can stay the same for the time being but learning to change it is worthwhile.
[*]Public password or not: From a security perspective, does no password mean that anybody on the network can access the folder, or just those in group users?
[*]Add/delete other's files with the ../public - yes, that's fine. That's a large part of it's use - co-working on files.
[/LIST]

I will add the code you've outlined and test it.

Delay to a space-time convergence of a slingshot and a lego block followed almost immediately by a similar convergence of said lego block and child's eye.  Yay dad!

Woohoo!  Success!  I can see the Public share, add a file and delete a file.

> 
create mask = 0664
force directory mode = 2775
Can you elaborate on this a little more?

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Public password or not: From a security perspective, does no password mean that anybody on the network can access the folder, or just those in group users?

Yes, without a password means any user that is on your network (friend or someone else next door) has full access to the share.  They may not be able to change anything as the Linux file permissions won't all write permissions.  The share authenticates the user of the share (who are you) and the Linux permissions authorizes (you can do that) the user action at the file system level.  [COLOR="#0000FF"]Authenticate[/COLOR] /  [COLOR="#FF0000"]Authorize[/COLOR]. 
> 

Delay to a space-time convergence of a slingshot and a lego block followed almost immediately by a similar convergence of said lego block and child's eye.  Yay dad!
Now dad............  Don't let mom know.

> **andrew283 said:**
> Woohoo!  Success!  I can see the Public share, add a file and delete a file.
> The deleted file should be in the .smb-trash directory.  Hit ctrl+h to see the hidden directory

```
create mask = 0664
force directory mode = 2775 
```
Can you elaborate on this a little more?
When you create a file or directory there is a set of default permissions set.  These directives restate (or modify) the default settings for this share area. In the past the defaults were incomparable with multi-user use.  Remember how we had to alter the permissions and ownership setting?

[COLOR="#0000FF"]Edit:  Do you want to restrict this share to only the family and use the login?[/COLOR]

---

### Post by andrew283 on 2016-02-12
> **bab1 said:**
> When you create a file or directory there is a set of default permissions set.  These directives restate (or modify) the default settings for this share area. In the past the defaults were incomparable with multi-user use.  Remember how we had to alter the permissions and ownership setting?

[COLOR=#0000FF]Edit:  Do you want to restrict this share to only the family and use the login?[/COLOR]
Yes please. Conceptually, this isn't a public folder, it's a family folder. :) 

I do remember having to change the permissions, yes.

So, the samba share identifies you as belonging to group user or or kids or whichever, and the Linux systems takes that identity and restricts your activities according to your permissions. What permissions does a no-group user get?

> **bab1 said:**
> Now dad............  Don't let mom know.
We're like Vegas - what happens with dad stays with dad...until someone squeals.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Yes please. Conceptually, this isn't a public folder, it's a family folder. :) 

I do remember having to change the permissions, yes.

So, the samba share identifies you as belonging to group user or or kids or whichever, and the Linux systems takes that identity and restricts your activities according to your permissions. What permissions does a no-group user get?
Public for the network or public for the world?  In any event we can change this to ```

[Public]
        comment = Shared Data
        path = /srv/nas/public
        browseable = yes
[COLOR="#FF0000"];       guest ok = yes[/COLOR]
 [COLOR="#0000FF"]       guest ok =no
        valid users = @users[/COLOR]
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = smb-trash
        recycle:keeptree = yes
        recycle:versions = yes


```
The red is commented out with the leading ;
The blue is added to: a) allow only Samba users and b) only users that are in the user-group named users

We need to add all of the users to the Samba users database with this syntax```
sudo smbpasswd -a <user_name>
```
You will be prompted for the users Linux password.  Use that users password.

Then restart the Samba server```
sudo service smbd restart
```
You should now be required to login and only users of that Ubuntu machine that are in the **users group** will be authenticated.

---

### Post by andrew283 on 2016-02-12
My code, at the bottom of smb.conf

```
[Public]
        comment = Shared Data
        path = /srv/nas/public
        browseable = yes
;       guest ok = yes
        guest ok = no
        valid users = @ users
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = .smb-trash
        recycle:keeptree = yes
        recycle:versions = yes


```
has an obvious problem that I spotted as I posted this. Beware the whitespace.

Correcting that and restarting the service worked perfectly, however it didn't ask me to log in, it just shows the share. My Win user name is the same - andrew, so is it logging in using the passwords we entered earlier and the Windows login name then?

[COLOR=#0000ff]Edit: I should also learn to write a script that will change all of the user's network passwords from a single entry.[/COLOR]

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> My code, at the bottom of smb.conf

```
[Public]
        comment = Shared Data
        path = /srv/nas/public
        browseable = yes
;       guest ok = yes
        guest ok = no
        valid users = @ users
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = .smb-trash
        recycle:keeptree = yes
        recycle:versions = yes


```
has an obvious problem that I spotted as I posted this. Beware the whitespace.

Correcting that and restarting the service worked perfectly, however it didn't ask me to log in, it just shows the share. My Win user name is the same - andrew, so is it logging in using the passwords we entered earlier and the Windows login name then?
Samba compares the name sent by Windows to the name in the Samba password (smbpasswd) database.  If they are the same it should ask for a password.  It may have cached that from before.  What are the ownership and permissions on a file you create in that share?  I assume you restarted the Samba server, right?

---

### Post by andrew283 on 2016-02-12
```
-rw-rw-r-- 1 andrew users       0 Feb 12 13:46 whatsmypermission.txt
drwxrwsr-x 2 andrew users    4096 Feb 12 13:47 whatarefolderpermissions


```

Created from within the share on the windows machine.

Sorry - missed answering your restart question - yes, restarted as the final step.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> ```
-rw-rw-r-- 1 andrew users       0 Feb 12 13:46 whatsmypermission.txt
drwxrwsr-x 2 andrew users    4096 Feb 12 13:47 whatarefolderpermissions


```

Created from within the share on the windows machine.
Yes!  This is using your Samba/Linux username.  It is working correctly for you.  Log in to the Windows machine as your wife or a kid.  See what happens then.  Samba should ask for a login.  If not then it is Windows helping you along.  You can try a Linux or Mac machine if you want.  Aways use the same username/password combo on all machines.  Each user is distinct, but that user should be the same on all hosts.

Shall we try a TV or Movies share?  Parents or Kids?

---

### Post by andrew283 on 2016-02-12
I'll create new users on my Win machine for this experiment (let the kids use my computer? hahahahah) and log in.

In the meantime, I would like to try ../tv/parents :D

So very pleased with the success here. Thank you Bab1.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> I'll create new users on my Win machine for this experiment (let the kids use my computer? hahahahah) and log in.

How would the kids use the Samba share as it stands now.  Do they have their own devices?  Use that instead.  We don't need to do anything "extra".  Just testing the system as it would be used today and in the future.
> 

In the meantime, I would like to try ../tv/parents :D

So very pleased with the success here. Thank you Bab1.
Lets do this ```

[Parents-TV]
        comment = Shared Data
        path = /srv/nas/tv/parents
        browseable = yes
        guest ok = no
        valid users = @parents
        force group = parents
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = .smb-trash
        recycle:keeptree = yes
        recycle:versions = yes

```...and restart the Samba server
Notice how similar this is to the public folder.  Just change the share name, path, valid users and force group.

---

### Post by andrew283 on 2016-02-12
Woohoo! wife account can log in and see the public folder, create and delete from within the windows environment. As andrew, I can edit / delete the files wife creates and vice versa.  Perfection! Many smiles.

The same success with kid1 file! Yay. Changes propogate immediately as is ideal, so edits I make on the file within terminal from the ipad (that's not fun) are present immediately when opening the file in windows, as you'd expect.

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> Woohoo! wife account can log in and see the public folder, create and delete from within the windows environment. As andrew, I can edit / delete the files wife creates and vice versa.  Perfection! Many smiles.

The same success with kid1 file! Yay. Changes propagate immediately as is ideal, so edits I make on the file within terminal from the ipad (that's not fun) are present immediately when opening the file in windows, as you'd expect.It's important to check the ownership too.  You can use the GUI to check it.  The individual user should show up as the owner/creator of the object while the user-group should always be **users**.

---

### Post by andrew283 on 2016-02-12
> **bab1 said:**
> It's important to check the ownership too.  You can use the GUI to check it.  The individual user should show up as the owner/creator of the object while the user-group should always be **users**.
Owners for the various files in ../public and ../tv/parents were as per their creator
```

wife users
kid1 users
andrew users
------------
wife parents
andrew parents

```
kid1 can see that there's a share called Parents-TV, but can't access it using their username and password. :) Perfect.

This is a good time to stop and take a break - not necessarily for my sake, but for my sake because the kids are getting cabin fever. Need to take them out and run them for a bit!

I'll apply what you've taught me here to the remaining folders and report back, hopefully this evening. The success here has unquestionably been rewarding, and it's spawned a desire to work towards being able to access the server from the internet.

Thanks for the hours of support and teaching!

---

### Post by bab1 on 2016-02-12
> **andrew283 said:**
> This is a good time to stop and take a break - not necessarily for my sake, but for my sake because the kids are getting cabin fever. Need to take them out and run them for a bit!

I'll apply what you've taught me here to the remaining folders and report back, hopefully this evening. The success here has unquestionably been rewarding, and it's spawned a desire to work towards being able to access the server from the internet.

Thanks for the hours of support and teaching!
Check back at least once to let me know it all works.  Later this afternoon or early evening would be great.

---

### Post by andrew283 on 2016-02-12
> **bab1 said:**
> Check back at least once to let me know it all works.  Later this afternoon or early evening would be great.Woah aye aye woah now... :D At least once? We haven't addressed the old drive yet. Or the /home/<user> shares. I'm not sure I'm ready to be set loose :-|

Questions and/or issues that are arising as I go around testing the implementation:
[LIST=1]
[*][SIZE=4][COLOR=#ff8c00][FONT=impact]The *speed!!  Wow it's fast![FONT=garamond][/FONT] *[/FONT][/COLOR][/SIZE]
[LIST=1]
[*][SIZE=4][COLOR=#ff8c00][FONT=impact][/FONT][/COLOR][/SIZE]I have thousands of artists in the iTunes folder, and the old LACIE NAS was sllllloooooooowwwwwwwww.... trying to work in there to clean things up was a nightmare. This is instant.
[/LIST]

[*]Previously, while watching a NAS-based movie, it would occasionally cough and buffer. I have just successfully played 4 movies simultaneously while it served up music to two different users. :KS
[*]I created a folder called z_ in /home/wife and moved the contents over from the old NAS. In order to do this, I had to switch to root, which has made root the owner now. Have since learned I could have simply used *su wife* to change users, and the permissions would have been fine.
[*]Attempting to sudo with kid1 and wife has got me reported. I love the message *This incident will be reported.*
[/LIST]
So there we are - the bulk of the basics completed.  Need to share the home directories and deal with the 2nd drive and this stage, I think, becomes complete!

I'm all caught up with the /srv/nas shares. Testing all the users, they can upload, download, create, delete, edit only where they're supposed to. Users not in the Parent category can see Parent shares, but can't access them. When logged into Windows as kid1, I tried to log into Parent-Movies share using *wife* and it was still refused which is exactly as I'd like it. In a perfect world, users wouldn't see shares to which they have no access/permissions (out of site, out of mind) but it hardly matters.

You asked earlier about how the kids will access things. At the moment, they don't. We're somewhat Luddite in that respect - our kids have no phones, no consoles and no computers. They use computers at school so they're by no means unfamiliar or handicapped when it comes time to use them.  My wife will allow them to use her Mac under supervision on a guest account (they virtually destroyed her previous Asus laptop) and they have limited access to the android tablet and older iphones for games or taking pictures. 

Obviously as they get older, things will change and my oldest is knocking on that door. He uses assistive technology in school now and will likely always do so. I've been thinking about setting up one of the older laptops with Ubuntu for him to use. Still teetering on the "give him the opportunity to learn this stuff from the inside out and truly know it" vs. "wow there are dangerous creeps out there". 

Now for a night of fibreglass and carbon fibre fabrication in the garage (where the "offsite" sever will go eventually). Making up a seat for a '90s era Triumph turned cafe racer.

Of course, this big question is - why do I have the share *homes* which is a duplicate / alias of /home/andrew showing up? I have messed with smb.conf around [homes] in an effort to have it disappear, to no avail.

---

### Post by bab1 on 2016-02-13
> **andrew283 said:**
> Of course, this big question is - why do I have the share *homes* which is a duplicate / alias of /home/andrew showing up? I have messed with smb.conf around [homes] in an effort to have it disappear, to no avail.
I have to apologize.  I took thought I would take a nap and it turned into a long sleep.  

I have a friend in Edmonton who rides a Harley.  I kid him about being able to ride only the 3 weeks of summer.  Haha.  He spend time here in So Cal where its summer all the time.

The homes share can be made invisible by changing the  **browseable = yes** to ** browseable = no**.  Then the user just has to know that the share is //server/<user_name>  Of course the user can bookmark the location so it will show up on the left pane of the file manager display.  I would not let the kids use your account.  Get in the habit of them using there own account on whatever client they end up using.  Each user has their own configuration files in their home directory.

The Lacie uses Samba v2 where Ubuntu uses Samba v4.  There have been speed improvements made to the SMB protocol.  But my guess is the I/O speed of the HDD you are using is also faster than the drive from the Lacie.

So where do we stand right now?  Finish off the [homes] share.  I'm sure you saw the lines that you had to uncover.  It looks like you have the iTunes set up already.  Are we down to just formatting the old Lacie HDD and setting up the mount commands for it?  I'm not sure what backup scheme you want to use.  We will have to talk about that.

Sorry for the late arrival back here by me.  At least you have time to get some MC stuff done.

---

### Post by andrew283 on 2016-02-13
> **bab1 said:**
> I have to apologize.  I took thought I would take a nap and it turned into a long sleep.  
That's very Canadian of you, to apologise for sleeping. I like naleeps myself, just don't get the chance.

> 
I have a friend in Edmonton who rides a Harley.  I kid him about being able to ride only the 3 weeks of summer.  Haha.  He spend time here in So Cal where its summer all the time.
While by no means California weather, it was +16 'C / 60 'F here earlier this week. A remarkably warm day given Feb typically has two weeks of -30 C. Lots of motorcycles out and about. 

> 
The homes share can be made invisible by changing the  **browseable = yes** to ** browseable = no**.  Then the user just has to know that the share is //server/<user_name>  Of course the user can bookmark the location so it will show up on the left pane of the file manager display.  I would not let the kids use your account.  Get in the habit of them using there own account on whatever client they end up using.  Each user has their own configuration files in their home directory.

The Lacie uses Samba v2 where Ubuntu uses Samba v4.  There have been speed improvements made to the SMB protocol.  But my guess is the I/O speed of the HDD you are using is also faster than the drive from the Lacie.

So where do we stand right now?  Finish off the [homes] share.  I'm sure you saw the lines that you had to uncover.  It looks like you have the iTunes set up already.  Are we down to just formatting the old Lacie HDD and setting up the mount commands for it?  I'm not sure what backup scheme you want to use.  We will have to talk about that.

Sorry for the late arrival back here by me.  At least you have time to get some MC stuff done.

I'm not sure I'm fully grokking the interaction between Windows at the home share, in that the results of *change this parameter in smb.conf, get this behaviour in Windows *does not seem to be consistent. For the moment I have```

[homes]
     comment = Home Directories
     browseable = no
     read only = no
     valid users = %S
;   create mask = 0700 <- commented out
;   directory mask = 0700 <- here too

```
Yesterday it was showing /home/andrew as share andrew and share homes, likewise for /home/wife - share wife, share homes.  Today, with the above homes definition in the smb file, only the named shares are there - behaviour I'd expected. 

I will be away from the server for a while (I need to go to Edmonton oddly enough), so unable to make any changes. In the meantime, are there backup schemes that I can read up on? I have no information from which to make an informed decision.  Really, all that's left of this first project is, as you noted, format and mount the old Lacie drive.

Thank you so much for all of your help Bab1. I've learned a ton, become far more comfortable with the command line and successfully completed a (very) useful little share box.

You can tell your Edmonton friend that your Calgary friend sends his condolences because, well, Edmonton. :)

---

### Post by bab1 on 2016-02-13
> **andrew283 said:**
> I'm not sure I'm fully grokking the interaction between Windows at the home share, in that the results of *change this parameter in smb.conf, get this behaviour in Windows *does not seem to be consistent. For the moment I have```

[homes]
     comment = Home Directories
[COLOR="#FF0000"]     browseable = no[/COLOR]
     read only = no
     valid users = %S
;   create mask = 0700 <- commented out
;   directory mask = 0700 <- here too

```
Yesterday it was showing /home/andrew as share andrew and share homes, likewise for /home/wife - share wife, share homes.  Today, with the above homes definition in the smb file, only the named shares are there - behaviour I'd expected. 

It is working as expected.  The item in red above makes the share disappear from view while browsing.  It is still available via //SERVER/user_name directly.  You can hide any share.  If you wanted to hide //SERVER/Parents-TV you could do that.
> 
I will be away from the server for a while (I need to go to Edmonton oddly enough), so unable to make any changes. In the meantime, are there backup schemes that I can read up on? I have no information from which to make an informed decision.  Really, all that's left of this first project is, as you noted, format and mount the old Lacie drive.

I'll think about what backup system to use and post back as an edit to this post.  It may be much later today.  I have things to do today also.  There are other "housekeeping" items we need to take car of.  We have more to do than just adding the backup disk.  At the present time you are not able to delete any files or directories permanently.  These just disappear from view and end up in a hidden directory.  You need to know how to manage that. 

Let me know when you are back and have time to spend on this project.

---

### Post by sukelis on 2016-02-13
Sorry to bump in, but . . .  I've been following this thread with great interest as I'm planning on doing something similar.  It has been and is a great learning tool.  Not only do we have a great instructor but a very competent student as well, so the value is enormous.  I'm sure there are many of us who are very appreciative of the whole lesson.  

However, I was also reading this thread earlier this morning and when I left my pc around 6AM (eastern) there were 109 posts, but when I came back to it this afternoon, there were only 99 posts.  I thought it must be some fluke, but the missing 10 posts haven't come back, only 2 more new ones.  Any idea where they went?  IFIRC, there was some good stuff in those 10 posts...

---

### Post by andrew283 on 2016-02-14
It appears I fell afoul of some general posting guidelines and posted more than one post before getting a response. I don't *think *anything was deleted, just merged.  Now I know, one post only, then edits only to a previous post - not new posts - or just close my piehole.

---

