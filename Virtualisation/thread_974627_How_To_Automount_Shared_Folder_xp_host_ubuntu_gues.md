---
title: "How To Automount Shared Folder xp host ubuntu guest"
date: 2008-11-07
forum: Virtualisation
---

### Post by wah fun on 2008-11-07
On xp host with ubuntu 8.0.4 guest (Virtual box 2.0.4) I want to automount the shared folder. I can manually mount the folder so it does work. I have googled and searched this web site and found a couple of solutions but nothing seems to work. Since I am a linux noob, I would really appreciate anyone's help with this. I understand the solution probably lies in editing fstab but I can't seem to find the correct information to enter.

My shared folder in Virtual Box is "LinuxShare"
I created the folder xpdocs in mnt (/mnt/xpdocs)

I can manually mount the folder with this command:
sudo mount -t vboxsf /mnt/xpdocs

I would appreciate anyone's help with this.

Thx

---

### Post by yankeeDDL on 2009-01-18
Hello,
I have your same problem: did you find a solution?
Thanks.

---

### Post by ERoe on 2009-02-15
Hey guys, I just had this same problem, and it was solved by this solution:

[http://ubuntuforums.org/showthread.php?p=6740864&posted=1#post6740864](http://ubuntuforums.org/showthread.php?p=6740864&posted=1#post6740864)

I'll reiterate to provide some additional helpful info, but the link is there just in case I make a mistake explaining it.

You'll need to edit your fstab file, which is located in the /etc directory. But before you can do that, you'll either need to be logged in as root, or browse to and open the file from Nautilus, or you won't be able to save the changes. To open Nautilus, press Alt+F2, then type gksu Nautilus. Provide password if prompted.

OK, so once fstab is open, add this command to the bottom:

Share /Shared vboxsf defaults 0 0

Share=what you named the shared host folder in Virtualbox.
Shared=the location of the folder you want the shared files to appear in.

I named my shared host folder "Music", and the folder I wanted the files to appear in was "/home/eric/Musicshare", so my example would be:

Music /home/eric/Musicshare vboxsf defaults 0 0

Hope this helps.

---

### Post by ubu-for on 2009-12-11
> **ERoe said:**
> Hey guys, I just had this same problem, and it was solved by this solution:

[http://ubuntuforums.org/showthread.php?p=6740864&posted=1#post6740864](http://ubuntuforums.org/showthread.php?p=6740864&posted=1#post6740864)
Thanks!

But does anybody know, how I get write permissions as user?

If I try to change the preferences as root with Nautilus, nothing changes.

---

### Post by worksofcraft on 2009-12-20
when creating the shared folder in virtualbox you can tick the Read-only option and then your virtual machine cannot write to the shared files.

Otherwise you can use command line to change file attributes using super user privilege as follows:

sudo chmod 777 fileToGainWriteAccessTo

note 777 gives read, write and execute permissions for that file to everybody.

INstead of changing mode, you can also use sudo for editing system files like fstab:

cd /etc
sudo gedit fstab

---

### Post by lmarmisa on 2009-12-20
You have to add one line to the **/etc/fstab** file. Open a terminal and type:

```

sudo gedit /etc/fstab

```Append this line:

```

LinuxShare /mnt/xpdocs vboxsf defaults 0 0

```Save and close the file.

If you wish to add a lynk in your Desktop pointing to the shared folder, type this command:

```

ln -s /mnt/xpdocs $HOME/Desktop/xpdocs

```

Best regards,

Luis

---

### Post by turnersd on 2010-11-10
I followed the instructions here as well as on the post linked above. Tried putting it in my fstab. I also tried putting the mount commands in the /etc/rc.local, and in /etc/init.d. Nothing seems to work. Seems the problem is that at least with Ubuntu guest and Windows host that the shared folders are not loaded until late in the boot process. I found another post online that tried to address this by putting the relevant mount commands in the /etc/init.d/vboxadd file, but that didn't help either. Has anyone had any luck figuring this out?

Thanks in advance.

---

### Post by Morbius1 on 2010-11-10
Is the target folder on WinXP shared by any chance? As in shared for the network. You don't need to do that for VBox but if it is shared then you should be able to access it from Network in Places?

There's a couple of ways to automount at that point without using fstab.

---

### Post by turnersd on 2010-11-10
No, it's on the same physical disk as the vbox image. It looks like the vbox shared folders aren't mounting until near the end of the boot sequence, and any of the methods using /etc/init.d, /etc/rc_.d, update-rc.d to create symlinks, none are working.

---

### Post by Morbius1 on 2010-11-10
What I was suggesting was to use the samba client on the Ubuntu guest to access the Windows host's shared folder. VBox sees the host as another machine on the local network.

Anyway, Let's go back to lmarmisa's idea of using fstab and vboxsf to automount. When you do that and reboot go to a terminal and type:
```
sudo mount -a
```If it mounts then VBox is suffering from the same bug as cifs ( samba ) does. There is a relatively easy fix if this is the case.

---

### Post by lmarmisa on 2010-11-10
Hi turnersd,

Could you inform us about your VirtualBox and Ubuntu versions?.

I am running VirtualBox 3.2.10 on a XP host and I am able to share folders with different versions of Ubuntu guests (from 9.04 to 10.10) without any problem.

Some details are different in function of the Ubuntu version. So, please, tell us which you use.

---

### Post by turnersd on 2010-11-10
Morbius and lmarmisa,

First thanks for taking the time to help me out. I'm relatively new to Ubuntu, and the community here is great.

Alright, the name of the shared folder I'm trying to mount is "dropboxlinux". The share point is an empty directory I've created called "~/host-dropboxlinux". I have no problem mounting this shared folder after boot using

```
sudo mount -t vboxsf dropboxlinux ~/host-dropboxlinux
```

I edited fstab to include the line:

```
dropboxlinux ~/host-dropboxlinux defaults 0 0
```

And when I try to reboot, I get an error: 

> 
An error occured while mounting ~/host-dropboxlinux.

Press S to skip mounting or M for manual recovery.


After hitting S to skip, sudo mount -a doesn't do anything. Again, I can still use the first command above to mount after a full boot sequence, but if I try putting this in the /etc/init.d directory and using update-rc.d I still have no luck. I even tried setting up a cron job as I saw somewhere else from another user that's having the same trouble I am, but that didn't work either. I set up a shell script to run the mount command above, and if I run this script after boot, it mounts no problem, but if I try to run the script by symlinking in /etc/init.d and running update-rc.d on the script name, it doesn't work. It just seems like the shared folder is not "visible" to Ubuntu until after the full boot sequence, and anything I try to automate the mount tries to execute before the shared folder is visible.

I'm using Ubuntu 10.10 as guest, under VirtualBox 3.2.10 r66523 on a Windows XP SP3 host. 

Morbius1 - I haven't tried making the folder shared on the host machine, but that also seems like a valid solution if I can't get this figured out.

---

### Post by lmarmisa on 2010-11-10
Do not use the symbol ~ because it makes only sense after you login in your account.

So, you should use **/home/yourusername**/ instead.

A second problem: Ubuntu 10.04 and Ubuntu 10.10 fail to mount automatically vboxsf devices from the /etc/fstab file.

You can fix this problem editing the file /etc/rc.local and adding a line similar to this:

> 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# auto mount VirtualBox shared folders
**mount.vboxsf -w -o fmode=0777,dmode=0777 dropboxlinux /home/yourusername/host-dropboxlinux**

exit 0

Don't forget to delete the vboxsf line in the file /etc/fstab.

---

### Post by turnersd on 2010-11-10
Thanks lmarmisa, this seemed to solve the problem very well. I did not add the -w -o fmode=0777,dmode=0777 options however, and it still worked for me. I could find little documentation on mount.vboxsf - just wondering what these do. Thanks again.

---

### Post by whatdoesitwant on 2011-03-14
I noticed that as of Virtualbox 4 Virtualbox has an automount option that can be activated in the virtualbox shared folder settings.
The foldername that you define here "<sharename>" will be mounted on ubuntu & debian as */media/sf_<sharename>*. It is possible to use symlinks on this folder.
The folder is only accessible to members of the vboxsf group.
To add a user use ```
sudo adduser <username> vboxsf
```

When you make use of this default automount method, it's not useful nor possible to use the historic mount method. You also need to choose between this method and the fstab method for automounting. The documentation tells me that with the automount method the folder only becomes available at user login instead of at server start. I don't know how to confirm this.

It is possible to symlink to the folder. 

The default prefix can be edited in */VirtualBox/GuestAdd/SharedFolders/MountPrefix*.
For more information:
[http://www.virtualbox.org/manual/ch04.html#sf_mount_auto](http://www.virtualbox.org/manual/ch04.html#sf_mount_auto) 

Note
Apache warns for issues with sendfile. I am not far enough into my setup yet to have tested for this, but here are the links.
The issue:
[http://forums.virtualbox.org/viewtopic.php?f=5&t=1940](http://forums.virtualbox.org/viewtopic.php?f=5&t=1940)
The error message:
[http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile](http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile)
And the solution:
[http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile](http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile)
```
<Directory "/path-to-nfs-files">
EnableSendfile Off
</Directory>
```

---

