---
title: "Making a file server....not working for me...using Ubuntu Server 10.04"
date: 2010-05-20
forum: Server Platforms
---

### Post by useful1 on 2010-05-20
Hi guys,

Im trying to make a server for my home network, so I can backup regularly a folder on a windows machine of mine.

Please bear with the newbie linux guy here.  Just learning about Ubuntu a few days ago.  

My setup looks like this:
```

Internet <----> Modem <-------> Router 
                                | |  |
                                | |  |
Ubuntu Server 10.04 ------------| |  |
                                  |  |
Windows XP PC --------------------|  |
                                     |  
Windows Vista PC --------------------|

```

So basically, all the computers are connected to the router.
And just installed Ubuntu Server 10.04 on one.

I've been following a tutorial about making a file server.
And the link is [http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3")

I've made changes to /etc/network/interfaces to:

```

address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.199
gateway 192.168.1.1

```

Then I made changes to the file /etc/hosts to:

```

127.0.0.1         localhost.localdomain    local hosts
192.168.1.192     server.rice.com          server1

```

Then when the tutorials asks me to:
```

echo server.rice.com > /etc/hostname
/etc/init.d/hostname.sh start

```

Ubuntu couldnt the find hostname.sh executable, 
so I tried "/etc/init.d/hostname start", and that seemed to work.

But I get a response:
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service hostname start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start hostname hostname stop/waiting.

So, basically, i get some response back of jibberish, I dont understand.  

Then according to the tutorial, I should run:
hostname
hostname -f

When I type hostname, I get: server.rice.com
When I type hostname -f, I get: Name or service not known


-----

So, Im afraid to continue with the tutorial until I solve this part since, Im getting not normal response from the tutorial.

Any advice guys?

- U

---

### Post by -Jeremy- on 2010-05-20
With hostname -f you are trying to ask the system's fully qualified domain name, other than that it does nothing and should really be of no importance to you if your server is just for the clients within your own LAN.

But if you'd really like to know you could (and should, according to the manual!) use:

'hostname --all-fqdns'

---

### Post by useful1 on 2010-05-20
Ok, after reading that post, I continued on with the tutorial.
And everyone was going smoothly until I reached section 8.

Which is the section on Installing the second hard drive.
----
Tutorial asks to do a: fdisk -l
in my case brings up:
```

Disk /dev/sda: 3227 MB, 3227148288 bytes
255 heads, 63 sectors/track, 392 cylinders
Units - cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x000a0fd4
   
Device    Boot      Start         End     Blocks    Id    System
/dev/sda1   *           1         368    2952192    83    Linux  
Partition 1 does not end on cylinder boundary.
/dev/sda2             368         393     196609     5    Extended
/dev/sda5             368         393     196608    82    Linux swap / Solaris

Disk /dev/sdb: 3243 MB, 3243663360 bytes
255 heads, 63 sectors/track, 394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069d30

   Device    Boot     Start      End    Blocks    Id System


```

I proceed with the following commands as stated by the tutorial:

mkdir /media/store
chmod 777 /media/store

which means, make a directory.  then change permissions to
/media/store.  Im not exactly sure what is store.  Its not a file
or a directory.  It seems more like a pointer to a location.  But thats just a guess.

The tutorial then asks to: mount /dev/hda /media/store
In my case, my secondary hard drive is called "/dev/sdb"
So I type in:

mount /dev/sdb /media/store

The feedback I get is:
mount: you must specify the filesystem type

----
As yet again, Im halted from going forward with the tutorial.
Any tips here guys?

- U

p.s.  Thanks again for viewing and attempting to explain stuff for me.

---

### Post by CharlesA on 2010-05-20
The IP address looks strange. For the default subnet mask of 255.255.255.0, the broadcast should be 192.168.1.255. Everything else looks ok.

It sounds like you want to set the DNS domain name, but I am not sure how to set that, outside of reinstalling or using DHCP to assign it.

You created a directory/folder by creating the /media/store directory. It sounds like you will be using it as a [mountpoint]("http://www.psychocats.net/ubuntu/mountlinux").

As for mounting: What file system does /dev/sdb use? It looks like it has no partitions on it, judging from the fdisk command.

---

### Post by useful1 on 2010-05-20
> 
The IP address looks strange. For the default subnet mask of 255.255.255.0, the broadcast should be 192.168.1.255.

Oops, that looks like a typo on my part.  The IP Address
is 192.168.1.102.  Instead of 192.168.1.192 posted earlier.
And I'll change the broadcast to 192.168.1.255.

Although, I'm not sure what the changes does.  Im just blindly trying to get this to work. 

> 
As for mounting: What file system does /dev/sdb use? It looks like it has no partitions on it, judging from the fdisk command.


Normally, on windows XP.  I would just format the hard drive.
usually in the Windows GUI by right clicking and hitting format.
Or I would go into the command prompt and type format D: (where D: is the drive location)

I'm not sure how about to go and do that from the linux 10.04 command prompt.

---

### Post by CharlesA on 2010-05-20
Best thing to do would be to boot off an Ubuntu livecd and run sudo gparted from a terminal, that way you can check to see if there are any partitions on it and create/format them there.

It can be done by command line, but I've always found that it's easier if you can see it.

---

### Post by useful1 on 2010-05-20
Ok so, I continued on.  Trying to figure out how to partition and format the 2nd hard drive.  And after 2 hrs of online searching.

the command: "fdisk /dev/sdb1" was the answer.  Then pressing n for a new partition, then p for primary partition then 1 for making 1 partition, so that I use the whole disc.

Afterwards formatting was a problem.  Since I was in the command line, I wanted to use command line options instead of rebooting of and using the recommended GParted GUI.  

At first, I tried mkfs -t ntfs /dev/sdb1.  Then I got an error.
Turns out Ubuntu doesnt know what ntfs is. (I think)  So I had to install stuff to the OS, using the apt-get ntfsprogs command.

After installing that stuff.  mkfs -t ntfs /dev/sdb1 worked.
----------
After partitioning, then formatting, I continued following
the tutorial on [http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3")

So, I did what the tutorial asked.  
mkdir /media/store
chmod 777 /media/store
mount /dev/sdb1 /media/store
vi /etc/fstab

then i added: 
```

/dev/sdb1 /media/store ntfs defaults 0 0

```
closed the file
typed: mount -a
--
Then I edited the smb.conf (vi /etc/samba/smb.conf)

The workgroup setting was already set to WORKGROUP,
so I didnt change that.

then added the following lines per the tutorial:
```

[sdb1 public hard disk]
comment = Public Folder
path = media/store
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group

```

Now, the tutorial asks me to do the following command:

/etc/init.d/samba force-reload
smbpassword -a family

---
But when I do the /etc/init.d/samba force-reload, I get an error.
bash: /etc/init.d/samba: No such file or directory

And hence, Im stopped again from continuing on.  
Any ideas on what to do next anyone?

- U

---

### Post by CharlesA on 2010-05-20
It just wants you to restart samba.

Run this:

```
sudo restart smbd && sudo restart nmbd
```

---

### Post by useful1 on 2010-05-20
```

sudo restart smbd && sudo restart nmbd

```

Ran this.  restart smbd worked.  restart nmbd didnt work.
Got an error restart: Unknown instance:

----------

It looks like I completed the tutorial to make a file server on
ubuntu.  After that restart step.  

I went to go to my Windows networking and sharing center, but,
alas, I could not find the server on the Windows Networking and Sharing Center.  It looks like all that setup time was a bust.
I was hoping to see an icon showing a new computer or something
that I could put files onto.  But the networking page on windows looks like same to me.

Any ideas if I need to do any additional steps?

Thanks,
- U

---

### Post by NeddyDownUnder on 2010-05-20
Seems like you've got most of it working ok, but that tutorial you followed does not look all that great. It tells you what to do with little explanation of what you are doing, thus when you get stuck you are lost.

Now that you have a static IP and the host name setup and your storage HD mounted with fstab maybe you should just follow this guide to get Samba up and working...

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

In future if I were you I would be more inclined to follow the howtos and help files in the Ubuntu documentation and then use external sources when necessary... The link below is a good place to start:

[https://help.ubuntu.com/10.04/serverguide/C/index.html]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

Or if you do use an external source try to find one a little more up to date as a lot of your problems were caused by changes in Ubuntu Server (i.e. upstart)

Good luck.

---

