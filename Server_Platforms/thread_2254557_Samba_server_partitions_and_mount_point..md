---
title: "Samba server partitions and mount point."
date: 2014-11-28
forum: Server Platforms
---

### Post by gardenair on 2014-11-28
[COLOR=#333333][FONT=UbuntuRegular]hi,  am going to deploy Ubuntu server having following server on it:[/FONT][/COLOR]

[LIST]
[*]Samba server
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]The thing which I want to discuss is what is the best approach for the mount point of partition. Suppose I want to create samba server for a production environment where the users will keep their  How should I set up my partition scheme? [FONT=Arial]**For 70 users using (Windows xp,Windows 7 and windows 8 ) to keep their office files which are office 2007 and pdf files in their file server **.I do it by my own mind and i will make partition generic. 
My Hard Disk size is 300 GB and the size is which i will create is 

[/FONT][FONT=Arial]/boot 100 MB [/FONT]
[FONT=Arial]Swap (Double of ram) [/FONT]
[FONT=Arial]/home (according to own will like 5 GB) [/FONT]
[FONT=Arial]/ (Rest of the space for whole hard disk 

Normally the mount points are

[/FONT][FONT=Arial]/ [/FONT]
[FONT=Arial]/boot [/FONT]
[FONT=Arial]/home [/FONT]
[FONT=Arial]/tmp [/FONT]
[FONT=Arial]/usr [/FONT]
[FONT=Arial]/var [/FONT]
[FONT=Arial]/usr/local [/FONT]
[FONT=Arial]/opt [/FONT][FONT=Arial]
[/FONT]
[/FONT][/COLOR]
Is it is professional approach for samba server ? please guide me.

thanks
gardenair

---

### Post by mikewhatever on 2014-11-28
Not sure what you mean by "professional". 
What exactly are you planning to do with those mount points?
Why do you need /boot?
Where will you keep all the user data?

---

### Post by Jonathan L on 2014-11-28
Hi Gardenair

The main thing is where your users will keep all their files, what kind of shared areas they need and so on.  My suggestion would be to make it as simple as you can: perhaps just root, swap, home.

I'd also recommend taking a look at quotas to see if that helps your space management.  ([Notes]("http://timstaley.co.uk/posts/setting-up-disk-quotas-with-ubuntu-1204/"))

If you have significant sharing requirements you might find that BSD-style group inheritance is a good idea (mount option bsdgroups, see mount(8) ) and also take close look at the permissions settings in Samba, especially umask.  In general it's easier to manage sharing/privacy with group membership than permission bits.

Hope that's of some use.

Jonathan.

---

### Post by redmk2 on 2014-11-28
> **gardenair said:**
> [COLOR=#333333][FONT=UbuntuRegular]hi,  am going to deploy Ubuntu server having following server on it:[/FONT][/COLOR]

[LIST]
[*]Samba server
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]The thing which I want to discuss is what is the best approach for the mount point of partition. Suppose I want to create samba server for a production environment where the users will keep their  How should I set up my partition scheme? [FONT=Arial]**For 70 users using (Windows xp,Windows 7 and windows 8 ) to keep their office files which are office 2007 and pdf files in their file server **.I do it by my own mind and i will make partition generic. 
My Hard Disk size is 300 GB and the size is which i will create is 

[/FONT][FONT=Arial]/boot 100 MB [/FONT]
[FONT=Arial]Swap (Double of ram) [/FONT]
[FONT=Arial]/home (according to own will like 5 GB) [/FONT]
[FONT=Arial]/ (Rest of the space for whole hard disk 

Normally the mount points are

[/FONT][FONT=Arial]/ [/FONT]
[FONT=Arial]/boot [/FONT]
[FONT=Arial]/home [/FONT]
[FONT=Arial]/tmp [/FONT]
[FONT=Arial]/usr [/FONT]
[FONT=Arial]/var [/FONT]
[FONT=Arial]/usr/local [/FONT]
[FONT=Arial]/opt [/FONT][FONT=Arial]
[/FONT]
[/FONT][/COLOR]
Is it is professional approach for samba server ? please guide me.

thanks
gardenair

The traditional approach to this is to have all of the shared directories at */srv/samba/*.  This way all of the *shared* directories are in one area.  The home directories can also be in this area.    See [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for an explanation of the Linux file system directory structure.  Here is the listing for /srv from that site```

    /srv

	Site-specific data which are served by the system.
```...served data.

Samba has one share configuration for all the users private (home) directories.  It's called [homes].  The rest of the shared directories should have common user group(s) that the participating users are a member of.  The group ownership inheritance needs to be set by command chmod. 

Explain you mean here; what are you doing here?```

Normally the mount points are

/boot
/home
/tmp
/usr
/var
/usr/local 
/opt

```

How many groups are needed for you environment?  How many shared directories are needed for each of these groups?

A very basic setup for NAS host partitioning would be```

 /   = the root file system (10 GB)
swap (1.5 X RAM on non gui setup)
/home  = local users home directories (5GB)
/srv = the rest of the disk -- this can be used for Samba and NFS file sharing
```...more complex partitioning can be used if needed.  Note that 300 GB is kind of on the smallish side for 70 Windows users.  My home setup for 4 Windows users is 1TB for /srv alone.

---

### Post by gardenair on 2014-12-01
Thanks all for your kind reply. Well I have only 70 users using windows xp,windows 7 and windows 8 at client side. They want to same there office files  which are normally in Ms office 2007 and in pdf format.A common share like z drive where each users can keep data and rest of the people can also see but can not delete it.Currently i am using windows server 2003 which is doing this job and 30GB is assign in my D partition of windows server 2003.
I want to switch it into Linux  so the viruses should not spread over the network.
The main thing is that should I assign /home partition for this purpose or /var  partition.  

*You can see the  drive in the attachment here where i keep my file over the server*.


thanks
gardenair

---

### Post by redmk2 on 2014-12-01
> **gardenair said:**
> Thanks all for your kind reply. Well I have only 70 users using windows xp,windows 7 and windows 8 at client side. They want to same there office files  which are normally in Ms office 2007 and in pdf format.A common share like z drive where each users can keep data and rest of the people can also see but can not delete it.Currently i am using windows server 2003 which is doing this job and 30GB is assign in my D partition of windows server 2003.
I want to switch it into Linux  so the viruses should not spread over the network.
The main thing is that should I assign /home partition for this purpose or /var  partition.  

*You can see the  drive in the attachment here where i keep my file over the server*.


thanks
gardenair
I understand that you have 70 Windows clients that want to share their Office and PDF files.   The Z: drive is just the mapping to wherever the shared directory is located on the server.

What I don't understand is this:> *[COLOR="#0000FF"]The main thing is that should I assign /home partition for this purpose or /var  partition. [/COLOR]* 
After stating this> *[COLOR="#800080"]Is it is professional approach for samba server ? please guide me.[/COLOR]*

You can share any section of the Linux file system but the 2 sections you propose (/home and /var) are not the most professional (or traditional) locations.  You can use the /home branch for the [homes] share but this is not the place on a server for the commonly shared data.  Neither is the /var branch.  Does this mean you can't do that?  No.  It just means you can find more appropriate locations for the data.

It is unclear what permissions you want for your users common data.  If you want users to share data (read, write) then all you need to do is create a common group for these users and set the group ownership at the root directory of that share.  To provide BSD style group inheritance you should chmod the root directory of the share to 2775 permissions.  All users can modify and delete any file or directory. 

For users to be able to create (write) files and directories without the ability to be to delete others files from a directory is a somewhat more complicated.  You should set ownership of the root directory of the share to  root:root and chmod the directory to 1775 permissions.  This last directory will allow any user to create and modify a file.  All directories will by default be set to 3775.  This is due to the default umask setting.  The best way is to set the create mask for directories using the Samba parameters since these will be Samba Shares anyway.  I know this is complicated, but if you want user access to read others data without the ability to delete this is the way to do that with Linux.  If you wanted to you can use ACL's to do the same thing.

There will be plenty of experimentation to get this set correctly, but it can be done.  Once again; where in the file system you do this is up to you.  I advise you to create all of this at /srv/samba with root:root ownership on /srv and /srv/samba.  Then set up the [homes] share for the users private data by sharing their individual /home to that user only.

---

### Post by gardenair on 2014-12-01
Thanks "[COLOR=#000000]redmk2" for your prompt reply. Well i now just focus on data location of users. 

I know how to do make partitions,file system**.I just want the appropriate location so that the users may keep their date .**Just imagine for a moment  that you are going to make a Samba server so where u will keep the data? So what will be your appropriate location. 

I am taking now in a broad scope of Linux. Either you r using Red Hat,Cent OS ,Debian or Ubuntu. 


[/COLOR]

---

### Post by redmk2 on 2014-12-01
> **gardenair said:**
> Thanks "[COLOR=#000000]redmk2" for your prompt reply. Well i now just focus on data location of users. 

I know how to do make partitions,file system**.I just want the appropriate location so that the users may keep their date .**Just imagine for a moment  that you are going to make a Samba server so where u will keep the data? So what will be your appropriate location. 

I am taking now in a broad scope of Linux. Either you r using Red Hat,Cent OS ,Debian or Ubuntu. 


[/COLOR]
I told you where to put the data in post  #4 and again in my last post.  Put the users Office data at** /srv/samba** and their private data at **/home**.  Go back and re-read my #4 post.  There is a link that shows you the Linux file system hierarchy with a description of what each file system branch is used for.

You will then share the /srv/samba directory and the /home/<user> directories using Samba.

---

### Post by gardenair on 2014-12-02
thanks for your reply.I appreciate your great guidance.One thing more i want to discuss,in Ubuntu during installation we create partition and by default under the mount point there is /srv  as well.For user data i will keep under that partition. Now in a broad sense if we talk rest of the linux operating system like Centos there is no /srv mount point by default durning installation. The only mount points are they offer are

[COLOR=#333333][FONT=Arial]*/ *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/boot *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/home *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/tmp *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/usr *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/var *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/usr/local *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][I]/opt 

[/I][/FONT][/COLOR]
So being a linux users i want to know where they will keep users files .Though there is srv  directory but there is no /srv mount point as ubuntu offers.So other than ubuntu users there is no such way to mount /srv as a separate partition. What you say about it.

thanks once again for guiding me.
gardenair

---

### Post by redmk2 on 2014-12-02
> **gardenair said:**
> thanks for your reply.I appreciate your great guidance.One thing more i want to discuss,in Ubuntu during installation we create partition and by default under the mount point there is /srv  as well.For user data i will keep under that partition. Now in a broad sense if we talk rest of the linux operating system like Centos there is no /srv mount point by default durning installation. The only mount points are they offer are

[COLOR=#333333][FONT=Arial]*/ *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/boot *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/home *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/tmp *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/usr *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/var *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]*/usr/local *[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][I]/opt 

[/I][/FONT][/COLOR]
So being a linux users i want to know where they will keep users files .Though there is srv  directory but there is no /srv mount point as ubuntu offers.So other than ubuntu users there is no such way to mount /srv as a separate partition. What you say about it.

thanks once again for guiding me.
gardenairYou are free to create a *_directory that is shared_* anyplace in the file system.  These shared directories are not called "partitions" or "mountpoints".  A partition is a section (part of) of a block device such as a hard drive (HDD), solid state drive (SSD) or a flash drive.  A mountpoint is a directory that the system uses to mount a portion of the file system that is on a separate partition.  Samba shares are  directories.

The question of where to create a shared directory is your personal choice.  It is more important that the shared directory be somewhere that is generally accepted by most Linux system administrators. My general rule is to place general data outside of the /home file system.  I'm also concerned that there be some flexibility.  Later on you may indeed need to add more storage capacity by mounting a files system that resides on a partition that is on separate hard drive.  My Samba server also hosts my backup drive.  This drive is not mounted until I need it.  The drive has 1 partition and that partition is mounted at /srv/backup.  In my systems all

Think about that for a second.  An entirely separate file system that resides on a separate device.  For my documentation I  just list all served and stored data is located below /srv.  It is not scattered around separate sections of the file system.  If you wanted to store all of this at */data *or* /mystuff* or* /var/data* anywhere else you certainly can.  Your question was what is most appropriate (i.e. professional).  In the end you just have to create the directory you want to share (mkdir), set the ownership and permissions and define the share parameters (in smb.conf).

---

### Post by gordintoronto on 2014-12-02
First, Samba shares folders, not partitions. Keep them in /home. Don't bother with anything but / and /home (and maybe swap.)

If at all possible, you should take some old computer and install Ubuntu Server 14.04, and play around with it. Put a router on your network, attach the server and another old computer as a client (so those computers are on a separate sub-net from your main network.). 10 hours of hands on is worth 1000 hours of reading.

---

### Post by redmk2 on 2014-12-02
> **gordintoronto said:**
> First, Samba shares folders, not partitions. Keep them in /home. Don't bother with anything but / and /home (and maybe swap.)

If at all possible, you should take some old computer and install Ubuntu Server 14.04, and play around with it. Put a router on your network, attach the server and another old computer as a client (so those computers are on a separate sub-net from your main network.). 10 hours of hands on is worth 1000 hours of reading.

Respectfully, I disagree on both parts.  The OP was looking for guidance on how to setup a Samba file server from a professional point of view.  Not just a "slap dash get it up and running any way you can" scenario.

My feeling is that if you want to learn how to install and maintain Samba you should learn how it works in theory and then apply that knowledge to a testbed server.  There are plenty of non-intuitive aspects to Samba in particular and SMB/CIFS in general.

I say;  understand the technical parts of Samba and apply that knowledge to the real world if you want to be professional about the task.

---

### Post by gardenair on 2014-12-03
Thanks a lot for your comprehensive reply. I appreciate you. :popcorn:

---

