---
title: "Can't get locally hosted websites working"
date: 2015-05-02
forum: Server Platforms
---

### Post by lucy5 on 2015-05-02
Hi,

I changed the file apache2/sites-available/000-default.conf so the document root is a folder I have in a storage partition (so I can also access it on my Windows partition, mainly for testing purposes). Now when I go to localhost or localhost/portfolio/home.html (the one website currently in the folder) I get the error: Forbidden 
You don't have permission to access / (or /portfolio/home.html) on this server.

So I tried adding this to the file (same path as the document root part):
<Directory "/media/lucy/storage/www">
Order allow,deny
Allow from all
Require all granted
</Directory>

It's still not working. I've tried lots of things but already nearly broke apache, so thought it might be better to ask you guys for guidance :) I really don't know what I'm doing with all this, as I'm very new to Linux, but I'm determined to use it.

Thanks in advance.

---

### Post by spjackson on 2015-05-02
I suspect this is file permissions rather than the apache configuration. From a terminal, if you do
```
sudo su www-data -c "ls /media/lucy/storage/www"

```
do you get "Permission denied"? If so, then it's not to do with the apache configuration.

If it's a vfat or ntfs partition, you won't be able to chmod beneath the mount point, so the solution will be to do with how you mount the partition. How do you do that?

---

### Post by lucy5 on 2015-05-02
I get "this account is currently not available".

It's a ntfs partition. I've set it to mount at startup (I think).

---

### Post by spjackson on 2015-05-02
> **lucy5 said:**
> I get "this account is currently not available".

Ah yes, that's possible. Try
```

sudo su www-data -s /bin/sh -c "ls /media/lucy/storage/www" 

```

---

### Post by lucy5 on 2015-05-02
Okay - that one results in 'permission denied'.

---

### Post by bab1 on 2015-05-02
> **lucy5 said:**
> Hi,

I changed the file apache2/sites-available/000-default.conf so the document root is a folder I have in a storage partition (so I can also access it on my Windows partition, mainly for testing purposes). Now when I go to localhost or localhost/portfolio/home.html (the one website currently in the folder) I get the error: Forbidden 
You don't have permission to access / (or /portfolio/home.html) on this server.

So I tried adding this to the file (same path as the document root part):
<Directory "/media/lucy/storage/www">
Order allow,deny
Allow from all
Require all granted
</Directory>

It's still not working. I've tried lots of things but already nearly broke apache, so thought it might be better to ask you guys for guidance :) I really don't know what I'm doing with all this, as I'm very new to Linux, but I'm determined to use it.

Thanks in advance.
I think you should leave the default website alone, or at the least have a backup of the configuration.  You can use virtual hosts to create the test website.  See [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts") for details.  I move the doc root to a completely different location and it works perfectly.  I can access it via Samba shares (Windows sharing) remotely.  The location I use is /srv/share/www.  I set the permissions for the group **users** to have access and add the folks I want to access into the **users** group.

[COLOR="#0000FF"]Edit: Of course you will need to mount the partition with the data at whatever mount point (location) you choose.  If this is a NTFS formatted disk you will need to set the permissions at mount time (boot?).  You can't change permissions on a mounted NTFS partition via the terminal. [/COLOR]

---

### Post by lucy5 on 2015-05-03
bab1 - 
Thanks - I tried to follow the instructions in your link but am getting the same problem. I might be misunderstanding you, but I checked the permissions for the partition and all users have 'read and write' - is this not enough? Looking at the options available (this is via 'properties', not the terminal) there isn't anything more other than 'access' which seems to be a seperate option - I tried clicking that and it changed it back to read and write... If I need to change the permissions during boot, how would I do that? Or should I just set it to not mount straight away so I can change permissions through the terminal (on that note, how come I can't change them with the terminal but can through the properties?)?

---

