---
title: "SAMBA: Cannot share folder on NTFS drive"
date: 2007-10-20
forum: Server Platforms
---

### Post by Robvdl on 2007-10-20
I think I just found a bug in Gutsy.

When I installed Gutsy, it mounted my NTFS drive automatically, I left the mount options as they were, I just changed it (by altering my /etc/fstab file) to mount under /windows instead of /media/sda1 as I do not want an icon on my desktop.

Everything works fine, and this is not the problem. The problem is, when I tried to share say /windows/Stuff using SAMBA.

If I right click the Stuff folder, and attempt to share it, I get the following message box:

> **The folder content could not be displayed.**

error accessing 'file:///windows/Stuff': Access denied

Now this issue does not happen on my normal Linux partition, I can happily share /home/rob/Pictures for example..

I think it may be to do with permissions?? Maybe Samba does not have permissions to the NTFS drive?? Can anyone help guide me with this?

Maybe I need to add Samba user to a group?? (is it the fuse group maybe)

---

### Post by beko on 2007-10-21
I have the same problem too.. somebody help please](*,)

---

### Post by HermanAB on 2007-10-21
So you wish to run a Samba server and share the NTFS drive?

First of all, you need the ntfs-3g file system, since the default NTFS filesystem driver is read-only.

Cheers,

Herman

---

### Post by beko on 2007-10-21
I thought since I am on gusty it already have read/write access for NTFS partitions !!
I will tell you exactly what I want to do:
I have 3 computers 2 of them have Ubuntu Gusty with mixed files systems (NTFS and FAT32)an the third one has xp with a few shared folders on it.
All of them are connected through a router...what I want to is to make all the shared folders on any of these 3 computers to be under my Network folder.
I can see the shared folders on windows from both the Ubuntu machines .
when I choosed to share a folder located under media/sda5 Ubuntu asked to install a few packages to enable sharing .
After it finished installing these packages I tried to click on share again to share this folder on the network but it gave me this message (***The folder contents could not be displayed - error accessing 'file:///media/sda5/site_flash': Access denied*** )
neither ubuntu machines can see each other although I make sure that the Workgroup in smb.conf are the same .

---

### Post by HermanAB on 2007-10-21
To really figure out what is wrong, you need to see the error messages.  Therefore open a command shell and use telnet and smbclient to debug the connection:

$ telnet windowsipaddress 445

If it won't connect then you have a firewall problem.

If it works, try smbclient:
$ smbclient -L //windowsipaddress -N

You should get a list of shares.  

Try to connect to a share:
$ smbclient //windowsserver/sharename -U username
Password: youruserpassword

It really helps to see the errors.  Google the error messages to learn about the problems.

Cheers,

Herman

---

### Post by Robvdl on 2007-10-21
My network isn't the problem. I am able to access other SAMBA shares on the network no problem. I am also able to share folders on my normal Linux partition.

I am just not able to share any folders on my NTFS partition, because of some security issue, most likely because it does not have the permissions to use fuse.

I tried:

```

sudo aduser rob fuse

```

```

sudo adduser samba fuse

```

```

sudo adduser fuse samba

```

...none of which work.

I know it is a security bug in Gutsy, I just don't know how to fix it.

I was thinking, maybe it's apparmor blocking it? But I don't know how to check this just yet.

---

### Post by Robvdl on 2007-10-21
Ok, did some more tests, here's what I did:

Since I was unable to share a folder on my NTFS drive using the GUI, I edited my samba configuration file by hand. Now my windows partition is mounted under /windows and in there is a folder "Demos", so I am trying to share /windows/Demos as a test. Here is part of my samba configuration:

/etc/samba/smb.conf:

```
[Demos]
path = /windows/Demos
available = yes
browsable = yes
public = yes
writable = no

```

Next, I reloaded samba:

```
sudo /etc/init.d/samba restart
```

Now, I ran the test listed above to try to connect to the share using a terminal, even though it's my own machine:

```
smbclient //rob-desktop/Demos -U rob
```

I then got the following error message:

