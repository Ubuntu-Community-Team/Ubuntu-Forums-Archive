---
title: "Creating a backup image"
date: 2008-01-03
forum: Server Platforms
---

### Post by hds17 on 2008-01-03
Hi All,  I am sure some one can point me to the right answer here.  
I have a server running Edgy that I use for production  Lets call it server1

I want to take an image of it and place it on server2.  What is the best way to create an exact mirror image of server one and place it one server2 and/or CD?  

Ultimate goal is if server1 goes down have server2 take over.  

Server1 is a production box that handles data aggregation via Perl and Shell scripts.  I want to replicate the same set up on server2.  

I am sure this question has been asked before, just looking to be pointed the the answer.  

Thanks in advance..

MM

---

### Post by kebes on 2008-01-03
If you want an exact disk image, you can use [partimage]("http://www.partimage.org/Main_Page"). This is similar to "Norton Ghost" in that it creates an image of a partition that you can store on a CD/DVD or backup over the network. You can then copy the image onto a different hard drive if you want (you can boot into a LiveCD like [System Rescue CD]("http://www.sysresccd.org/Main_Page") in order to create/restore images).

You can also use rsync to copy files across the network from one machine to another. I would probably use partimage to clone the 1st server to the 2nd, and then use rsync to periodically sync the two machines.

Hope that helps.

---

### Post by hds17 on 2008-01-03
Great thanks I will give it a try.  I appreciate the speedy response.  

MM

---

### Post by kamaboko on 2008-01-03
OK, this may be a painfully stupid question, but I just want to confirm my assumption.  I like how I have my computer set up at the moment.  I'm not too concerned about creating an image for my home folder, but in the event all goes to hell, I do want my system settings backed up or imaged.  That said, should I only be concerned with making an image of the root directory?

Thanks

---

### Post by kebes on 2008-01-03
> **kamaboko said:**
> OK, this may be a painfully stupid question, but I just want to confirm my assumption.  I like how I have my computer set up at the moment.  I'm not too concerned about creating an image for my home folder, but in the event all goes to hell, I do want my system settings backed up or imaged.  That said, should I only be concerned with making an image of the root directory?


It depends what you mean by "system settings." Most of your user preferences (including email, Firefox bookmarks, etc.) are stored in your home folder (in hidden directories). So if you want to save all of that, you should backup your home directory.

Setting for the system and for servers are stored mostly in /etc/. So if you want to save the status of the "system" (hardware settings, installed applications, and server software settings) you should backup root (/) and everything below it, but you can ignore /home/.

Does that answer your question?

---

### Post by kamaboko on 2008-01-03
Yes, it does thanks.

---

### Post by twistedtwig on 2008-01-04
personally I used this tutorial and found it great!

[http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup)

basically it zip / tar's the whole system for you.

you can then rysnc (copy) it to another machine and unzip it all and "poof" you have the same system running on a different machine.

N.B... I don't know how this will deal with different hardware, i.e. will it get upset.  Also it would have the same server name etc.

you could try and copy just the bits you need.. anyway, its something to think about but I see people have already given other thoughts... just thought I would give something else to you.

---

### Post by kebes on 2008-01-04
> **twistedtwig said:**
> 
N.B... I don't know how this will deal with different hardware, i.e. will it get upset.  Also it would have the same server name etc.

Yes, that may be a problem.

For what it's worth, I have swapped a hard-drive with Linux into a new computer once or twice, and it always auto-detected all the new environment perfectly (just treated it like any other "detected new hardware" situation). This probably isn't universally true (e.g. custom settings may not work, new video driver may be necessary), but Linux does a pretty good job dealing with hardware changes.

---

### Post by rconnely on 2008-01-31
This may be a bit late, but if you want to make a complete backup of your system without having to worry about hardware issues, I suggest Remastering the Live CD.  You can either backup everything (home dir and all) or just the distrobution.