### Post by bab1 on 2015-05-03
> **lucy5 said:**
> bab1 - 
Thanks - I tried to follow the instructions in your link but am getting the same problem. I might be misunderstanding you, but I checked the permissions for the partition and all users have 'read and write' - is this not enough? Looking at the options available (this is via 'properties', not the terminal) there isn't anything more other than 'access' which seems to be a seperate option - I tried clicking that and it changed it back to read and write... If I need to change the permissions during boot, how would I do that? Or should I just set it to not mount straight away so I can change permissions through the terminal (on that note, how come I can't change them with the terminal but can through the properties?)?
There are a few considerations that need addressing before you can set this up correctly.

[LIST]
[*]How many users are there that are going add files to the doc root?
[*]How are these users going to access the doc root?
[*]Are you going to have multiple sites that you will need to created at a later date?
[*]Do you have sudo rights on this host (computer)?   Are you an administrator? 
[/LIST]
Under normal circumstances only the root user (a user with sudo rights) can make a directory in the /srv file system.  I'm not sure exactly what you have done so far, so let's look at it using the terminal (e.g. the command line interface(CLI)).  Post he output of this command ```
ls -l /srv
```

I also can use the information in the /etc/apache2/sites-available directory.  Post the output of this command ```
/ls -l etc/apache2/sites-available
```

When you post this information place it between the [noparse]```

```[/noparse] code blocks.  It will be much easier to read and understand.  The esiest way to do this is to click on the [SIZE=5]**#**[/SIZE] icon located at the top of the advanced editor that you use to reply with.  This will add the code blocks and you can just paste the date in between them.

Explain how and where you have mounted the NTFS partition that we are going to use.  If you are going to have multiple users accessing the doc root then we need to use a group that all the users are part of.  Most fold use an already created user group named "users".  You need to set that in the options declared when you add a line to the fstab file.

If you provide the basic idea of what it is you want in the end I will show you how to create the infrastructure you will need.  Everything needs to be set up manually from the CLI.  It is not hard once you are shown what to do.

---

### Post by lucy5 on 2015-05-03
Thanks for helping with this :) 

> How many users are there that are going add files to the doc root?
Just the one (my account). 

> How are these users going to access the doc root?
As in, the place where the sites will be stored? Well, I'm not sure I completely understand your question, but I plan on creating and editing files with notepad++ through wine?

> Are you going to have multiple sites that you will need to created at a later date?
Yes

> Do you have sudo rights on this host (computer)? Are you an administrator? 
Hm... I'm not quite sure, actually. I can use the sudo command in the terminal with my user password but otherwise don't have sudo rights. 

First command output:
```
total 0
```