```
session setup failed: NT_STATUS_LOGON_FAILURE
```

Like I though, samba is unable to access the NTFS mount, fuse?

---

### Post by dmizer on 2007-10-22
haven't had to tackle this myself, but it sounds to me like you're asking samba to do something fairly risky.

here's my suggestion.  create a folder on an ext3 partition, create symbolic links from the ntfs drive to the ext3 folder, and share the ext3 folder instead of the ntfs drive directly.  this will cost you zero drive space, and i believe it will be a lot less risky.

```
ln -s /windows/Demos/ /home/<UbuntuUserName>/shared-folder
```

and your samba entry should look like this:
```
[Demos]
path = /home/<UbuntuUserName>/shared-folder
available = yes
browsable = yes
public = yes
writable = no
```

however, i do not know if it will work or not.

---

### Post by Robvdl on 2007-10-22
That's actually how I had it setup initially, create symlinks in my home folder to the folders on the NTFS drive and share those, but I got the same result.

So what I did then, to narrow down the problem is try to share the folders directly from the NTFS drive, but obviously I got the same result there.

It has to be a bug. Because I've always done this, Dapper, Edgy, Feisty. Most of my data is on my NTFS partition, and I need to share this on the network.

It just doesn't work in Gutsy because of some sort of security issue.

I think it might be AppArmor since this is newly introduced in Gutsy and I remember when I used to run Fedora a long time ago, I also had a lot of trouble with security and selinux blocking too much. So, how do I temporarily disable AppArmor to test this theory?

---

### Post by Sirmatto on 2007-10-22
I too had the problem of sharing NTFS drives upon installing NTFS.  I found out a quick fix that is detailed at: [http://ubuntuforums.org/showthread.php?p=3605477](http://ubuntuforums.org/showthread.php?p=3605477)

---

### Post by beko on 2007-10-22
First of all I would like to thank all of you ...I have figured it out so I wanted to share you the solution .
The problem was in the files system permission in fstab.
This partition used to be:
```
# /dev/sda5
UUID=8608DA1108D9FFDB /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
```and I changed it to :
```
# Entry for /dev/sda5 :
UUID=8608DA1108D9FFDB /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```until here the message used to come (***The folder contents could not be displayed - error accessing 'file:///media/sda5/site_flash': Access denied*** )  when I click on share disappear  and I could share the folder on NTFS partition.
for samba problem with the two Ubuntu machines I found that samba won't show any shared folders unless I reboot my computer and not just by restarting samba. So what I had to do is to do one step each time. I choosed the folders I want to share on one machine then restarted it and after it booted I went to the other one and shared the folders I want too then rebooted it .
The two Ubuntu machines are fine now and can see each other plus the windows machine.

I feel that it's a little silly that samba won't share the folders until I restart but that's how it worked with me.

If anybody see anything could be risky on my network or storage hard drives please let me know.

---

### Post by Robvdl on 2007-10-23
I too fixed mine, from this thread:

[http://ubuntuforums.org/showthread.php?p=3606831](http://ubuntuforums.org/showthread.php?p=3606831)

Replace the part in /etc/fstab where it mounts the NTFS partition as "defaults,umask=007,gid=46" and just replace it with "defaults". i.e. get rid of umask=007,gid=46

---

### Post by Gary_inNYC on 2007-10-30
This is how I got my NTFS partitions shared in Ubuntu.  The end result by the way, is a shared ntfs data partition using share authentication with guest user, no username or password configuration required, or fstab editing, or any fuss really.

first off, since it was mentioned in this thread, to get rid of those icons that show up on your desktop when you mount an ntfs partition, just hit alt+f2,  gconf-editor
then go to apps/nautilus/desktop, and uncheck volumes visible.  

now back to the topic at hand.  to get the effect i described earlier about ntfs shares, first install ntfs-config from synaptic, then run the program and enable write for internal devices.  It will remount your partitions in the process.  This is assuming you're using gutsy, therefore, ntfs-3g is already installed and not mentioned any further.

second, make a share from your target ntfs partition or folder.  there are multiple ways of actually making the share.  
1) System / Administration / Shared Folders
OR
2) in Nautilus, navigate to /media/whereever_your_partition_and/or_folder is, right click, share.  