Find out more @ [http://www.remastersys.klikit.org/]("http://www.remastersys.klikit.org/")

**1 Installing Remastersys **
Open a terminal and become root:

```
sudo su
```

Then add the Linux Mint romeo repository to /etc/apt/sources.list and update the package database:

```
echo "deb http://www.remastersys.klikit.org/repository remastersys/" >>/etc/apt/sources.list
apt-get update
```

Afterwards you can install remastersys like this:

```
apt-get install remastersys
```

Then leave the root shell so that you are logged in as your normal user again:

```
exit
```

 

**2 Remastersys Usage**
In order to learn how you can use remastersys, run

```
sudo remastersys
```

It will then print all available options:


> rconnely@rconnely-server:~$ sudo remastersys
[sudo] password for rconnely:

Usage of remastersys is as follows:

   sudo remastersys backup|clean|dist [cdfs|iso] [filename.iso]


Examples:

   sudo remastersys backup   (to make a livecd/dvd backup of your system)

   sudo remastersys backup custom.iso
                             (to make a livecd/dvd backup and call the iso custom.iso)

   sudo remastersys clean    (to clean up temporary files of remastersys)

   sudo remastersys dist     (to make a distributable livecd/dvd of your system)

   sudo remastersys dist cdfs
                             (to make a distributable livecd/dvd filesystem only)

   sudo remastersys dist iso custom.iso
                             (to make a distributable iso named custom.iso but only
                              if the cdfs is already present)

   cdfs and iso options should only be used if you wish to modify something on the
   cd before the iso is created.  An example of this would be to modify the isolinux
   portion of the livecd/dvd

rconnely@rconnely-server:~$
 

**3 Creating An ISO Image Of Your Installation**
To create an iso image of your installation, simply run

```
sudo remastersys dist
```

This will create an iso image called customdist.iso in the /home/remastersys directory. The dist option makes that your personal folder (e.g. /home/rconnely) will not be included in the iso image. You might have to insert your Ubuntu/Linux Mint installation CD during the process. 

This is how the end of the process looks:

> [...]
 92.16% done, estimate finish Wed Nov 28 15:31:25 2007
 93.39% done, estimate finish Wed Nov 28 15:31:25 2007
 94.62% done, estimate finish Wed Nov 28 15:31:24 2007
 95.85% done, estimate finish Wed Nov 28 15:31:24 2007
 97.08% done, estimate finish Wed Nov 28 15:31:25 2007
 98.31% done, estimate finish Wed Nov 28 15:31:25 2007
 99.54% done, estimate finish Wed Nov 28 15:31:25 2007
Total translation table size: 2048
Total rockridge attributes bytes: 3950
Total directory bytes: 9094
Path table size(bytes): 54
Max brk space used 0
406890 extents written (794 MB)
/home/remastersys/customdist.iso is ready to be burned or tested in a virtual machine.

Check the size and if it is larger than 700MB you will need to burn it to a dvd

```
796M /home/remastersys/customdist.iso
```

It is recommended to run 'sudo remastersys clean' once you have burned and tested the customdist.iso

> rconnely@rconnely-server:~$

As I've just mentioned, the iso image has been created in /home/remastersys:

```
ls -l /home/remastersys/
```

> rconnely@rconnely-server:~$ ls -l /home/remastersys/
total 814596
-rw-r--r-- 1 root root        73 2007-11-28 15:08 control
-rw-r--r-- 1 root root 833310720 2007-11-28 15:31 customdist.iso
drwxr-xr-x 9 root root      4096 2007-11-28 15:07 dummysys
dr-xr-xr-x 5 root root      4096 2007-10-19 02:08 ISOTMP
-rw-r--r-- 1 root root       904 2007-11-28 15:06 varexc
rconnely@rconnely-server:~$

Now you can burn /home/remastersys/customdist.iso onto a CD or DVD (if the iso file is bigger than 700MB, you must use a DVD). 


**4 Cleaning Up**
After you've burnt the iso image onto a CD/DVD, you can run

```
sudo remastersys clean
```

to remove all temporary file created during the iso generation as well as the /home/remastersys directory. 

Cheers :)

---

### Post by dboot on 2008-02-27
I'm in the same situation as hds17:

I have a production webserver and a dev webserver. I'm using the dev webserver to test installations and as a linux "sandbox" for new users helping me out. Both servers have the same base install (Debian 4) and only differ with packages, websites, and databases.

