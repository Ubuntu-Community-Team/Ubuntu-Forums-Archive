---
title: "HowTo: Create a shared directory for local users (with bindfs)."
date: 2010-04-22
forum: Tutorials
---

### Post by sisco311 on 2010-04-22
The information in this thread has been moved to [https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers](https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062098#post12062098](http://ubuntuforums.org/showthread.php?p=12062098#post12062098)

Thread closed.



[size=4]**[color=DarkOrange]Before you start[/color]**[/size]

This guide assumes that you already know:
[list]
[*]the basics about Linux file permissions: [uhelp]community/FilePermissions[/uhelp]
[*]how to use the terminal: [uhelp]community/UsingTheTerminal[/uhelp]
[/list]


[size=4]**[color=DarkOrange]Introduction[/color]**[/size]

The guide is aimed to show you how to allow multiple local users to **read and write** (create, delete, rename, modify...) _all files (including newly created ones) from a shared directory and its subdirectories_. If you want to set up more advanced permissions for different users and/or group try [ACLs]("https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport"). 



[size=4]**[color=DarkOrange]About bindfs[/color]**[/size]

[bindfs]("http://code.google.com/p/bindfs/") is a [FUSE](""http://en.wikipedia.org/wiki/Filesystem_in_Userspace") filesystem for mounting a directory to another location (mountpoint), with permission settings. It allows you to specify the ownership and permissions of the files from inside the mountpoint.



[size=4]**[color=DarkOrange]Steps[/color]**[/size]

1. **Installing bindfs**
2. **Create the shared directory**
3. **Setting the permissions with bindfs** 
4. **Testing the settings (Tips & Tricks)**
5. **Setting the permissions at boot time**
[indent]**Method 1 - fstab**
**Method 2 - Upstart**[/indent]
6. **That's all** [noparse]:)[/noparse]


1. [size=4]**Installing bindfs**[/size]

Since Ubuntu 8.10 (Intrepid Ibex), bindfs is in the unverse repository.

[list=i]
[*]Make sure that the repo is enabled, open up a terminal and run:
```
sudo software-properties-gtk --enable-component universe
sudo apt-get update
```



[*]Install it:
```
sudo apt-get install bindfs
```
[/list]


If you are using 8.04 (Hardy Heron), you can install it from [this]("https://launchpad.net/~shenki/+archive/ppa") ppa repository or [compile it by hand]("http://code.google.com/p/bindfs/wiki/Installation").



2. [size=4]**Createing the shared directory**[/size]


[list=i]

[*]e.g. in the /home directory:
```
sudo mkdir /home/shared
```
NOTE: If the directory already exist skip this step.


[*]allow only root to access it, we will set the permissions later with bindfs:
```
sudo chown root: /home/shared
sudo chmod 0700 /home/shared
```
[/list]



3. [size=4]**Setting the permissions with bindfs**[/size]


[list=i]
[*]Now use the bindfs command to mount the shared directory with altered permissions.

Syntax of the command:
```
bindfs [options] dir mountpoint
```


1. example:
```
sudo bindfs -o [color=red]perms=0700[/color],[color=blue]mirror-only=**user1**:**user2**:**user3**[/color] /home/shared /home/shared
```

[color=red]perms=0700[/color] sets the permissions to 0700 (read/write for the owner, none for the group and other);

[color=blue]mirror-only=**user1**:**user2**:**user3**[/color]: **user1**, **user2** and **user3** will see itself as the owner of the files (user names are separated by a colon).


2. example:
```
sudo bindfs -o [color=red]perms=0750[/color],[color=blue]mirror=**user1**:**user2**:**user3**[/color],group=**groupX** /home/shared /home/shared
```

[color=red]perms=0750[/color] sets the permissions to 0750 (read/write for the owner, read permission for the group and none for other);

group=**groupX** makes all files owned by the group **groupX**


For more options, see:
```
man bindfs
```


[*]To unmount the directory:
```
sudo umount /home/shared
```
[/list]



4. [size=4]**Testing the settings (Tips & Tricks)**[/size]

Log in as user1 (user2, user3...) and try to create/delete/rename files in the shared direcctory. You can use the CLI for testing:

[list=i]
[*]To try out different permissions you have to unmount the directory (3.ii.) then remount it with different permissions (3.i.).


[*]You can use *su* or *sudo* to log in as a different user:
```
su - **username**
```
```
sudo -u **username** -i
```
su prompts for the target user's (**username**'s) password, while sudo prompts for your admin password. 

To log out the user press Ctrl+d or run:
```
exit
```


[*]You can run the file manager as a different user. 

1. Allow the user to connect to the X server:
```
xhost +SI:localuser:**username**
```
2. Run the file manager:
```
sudo -u **username** -i nautilus /home/shared
```
3. Test the permissions, then close the file manager.

4. Remove the user form the list of allowed users to connect to the X server:
```
xhost -SI:localuser:**username**
``` 

[/list]

5. [size=4]**Setting the permissions at boot time**[/size]

**Method 1 - fstab**

NOTE: Because of a [BUG in mountall](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/503003) this method doesn't work, in Ubuntu 9.10 or higher (including Natty 11.04 Alpha-1), if the shared directory is not on the root (/) partition. For a workaround see **Method 2 - Upstart** below.

[list=i]
[*]Backup the fstab file:
```
sudo cp /etc/fstab{,-backup}
```

[*]Open it in a text editor:
```
gksu gedit /etc/fstab
```

[*]Add an entry at the end of the file. The syntax of an entry:
```
bindfs#/path/to/dir    /path/to/dir    fuse    options    0    0
```


1. example:
```
bindfs#/home/shared    /home/shared    fuse    [color=red]perms=0700[/color],[color=blue]mirror-only=**user1**:**user2**:**user3**[/color]    0    0
```


2. example:
```
bindfs#/home/shared    /home/shared    fuse    [color=red]perms=0750[/color],[color=blue]mirror=**user1**:**user2**:**user3**[/color],group=**groupX**    0    0
```


[*]Save the file and exit.


[*]Unmount the partition and mount all filesystems mentioned in fstab to check if the entry works as expected:
```
sudo umount /home/shared
sudo mount -a
``` 

[*]If something went wrong, restore the original fstab file:
```
sudo cp /etc/fstab{-backup,}
```
Or edit it and remove the line you added.


[/list]

**Method 2 - Upstart**

NOTE: This method should work in Ubuntu 9.10 or higher. If you are using an earlier release the fstab method is preferred.

We need to create an Upstart job, which executes the bindfs command after all filesystems are mounted.


[list=i][*]Create the job file and open it for editing:
```
gksu gedit /etc/init/mount-bindfs.conf
```


[*]Paste the following code into the file:
```
# Remount directories with bindfs
#
# Temporary workaround until BUG 503003 is fixed
#

description "Remount directories with different permissions"

start on stopped mountall 

script
  bindfs -o [color=red]perms=0700[/color],[color=blue]mirror-only=**user1**:**user2**:**user3**[/color] /home/shared /home/shared
end script

```


[*]Adjust the bindfs options and mount point to fit your needs. Save the file and exit.


[*]Unmount the partition and start the Upstart job to check if it works as expected: 
```
sudo umount /home/shared
sudo initctl start mount-bindfs
```


[*]If something went wrong remove the job file: 
```
sudo rm /etc/init/mount-bindfs.conf
```
[/list]




6. [size=4]**That's all**[/size]

Copy the files you want to share with the other users in the directory (/home/shared). :)




