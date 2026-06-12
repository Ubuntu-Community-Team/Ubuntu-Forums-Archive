---
title: "Setting up a home server correctly?"
date: 2006-04-19
forum: Server Platforms
---

### Post by peterscj on 2006-04-19
I have been playing with Ubuntu and working on setting up a home server for a few weeks now and I would like some advice on how to set it up correctly.  I have set it up as a Samba server a couple times because I can't decide exactly how I should partition it.  I want to make sure that it is partitioned so that I can upgrade my distro without touching my stored data.  I should warn you that I am pretty new at working with Linux in general and have absolutely no experience setting one up as a server.

I would like to get my server set up to run as a samba server and as a ftp server for now but will probably want to add webhosting and mail later.  If this is a problem,  I can use a seperate computer for these two tasks later.

The system I am wanting to use has a 1.2GHz processor, 512 MB RAM, and a 250GB hard drive.

I have looked at different guides on setting up a samba server and some say to make a partition for /data or some other such folder while others say to just make a big partition for /home.  I am kind of curious as to which would be a better solution. Considering that I want to be able to also use it as an ftp server and maybe a web/mail server later.

Finally, is there a way that I can sftp into a samba shared directory?  I would like to have a directory for storing some of the programs I have written for school but would also like to be able to sftp into the file from outside my network in order to pull them off my server.  I know that I could just make a duplicate copy in each file but that seems like a bad idea since I would then have to worry about keeping them synchronized.

I would like to make this a work in progress so if anyone can point me in the right direction I will update this with where I am in the process.  I will try to take notes so that I can write up a how to later.

Thanks in advance for any help you can provide

---

### Post by peanut butter on 2006-04-19
ok for ftp (i will probably get a bunch of opposition on this) i would install wu-ftpd. it worked for me out of the box.
for sftp just install openssh-server and youhave sftp.
for smaba i would do the /home thing if ftp is wanted

---

### Post by Jason_25 on 2006-04-19
Setting up a server like you require is easy.  Do a server install, sort out your network, then 
```

sudo apt-get install openssh-server

```
and
```

sudo apt-get install samba

```
You'll need to configure samba a little of course.  I keep a large samba share partition at /media/shared.  I can post my smb.conf if needed.  SSH will work as soon as you install it but you might want to consider running on a different port and disabling root logins.  Then install the standard security programs you would put on any pc providing network services.  You might be able to get away with using sftp as your ftp server.

---

### Post by peterscj on 2006-04-19
I guess I'm a littel confused.  How is ssh an sftp client?  I have only used ssh to connect from one lab machine to another or by using PuTTy to connect from a windows machine.

I would still like to use a regular ftp program (possibly vsftp or proftp) but is there a way to share one of my samba directories as a ftp directory and not let people change stuff in there?

About the partitioning, the guide [here]("http://www.howtoforge.com/samba_setup_ubuntu_5.10_p2") says to make a /boot partition 50MB, /swap 1GB, / 10 GB, and then /home.  Why do I need a /boot and a / partion?  I see a reason for a /home.  I was thinking about doing a /data partion instead of /home though.  Would this be a good idea or should I stick to /home?  If I do a /data partion I would use it to make the different directories for the samba share.  Is this the right line of thought?

---

### Post by Iowan on 2006-04-19
Samba can be set up with different permissions for different "shares".  You could have some free access, some read-only (with a few people granted write access), etc.  FTP is still on my list of things to try.
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") 
 Here's another how-to from howtoforge.com. 
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server") 
... and another you might check.
Don't know how you plan to access files from outside your network, but I suspect you'll need a firewall of some sort, too.  SSH (and the asociated sftp) adds a little extra security for external access, too.

---

### Post by Jason_25 on 2006-04-19
I'm running SSH on a PC behind a router with port forwarding enabled.  If I want to get a file off of that PC from any windows pc on the net I use [FileZilla]("http://filezilla.sourceforge.net/") and connect through my static hostname through sftp like I would with any ftp server, except of course I specify psftp over ssh2.  From OSX or linux, I would typically use sftp.

Of course, if you require public access you might want to go with a more traditional ftp server.

---

### Post by peterscj on 2006-04-20
OK I think I have it set up.  I made a 200G /data partition and am trying to move music over first.  I have subfolders in the /data/music folder but when I do a ls -d it only shows .  Is there a reason for not showing the folders?

Another problem I am having is, I have my music back up on DVDs but when I try to copy them to the directory I get errors.  I tried doing a 
```
cp -dpr /media/cdrom0 /data/music
```

but it give me a ton of errors so I am copying it over the network.  Any ideas?

---

### Post by skirkpatrick on 2006-04-20
As to your earlier question about partitions, you always need a /boot partition (that's where GRUB goes) and a / or root partition.  The OS and everything else goes in the / partition if you have no others.  If you make a separate /home partition, then all of your data files go there automatically.  However, I believe that the "standard" webpages, when you set up Apache, will go into /var/www.  I've got a server that is still running RedHat 8.0 and need to move it over to Ubuntu.  It uses a 2nd drive for all my data files but you can accomplish the same thing with partitions.  You can setup Apache to use another directory for its base and you can tell Samba to share any directory that's in your system.

What does a **ls -l** show you?

What kind of errors?

---