Second (without forward slash before ls, as it didn't work):
```
total 16
-rw-rw-rw- 1 root root 1342 May  3 07:43 000-default.conf
-rw-rw-rw- 1 root root 6437 Nov  8 22:16 default-ssl.conf
-rw-rw-r-- 1 lucy lucy  246 May  3 07:35 portfolio.conf
```

> Explain how and where you have mounted the NTFS partition that we are going to use. 
I used these instructions to automatically mount on startup:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

It seems to be in /media/Lucy(my account)

> If you provide the basic idea of what it is you want in the end
To be honest, I just need it to be similar to how I've been working on Windows. I've only recently started using a local server, as I added PHP to my websites and needed to test it. I have been using wamp server (here: [http://www.wampserver.com/en/](http://www.wampserver.com/en/)) and had also been following these instructions to create virtual hosts: [http://forum.wampserver.com/read.php?2,127757](http://forum.wampserver.com/read.php?2,127757) - apparently it's necessary for everything to work the same as it would online, if I'm understanding it correctly. It also meant I could type portfolio/home.html for instance, rather than localhost/portfolio/home.html. As might be obvious, I don't fully understand this stuff. I don't need anything complicated setting up, just enough that it will emulate how the websites will work online (with php files) enough that I won't get any surprises after putting them up. Also, it only needs to work on this computer (I'll have wamp server installed in the Windows partition for IE testing). Oh, in case it's relevant I have also been using this for testing wordpress sites locally too.

If what I'm trying to do isn't a good idea, I can always just put the websites in the normal place and just copy the files over to the storage partition when I want to test in Windows.

---

### Post by bab1 on 2015-05-03
> **lucy5 said:**
> ...
Do you have sudo rights on this host (computer)? Are you an administrator?  

Since you are the only user that simplifies the situation a bit.  As the only user of Ubuntu you have administrator rights via sudo.

By "access" I meant whether you a local user or a remote user (by ssh or sFTP or Windows sharing).  As a local user this also simplifies the situation. 

As you are planning to have multiple sites we should keep the doc root for each site separate.  I have only glossed over the WAMP stuff.  I do see that they recommend the same thing.  This means we need to set the storage location appropriately.

> As in, the place where the sites will be stored? Well, I'm not sure I completely understand your question, but I plan on creating and editing files with notepad++ through wine?
What I meant by this is how are you going to add or modify the files in the doc root -- upload completed pages or directly modifying the files in the doc root.  I would not use notepad++ via w wine.  It is needless complication.  There are plenty of text editors available in Ubuntu.  I use Gedit as a basic editor or BlueFish which is more like the old Dreamweaver.

> 
Second (without forward slash before ls, as it didn't work):

The slash was a typo of mine.  Sorry about that.
> 
```
total 16
-rw-rw-rw- 1 root root 1342 May  3 07:43 000-default.conf
-rw-rw-rw- 1 root root 6437 Nov  8 22:16 default-ssl.conf
-rw-rw-r-- 1 lucy lucy  246 May  3 07:35 portfolio.conf
```


I used these instructions to automatically mount on startup:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

It seems to be in /media/Lucy(my account)
So what you are saying is:  You didn't have to do anything to mount the NTFS partition at /media/Lucy> 

To be honest, I just need it to be similar to how I've been working on Windows. I've only recently started using a local server, as I added PHP to my websites and needed to test it. I have been using wamp server (here: [http://www.wampserver.com/en/](http://www.wampserver.com/en/)) and had also been following these instructions to create virtual hosts: [http://forum.wampserver.com/read.php?2,127757](http://forum.wampserver.com/read.php?2,127757) - apparently it's necessary for everything to work the same as it would online, if I'm understanding it correctly. It also meant I could type portfolio/home.html for instance, rather than localhost/portfolio/home.html. As might be obvious, I don't fully understand this stuff. I don't need anything complicated setting up, just enough that it will emulate how the websites will work online (with php files) enough that I won't get any surprises after putting them up. Also, it only needs to work on this computer (I'll have wamp server installed in the Windows partition for IE testing). Oh, in case it's relevant I have also been using this for testing wordpress sites locally too.

If what I'm trying to do isn't a good idea, I can always just put the websites in the normal place and just copy the files over to the storage partition when I want to test in Windows.
Are you trying to put the websites for both WAMP and LAMP in the same partition ( the same directories)?  Sharing the directory space sounds reasonable to me.

Although you will have 2 web servers you can point both of them to the same directory (doc root) on the partition.  Is this what you are trying to do?

I know this is a lot of questions, but it's better to sort out the details first before actually configuring all of this.

---

### Post by lucy5 on 2015-05-06
Sorry about the late response.

> What I meant by this is how are you going to add or modify the files in the doc root -- upload completed pages or directly modifying the files in the doc root.
Oh, right - yes, just going to modify them directly. 

> I would not use notepad++ via w wine. It is needless complication. There are plenty of text editors available in Ubuntu. I use Gedit as a basic editor or BlueFish which is more like the old Dreamweaver.
Okay, I'm trying out some other editors at the moment. Possibly going to go with Geany. 

> Are you trying to put the websites for both WAMP and LAMP in the same partition ( the same directories)? Sharing the directory space sounds reasonable to me.

Although you will have 2 web servers you can point both of them to the same directory (doc root) on the partition. Is this what you are trying to do?
Yes to both :)

---

### Post by bab1 on 2015-05-06
We need to mount the storage partition manually.  You can only set the permissions at mount time.

Here is a the command I use to mount a NTFS partition temporarily via the terminal:

```
Mount -t ntfs UUID= <<The_UUID_number>> /media/Lucy/storage/www -o defaults,uid=1000,gid=1000,umask=002,iocharset=utf8
```

The <<  >> is a variable we need to know.  The stuff after -o is the options needed to set the ownership and permissions and file formatting (unicode).

To give you the exact command that you can cut and paste into the terminal I need some more information.  Post the output of this command:
```
sudo blkid -c /dev/null -o list

```
This should list the UUID of the partition we are using.  Am I correct about where we are mounting the partition?  Are you mounting the partition at:```
 /media/Lucy/storage/www


```or is it```


/media/Lucy/storage
```

Ultimately we will need to mount this via the fstab file so the partition is automatically mounted at boot up time.  The line will look something like this:

UUID=<<some_long_number>> /media/Lucy/storage/www ntfs defaults,uid=1000,gid=1000,umask=002,iocharset=utf8  0  0 

As I said above we need to start with the UUID numbers that we get from the blkid command.

---

### Post by lucy5 on 2015-05-06
The output is:

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  4A54CBCF54CBBBC7
/dev/sda3  ntfs    storage  /media/lucy/storage 6CECCCC8349AB8A5
/dev/sda5  ext4             /              0bd01f15-b827-4b8a-afef-bd86a0e561f7
/dev/sda6  swap             <swap>         18440039-3eaa-46c5-a426-438dc6fdebf2
```

> Am I correct about where we are mounting the partition?
The actual partition is just /media/lucy/storage (it contains other stuff as well) - but the location for the websites is /media/lucy/storage/www

---

### Post by bab1 on 2015-05-06
> **lucy5 said:**
> The output is:

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  4A54CBCF54CBBBC7
[COLOR="#FF0000"]**/dev/sda3**[/COLOR]  ntfs    storage  /media/lucy/storage [COLOR="#0000FF"]**6CECCCC8349AB8A5**[/COLOR]
/dev/sda5  ext4             /              0bd01f15-b827-4b8a-afef-bd86a0e561f7
/dev/sda6  swap             <swap>         18440039-3eaa-46c5-a426-438dc6fdebf2
```


The actual partition is just /media/lucy/storage (it contains other stuff as well) - but the location for the websites is /media/lucy/storage/www
You need to unmount the storage partition ([COLOR="#FF0000"]/dev/sda3[/COLOR]).  The you need to modify the mount point (/media/lucy/storage).

Unmount the partition with this command```
sudo umount /media/lucy/storage
```

Then set the permissions on the /media/lucy mountpoints```

sudo chmod -R 775 /media/lucy
```
Then we check our work.  Post the output of these commands```
ls -l /media

ls -l /media/lucy
```

On my machine I had to change the permissions on /media/bab so I could successfully mount a NTFS partition that was accessible by the web server.

Then you can manually re-mount the partition with this command```

sudo mount -t ntfs UUID=[COLOR="#0000FF"]6CECCCC8349AB8A5[/COLOR] /media/lucy/storage -o defaults,uid=1000,gid=1000,umask=002,iocharset=utf8

```
The number in blue is the UUID for the partition you have labeled as storage.  If all goes well you should see it mounted with this command```
df -h

```...the output will look something like this```
[COLOR="#FF0000"]/dev/sda3 [/COLOR]       30G   91M   30G   1% /media/lucy/storage
```

If this is correct then you should have permissions shown like this```

$  ls -l /media/lucy
drwxrwxr-x  1 lucy lucy 4096 Dec  1  2013 storage

```
If all goes well to this point, you should be able to create, modify or delete files in your doc root and the Apache2 web server should be able to display the web page.  If not we will have to find out what is not exactly correct.  I'm sure we can work it out.  

This will only work until you shut the machine off.  A reboot means you will have to manually remount the partition as we did above.  When we get everything working we can then edit the fstab file and make the mount automatic at boot time.

---

### Post by lucy5 on 2015-05-07
Output for
```
ls -l /media
```
is:
```
total 8
drwxrwxr-x+ 3 root root 4096 May  7 10:31 lucy
drwxr-x---+ 2 root root 4096 Apr 30 05:53 simon
```

Output for
```
ls -l /media/lucy
```
is:
```
total 4
drwxrwxr-x 2 root root 4096 Apr 30 06:46 Ubuntu 15.04 i386
```

Now, when I tried to re-mount as you said I got this:
```
ntfs-3g-mount: failed to access mountpoint /media/lucy/storage: No such file or directory
```

What should I do about this? One thing I should mention is just before I put that command in, I tried to copy something with ctrl-c which seems to send a command saying:
```
^C
```
I've done that before and have since been trying to right click instead, but it's a hard habit to get out of. I don't know what that does, so it could have something to do with that?

---

### Post by volkswagner on 2015-05-07
When posting requested commands, please include the command in your reply. We have to assume the result

```
total 4
drwxrwxr-x 2 root root 4096 Apr 30 06:46 Ubuntu 15.04 i386
```

Is from running:

```
ls -l /media/lucy
```

If this is true, it indicates your expected path of /media/lucy/storage may not be correct.

```

```


When copy and pasting in a terminal you can also use the shift key ("ctr + shift +c" or "ctr + shift +v") but I assume this would be
another habit to create ;)

Perhaps /media/lucy/storage is created by your previous mounting mechanism.

If you only find:
```
drwxrwxr-x 2 root root 4096 Apr 30 06:46 Ubuntu 15.04 i386
```
When running
```
ls -l /media/lucy
```

Then there's a problem. 

I don't want to make suggestions here, but I'll tell you possible pitfalls.
If you create /media/lucy/storage it will likely mess up your current mounting mechanism.
If you create a new directory /media/lucy/new and mount there, it will require changing apache vhost config.

First step is to post back bab1's request while including the command itself.

---

### Post by Morbius1 on 2015-05-07
Please post the output of the following command:
```
cat /etc/fstab
```
It appears that this is an internal partition and you shouldn't be mounting it under /media/$USER ( /media/lucy in this case ). /media/$USER is created by the system, it assigns permissions via an ACL such that only root and $USER can traverse the folder, and all of that is by design.

---

### Post by lucy5 on 2015-05-07
> **volkswagner said:**
> When posting requested commands, please include the command in your reply.
Sorry - I was in a rush. I've edited my post.

---

### Post by lucy5 on 2015-05-07
> **Morbius1 said:**
> Please post the output of the following command:
```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0bd01f15-b827-4b8a-afef-bd86a0e561f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=18440039-3eaa-46c5-a426-438dc6fdebf2 none            swap    sw              0       0
```

---

### Post by Morbius1 on 2015-05-07
Let's automount the partition so that it mounts at boot time:

[1] Unmount the partition if it's mounted:
```
sudo umount /media/lucy/storage
```
[2] Create a new directory under /media:
```
sudo mkdir /media/storage
```
[3] Edit /etc/fstab and add a line to the end:
```
UUID=6CECCCC8349AB8A5 /media/storage ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```
[4] Mount the partition:

Are you really running Ubuntu 15.04? If you are run these commands - one at a time to mount the partition to /media/storage:
```
systemctl daemon-reload
systemctl restart /media/storage

```
If you are not running 15.04 just run this command:
```
sudo mount -a
```
[COLOR=#0000cd]*You could probably run that command in 15.04 but systemd is a little confused about what fstab is for so it may error out on you.*[/COLOR]

Then run the following command and verify that everything is where it should be:
```
ls -l /media/storage
```

The fstab entry I posted above will allow access to everyone. You may want to adjust that in the future and the others who have posted no doubt have their own suggestions. But for now just adjust your server configuration to point to /media/storage/whatever instead of /media/lucy/storage/whatever and see if things improve for you.

---

