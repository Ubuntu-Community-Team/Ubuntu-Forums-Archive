---
title: "New to Ubuntu; need help with auto reconnect of windows share not working"
date: 2022-06-30
forum: Virtualisation
---

### Post by marklyn on 2022-06-30
I'm very new to ubuntu and loving it so far but I'm learning a lot each day I research something new with Ubuntu.
I'm stuck right now and need a gentle hand of guidance so please be patient as I'm learning.
I've currently installed Ubuntu 20.04 LTS from scratch on a VMWare virtual machine.  My background was IT support so I'm pretty fluent in everything Windows and general networking, just not much at all in Linux world.
I have two shares on my Windows system I want to access and auto-reconnect to each time I launch Ubuntu.
I've set up the shares in Ubuntu's File manager and they work fine, reading/writing to my Windows shares except, when I log out of Ubuntu, I have to click on each share to reconnect for that session (until I log out again).
I have found some websites that detail how to setup shares and reconnect by editing the fstab file but I'm not quite there in confidence to do that (yet).
I thought I found an easier way by downloading/installing Gigolo (v. 0.52) but, even after following instructions to auto reconnect, it seems that isn't working after a login/logout cycle.
Would the best method be to edit the fstab file or use a 3rd party app like gigolo to make a permanent reconnect my windows shares? 
I've searched different websites for an answer or for novice details on editing the fstab file but if someone knows of a good, easy to follow resource, please post it.
Again, my Windows/networking and general PC experience is very good and much of it translates over to me getting Ubuntu set up and understanding differences from the Windows world but there are some minor details that hang me up sometimes :)

---

### Post by dragonfly41 on 2022-06-30
I will summarise the basic approach I take in sharing files between Windows 10 and Ubuntu 20.04.
My Windows is in first SSD (having replaced HDD) and Ubuntu in external USB SSD,
I used GParted (in LiveUSB or my Ubuntu instance) to create a new partition file type NTFS. I named it SHARE.
I mount SHARE and just place common files in there.
They open and run in either Windows or Ubuntu. So for example I have LibreOffice installed in Windows and Ubuntu. LibreOffice files in SHARE can be just clicked to open.

Just one more note of caution. If you have Ubuntu in a VM in a Windows HDD, use Windows (not GParted) to shrink your partition using Windows Partition Manager (if you have no unallocated space left).

And of course have a backup first.

---

### Post by marklyn on 2022-06-30
Yes, my ubuntu is in a VM in a Windows HDD.  I am intrigued by your approach but I'm not sure if using or allocating around 10gb of space for a share in the VM is the best way to do this since I'd need to be mindful of the VM overall size, but I may play around with your suggestion as a learning experience for how to use Gparted on Ubuntu, etc..  I was really wanting to have Ubuntu seamlessly connect to my existing Windows share as my first preference.

---

### Post by dragonfly41 on 2022-06-30
I understand, but I am inclined to keep Windows and Ubuntu far apart as tenants sharing a desktop.

There are other guides around if you favour Windows.

