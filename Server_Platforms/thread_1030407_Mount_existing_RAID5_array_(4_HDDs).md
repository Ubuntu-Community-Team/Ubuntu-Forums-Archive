---
title: "Mount existing RAID5 array (4 HDDs)"
date: 2009-01-04
forum: Server Platforms
---

### Post by adlabens on 2009-01-04
I built a RAID5 array in OpenSuSE 11.0, then realized that I didn't want to use OpenSuSE but instead prefer the Ubuntu distros. The OS is on it's own HDD - so I can easily (& have) swap it out for a blank drive upon which I've installed Ubuntu Ibex Server, and the RAID5 array is 4 separate drives. I installed Ubuntu without the RAID5 array physically connected.

I can simply swap out the OS HDD and change the operating system - takes less than 2 minutes. I'm trying to mount the existing RAID5 array in Ubuntu Server 8.10 so that I can get access to my data without having to restore nearly 300 gB from our two desktops (thankfully, I've not yet erased them!).

I've tried using Webmin, but I'm getting error messages with everything that I try. My OS drive is /dev/sda (doesn't matter which OS [HDD] I'm using), and my four RAIDed drives are sdb, sdc, sdd, & sde. My mount point is /NW-DATA. 

I'm thinking it should be an easy task to simply mount the array, but it's turning into far too many hours of hacking. This is our home server. But, I'm wanting to get completely away from Microsoft, and this is the first step - migrating our data off the WinXP Pro boxes.

BTW, it works great in OpenSuSE, internet access, access to the files (yes, Samba) from the XP Pro boxes, and everything. & I have access to the Ubuntu "machine" from the XP Pro boxes.  I just need to get the RAID5 array mounted - preferrably without any loss of data, but I've got it backed-up, just in case!

Any help will be GREATLY appreciated.

THANK YOU!!!
David
San Antonio, TX

---

### Post by fjgaude on 2009-01-04
Well, we've run across this situation before, and this has worked most of the time: re-name or delete the **/etc/mdadm/mdadm.conf** file, remove **mdadm**, re-boot. The re-install mdadm and run this:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto created and you should be able to mount the raid5 array.

Let us know how you do.

---

### Post by adlabens on 2009-01-04
That resulted in ...

/dev/md/0 has been started with 4 drives

Now, I'm wondering what I need to do with it.  I'm thinking using the mount command, but need to read up on how it works.  There are shared folders on the array, and it attempts to allow me to log-in to it/them, but it fails.  I did redo the smbpasswrd, but that didn't allow access.  I think it's because I can't see /NW-DATA (the name of the highest-level shared folder) in the root (/) folder.

I am keeping all these commands, and their results, in a document - because I KNOW there will be a day when I need to do this again because of an OS HDD crash.  But, more than that, once I get this all working - I'm putting in another blank OS HDD & doing it all again, following the instructions that I am putting into the document, so that I'll know I can do it again in several years (after I've forgotten all this)!

THANK YOU!
David Labens
San Antonio, TX

---

### Post by fjgaude on 2009-01-04
You have to mount the /dev/md0 to a mountpoint, any will do.

```
sudo mkdir /home/raid
```

Then mount:

```
sudo mount -t ext3 /dev/md0 /home/raid
```

I'm assuming the filesystem is ext3. Change the command to whatever it is, if it isn't.

Let us know how you are doing.

---

### Post by luckyluke699 on 2009-01-04
Hi,

I've been learning about this for the first time recently too, and I thought I'd just add the following link for you in this excellent forum post by kragen, so take a look at...

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)


Section 7 basically lists everything you need to know. It's easy as 1,2,3 and is listed in that excellent thread...

1) Install mdadm 
2) Create or assemble your drive
3) Mount your drive

---

### Post by adlabens on 2009-01-04
Frank,

[INDENT]I actually had tried that within a few minutes of running the instructions for fixing mdadm.

I ran the mount command:
  mount -t ext3 /dev/md/0 /NW-DATA

& got the error message: 
  mount: mount point /NW-DATA does not exist

So, I thought about it (this was prior to your last post), and tried to make the directory like this (from the root directory):
  mkdir /NW-DATA