[size=4]**[color=DarkOrange]Links[/color]**[/size]

[http://code.google.com/p/bindfs/](http://code.google.com/p/bindfs/)
[uhelp]community/FilePermissions[/uhelp]
[HowTo: Use ACLs]("https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)



Questions? Suggestions?

---

### Post by CornMaster on 2010-04-26
Looks like a good tutorial.  I haven't had a chance to try it yet, but curious as to what the benefit of this is over simply adding all of your target users to a regular group, making the folder writable by the group and enabling the group access to all future files.

Other then with bindfs, where all users think they own all the files (which I'm not convinced is a good thing. ;)), both solutions would appear to work the same.  Is that a correct interpretation, or are their other benefits gained here?

---

### Post by sisco311 on 2010-04-26
> **CornMaster said:**
> Looks like a good tutorial.  I haven't had a chance to try it yet, but curious as to what the benefit of this is over simply adding all of your target users to a regular group, making the folder writable by the group and enabling the group access to all future files.

Other then with bindfs, where all users think they own all the files (which I'm not convinced is a good thing. ;)), both solutions would appear to work the same.  Is that a correct interpretation, or are their other benefits gained here?

The main benefit is that the new files created in the shared directory will inherit the ownership & permissions.

---

### Post by Morbius1 on 2010-04-26
I hope you don't mind this because I think BINDFS is a gift and I wouldn't have  known about it if not for you, but I have a few suggestions:

**ITEM 2i/2ii**

You're creating a directory "/[COLOR=Blue]home[/COLOR]/shared" then chmod'ed directory "/[COLOR=Blue]media[/COLOR]/shared". I would vote for /home/shared because automounting /media/shared will cause an icon on the desktop. When a user tries to unmount it ( he has no need to unmount it but he'll still try ) he can't because he's not root.

**ITEM 3**

You might want to show them how to unmount it from the terminal. It may not be obvious how one does that.

**ITEM 3.i.2**

Most likely I need to read the manual more carefully but I can't get past this example.

When I first read it I interpreted it to mean that user1,2,3, AND groupX had read / write permissions but it doesn't work. Something like this does:
> sudo bindfs -o perms=0750,mirror-only=user1:user2:user3:@groupX /media/shared /media/sharedThen I figured that what it meant was that user1,2, and 3 related to the "7" in "perms" and groupX related to the "5". But that doesn't work either because "mirror-only" blocks the group out. The only way I can get this to work under this assumption is this way:
```
sudo bindfs -o perms=0750,mirror=user1:user2:user3,group=groupX /media/shared /media/shared
```Again, on item 3.i.2, if this is just a case of me not reading the manual I will not be offended by being told so :wink:

---

### Post by sisco311 on 2010-04-26
> **Morbius1 said:**
> I hope you don't mind this because I think BINDFS is a gift and I wouldn't have  known about it if not for you, but I have a few suggestions:

**ITEM 2i/2ii**

You're creating a directory "/[COLOR=Blue]home[/COLOR]/shared" then chmod'ed directory "/[COLOR=Blue]media[/COLOR]/shared". I would vote for /home/shared because automounting /media/shared will cause an icon on the desktop. When a user tries to unmount it ( he has no need to unmount it but he'll still try ) he can't because he's not root.

**ITEM 3**

You might want to show them how to unmount it from the terminal. It may not be obvious how one does that.


fixed ;)

> **Morbius1 said:**
> 
**ITEM 3.2**

Most likely I need to read the manual more carefully but I can't get past this example.

When I first read it I interpreted it to mean that user1,2,3, AND groupX had read / write permissions but it doesn't work. Something like this does:
Then I figured that what it meant was that user1,2, and 3 related to the "7" in "perms" and groupX related to the "5". But that doesn't work either because "mirror-only" blocks the group out. The only way I can get this to work under this assumption is this way:
```
sudo bindfs -o perms=0750,mirror=user1:user2:user3,group=groupX /media/shared /media/shared
```Again, on item 3.2, if this is just a case of me not reading the manual I will not be offended by being told so :wink:

@group in the mirror mount options means that all members of the group will see themselves as the owner of all files.

Yes, you're right, you can't use mirror-only & group together. (fixed!) 


Thank you very much!

---

### Post by Morbius1 on 2010-05-23
I've been using bindfs in 9.04 and everything has worked just as you're described it, but now that I'm in 10.04 it's not working as expected.

For example I have these two fstab lines in both 9.04 and 10.04 ( I multi-boot ):
```
LABEL=Data /DATA           ext3    defaults        0       2
bindfs#/DATA /DATA fuse perms=0666:+X 0 0
```In 9.04 everything works as expected. In 10.04 the /DATA mount point is empty.

I can recreate the error in 10.04 by commenting out both lines in fstab then:

- adding the bindfs line first followed by a sudo mount -a 
- then adding the normal mount line for /DATA followed by a sudo mount -a.

I receive an error: **mount: according to mtab, bindfs is already mounted on /DATA**
And the partition is empty.  Based on this it would appear that the bindfs line is being executed before the normal mount line. Maybe there was some kind of mechanism that prevented that from happening in 9.04 and now it's missing. Or maybe the accelerated boot process in 10.04 has claimed another victim.

Anyway, this is a long winded way of asking you if you have had any problems using bindfs in 10.04.

---

### Post by sisco311 on 2010-05-23
> **Morbius1 said:**
>  Or maybe the accelerated boot process in 10.04 has claimed another victim.


Probably... I have read about similar issues with network shares (cifs and/or nfs). 

> **Morbius1 said:**
> 
Anyway, this is a long winded way of asking you if you have had any problems using bindfs in 10.04.

To be honest I don't use bindfs (and I also upgraded my Ubuntu installation to maverick :)), but I will try investigate this tomorrow (or today :), it's 2:38am here).

---

### Post by albinootje on 2010-05-23
Very interesting! Thanks for posting this! :)

---

### Post by Morbius1 on 2010-05-24
Well, I'm not smart enough to know why this is happening but I have found out how to avoid the problem. 

You can't bind a directory to itself in 10.04. At least you can't bind a mount point to itself.

If I have this in fstab 10.04 fails but 9.04 does not:
```
LABEL=Data /DATA           ext3    defaults        0       2
bindfs#/DATA /DATA fuse perms=0666:+X 0 0
```But if I change the bindfs mount point to something else it works:
```
LABEL=Data /DATA           ext3    defaults        0       2
bindfs#/DATA /home/Shared fuse perms=0666:+X 0 0

```It's worked through 5 reboots anyway.:wink:

---

### Post by sisco311 on 2010-05-27
> **Morbius1 said:**
> Well, I'm not smart enough to know why this is happening but I have found out how to avoid the problem. 

You can't bind a directory to itself in 10.04. At least you can't bind a mount point to itself.

If I have this in fstab 10.04 fails but 9.04 does not:
```
LABEL=Data /DATA           ext3    defaults        0       2
bindfs#/DATA /DATA fuse perms=0666:+X 0 0
```But if I change the bindfs mount point to something else it works:
```
LABEL=Data /DATA           ext3    defaults        0       2
bindfs#/DATA /home/Shared fuse perms=0666:+X 0 0

```It's worked through 5 reboots anyway.:wink:

This only happens when you try to remount a whole partition. I found another workaround ;), see the OP.

> **albinootje said:**
> Very interesting! Thanks for posting this! :)

You're welcome!

---

### Post by yota on 2010-05-28
You, and obiouvsly Martin Pärtel who did the job in first place, are my heroes!

I have been searching something like this for endless time and neither using sgid or acls worked as I wanted.

File permissions are a great security feature, but the possibility to create non militarized zones in the FS is something which was badly missing in my opinion.

Thank you!

---

### Post by Morbius1 on 2010-05-28
I never considered a hard link. I'll have to try it out. Thanks for the update.

---

### Post by Vishal Agarwal on 2010-05-28
Excellent post

But what all  I love is :
sudo cp /etc/fstab{,-backup}

---

### Post by Morbius1 on 2010-11-14
I was in another post and I was referring the OP to this howto when I discovered you made a change a few weeks ago: [B]Method 2 - Upstart

[/B]That's an elegant way around the problem but I have a question. How is it unmounting ? Entires in fstab are unmounted cleanly at shutdown and it's probably my ignorance of the upstart and bindfs processes but it's not clear how this is being unmounted or if it even needs to be unmounted.

---

### Post by sisco311 on 2010-11-14
> **Morbius1 said:**
> How is it unmounting ? Entires in fstab are unmounted cleanly at shutdown and it's probably my ignorance of the upstart and bindfs processes but it's not clear how this is being unmounted or if it even needs to be unmounted.

All filesystems (including virtual ones: dev, proc, bindfs, autofs...) are unmounted cleanly regardless how they were mounted. 

The init script (/etc/init.d/umountfs) uses /proc/mounts.

/proc/mounts contains a list of the currently mounted devices and their mount points (and which file system is in use and what mount options are in use).

---

### Post by Morbius1 on 2010-11-14
As always, a wealth of information. Thank you very much.

---

### Post by r.darwish on 2011-09-08
Great tutorial!
It works great when trying to set permissions to different folders inside an NTFS partition.

---

### Post by sisco311 on 2011-09-08
Thanks. :)

---

### Post by Morbius1 on 2012-01-11
Now that you're a moderator do you have any influence or at lest any insight on when we can expect to be able to actually install bindfs. 

It's broken on Oneric: [https://bugs.launchpad.net/ubuntu/+source/bindfs/+bug/851600](https://bugs.launchpad.net/ubuntu/+source/bindfs/+bug/851600)

Short version of bug:

Package states that "fuse" is a dependency.
There is no "fuse" package.
Bindfs is dependent on "fuse-util" not "fuse"

---

### Post by s3t_sk8 on 2012-05-16
This thread is amazing!

I use linux for 7 years and I can finally share music with my family without messing with permissions.


I have one more question: Do you guys know how can I do this trick with a separated partition instead of a folder?

I keep all my stuff in a separated drive.


Thanks in advance!

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers](https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012420](http://ubuntuforums.org/showthread.php?t=2012420)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