What I want to do:
- sync both servers
- install/test/document something on the dev server
- install on production server
- sync dev server with production server (so any previously failed attempts of the installation is erased with the working one on the production server)
- sync only when production server is running perfectly so if it gets messed up it can be synced back with what's on the dev server

rsync is what I've heard to be the best solution to keep these two servers "synced" up. I just have a few questions.

Is there an rsync option to make the servers identical in every way (not just certain directories)?

Do mysql databases sync?

Ultimately, can I create a forum on the dev server and rsync it to the production server in its entirety with ease?

If rsync is capable of doing this...\\:D/

Thanks for any help!

---

### Post by kebes on 2008-02-27
> **dboot said:**
> 
rsync is what I've heard to be the best solution to keep these two servers "synced" up. I just have a few questions.

I think rsync should be able to handle this, but it may take some tricks. Rsync can preserve file attributes such as permissions (use the --archive [option]("http://linux.die.net/man/1/rsync")), so if you apply rsync from the root of one filesystem to the other, you will get an exact copy.

Webpages are stored in /var/www/, MySQL databases are stored as files (in /var/lib/mysql/), etc. ... So if you do a complete file sync, then yes everything should be identical.

The problems I foresee are:
1. Some files you are syncing from are not really files (e.g. processes listed in /proc/, some of the devices listed in /dev/). So you may have to spend some time figuring out what directories need to be excluded.
2. Similarly on the server you are syncing to, if you try to "write" into certain system resources (like files listed in /dev/) you will get all kinds of errors. (Since these are not normal files: they are pointers to devices; and writing to them means you are trying to copy data directly to them.)
3. On the server you are syncing to, you may be attempting to overwrite files that are in use, which may cause errors. Linux can usually handle files being updated (the current version keeps being used until the program is closed and re-opened), but it may take a reboot to get all the files "right" if you've over-written system files (e.g. updates to kernel).


I think as long as your two systems are nearly identical (e.g. you use [partimage ]("http://www.partimage.org/Main_Page")initially to clone one drive to the other), then you should be able to easily sync the changes from one to the other (which will all be confined to config changes and software installs).

---

### Post by dboot on 2008-02-28
Excellent! Thanks for the confirmation.

I tried to test out some parameters with rsync and got an error:

```
rsync -avz dev:/var/tmp/ /var/tmp/
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(453) [receiver=2.6.9]
```

I have a few files in /var/tmp/ on the server dev (which is listed in my hosts file) that I wanted to copy to /var/tmp on my current server.

Any ideas? And do you suggest using these parameters? Eventually I'll add several more directories to sync the servers completely.

---

### Post by kebes on 2008-02-29
> **dboot said:**
> I have a few files in /var/tmp/ on the server dev (which is listed in my hosts file) that I wanted to copy to /var/tmp on my current server.


If you're rsync-ing from server to server, it's more secure (and easier) to tunnel it through SSH. It will look something like:

```
rsync -av --delete -e "ssh" user@dev:/var/tmp/ /var/tmp/ 
```
The "--delete" removes files on the destination of the transfer. This is necessary to get a perfect copy, since otherwise it won't remove files on the target that have been deleted on the source side. But, of course, be careful when using the "--delete" switch!

The -e "ssh" opens an SSH tunnel and pushes the rsync data through that. This has the advantage that the data is encrypted (always good to be secure!), and means that you can transfer as long as SSH is running on both computers. (If you're running a server you probably already use SSH; no need opening new ports for rsync.) You will of course have to enter the SSH password for the server you're accessing.


> I'll add several more directories to sync the servers completely.
When you're ready to do that, you can implement it a number of ways:
1. Create a bash script that has several rsync commands in a row, for all the directories you want to sync.
2. Use rsync's "--files-from" switch, which lets you specify a file that lists all the directories/files it should try to sync.
3. Use a command that does rsync from the root directory ("/") of one machine to the root on the other machine. You will have to use "--exclude-from" to specify a file that lists the directories to ignore (as mentioned before, things like /proc/ won't work).

I would probably use #1, since it's easier to see what's going to happen, and to edit it when required. (E.g. you might want to use the "--delete" flag on some directories, but not on others...)

Hope that helps.

---