That worked, so I retried the mount command:
  mount -t ext3 /dev/md/0 /NW-DATA

and it brought me back to the command prompt.

SO, I did "cd /NW-DATA" and it had the /DATA folder that I'd created in OpenSuSE, and in that folder were the other sub-folders that I'd created & populated.  So, I can see everything in PuTTY, giving me a huge sigh of relief that the data is intact and on the system.

However, I can't seem to get to the data from my WinXP Pro boxes.  I've created my username & password with smbpasswd.  I can see the server in the workgroup, and I can get TO the server (my /home folder), but not to the /NW-DATA folder.  

This feels like a sharing issue.  I'm thinking that the folders need to be shared in Ubuntu (it's not enough that they were shared in OpenSuSE, the tag apparently doesn't flow with the data but with the OS, which could well be a security flaw - you could pull out the HDD and mount them in another system & get access to them???).  

Let me see what I can do with this ...[/INDENT]

Lucky Luke,

[INDENT]Thanks for the link.  I had actually read through that entire thread before I posted my question.  Now that Frank has set me on the proper path, that other thread is a lot more understandable:KS[/INDENT]

THANK YOU!!!
David Labens
San Antonio, TX

---

### Post by aesis05401 on 2009-01-04
> **adlabens said:**
> ...This feels like a sharing issue.  I'm thinking that the folders need to be shared in Ubuntu (it's not enough that they were shared in OpenSuSE, the tag apparently doesn't flow with the data but with the OS, which could well be a security flaw - you could pull out the HDD and mount them in another system & get access to them???) ...


The behavior you are describing is why conventional wisdom says that if you have physical access to a machine you own the machine... And there is no need to swap any HDDs.

While whole disk encryption is coming along nicely (SSD speed increases are huge), most data can be compromised by rebooting AverageComputerX with a bootable usb key or livecd inserted.

---

### Post by adlabens on 2009-01-04
> **aesis05401 said:**
> The behavior you are describing is why conventional wisdom says that if you have physical access to a machine you own the machine.

But, if someone stole my computer, they'd not need my passwords to get access to the data - they could simply plug in their own OS HDD and they'd have everything.  

Not that I've considered this with our Windows environment (I've not), but this situation has prompted me to think about it.  Of course, all of our important stuff (spreadsheets with accounts & passwords) have the data hidden & password protected, but I do have images of our social security cards.  Which means I need to consider a little better security.  

Very thought provoking.  You have confirmed what I was thinking, and that I need to think a little deeper about this issue.  I guess, if we were to go on an extended vacation, we should yank the data array and lock it up off-site, rather than simply pulling the OS HDD.

THANK YOU for the info!

David Labens
San Antonio, TX

---

### Post by fjgaude on 2009-01-04
I'm not sure, adlabens, but have you set the shares in Ubuntu? You certainly have to do that before Windows can see them.

If you are using Gnome and **Nautilus** it is easy simply right-clicking a folder and noticing the Sharing Options near the bottom-left pane.

Or you can add them to the bottom of the **/etc/samba/smb.conf** file, like so:

```
[raid]
path = /NW-DATA
available = yes
browsable = yes
public = yes
writable = yes
```

Let us know how you are doing.

---

### Post by adlabens on 2009-01-04
> **fjgaude said:**
> I'm not sure, adlabens, but have you set the shares in Ubuntu? You certainly have to do that before Windows can see them.

If you are using Gnome and **Nautilus** it is easy simply right-clicking a folder and noticing the Sharing Options near the bottom-left pane..

Frank,

I'm actually trying NOT to use the keyboard & monitor connected to the server.  If I can do all this without them, then I'll feel much more confident making it headless, and then also more confident to put the server into a more remote location in the house.  I'm running everything, so far, with PuTTY from my desktop, and I've installed Webmin for a remote GUI, tho I've not got much confidence in that.  

That said, I did go into Webmin and create the shared folder, and then made sure that the machine had users for myself & my wife, then went back to PuTTY and ran "smbpasswd -a user" for both myself and my wife, then did a reboot of my desktop machine to login, but I still can only see the folder and can't get into it.  Your next suggestion (& something else I had to do when setting up OpenSuSE so that we could BOTH write and change files from the other) are my next effort.

