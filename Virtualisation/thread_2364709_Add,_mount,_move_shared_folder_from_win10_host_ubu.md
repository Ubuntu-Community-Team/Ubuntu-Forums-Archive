---
title: "Add, mount, move shared folder from win10 host ubuntu 17.04 guest in VirtualBox"
date: 2017-06-27
forum: Virtualisation
---

### Post by jetgraphics on 2017-06-27
I am a retro - newbie (last used Linux back in 2004 - Mandriva), but I am confused / baffled.

I want to add shared folders from Win10 to Ubuntu 17.04.
So far, I've successfully installed GUEST ADDITIONS. (Which was a hassle in Kubuntu).
I've located the shared folder sf_name in root/media/username.
I added my username to the vboxsf group.
I can open it as "root." But I cannot access it from my username account so other software can easily see it.
I want to move the folder to home/username/Shared.
And in the future, mount the shared folder to that folder.

I cannot decipher the VB manual, and the various videos have contradictory instructions or they don't work on my system.

From the VB manual - - - 
[I]To change the mount directory to something other than /media, you can set the guest property : 
/VirtualBox/GuestAdd/SharedFolders/MountDir.
[/I]I assumed that SharedFolders = sf_name; MountDir = /home/username/Shared (target)
So I entered /VirtualBox/GuestAdd/sf_SharedFoldername/home/username/Shared in the terminal.
&#8220;No such file or directory&#8221;

Was there something I missed in that simple sentence?
Was that a command to be entered into VB?

Or other variations:
"Protocol error" "Can't find folder" "You are a newbie - go away!"

Can someone please spell out the EXACT procedure to :
[LIST]
[*]MOVE a mounted shared folder 
[/LIST]
-and - 
Set future reboots to 
[LIST]
[*]MOUNT the shared folder to home/username/sharedfolder ? 
[/LIST]

Thank you.

**UPDATE:**
After rebooting, now I can "see" the shared drive in FILES and access them from other applications.
SIGH
. . . 
I guess it is moot with respect to mounting to a different location.

---

### Post by TheFu on 2017-06-27
You cannot "move" a mount using a GUI.  You have to choose where to mount it at mount time.  There are some security reasons why using host-to-guest access isn't a good idea, BTW. 

vbox shares don't handle file locking correctly, so be very careful if you open the same file from both the host and the guest.  My editor refused to open some files because it couldn't get a lock.

The typical mount command would look like this:
```
$ sudo mount -t vboxsf Data /Data
```
"Data" is the name I gave the share inside vbox.
"/Data" is an empty directory where I want the storage to be mounted.

I prefer to never mount storage under a HOME directory, for a number of reasons, but feel free to do whatever you like. Perhaps you won't be burned like I have been.

---

### Post by Morbius1 on 2017-06-28
It seems you have discovered that you need to re-logon to the client to get your vboxsf group membership to take affect so this is for the unlikely possibly that someone wants to actually change the mount point of the shared folder.

[COLOR=#0000cd]*Side Rant: There is a special place in hell for the kind of folks that write the kind of user manuals like VirtualBox. I thought Samba documentation was bad ...*[/COLOR]
> From the VB manual - - - 
[I]To change the mount directory to something other than /media, you can set the guest property : 
/VirtualBox/GuestAdd/SharedFolders/MountDir.
[/I]I assumed that SharedFolders = sf_name; MountDir = /home/username/Shared (target)
So I entered /VirtualBox/GuestAdd/sf_SharedFoldername/home/username/Shared in the terminal.
&#8220;No such file or directory&#8221;

Was there something I missed in that simple sentence?
Was that a command to be entered into VB?

You were missing a whole bunch of stuff:

In the Linux guest run -  I will set it to /mnt in this example:
```
sudo VBoxControl guestproperty set /VirtualBox/GuestAdd/SharedFolders/MountDir /mnt
```
To verify:
```
sudo VBoxControl guestproperty get /VirtualBox/GuestAdd/SharedFolders/MountDir
```
> tester@vlinuxlite:~$ sudo VBoxControl guestproperty get /VirtualBox/GuestAdd/SharedFolders/MountDir
Oracle VM VirtualBox Guest Additions Command Line Management Interface Version 5.0.36_Ubuntu
(C) 2008-2017 Oracle Corporation
All rights reserved.

Value: /mnt

To set it back to where is was under /media - don't do the obvious and run the set command again setting it to /media. Instead you clear it out by setting it to "":
```
sudo VBoxControl guestproperty set /VirtualBox/GuestAdd/SharedFolders/MountDir ""
```
And you have to reboot ( the client ) every time you set this parameter.

I can't think of any use case at the moment where one would want to do this but .......

---

### Post by TheFu on 2017-06-28
> **Morbius1 said:**
>  [COLOR=#0000cd]*Side Rant: There is a special place in hell for the kind of folks that write the kind of user manuals like VirtualBox. I thought Samba documentation was bad ...*[/COLOR]
 
And whoever decided that "vboxsf" was the proper name should never be allowed coffee, tea, candy, or pizza again either.  It should be "**vboxfs**", clearly.  I was burned by this for a week many years ago.

After all, we have n**fs**, ci**fs**, reiser**fs**, btr**fs**, z**fs**, .... they all end in "fs."  Those were just off the top of my head, BTW.

---