either way of sharing will make an entry in smb.conf  which is where a lot of (if not all?)  changes are really made when talking about shares.  
you can find it at /etc/samba/smb.conf

go ahead make a share, then open the smb.conf file and scroll all the way to the bottom.  you'll find your corresponding share referenced in brackets [your comment entered for share].  

here's what you gotta do:  
scroll up a bit, and look for  the Authentication Subsection 
1) look for the line with ; security = user    what you gotta do here is get rid of the semi colon (activating the line in doing so) and replacing user with share
it should look like:      
security = share

still in Authentication subsection,
2) get rid of the semi colon, where  guest = nobody   is located.  make sure guest is in fact, equal to the word nobody.
looking like:
guest = nobody

last but not least, you have to _enable guest access for your share_...
here's what my entire share entry looks like:

[gary_files]
path = /media/sdb1
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes

what i had to add here was the **guest ok = yes**   line.  Also, if you look, writable = no means it's read only for anyone accessing my files.  the other lines are pretty self explanatory.  Path is location of share, the stuff in brackets is the comment i made for the share that shows up in network browser, etc.  

after your editing is done, save changes for smb.conf, then restart samba, from terminal:

sudo /etc/init.d/samba reload

why reboot, keep it simple.  with this method, you won't have to keep dibs on usernames and passwords, or complex clauses in syntax, because for the most part, we didn't do anything but add a line, or remove a semi colon. 

Note: you'll probably have to re enter the guest ok = yes line in smb.conf for (each) share to exhibit the same behavior.  Still idiot-proof imo.

- Gary_inNYC

---

### Post by Robvdl on 2007-10-30
I'm fully aware of the unchecking "volumes visible" thing for the desktop under gconf-editor. However, this has the other side effect of not showing an icon on the desktop if you insert a CD or USB flash disk, which is not quite what I want. It is normally really easy to unmount a flash disk, by right-clicking the icon on the desktop, so i do want to actually see those icons.

If you only want to hide your NTFS drives from your desktop, but do not want to hide your CD-ROM and USB flash disk icons, then editing the /etc/fstab file is still the way to go.

Just set your mount point to anything other than /media/xxx and the icon for that drive will not show up on the desktop. Just make sure you create the mount point first, e.g. "sudo mkdir /windows"

...Also, I personally don't think messing around changing guest = nobody, etc and stuff isn't really a good idea for security. I am sure that the security in /etc/samba/smb.conf has been set just right by the Ubuntu team and shouldn't need changing. Samba works no problem in Gutsy with sharing folders on your standard EXT3 partitions, it just doesn't work by default for your NTFS partition. To me, this appears because by default an NTFS partition is mounting using gid=46 (group id 46). If I type "id" from my terminal, it tells me group id 46 is for "plugdev". I imagine that Samba just doesn't have access to that group by default. Anyway, removing the group id and umask from where it mounts the partition in your /etc/fstab fixes it just fine.

---

### Post by tvtech on 2008-03-21
instead of removing your security options and dumping everything to default pop into a terminal 
user@localhost:~$man ntfs-3g 
or user@localhost:~$man 8 ntfs-3g 
it'll be a minute or two of reading !  but you'll better understand the permissions I promise, and you can set them up so they are compatible with samba

this link show's a usable permission set, that doesn't thrash your security!
[URL="http://http://ubuntuforums.org/showthread.php?p=3606831"]
http://ubuntuforums.org/showthread.php?p=3606831[/URL]

man pages aren't fun I know but they're chocked full of complicated unreadable technobabble, and lack of references

another useful thread I found was
[http://http://ubuntuforums.org/showpost.php?p=4256702&postcount=3]("http://http://ubuntuforums.org/showpost.php?p=4256702&postcount=3")

this opens up the world on umask information hopefully this helps a little I was running myself in circles trying to get this all sorted without having lost total control of my permission set

---