> **fjgaude said:**
> Or you can add them to the bottom of the **/etc/samba/smb.conf** file, like so:

```
[raid]
path = /NW-DATA
available = yes
browsable = yes
public = yes
writable = yes
```

Let us know how you are doing.

Thanks,
David Labens

---

### Post by adlabens on 2009-01-04
> **fjgaude said:**
> 

```
[raid]
path = /NW-DATA
available = yes
browsable = yes
public = yes
writable = yes
```

Let us know how you are doing.

I tried this, and I can see "raid" in my Windows Explorer but can't get to it.  I changed the [raid] to [NW-DATA] and I can now see THAT, but still can't get to it.  I've confirmed that I have the users in SAMBA.  It even asks me for a password (& I'm giving the right one), but then won't let me in!

And, just for grins, I go back into PuTTER & confirm that the folder is present & populated.  HOWEVER, I have to SUDO to get into it, I can't get into it under my own login!

This weekend has been a lot of progress, albeit a long weekend.  I've managed to gain enough confidence in Ubuntu to close the server box (albeit with the OpenSuSE drive still physically installed, although without the data cable).  As soon as I'm over this little hump, I'll wipe out the OpenSuSE HDD completely, and do a fresh install of Ibex, just to get more familiar with it - & to make sure my documentation is correct!

Meanwhile, I'm calling it a night.  The 7 yr old starts back to school tomorrow morning, and I'm back at work at 11:15 am.  

THANKS,
David Labens
San Antonio, TX

---

### Post by fjgaude on 2009-01-06
Would let you in, likely because you don't have the password in samba:

```
sudo smbpasswd -a <name>
```

Your name or others who have access.

---

### Post by adlabens on 2009-01-06
> **fjgaude said:**
> Would let you in, likely because you don't have the password in samba:

```
sudo smbpasswd -a <name>
```

Your name or others who have access.

Frank,

No, I confirmed that I had created the user for myself and my wife, with a password included.  It still wouldn't let me in.  Finally, last night, I broke down & reconnected the OpenSuSE drive & booted it up, then copied the smb.conf file to my desktop, then shut it down and reconnected the Ubuntu drive and copied a few of the data sections from the saved smb.conf file to the one on the Ubuntu HDD, restarted Samba, then rebooted my WinXP Pro desktop, and I'm in.  So is my wife.  Obviously, I have much to learn about Samba, but at least I know that I have a working smb.conf file that I can use, if needed.

So, now, my next step is to wipe out the OpenSuSE HDD and do a fresh install onto it of Ubuntu Server 8.10.  I've played with the current Ubuntu installation to get it working, so now I can play with a fresh one without having to worry about messing up the first one (separate HDDs), and I'll eventually have a perfectly executed installation along with a documentation containing complete instructions that will enable me to easily and quickly do a fully functional reinstallation (disaster recovery) and be confident that it'll work with no problems.

Obviously, I don't have to know how the circuitry works to be able to watch TV.  But, I definitely want to know more about Samba so that I can do an increasingly better job of establishing stronger security.  I don't have to build Fort Knox.  But, I'd like something that'll be adequately secure, with the possible exception of replacing the OSS HDD and getting access that way.  I have spent a little time reading the samba.org website (HOWTOs and Examples), so that's one resource - albeit a bit over my head at this point.  **If you have any books or websites that are good for learning, I'd appreciate any suggestions.**

I appreciate your help.

Thank you,
David Labens
San Antonio, TX

---

### Post by ljwobker on 2009-01-07
David-

On the security note, you may want to look into the encrypted directory functionality built into 8.10: 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

this is the simple route, and allows each user to selectively put stuff into an encrypted "~/Private" directory. 

A different approach is to encrypt the entire disk, or build a partial encryption 'container' within the file system and then put stuff selectively into that.  Lots of good info on the options can be found here:

[http://ubuntuforums.org/search.php?searchid=54153902](http://ubuntuforums.org/search.php?searchid=54153902)

-- I just ran it and several of the early hits looked quite useful.

Viel Gluck!

---