[https://www.answertopia.com/ubuntu/sharing-files-between-ubuntu-and-windows-systems-with-samba/](https://www.answertopia.com/ubuntu/sharing-files-between-ubuntu-and-windows-systems-with-samba/)

---

### Post by TheFu on 2022-06-30
When it comes to using network shares, my rule of thumb is to always use text configuration files and avoid any GUI methods. I've been burned far too many times.

Sadly, gaining access to MS-Windows CIFS shares requires all sorts of compromises because MS-Windows doesn't honor standard Unix file system expectations. This means that things which are relatively easy unix-to-unix, become harder using Unix-to-MS-Windows since you'll need to manually set some things that you've never needed to deal with previously.  Permissions, Users, Groups to start.

In these forums, there are many examples of fstab entries to connect to Windows network shards.  Seek those out, try them and ask specific questions.  You can find the Ubuntu WIki which has a step-by-step guide to do this too, but because the wiki has to pre-answer many possible issues for hundreds of different types of connections, the 1-line you need is likely buried in 10 other examples.

Also, many VM hypervisors have methods to allow direct access to host storage, so if you would say the hypervisor being used - be very specific - then someone can probably point to that sort of solution too.  Not that using the hypervisor method is even a good choice from a security perspective, but it would solve a few complexities that happen with other methods, though you'll likely still need/want to put the settings into the fstab.

---

### Post by marklyn on 2022-06-30
TheFu, I am/have been just reading up on editing the fstab file and adding a line to directly connect to my two Windows shares and I'm going to attempt that after I do some more reading/research but I have a some questions, if I may indulge...
If I want to edit the fstab file do I need to add smbclient or CIFS prior to using this method or are both already baked into Ubuntu?
I found some resources talking about automatically/permanently mounting Windows shares...
The cifs method talks about making a system mount point in the mnt folder then using a sudo command to mount.
I found another document that talks about editing the fstab file and doing it that way.
So far, I see two methods (excluding a GUI like gigolo, etc.) that appear to let me accomplish the same thing.
Is one potentially better than the other and/or is there something else to consider?
I'm getting more familiar with Ubuntu, I really am enjoying learning more about the OS and appreciate the strong community and documentation that exists.

---

### Post by slickymaster on 2022-06-30
*Thread moved to **Virtualisation**.*

---

### Post by Morbius1 on 2022-06-30
You will need to make sure cifs-utils is installed on the ubuntu client:
```
sudo apt install cifs-utils
```

I would suggest doing a manual mount first to make sure you have the correct options set. This will be a temporary mount as it will not survive a reboot.

For a permanent mount you will need to change the syntax of that mount and add it to /etc/fstab.

Note: I find your original post confusing in that it isn't clear if these "Windows Shares" are in fact SMB shares on a separate Windows host machine. Or if they are a VMWare host "shared folder" that you are trying to access from the VMWare Ubuntu guest. The latter is a different thing.

If it is a network share and you are currently accessing it through the file manager posing the output of the following command would provide a more specific response here:
```
ls -l /run/user/$UID/gvfs
```

---

### Post by marklyn on 2022-06-30
Morbius1, These are Windows Shares and truly are smb shares which I can manually mount via the file manager in Ubuntu, but like you said, the mount doesn't survive a restart.
I did try to set up a VMWare host "shared folder" but never could really get it to work so gave up on that and set up shortcuts in Ubuntu's file manager to connect to each of the two Window shares (on demand).  I just want to them to be automatic.
Here is the result of the ls command above:
total 320
drwx------ 1 marklyn marklyn  24576 Jun 29 16:21 'smb-share:server=waterloo,share=d'
drwx------ 1 marklyn marklyn 303104 Jun 30 08:13 'smb-share:server=waterloo,share=e'

---

### Post by Morbius1 on 2022-06-30
Give this a shot - again it's temporary and easily reversed:

[1] Create a Mount point at say ... /mnt/WaterlooD:
```
sudo mkdir /mnt/WaterlooD
```
[2] Then do a temporary mount:
```
sudo mount -t cifs //waterloo/d /mnt/WaterlooD -o guest,uid=marklyn
```

I wasn't smart enough to ask you if these shares require credentials or if they are guest accessible.

If you need to pass credentials replace guest with those credentials:
```
sudo mount -t cifs //waterloo/d /mnt/WaterlooD -o username=windows-user-name,password=windows-password,uid=marklyn
```

To unmount run:
```
sudo umount /mnt/WaterlooD
```

---

### Post by marklyn on 2022-06-30
Morbius1, 
The first step must have worked (guessing) because I was prompted for my password, which I entered.
Then, the second step stated that the mount point does not exist.
I also tried the step using my Windows credentials, but it still states the mount point does not exist.
I did look in the mnt folder and see the waterlooD

I'm assuming we're trying this to see if it works, and if so, I can somehow add this to the fstab file for an automatic connection?

Researching until I hear back from you on what you think the issue is with the mount point.

---

### Post by marklyn on 2022-06-30
OK, I figured out that I didn't have cifs-utils installed, which I just did.
Then step 2 worked with using my credentials but I still don't see in the file manager (on Ubuntu) how it shows I'm permanently connected, maybe after doing a restart?
Nope, a restart still doesn't show any evidence of an autoconnect to the share.
Waiting for more help but also researching...

---

### Post by Morbius1 on 2022-06-30
Using this manual mount:
> sudo mount -t cifs //waterloo/d /mnt/WaterlooD -o username=windows-user-name,password=windows-password,uid=marklyn

[1] Unmount it:
```
sudo umount /mnt/WaterlooD
```
[2] Edit /etc/fstab and at the botom of the file add this:
```
//waterloo/d /mnt/WaterlooD cifs username=windows-user-name,password=windows-password,uid=marklyn 0 0
```
[3] Save the file then make systemd happy by running:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs.target
```

Now go to /mnt/WaterlooD and verify that all is well.

It should do this by itself on every boot.

NOTE: There is one thing that can still mess this up. The way Linux boots it can sometimes try to run the declarations in fstab before it's internal network stack is fully operational so it fails to mount the share.

You can get around this problem with a systemd automount. You do that by adding two more parameters to your fstab declaration: **[COLOR="#0000FF"]noauto,x-systemd.automount[/COLOR]**
```
//waterloo/d /mnt/WaterlooD cifs username=windows-user-name,password=windows-password,uid=marklyn,noauto,x-systemd.automount 0 0
```

Then do the systemd 2-step again:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs.target
```

---

### Post by marklyn on 2022-06-30
I have to run out for about 2 hours but will definitely try this when I return.
Question in the meantime... if this works, will I see the drives mounted in the File manager, or how do I know they're mounted after each reboot?

---

### Post by Morbius1 on 2022-06-30
>  will I see the drives mounted in the File manager

They aren't going to show up under Network like a mapped drive does in Windows if that is what you mean.

You will need to go to /mnt/WaterlooD to see the contents of the share. 

You can create a bookmark to the share however then it will show up on the side panel of Nautilus ( File manager ):

go to /mnt/WaterlooD

Then Bookmark it - like I did with my /mnt/Srv1 mount:
[ATTACH=CONFIG]290680[/ATTACH]
It will then show up at the bottom of the left side panel:
[ATTACH=CONFIG]290681[/ATTACH]

Running out of power - long story - I'll be back tomorrow.

---

### Post by TheFu on 2022-06-30
Mounts look like local directories, unless you go out of your way to cause something different.  I find having partition letters in a file manager highly undesirable.

Rant: I really wish MSFT would fix their nomenclature of "drive letters", since they aren't for a drive, they are for a partition, which is exactly how Linux file systems are usually mounted.

You'll likely find all sorts of things you may need don't work over a CIFS mount. That's the difference between a native file system and Windows file systems.

Also, if you say which version of VMware is being used (they make 6 different hypervisors), you might find that a Linux to NTFS mount using VMware compatibility tools to be much faster.

---

### Post by marklyn on 2022-06-30
TheFu, I'm using VM workstation 15, if that helps.

Mobius1, I got to step 2, added the line at the bottom of the fstab file and tried to exit/save (:wq!) but get an "/etc/fstab" E212: Can't open file for writing.

---

### Post by mIk3_08 on 2022-07-01
> **marklyn said:**
>  how to use Gparted on Ubuntu, etc..
On how to install Gparted you can [click here]("https://itsfoss.com/gparted/") and [click here]("https://gparted.org/download.php") for more instructions.
[HTML]https://itsfoss.com/gparted/[/HTML]  
[HTML]https://gparted.org/download.php[/HTML] 
On how it works and for the Documentation of Gparted [click here]("https://gparted.org/documentation.php") Good Luck. Regards and cheers.
```
https://gparted.org/documentation.php
```

---

### Post by Morbius1 on 2022-07-01
>  (:wq!) but get an "/etc/fstab" E212: Can't open file for writing. 
When I saw that error I got that terrible eye twitch that took decades of psychotherapy to quell so I did a Google search of that error message and found this:
[https://linuxpip.org/fix-e212-cant-open-file-for-writing/](https://linuxpip.org/fix-e212-cant-open-file-for-writing/)

I can't help you with vi / vim. Just not going to do it. It's taken me too long to recover from the last time I used it.

Maybe it's just becase you are trying to edit without sudo privileges.

If the issue is something weird about VMWare installing Ubuntu in a ro partition somehow which would affect any text editor I can't help you with that either. Maybe the link about can help/

---

### Post by TheFu on 2022-07-01
To edit any system files on any Unix, use **sudoedit**.  There are other methods and you'll see those spread all over the internet, but sudoedit is the safest method AND it supports using whatever editor you like that is installed on the system.  That can be vim, nano, gedit, or anything else that already works on the box ... er ... provided it isn't a snap package.  I haven't tested snap packaged editors, but generally, snaps only have access to your HOME directory and system files get copied elsewhere for safe editing.

---

### Post by marklyn on 2022-07-01
> **Morbius1 said:**
> When I saw that error I got that terrible eye twitch that took decades of psychotherapy to quell so I did a Google search of that error message and found this:
[https://linuxpip.org/fix-e212-cant-open-file-for-writing/](https://linuxpip.org/fix-e212-cant-open-file-for-writing/)

I can't help you with vi / vim. Just not going to do it. It's taken me too long to recover from the last time I used it.

Maybe it's just becase you are trying to edit without sudo privileges.

If the issue is something weird about VMWare installing Ubuntu in a ro partition somehow which would affect any text editor I can't help you with that either. Maybe the link about can help/
I'm confused... is using VIM a bad thing? Should I have not attempted this using VIM?  Sorry I don't yet know/understand why this would be a bad thing.  I was just using what I researched and was found to be an easy to use editor to make changes to the fstab file.  I will continue to research your last statement about sudo privledges.

---

### Post by marklyn on 2022-07-01
> **Morbius1 said:**
> When I saw that error I got that terrible eye twitch that took decades of psychotherapy to quell so I did a Google search of that error message and found this:
[https://linuxpip.org/fix-e212-cant-open-file-for-writing/](https://linuxpip.org/fix-e212-cant-open-file-for-writing/)

I can't help you with vi / vim. Just not going to do it. It's taken me too long to recover from the last time I used it.

Maybe it's just becase you are trying to edit without sudo privileges.

If the issue is something weird about VMWare installing Ubuntu in a ro partition somehow which would affect any text editor I can't help you with that either. Maybe the link about can help/
I'm confused... is using VIM a bad thing? Should I have not attempted this using VIM?  Sorry I don't yet know/understand why this would be a bad thing.  I was just using what I researched and was found to be an easy to use editor to make changes to the fstab file.  I will continue to research your last statement about sudo privileges.

---

### Post by Morbius1 on 2022-07-01
I believe in the separation of religion and technology so I'm not going to get into a debate about vim. Just follow the link I provided if you prefer vim would be my suggestion.

---

### Post by TheFu on 2022-07-01
> **marklyn said:**
> TheFu, I'm using VM workstation 15, if that helps.

VM workstation 15 just says that is the documentation you should use to look up local access to storage on the VM host.  
When I searched for "vmware workstation 15 local storage access", a bunch of documents were in the results from vmware.com, but since they required javascript to see anything at all, I decided unblocking JS wasn't worth my time.  Other hypervisors provide similar capabilities, usually through their "guest additions".

---

### Post by marklyn on 2022-07-01
Morbius1, I read the link you provided.  I don't have any special affinity to using VIM, if using another editor is better.  I just didn't know.  Can you suggest a better editor?

---

### Post by TheFu on 2022-07-01
> **marklyn said:**
> Morbius1, I read the link you provided.  I don't have any special affinity to using VIM, if using another editor is better.  I just didn't know.  Can you suggest a better editor?

What editor do you normally use?  gedit is popular and much like notepad on that other OS.  
```
$ export EDITOR=gedit   sudoedit /etc/fstab 
```

That's the quick and dirty way to use gedit with sudoedit.

Long term, you'll probably want to add the 
```
export EDITOR=/usr/bin/gedit  
```
to your ~/.bashrc (way at the bottom), logout and login again, then use just
```
sudoedit /etc/fstab
```

P.S.   I don't know where gedit actually is on Ubuntu systems, so I guessed. That line could be wrong.  I'm a long-time vim user.  Using any graphical editor can cause challenges when editing files over the network or when on a system that doesn't have any GUI. But if you have 1 computer and only use it while sitting at that computer, then there won't likely be any issues.

If you want some other editor just for editing system files, nano isn't THAT bad for quick editing by most end users.  Admins and programmers will quickly get frustrated, however.

---

### Post by marklyn on 2022-07-01
TheFu, Yes, I like gedit much better and you're right, it looks like something familiar to me as a Windows user! Thank you!
I am now trying to add it long term, if I understand your instructions correctly.
Advise I should probably remove VIM since I won't be using it anymore?

---

### Post by marklyn on 2022-07-01
> **TheFu said:**
> What editor do you normally use?  gedit is popular and much like notepad on that other OS.  
```
$ export EDITOR=gedit   sudoedit /etc/fstab 
```

That's the quick and dirty way to use gedit with sudoedit.

Long term, you'll probably want to add the 
```
export EDITOR=/usr/bin/gedit  
```
to your ~/.bashrc (way at the bottom), logout and login again, then use just
```
sudoedit /etc/fstab
```

P.S.   I don't know where gedit actually is on Ubuntu systems, so I guessed. That line could be wrong.  I'm a long-time vim user.  Using any graphical editor can cause challenges when editing files over the network or when on a system that doesn't have any GUI. But if you have 1 computer and only use it while sitting at that computer, then there won't likely be any issues.

If you want some other editor just for editing system files, nano isn't THAT bad for quick editing by most end users.  Admins and programmers will quickly get frustrated, however.
When I try to edit the ~/.bashrc (ie: sudoedit /.bashrc)   the file appears to be empty, is that correct, do I add the line there?
Or, when I try and use this command line to edit, (sudoedit ~/.bashrc) I get a editing files in a writeable directory is not permitted.
However, if I try to use VIM (VIM ~/.bashrc), the file opens up.

---

### Post by TheFu on 2022-07-01
Learn to understand the different between ~/ and /.  They are VERY different.

sudoedit /.bashrc 
**is incorrect** and there's no need to use sudoedit for personal files (files in your HOME directory).

~/.bashrc  ===== $HOME/.bashrc

This is NOT the same as /.bashrc which would be a file at the top of the / directory. That location is protected.

To learn the basics, please check out [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - it is a no-hassle PDF file that covers the basics of Linux/Unix in the correct order, so you learn things the most efficiently.  Coming from a single-user OS into a multi-user OS build from the start to support 50,000 users on a single system can be a bit of a learning curve.  Things are necessarily different and required to be different for security.

sudoedit is to be used to edit system files, not personal files. That's why you got an error trying to edit the personal file ~/.bashrc

---

### Post by marklyn on 2022-07-01
Thanks for everyone's help so far. I'm making some progress and my understanding of Ubuntu is growing by the hour.  I still haven't been able to make the permanent auto reconnection to the Windows shares work from all of the help here but I will continue to explore and research further on my own for at least a day or two.  I feel I'm too much of a novice at this point and the only way to correct that is to keep reading, trying and researching.  Appreciate everyone's patience though!

---

### Post by Morbius1 on 2022-07-01
It's not at all clear at this point if you ever successfully edited fstab

---

### Post by marklyn on 2022-07-01
Yes, I was able to edit the fstab file.
I also was able to change the default editor to gpedit and use that, which I liked better.
The reason why I didn't reply back was because even after being able to edit the fstab file and try the suggested mount command, it never worked.
So I researched and found variations of the same command and have been in the process of trying that.
I'm also trying variations of where to place the share (ie: /media  or /mnt), as suggested by some web resources I've come across.
I've also experimented with successfully creating and using a credentials file.

The bottom line, for me, is that I'm able to do these things, learning more as I go, but I'm never getting a persistent reconnect to my windows share upon a restart.
I felt I was bothering the community each time I reported one thing back.

---

### Post by Morbius1 on 2022-07-01
Why not post the output of the following command so we can see where you are:
```
cat /etc/fstab
```

---

### Post by TheFu on 2022-07-01
Post #13 above says there are 2 modes.  
a) Try it mode - use the **sudo mount** command directly 
and after that is working, 
b) take the exact mount options and place those into the /etc/fstab file as a separate line at the bottom, then run a few commands to have the fstab re-read and the mounts happen.

If you post the exact line that you added to the bottom of the fstab, it is likely someone will see a tiny error.  Spaces matter a little. At least 1 space is needed between the fields as long as it is a single line. There must be 6 different parts/fields and those cannot have any spaces
Also, the '#' character is a comment and means nothing.

---

### Post by marklyn on 2022-07-01
I'm sorry, but I'm using ubuntu on a VM so when I've done quite a bit of changes or experimenting with things I'm researching, I revert to my base install so I know everything is good.
I'll post what you are asking in the order as I'm re-reading the posts/suggestions and starting with a fresh image restore that includes cifs & all ubuntu updates.
Regarding post #10...
sudo mkdir /mnt/WaterlooD
sudo mount -t cifs //waterloo/d /mnt/WaterlooD -o username=windows-user-name,password=windows-password,uid=marklyn

This seemed to have created a mount because when I did the df command it showed:
Filesystem     1K-blocks    Used Available Use% Mounted on
tmpfs             398492    3508    394984   1% /run
/dev/sda3       19946096 9914956   8992600  53% /
tmpfs            1992460    1372   1991088   1% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
/dev/sda2         524252    5364    518888   2% /boot/efi
tmpfs             398492    2420    396072   1% /run/user/1000
//waterloo/d    52428796 4267128  48161668   9% /mnt/waterlooD


But, I don't see that share mounted in the Files manager app.
I will try the next suggestion regarding the editing of the fstab file, post #13

---

### Post by marklyn on 2022-07-01
Regarding post 13 instructions, results:
I edited the /etc/fstab file and added (with username/pw substitutions):
//waterloo/d /mnt/WaterlooD cifs username=windows-user-name,password=windows-password,uid=marklyn 0 0
I did the: sudo systemctl daemon-reload   and   sudo systemctl restart remote-fs.target
I did the df command and it shows the mount, but I still don't see it mounted in the files app.
Filesystem     1K-blocks    Used Available Use% Mounted on
tmpfs             398492    3512    394980   1% /run
/dev/sda3       19946096 9914976   8992580  53% /
tmpfs            1992460    1372   1991088   1% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
/dev/sda2         524252    5364    518888   2% /boot/efi
tmpfs             398492    2420    396072   1% /run/user/1000
//waterloo/d    52428796 4267128  48161668   9% /mnt/WaterlooD

I also restarted the system; no change.
This is the contents from the /etc/fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=e5dea946-8bab-49ef-9ab1-6f731154205d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=D3D1-010F  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
//waterloo/d /mnt/WaterlooD cifs username=xxxxxx,password=xxxxxx,uid=marklyn 0 0

---

### Post by marklyn on 2022-07-01
OK, after going through every post I see in post #15, Morbius1 stated that I won't see this in Nautilus side panel like I would in something like Windows file manager.
I missed that and now realize that.
So it appears I am connecting to the share in both of the posted suggestions above because I do see the shares in the /mnt folder using Nautilus.
What I'd like to know is how to make those shares auto connect when I log into Ubuntu such that an app that uses those shares would work properly instead of failing because they're not mounted.
I've added those shares as bookmarks to Nautilus but they aren't mounted until I click on them in Nautilus.
Hope this makes sense.

---

### Post by Morbius1 on 2022-07-01
The share is automounting.

---

### Post by marklyn on 2022-07-01
> **Morbius1 said:**
> The share is automounting.
Does that mean the share won't mount until I click on the bookmark for it?

---

### Post by Morbius1 on 2022-07-01
The share is automounting without you clicking on the bookmark.

You just proved it by going to /mnt/WaterlooD

---

### Post by Morbius1 on 2022-07-01
Please post the output of this command:
```
cat $HOME/.config/gtk-3.0/bookmarks
```

---

### Post by marklyn on 2022-07-01
file:///mnt/WaterlooD
file:///home/marklyn/Documents
file:///home/marklyn/Music
file:///home/marklyn/Pictures
file:///home/marklyn/Videos
file:///home/marklyn/Downloads

---

### Post by Morbius1 on 2022-07-01
Reboot your VMWare Ubuntu client.

After you login immediately open a terminal and run:
```
mount | grep cifs
```
Does it show "//waterloo/d on /mnt/WaterlooD type cifs ......"

If it does not run this command:
```
sudo mount -a
```
THen run the mount command again:
```
mount | grep cifs
```
Is it mounted now?

---

### Post by marklyn on 2022-07-01
I'm not understanding the concept between Ubuntu and Windows.
In Windows, I set up a share on machine A.  Then from another Windows box  machine B, I can map to that the machine A's share, assign a drive letter, and have it reconnect when I reboot, as long as machine A is running.
I want to do this in Ubuntu.
I use qbitorent on Ubuntu with a save folder location to the windows share but Qbitorrent fails with downloads because that location is not connected (mounted?) until I click on the bookmark for it in Nautilus.
Once I do that and I see it's mounted in Nautilus, Qbitorrent works.
(this was posted after what you posted above)

---

### Post by marklyn on 2022-07-01
> **Morbius1 said:**
> Reboot your VMWare Ubuntu client.

After you login immediately open a terminal and run:
```
mount | grep cifs
```
Does it show "//waterloo/d on /mnt/WaterlooD type cifs ......"

If it does not run this command:
```
sudo mount -a
```
THen run the mount command again:
```
mount | grep cifs
```
Is it mounted now?

mount | grep cifs
//waterloo/d on /mnt/WaterlooD type cifs (rw,relatime,vers=3.1.1,cache=strict,username=marklyn,uid=1000,noforceuid,gid=0,noforcegid,addr=172.21.112.1,file_mode=0755,dir_mode=0755,soft,nounix,serverino,mapposix,rsize=4194304,wsize=4194304,bsize=1048576,echo_interval=60,actimeo=1)

---

### Post by Morbius1 on 2022-07-01
Your Ubuntu machine is doing the exact same thing as your Windows machine would do.

It is mounting the Windows D share to /mnt/WaterlooD every time it boots.

Clicking on  file:///mnt/WaterlooD bookmark in Nautilus doesn't mount the share. It simply displays the contents of that share in Nautilus.

As far a this Qbitorrent thingy you speak of I have no idea. I would only note that there are two versions in the repositories. One deb based and the other is a snap. Snaps work differently which may be the problem here. 

I have managed to avoid using them so I'm not the right person to talk about that.

---

### Post by marklyn on 2022-07-01
Morbius1, thanks for all of your help here. I'm going to call it a day and start fresh tomorrow.
I know I have lots to learn and I may be putting the cart in front of the horse by tackling something like this before I have a better understanding of many things Ubuntu.
Appreciate you!

---

### Post by TheFu on 2022-07-02
> **marklyn said:**
> Does that mean the share won't mount until I click on the bookmark for it?

No.  It is mounted when the command is run.  It isn't going to show up as a separate button inside any file manager and that is a good thing.  I suppose there are ways to get a specific file manager to recognize that sort of mount, but since I don't use file managers much, I wouldn't know how.

**Vim: **
As for vim or not to vim.  I'm a vim user and use it for all editing on every platform from routers to Windows  to single-board-computers to $5M huge UNIX DB servers.  I purge nano and all other editors from my systems, since vim works locally and remotely on all systems.

However, vim is a very different sort of editor compared to anything you've likely experienced before. There is a steep learning curve and if you aren't trying to be a Linux admin or UNIX professional, there is little reason to learn more than the vimtutor teaches.  I didn't always use vim, but since I converted over 25 yrs ago because my editor at the time kept lacking some capability that was trivial in vi (this was pre-vim).  I'd never say that someone else has to learn vim, but just know that is is probably THE most powerful editor made with unlimited customization and extensibility.  I barely customize my setup, so I don't miss things on random servers, but on my desktops where I do coding, I do have about 10 vim modules to make life easier.  With each vim release, things that were modules 10 yrs ago become part of the core features.

I use vimwiki to store and organize notes for everything. That's a module.

The problem with using any GUI editor like gedit is that GUI stuff doesn't work on servers and that some GUI stuff will break due to stupid library changes.  vim doesn't have those dependencies and it always works - local or remote.

There are long threads on almost every Unix/Linux forum about vim or emacs or xyz editor.  Did you know that gedit is going away soon?  The gnome project decided to replace it.  Atom is deprecated too.  People who like Notepad++ would probably like geany - geany is cross platform so you can install and use it on almost any platform with a GUI.  Just another option to consider.

If you post your fstab line, I bet we can help.  10 seconds of our time would likely point out the problem. That's why we are here.

---

### Post by mIk3_08 on 2022-07-03
> **marklyn said:**
> file:///mnt/WaterlooD
file:///home/marklyn/Documents
file:///home/marklyn/Music
file:///home/marklyn/Pictures
file:///home/marklyn/Videos
file:///home/marklyn/Downloads
Are you trying to share this folders via browser, is this possible? Are you using VM right?

---

### Post by marklyn on 2022-07-03
> **mIk3_08 said:**
> Are you trying to share this folders via browser, is this possible? Are you using VM right?
I'm trying to write to a windows share at the top of the list.

---

### Post by marklyn on 2022-07-03
I'm happy to report that a solution has been found, actually excited.  It's amazing how many different, yet similar "solutions" are out there for accomplishing the same thing!
My solution involved going back to the original idea of using VMWare's shared drive mappings, native to VMWare when building a VM.
I turned on drive mappings for two window share drives, D: and E:
then I eventually found this info on the web:
sudo mkdir /mnt/hgfs
edit fstab and add:
vmhgfs-fuse    /mnt/hgfs    fuse    defaults,allow_other    0    0
sudo mount -a  (remount)  & then restart the machine; should see D & E under /mnt/hgfs

This worked, so I logged out and back in to see if it still worked, it did.  Then I did a shut down/restart, logged in, and it still worked so it appears to be 'survivable' for restarts.
I learned a lot during this process and appreciate various people sticking by me (Morbius1 and TheFu, and others).  I'll post this in the networking thread as well so that thread can show 'solved'

The *only* thing I have to do, is to see how I can add the two Windows shares to the favorites.  I clicked on each one with Nautilus but there is no choice to add to the favorites list, but this is minor and even if I can't do that, I know they're in the /mnt/hgfs folder.

---

### Post by TheFu on 2022-07-03
Please just use the "thread tools" button to mark any solved thread as SOLVED, so people looking for answers and those seeking to help don't waste time.

Stuff in the /etc/fstab generally gets mounted early in boot, unless is has to be delayed due to a network dependency. Then it should wait until networking is "up" and network mounts will happen.

This process has NOTHING to do with any user logging in.

But Unix is flexible and with added options, you could specifically ask that an fstab mount NOT happen until requested.

BTW, "automount" is a specific thing and seldom used in an /etc/fstab.  Best to call those "automatically mounted via fstab" to limit confusion. autofs is the tool that handles automountd (automount daemon) these days.  I use autofs, and in the process table, the automountd is:
```
root      3812     1  0 Jul02 ?        00:00:13 /usr/sbin/automount --pid-file /var/run/autofs.pid
```
This is not used by fstab entries that I've ever seen.

"Favorites" would be a file manager thing.  The normal Unix-way would be to add a symbolic link to the other storage, if you want quick access into it.  I don't know the GUI way to do this, but ** ln -s <source>  <target>** is the command line way.  Symlinks can be to 1 file or a directory.  Symlinks were added to NTFS a few years ago. Unix has had them for longer than I've used Unix.  It is a file system capability.  Before MSFT added symlinks to NTFS, they attempted something similar using "Libraries", which never really worked because they were GUI-only objects and required using dotNet (I think).

Anyway, happy you were able to get this solved.

---

### Post by DuckHook on 2022-07-04
> **marklyn said:**
> …The *only* thing I have to do, is to see how I can add the two Windows shares to the favorites.  I clicked on each one with Nautilus but there is no choice to add to the favorites list, but this is minor and even if I can't do that, I know they're in the /mnt/hgfs folder.
To create a Favourites in the GUI, it must first be created as a .desktop file, then placed in ~/.local/share/applications/ then added as a Favourite through the Ubuntu Dock.

The following link shows how: [https://askubuntu.com/questions/966740/how-do-i-pin-my-favorite-folders-in-ubuntu-dock-like-in-windows](https://askubuntu.com/questions/966740/how-do-i-pin-my-favorite-folders-in-ubuntu-dock-like-in-windows)

---

