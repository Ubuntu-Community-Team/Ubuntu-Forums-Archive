---
title: "A suggestion for features"
date: 2015-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by mcrisonline on 2015-02-07
Hi All,
I am a returned Ubuntu user after actually going sans-PC for quite some time. I don't know how do-able this is, I know Linux in general is heavily geared to security, but I don't think my suggestion is going to impact security.

One of the things I did after I installed Ubuntu was to add another HD, that Home folder of mine was on a tiny HD, no problem.  I am not a dummy so I installed Gparted and formated/partitioned a hard disk (so far so good), but getting the user "mark" permission to write to that hard disk was more of a challenge. I tried sudo using the command prompt but I am getting on a bit and couldn't get the blasted thing to work (my fault I know, I could have asked for help, I know).  All I needed was the ability to write/read the disk.  I did something quite dangerous and typed "Sudo nautilus" and went via GUI to where the hard disk was to change the permissions to "mark".  

Unfortunately a faux-pas with my mouse meant that I released a quite long drop-box list on something and it was neither root nor "mark".  In the end I had to delete the partition again and create/format to get to where I was pre-screw up.  Eventually I selected "mark", closed nautilus and was able to use the hard disk (claps for me).  Anyway, an idea struck me,  would it be possible to either...

allow permissions to change in user mode (rather than ghosting out) after typing in the root password or after using gparted, have a small add on script that basically asks you who can use this disk post format.  In the version of Gparted I had none of the options allowed you to change permissions and I was running GParted using sudo, so everything was GUI except actually allowing you allowing you to set who can use the new disk.

I know Ubuntu doesn't control apps and open source is the bazaar, but I believe Canonical are looking for small, easy ways to make Linux better, and this small issue I believe could be resolved with very little work.

If ideas are not welcome, sorry!

---

### Post by ajgreeny on 2015-02-07
> **mcrisonline said:**
> Hi All,
I am a returned Ubuntu user after actually going sans-PC for quite some time. I don't know how do-able this is, I know Linux in general is heavily geared to security, but I don't think my suggestion is going to impact security.

One of the things I did after I installed Ubuntu was to add another HD, that Home folder of mine was on a tiny HD, no problem.  I am not a dummy so I installed Gparted and formated/partitioned a hard disk (so far so good), but getting the user "mark" permission to write to that hard disk was more of a challenge. I tried sudo using the command prompt but I am getting on a bit and couldn't get the blasted thing to work (my fault I know, I could have asked for help, I know).  All I needed was the ability to write/read the disk.  I did something quite dangerous and typed "Sudo nautilus" and went via GUI to where the hard disk was to [COLOR=#ff0000]change the permissions to "mark".  [/COLOR]

Unfortunately a faux-pas with my mouse meant that I released a quite long drop-box list on something and it was neither root nor "mark".  In the end I had to delete the partition again and create/format to get to where I was pre-screw up.  Eventually I selected "mark", closed nautilus and was able to use the hard disk (claps for me).  Anyway, an idea struck me,  would it be possible to either...

[COLOR=#ff0000]allow permissions to change in user mode (rather than ghosting out) after typing in the root password or after using gparted, have a small add on script that basically asks you who can use this disk post format.  In the version of Gparted I had none of the options allowed you to change permissions and I was running GParted using sudo, so everything was GUI except actually allowing you allowing you to set who can use the new disk.[/COLOR]

I know Ubuntu doesn't control apps and open source is the bazaar, but I believe Canonical are looking for small, easy ways to make Linux better, and this small issue I believe could be resolved with very little work.

If ideas are not welcome, sorry!
A few points about your suggestions!
A user can change permissions on his own files with no problem, but can not make any changes to files owned by any other user.  This is for security and that helps keep Linux as secure as it is.

You don't say in which filesystem you formatted that extra disk, but if it contains your /home partition it must be a Linux filesystem, eg ext4.  This can be set up to allow all users to read/write to it, and no doubt someone could write a script to allow that setup system, but it is easy to do with terminal commands so is probably thought to be not worth it, and I am sorry, but I do not understand what you were trying to do.

Gparted running on your installed ubuntu OS can not make any changes to partitions of that OS as they will, of course, all be mounted and gparted can not act on mounted partitions.  There is no way you can unmount a partition of your running OS; you must run gparted from a live system, CD, DVD or USB to make any changes to an installed OS's partitions.
However, gparted is not the tool to allow you to make changes to permissions of folders, filesystems or partitions; to do that you must use terminal command ```
sudo chmod
``` or to change owner ```
sudo chown
``` but for the moment I think you should slow down, explain more what you are trying to do, as I don't understand some of your comments and questions, eg "[COLOR=#ff0000]change the permissions to "mark".  "[/COLOR]

---

### Post by mcrisonline on 2015-02-07
Thank you for your answer.  I can see I wasn't being too clear.  The issue is not on the drive where ubuntu is installed, nor the home folder, which I decided not to muck around with because if I did something that would cause the PC not to boot I have no recourse to access the internet for help.  No windows partitions for me!

"mark" is my username on the system, what I was trying to say was Gparted does an excellent GUI job of partitioning / formatting drives, but it kind of leaves the job not completely finished, because permissions have to be set so that "mark" can access the drive.  It was automounting in Ubuntu but I couldnt create folders or move media from my Home folder to make room on my 1st hard disk.  

What I was proposing was when the disk creation tool was completed there should be a dialogue box that opens that allows you (as root) to set permission on that drive to plain old user or in my case "mark".  This would make the drive immediately available from exiting Gparted without chmod / chown.

In the end I sorted out the permissions via the command prompt (as you kindly illustrated) but I had to faff around some more so that Plex media server would see the hard disk (it didnt seem to like the name 6563983405304958349080349 or something!) so I again looked up to change it. 

I use the PC as my main PC, it is not a server per-se, I just use it to stream my media files using Plex to my Roku and I must say (I don't wanna go onto another topic) but it does an excellent job.

---

### Post by grahammechanical on 2015-02-07
If it was me, and I have been in this situation myself, I would open the file Manager with administrator (root) privileges by running

```
sudo -H nautilus
```

I would ignore the error messages and when the File Manager loads I would left click on the partition to mount it and then right click the partition and from the drop down menu I would select Properties and in the Permissions tab I would see that I am able to change the permissions for Group and Others from Access files to Create and Delete files.

We can do something similar with folders and files as well. I have several installations of different versions of Ubuntu and a partition for my data. I can access the folders in my data partition with the ability to create and delete files and I can do that from each installation but to create a folder in that data partition I need to run the file manager with administrator privileges and then after creating the folder I must change the permissions for Group and Others.

This works for me.

Regards.

---

### Post by mcrisonline on 2015-02-07
Thanks for the advice.  I prefer to do things GUI because I am more comfortable with it.  That is not to say I am adverse to using bash.  It's a shame you cannot adjust the settings as a plain user and when you try to "apply" them it pops up with the gksudo dialogue box. It scares me to have an entire nautilus session as root open (which I did too) because I am relatively new-again to Ubuntu and was afraid any and all root commands have the potential, if I am not careful to render my system useless (until re-install)!

---

