---
title: "HOWTO: Create, Recover and Automate System Images"
date: 2007-10-19
forum: Tutorials
---

### Post by GrammatonCleric on 2007-10-19
A disk image is a computer file containing the complete contents and structure of a data storage medium or device, such as a Hard drive, CD or DVD. The term has been generalized to cover any such file, whether originated from an actual physical storage device or not. As such, a disk image contains all the information necessary to replicate the structure and contents layout, as well as the actual contents, of a storage device, and this is the distinguishing feature between an ordinary backup and a disk image. A disk image file is usually created based upon the sectors on the medium, ignoring its filing system.

Originally disk images were used for backup and disk cloning, where replication or storage of an exact structure was necessary or efficient. With the advent of optical drives such as CD-ROM and DVD, a more commonly encountered type of disk image is a CD/DVD image, often in the form of an .ISO file (or sometimes a .BIN/.CUE file), referring to the ISO 9660 file system commonly used on such disks. These provide an exact digital replica of a CD/DVD, whereby all of the data is stored in one file to completely preserve the data structure and integrity of the CD/DVD. The .ISO format is the most common format for software disk images, but does not support multi-track data or audio CDs. In general, disk imaging is essential for retaining copy-protection data and multi-track data/audio on CD/DVD.

This how to covers creating, recovering and automating the imaging of linux systems.  Unlike other processes there is no need to unmount any partitions, run special agents, use only services like ftp, capture only one partition at time, and can be done with the server or workstation is up and running.


[SIZE=3]_**Step 1: Determine your hard drive device.**_[/SIZE]


From the Ubuntu system that you wish to image. Drop to the command line and run:

```

    df -h

```Look for the partition that is mounted on /.

```

    gcleric@libria:~# df
    Filesystem           1K-blocks      Used Available Use% Mounted on
    /dev/sda1             92196516  18761636  68751536  22% /
    varrun                 1037236       132   1037104   1% /var/run
    varlock                1037236         0   1037236   0% /var/lock
    udev                   1037236       112   1037124   1% /dev
    devshm                 1037236         0   1037236   0% /dev/shm
    lrm                    1037236     34696   1002540   4% /lib/modules/2.6.22-14-generic/volatile

```In the example above the / (or root partition) is mount to the file system device of /dev/sda1. So sda is your hard drive. Make note of that. When imaging your system you can either...[INDENT]     **1** - Image a single partition by specifying a the partition number (i.e. /dev/sda1)
[/INDENT][INDENT]     **2** - Or image the entire drive capturing the mbr, swap, and data by leaving off any partition numbers (i.e. /dev/sda).

[/INDENT][SIZE=2]
[/SIZE] [SIZE=3]_**Step 2: Clear free space on hard drive.**_[/SIZE]

[I][COLOR=Red]One of the disadvantages of the dd over software like Ghost, Acronis or Partimage is that dd will store the entire partition, including blocks not currently used to store files, whereas Ghost/Acronis understand the file system and overlook these unallocated blocks. The overhead isn't too bad as long as you compress the image and the unallocated blocks have low entropy. In general this will not be the case because the emtpy blocks contain random junk from bygone files. To rectify this, it's best to blank all unused blocks before making the image. After doing that, the unallocated blocks will contain mostly zeros and will therefore compress down to almost nothing.


This will fill entire unused space disk with zeros, then delete it again.


[/COLOR][/I][COLOR=Red][COLOR=Black]**Run as root or use sudo -i **[/COLOR][/COLOR]
```

dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp

```[B]
NOTE:[/B]  [COLOR=Red]*To a the status of dd progress  issue the following  command  from a new  terminal window. *[/COLOR]

```

sudo kill -SIGUSR1 thepidofdd

```[COLOR=Red]

This will send signal USR1 to any dd process you own every five seconds, triggering dd to tell you where it is in the transfer and how fast it&#8217;s going. Remember, look at dd&#8217;s terminal for the output! The output should look like...[/COLOR]

```


    137+0 records in
    137+0 records out
    143654912 bytes (144 MB) copied, 5.66717 seconds, 25.3 MB/s
    249+0 records in
    249+0 records out
    261095424 bytes (261 MB) copied, 11.5736 seconds, 22.6 MB/s
    388+0 records in
    387+0 records out

    405798912 bytes (406 MB) copied, 18.8116 seconds, 21.6 MB/s 

```'[SIZE=3]
[/SIZE] [SIZE=3]_**Step 3: Creating the hard drive image.**_[/SIZE]


There are many ways that the image can be created. You can dump the image over SSH, to a USB device, Samba or NFS shares, etc.[INDENT]**A**. Method 1 - SSH: using the hard drive example (sda) from step 1 drop to the command line and run:
[/INDENT]```

    sudo dd bs=15M if=/dev/sda conv=sync,noerror | ssh user@dest "gzip -9 > /path/to/image/ubuntu_linux.img.gz"


```[INDENT]**B**. Method 2 - USB Drive: using the hard drive example (sda) from step 1 drop to the command line and run:
[/INDENT]```

   sudo dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/usbdrive/ubuntu_linux.img.gz


```[INDENT]**C**. Method 3 - NFS Share: using the hard drive example (sda) from step 1 drop to the command line and run:
[/INDENT]```

    sudo dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/nfs-share/ubuntu_linux.img.gz


```    To learn how to setup NFS shares please refer to [NFSv4Howto.]("https://help.ubuntu.com/community/NFSv4Howto")[INDENT]**D**. Method 3 - SMB Share: using the hard drive example (sda) from step 1 drop to the command line and run:
[/INDENT]```

   sudo  dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/smb-share/ubuntu_linux.img.gz

```    To learn how to setup Samba shares please refer to [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba").[INDENT]**E**. Method 4 - FTP Server: using the hard drive example (sda) from step 1 drop to the command line and run:  (note this method requires that the package ncftp be installed.)
[/INDENT]```

   sudo  dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 | ncftpput -f ftp_server.cfg -d /var/log/ftp.log -c /media/path/to/ubuntu_linux.img.gz


```

The ftp_server.cfg shown in the above exaple would contain the following information about the server that you are trying to ftp the image to.

```

host some.server.ip
user foo
pass foomanchu10101

```

This set of commands will create a dd image of the sda drive. Then pipe the output of the dd if=/dev/sda to either ssh, usb drive, nfs or smb share which then will gzip the data using the best compression to a path where the image will reside.



[SIZE=3][U][B]
Step 4: Recovery of the image:[/B][/U][/SIZE]

To use the restore methods for SSH, SMB and NFS below it is assumed that the system that is being booted is connected to a network with a functional DHCP Server.[INDENT]     **A. From SSH.**
[/INDENT][INDENT][INDENT]         **1** - Using the Ubuntu Desktop CD boot from it on the system that you want to recover you image to.
[/INDENT][/INDENT][INDENT][INDENT]         **2 **- Once the Ubuntu Desktop CD is fully booted open a terminal:
[/INDENT][/INDENT]```

        Applications -> Accessories -> Terminal


```[INDENT][INDENT]**3** - Now verify the hard drive that you wish to restore your image to is seen by the Ubuntu Desktop CD.
[/INDENT][/INDENT]```

        grep "sd" /var/log/dmesg


``` or if you have a non SATA or SCSI drive

```

        grep "hd"  /var/log/dmesg


``` You should see something like.


```

        [17179577.532000] sda: assuming drive cache: write through
        [17179577.532000] SCSI device sda: 52428800 512-byte hdwr sectors (26844 MB)
        [17179577.532000] sda: cache data unavailable
        [17179577.532000] sda: assuming drive cache: write through
        [17179577.532000]  sda: sda1 sda2 < sda5 >
        [17179577.556000] sd 0:0:0:0: Attached scsi disk sda
        [17179587.844000] sd 0:0:0:0: Attached scsi generic sg0 type 0
        [17179594.060000] Adding 5815488k swap on /dev/sda5.  Priority:-1 extents:1 across:5815488k
        [17179595.068000] EXT3 FS on sda1, internal journal


```[INDENT][INDENT]**4** - Now restoring the image.
[/INDENT][/INDENT]With the drive information of the local hard disk to restore from SSH is as follows.

```

        ssh user@dest "gzip -dc /media/path/to/ubuntu_linux.img.gz" | sudo dd of=/dev/sda
        

```        5 - Once the restore completes reboot and remove the Ubuntu Desktop CD And enjoy.[INDENT]**B. From USB**
[/INDENT][INDENT][INDENT]         **1** - Follow steps 1 thru 3 in section A above.
[/INDENT][/INDENT][INDENT][INDENT]         **2** - In most cases your USB drive should automount to /media/disk or /dev/sdb1
[/INDENT][/INDENT][INDENT][INDENT]**         3** - Restoring image.
[/INDENT][/INDENT]```

        sudo gzip -dc /media/disk/to/usbdrive/ubuntu_linux.img.gz | sudo dd of=/dev/sda


```[INDENT][INDENT]**4** - Once the restore completes reboot and remove the Ubuntu Desktop CD and enjoy.[/INDENT][/INDENT][INDENT]**C. From NFS**
[/INDENT][INDENT][INDENT]         **1** - Follow steps 1 thru 3 in section A above.

        **2 **- Now install the NFS client. Yes install from the internet with the Ubuntu Desktop CD.
[/INDENT][/INDENT]```

        sudo apt-get install nfs-client
 

```[INDENT][INDENT]**3** - Create a mount point for the NFS share
[/INDENT][/INDENT]```

        sudo mkdir /mnt/nfs
    

```[INDENT][INDENT]**4** - Mount the NFS share that has the image that you want to restore.

[/INDENT][/INDENT]```

        sudo mount 192.168.2.2:/path/to/image /mnt/nfs
    
```[INDENT][INDENT] **5** - Restoring image

[/INDENT][/INDENT]```

        sudo gzip -dc /mnt/nfs/ubuntu_linux.img.gz | sudo dd of=/dev/sda

```[INDENT][INDENT]**6** - Once the restore completes reboot and remove the Ubuntu Desktop CD and enjoy.
[/INDENT][/INDENT]

[INDENT]**D. From SMB**
[/INDENT][INDENT][INDENT]         **1** - Follow steps 1 thru 3 in section A above.

        **2 **- Now install the SMB client. Yes install from the internet with the Ubuntu Desktop CD.
[/INDENT][/INDENT]```

        sudo apt-get install smbfs
        

```[INDENT][INDENT]**3 **- Create a mount point for the SMB share.
[/INDENT][/INDENT]```

sudo mkdir /mnt/smb

```[INDENT][INDENT]**4** - Mount the SMB share that has the image that you want to restore.
[/INDENT][/INDENT]```

        sudo mount -t smbfs  \\192.168.2.2\image_share /mnt/smb
    

```[INDENT][INDENT]**5** - Restoring image.
[/INDENT][/INDENT]```

        sudo gzip -dc /mnt/smb/path/to/ubuntu_linux.img.gz | sudo dd of=/dev/sda


```[INDENT][INDENT]**6** - Once the restore completes reboot and remove the Ubuntu Desktop CD and enjoy.
[/INDENT][/INDENT][SIZE=3]_**Step 5: Automating the imaging**_[/SIZE][INDENT]     **A. Over SSH:**
[/INDENT][INDENT][INDENT]         **1** - Read the "Public key authentication" section on...
[/INDENT][/INDENT]```

        https://help.ubuntu.com/community/SSHHowto?highlight=%28SSH%29

``` ..and setup public key authentication between the systems that you want to image to and from. I would recommend doing this as root on the system to image.[INDENT][INDENT]**         2** - Using your favorite editor create a bash script that looks like the following, changing the path and ip address to your needs:
[/INDENT][/INDENT]```

####################
# set date variable
####################

tdy=`date +%m%d%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

# dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda conv=sync,noerror | ssh root@192.168.2.2 "gzip -9 > /media/path/to/ubuntu_servername_$tdy.img.gz"


```[INDENT][INDENT]**3 **- Make the script executable.
[/INDENT][/INDENT]```

        chmod +x script_name.sh

```[INDENT][INDENT]**4 **- Add the script to crontab.
[/INDENT][/INDENT][INDENT][INDENT][INDENT]             **a**. First read the following about crontab.
[/INDENT][/INDENT][/INDENT]```

            http://en.wikipedia.org/wiki/Cron

```[INDENT][INDENT][INDENT]**b**. I'm not a fan of vi so I've change the default editior to nano by running this command at the command line.
[/INDENT][/INDENT][/INDENT]```

            sudo -i
            
``` then...
```

            export EDITOR=nano

```[INDENT][INDENT][INDENT]**c**. Now execute
[/INDENT][/INDENT][/INDENT]```

            crontab -e    
        
```[INDENT][INDENT][INDENT]**d**. Changing the path to your script, time, date and frequency to your needs add a line that looks like. The cron entry below will execute the imaging script every sunday at 11pm.
[/INDENT][/INDENT][/INDENT]```

            0 23 * * 7 /path/to/script/server_imaging.sh > /dev/null 2>&1

```    B. To a USB drive:[INDENT][INDENT]         **1** - Using your favorite editor create a bash script that looks like the following, changing the path and ip address to your needs:
[/INDENT][/INDENT]```

####################
# set date variable
####################

tdy=`date +%m%d%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

# dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda conv=sync,noerror | "gzip -9 > /media/disk/to/usbdrive/ubuntu_linux.$tdy.img.g


```[INDENT][INDENT] **2** - Make the script executable.
[/INDENT][/INDENT]```

        chmod +x script_name.sh

```[INDENT][INDENT]**3** - Add the script to crontab.
[/INDENT][/INDENT][INDENT][INDENT][INDENT]             **a**. First read the following about crontab.
[/INDENT][/INDENT][/INDENT]```

            http://en.wikipedia.org/wiki/Cron

```[INDENT][INDENT][INDENT]**b**. I'm not a fan of vi so I've change the default editor to nano by running this command at the command line.
[/INDENT][/INDENT][/INDENT]```

            sudo -i
            
``` then...
```

            export EDITOR=nano

```[INDENT][INDENT][INDENT]**c**. Now execute
[/INDENT][/INDENT][/INDENT]```
crontab -e    
        
```[INDENT][INDENT][INDENT]d. Changing the path to your script, time, date and frequency to your needs add a line that looks like.
[/INDENT][/INDENT][/INDENT]```

            0 * * * 7 /path/to/script/server_imaging.sh  > /dev/null 2>&1
        
```[INDENT]** C. To a SMB or NFS share:**
[/INDENT][INDENT][INDENT]        **1** - Using your favorite editor create a bash script that looks like the following, changing the path and ip address to your needs:
[/INDENT][/INDENT]```



####################
# set date variable
####################

tdy=`date +%m%d%Y`
    

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

# dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/share/ubuntu_linux.$tdy.img.gz


```[INDENT][INDENT]** 2** - Make the script executable.
[/INDENT][/INDENT]```

        chmod +x script_name.sh

```[INDENT][INDENT]**3** - Add the script to crontab.
[/INDENT][/INDENT][INDENT][INDENT][INDENT]             **a**. First read the following about crontab.
[/INDENT][/INDENT][/INDENT]```

            http://en.wikipedia.org/wiki/Cron

```[INDENT][INDENT][INDENT]**b**. I'm not a fan of vi so I've change the default editor to nano by running this command at the command line.
[/INDENT][/INDENT][/INDENT]```

            sudo -i
            
``` then...
```

            export EDITOR=nano

```[INDENT][INDENT][INDENT]**c**. Now execute
[/INDENT][/INDENT][/INDENT]```

            crontab -e    
        
```[INDENT][INDENT][INDENT]**d**. Changing the path to your script, time, date and frequency to your needs add a line that looks like.
[/INDENT][/INDENT][/INDENT]```

            0 * * * 7 /path/to/script/server_imaging.sh  > /dev/null 2>&1


```Well there you have it,


[COLOR=Red]**UPDATE**[/COLOR]:  If you'd like to remove images after a specified period of time you could setup a cron job to execute the following on the *TARGET* system where your images reside.
[SIZE=2][U][B]
[SIZE=3]Step 6: Image Clean Up.[/SIZE][/B][/U][/SIZE][INDENT]**A**. Using your favorite editor create a bash script that looks like the following, changing the path your needs:
[/INDENT]```


#######################################
# Remove img.gz  files older than 21 days
#######################################

find /path/to/images/*.img.gz -type f -mtime +21 -exec rm {} \;


```In the code above the **mtime** is the number of  days and older of files that should be removed.[INDENT]**B**.  By now you should have read
[/INDENT]```

            http://en.wikipedia.org/wiki/Cron

```[INDENT]**C**. Again if you want to change the default editor to nano  run this command at the command line. If you haven't already. =)
[/INDENT]```

            sudo -i
            
``` then...
```

            export EDITOR=nano

```[INDENT]**D**. Now execute
[/INDENT]```

            crontab -e    
 
```[INDENT]**E**. Changing the path to your script, time, date and frequency to your needs add a line that looks like.
[/INDENT]```

            0 * * * 7 /path/to/script/remove_old_images.sh  > /dev/null 2>&1


```[COLOR=Red]**Update/FYI.**[/COLOR]

If you restore an image to a system that has a different NIC than the one that was in the system that the image(s) was created from you may need to remark out setting in the /etc/iftab to restore eth0.

The setting may look like...


```


eth0 mac xx:xx:xx:xx:xx:xx arp 1


```By putting a [COLOR=Red]**#**[/COLOR] in front of this and rebooting will restore eth0.

---

### Post by GrammatonCleric on 2007-10-26
Fixed a few typo's.

---

### Post by thelocust on 2007-10-26
your avatar and username are awsome.

---

### Post by dthomasdigital on 2007-10-26
Very nice, great work..

---

### Post by Steve1961 on 2007-10-26
Excellent how to.  Thanks for this, one to bookmark I think :)

---

### Post by aldonova65 on 2007-10-26
I have a couple of questions.

First, I understand about backing up either specific partitions or entire drives by either including or excluding the partition number. (sda vs. sda1,sda2,etc..) My question is, how do I specify the partition number on the restore? Is it just the same way? For example, do I just say 'of=/dev/sda1'? 

Second, it appears to me there is a closing double quote missing in the code sample for automating the imaging for a USB drive. Am I correct?

<ignore>Third, in the code samples for both USB and SMF/NFS, I don't think you are using the date variable in the file name. Is that correct?</ignore>

Nevermind. I see the 'tdy' now. It was just hiding from me.:lolflag:

Thanks for this great writeup!

---

### Post by GrammatonCleric on 2007-10-26
aldonova65: 

Ok,  To answer your first question you would need to create the partition on  the destination drive first.  Making sure the maintain the same partition number(s) as the original drive.

As to your second question that is (was) a type-o which i've now corrected!  

Thanks for pointing it out. :smile:

-GC

---

### Post by GrammatonCleric on 2007-10-27
aldonova65,

 The best way to do what you are looking for is to backup and restore the partition structure of the orginal drive to the new drive by running the following.

** The Backup:**
```

sfdisk -d /dev/sda > /path/to/share/partition_structure_sda.dump

```**The Restore:**
```

sfdisk /dev/sda < /path/to/share/partition_structure_sda.dump 

```-GC

---

### Post by GrammatonCleric on 2007-11-05
Added dd info for M$ Windows boxes.

-GC

---

### Post by mnk0 on 2008-03-25
Noticed in the how to there was no mention on doing this on a mounted file system, in your experience would this be safe enough to do on a mounted file system.??

---

### Post by GrammatonCleric on 2008-03-25
There should be no problem running the backup dd and gzip on a mounted filesystem.  

-GC

---

### Post by GrammatonCleric on 2008-07-29
Updated post with image clean up information.

-GC

---

### Post by mdsharp24 on 2008-08-01
So, if you are using this method to backup a 100 GB sda drive and later want to restore to a 200 GB drive, you would:

sfdisk /dev/sda < partition_structure_sda.dump

restore image

Then resize the partition up to 200 GB using gparted?

---

### Post by GrammatonCleric on 2008-08-01
Hi mdsharp24,

If you image your 100gb drive using the /dev/sda  and you want to restore the image to a larger drive you do *not* need to restore the partition table with...


```


sfdisk /dev/sda < partition_structure_sda.dump


```Creating an image using anyone of the methods I've listed will capture bit for bit backup of everything on the original drive including the drives partition table and structure.    So all you would need to do is restore your backup to the larger drive, using one of the methods I've described, and use gparted to resize your partitions.  


That said, if you can... I would install your new drive as a secondary drive in your PC and run a direct dd from your 100gb drive to the 200gb drive. 

Assuming that your old 100gb is /dev/sda and your new 200gb is /dev/sdb you could clone your 100gb to the 200gb directly using...


```


sudo dd bs=15M if=/dev/sda of=/dev/sdb 



```If you already have the gparted install on your 100gb you can run it and resize the partitions on /dev/sdb.  Then power down your system swap the cables and test booting off your new drive.

Hope this helps,

-GC

---

### Post by mdsharp24 on 2008-08-01
Very cool!  So running dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp on the live filesystem will actually wipe free space?

---

### Post by GrammatonCleric on 2008-08-01
mdsharp24,

I would not say "wipe" rather over write.  Picture a balloon being blown up inside a glass, filling all the empty space until none exists then the balloon pops ( i.e. rm -f /tmp/disk_zero_fill.tmp).  So the...

```


dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp


```...over writes any files that have have been flagged as deleted.

If you want to securely clear empty space on your drive take a look at "scrub."

[http://ubuntuforums.org/showthread.php?t=333309](http://ubuntuforums.org/showthread.php?t=333309)

- GC

---

### Post by converted on 2008-08-28
Thanks for this fabulous howto.  I just used dd for the first time right before I found this thread.  (It's actually still going as I type this), and I do wish I had noted the ability to compress the image on the fly as you show in your examples.

If you don't mind explaining a bit just for my curiosity, regarding your USB example (just because it's the one most applicable to what I'm doing)

```
sudo dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/usbdrive/ubuntu_linux.img.gz
```

I assume I can look up conv=sync,noerror but I'm curious why use of gzip (apparently) removes the need for an of= paramerter (even though I can see that of course you have specified the actual output path).

Just curious...

Thanks!

---

### Post by GrammatonCleric on 2008-08-30
Hi [converted]("http://ubuntuforums.org/member.php?u=548648"),
 
Sorry for the delay in replying, busy week but then aren't they all?  =)

In the simplest terms there is no need to use the "of=" option because in using the "if=" in conjunction with pipe (i.e. "|") and gzip  dd  is sending data directly to gzip to compress as it receives it.

Hope this helps.

-GC

---

### Post by converted on 2008-09-09
Heh -- I do know how that is, and didn't get back to check this until today.

Wow, a more helpful response than you could know.  I knew that was a pipe symbol, but had no idea (until further googling based on your response) that this literally instructs one process to "pipe" data over to another, nor that using it in this fashion is what an "unnamed pipe" is.

Years of tinkering (though only recently with Linux) and you've filled in yet another hole (I'd heard the term, but didn't even have the vaguest notion of what it meant) that none of my classes nor prior experiences had forced me to learn.

And I also now understand why so many commands I've used from howtos and such have contained that symbol.  I had no idea what the significance was.

Thanks!!

---

### Post by G~[thc] on 2008-11-10
I would like to make a system image on my external USB HDD.  
So I attempted to follow your USB example instructions.  
I had a problem, when I entered in Terminal:

Code:
sudo dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /media/path/to/usbdrive/ubuntu_linux.img.gz

The output was:
bash: /media/path/to/usbdrive/ubuntu_linux.img.gz: No such file or directory

The results of 'df -h' are:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  4.0G   63G   6% /
varrun               1006M  100K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
procbususb           1006M  136K 1006M   1% /proc/bus/usb
udev                 1006M  136K 1006M   1% /dev
devshm               1006M   16K 1006M   1% /dev/shm
lrm                  1006M   33M  973M   4% /lib/modules/2.6.20-17-generic/volatile
/dev/sdb1             299G  255G   45G  86% /media/Storage
/dev/sde1             150G  112G   38G  75% /media/NEXT 160
 
Am I supposed to alter the line of code, 
so that '/usbdrive/' = '/dev/sde/' ?
(The System drive is sda1 and the external usb drive is sde1)
I'm Using 7.04 (Feisty) at the moment.  Is that a problem?

---

### Post by GrammatonCleric on 2008-11-10
Hi [G~[thc]]("http://ubuntuforums.org/member.php?u=594631"),

So to be a little clearer.  You want to image your current linux system and have the image file output to your USB drive, correct?   If this is the case lets outline things.

_**Source Drive:**_

The drive that linux appears to be installed on appears to be /dev/sda so this is what we are going to take an image of. 
[U][B]
Output Drive:[/B][/U]

You stated that you'd like the image file to output to your USB drive there appears to be 2 attached to your system.  they are...

```
/dev/sdb1             299G  255G   45G  86% /media/Storage
/dev/sde1             150G  112G   38G  75% /media/NEXT 160
```.. or is one of these an internal hard drive?   I ask because if there is data one either of these that you wish to "include" in your image this would require a second image of that drive (i.e. sdb1 or sde1).  

So I'll assume that you want the image to go to /dev/sde  or /media/NEXT 160.  

_**Other:**_

There are three things that we need to discuss about before we can kick off the image.  First being what file system does your USB drive use (i.e. FAT32, NTFS, EXT3, REISER, XFS, etc.)?  I ask because if it is using FAT32 there is a maximum limit of file size that FAT32 can handle which is 4gb. So if the output image file is larger than 4gb, and chances are that it will be, then this may cause the the image job to fail.

Secondly, the name of the mounted USB dive contains a space (i.e. /media/NEXT 160).  When you script out your imaging you will most likely need to include quotes around the full path, like....

```
"/media/NEXT 160/ubuntu_linux.img.gz"
```Last but not least I would really consider running the "dd" job that fills the empty space of your /dev/sda drive with zeros first.  

```
dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp

```This way you are going to get the smallest image file.  Be sure to run this as root (i.e.  sudo -i )!


_**Imaging:**_

If you are not scripting this out and going to run them interactively I would switch to root to run then rather that using sudo followed by the commands.

**Step 1 **-  Switch to root.

```
sudo -i
```**Step 2** - Kick off the zero fill (this will take a while).

```
dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp
```[B]

Step 3[/B] - Verify that the zero fill temp file has been deleted. Run a "df" and look to make sure that the root partition is not 100% full.  The zero fill will fill this partition but it should remove the file that is filling the partition. If for some reason the the file is not deleted remove it manually with...

```
rm -f /tmp/disk_zero_fill.tmp
```[COLOR=Red][U][I][B]
NOT VERIFYING THIS COULD RESULT IN A VERY LARGE IMAGE!!!![/B][/I][/U][/COLOR]

**Step 3** - Now that the zero fill is complete and the partition is ready to image. For your setup the command set should be. (again this should be run as root). Again this process could take a long time to complete. 

```
dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > "/media/NEXT 160/ubuntu_linux.img.gz"
```[COLOR=Red]*Notice that since you are running as root you do not need the sudo at the begining of the command set.*[/COLOR]

Feel free to change the name of the output file to whatever you like. But in your case be sure to include the quotes around the output path (i.e. "/media/NEXT 160/ubuntu_linux.img.gz")

Hope this helps,

-GC

---

### Post by G~[thc] on 2008-11-11
Wow, that's great.  You're really good at breaking down tasks and organizing instructions clearly.  

The result of the zero-fill is:
---------------------------------------------------------
dd: writing `/tmp/disk_zero_fill.tmp': No space left on device
8430+0 records in
8429+0 records out
70713696256 bytes (71 GB) copied, 1390.79 seconds, 50.8 MB/s
---------------------------------------------------------
And the result of the df is:
---------------------------------------------------------
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73742752   4591916  65404884   7% /
varrun                 1029648       100   1029548   1% /var/run
varlock                1029648         0   1029648   0% /var/lock
procbususb             1029648       168   1029480   1% /proc/bus/usb
udev                   1029648       168   1029480   1% /dev
devshm                 1029648         0   1029648   0% /dev/shm
lrm                    1029648     33788    995860   4% /lib/modules/2.6.20-17-generic/volatile
/dev/sdg1              2047488    723552   1323936  36% /media/disk
/dev/sdc1            156250144 114941440  41308704  74% /media/NEXT 160
---------------------------------------------------------
So it seems that, after z-f'ing the space, I've used about 7% of the drive.  
Thereafter, the result of dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > "/media/NEXT 160/ubuntu_linux.img.gz"  is:
---------------------------------------------------------
5087+1 records in
5088+0 records out
80027320320 bytes (80 GB) copied, 2843.15 seconds, 28.1 MB/s
---------------------------------------------------------
So it seems to have worked.  And the .img.gz file is indeed present in the portable drive.  So has this created an image of only the fs partition, or the swap as well? Is it a -complete-
system image?
Thanks so much.  Having folks like you around sure makes life a whole lot easier for those of us who are just starting to get the hang of it a bit.

---

### Post by GrammatonCleric on 2008-11-11
Hi [G~[thc]]("http://ubuntuforums.org/member.php?u=594631"),

Everything looks good and to answer your question yes it is a complete image (i.e. all partitions and partition structures) of your /dev/sda drive. =)

Now that you have an image have you read through the restore process?  In the event that the system that you just imaged is your only PC I would print out the restore process in case you need it.   

Glad to help!

-GC

---

### Post by sionghua on 2008-11-11
I added the script for imaging to usb drive via 'scheduled task', which uses cron and anacron, but when I try to run it I encounter permission error when the script tries to dd /dev/sda4 , which is the root directory that I am running on. What could be the problem?

---

### Post by GrammatonCleric on 2008-11-11
Hi [sionghua]("http://ubuntuforums.org/member.php?u=172948"),

Are you calling the script via which users cron job? Yours or root?  The script needs to be called from root's crontab.  To list what jobs are in the root crontab run.

```

sudo crontab -l  

```now to edit the root crontab...

```

sudo crontab -e

```Also are you trying to image the whole sda drive or just the single partition sda4?  I ask because dd-ing just sda4 will only image data in that partition.  Now if you want to image the the whole drive you will need to change your script to /dev/sda.

Can you post the output of  "df -h" ?

-GC

---

### Post by sionghua on 2008-11-11
What name should I save the crontab file to? df -h produces 

> Filesystem            Size Used Avail Use% Mounted on
/dev/sda4              20G  9.3G  9.5G  50% /
tmpfs                 886M     0  886M   0% /lib/init/rw
varrun                886M  328K  885M   1% /var/run
varlock               886M     0  886M   0% /var/lock
udev                  886M  2.7M  883M   1% /dev
tmpfs                 886M  888K  885M   1% /dev/shm
lrm                   886M  2.0M  884M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda7             129G   15G  107G  13% /home
/dev/sdb1             466G  347G  120G  75% /media/FreeAgentDesktop

I am trying to backup sda4 and sda7 to sdb1, my script file is

> ####################
# set date variable
####################

tdy=`date +%m%d%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda4 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.$tdy.img.gz"
dd bs=15M if=/dev/sda7 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.$tdy.img.gz"

Thanks again.

edit: Got it just ctrl+o and ctrl+x in nano, it will automatically update crontab. Thanks.

edit: upon running the script manually I get 'not found' error as follows:

> root@sionghua-desktop:/home/sionghua# sh ddbackup.sh
dd: writing `/tmp/disk_zero_fill.tmp': No space left on device
1339+0 records in
1338+0 records out
11229851648 bytes (11 GB) copied, 192.981 s, 58.2 MB/s
ddbackup.sh: 21: gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.11122008.img.gz: not found
ddbackup.sh: 22: gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.11122008.img.gz: not found

edit: I think I know why, there should not be " before and after the gzip command unless it is used in ssh.

edit: Thanks it works.

---

### Post by GrammatonCleric on 2008-11-11
Hi [sionghua]("http://ubuntuforums.org/member.php?u=172948"),

First, lets talk about why you are splitting your image into two?  Doing this will make restoring a little more tricky.  Also since both partitions that you are creating images of are on the same drive it would make your life much easier if you just capture the whole drive in one image.  Doing this will restore EVERYTHING (i.e. boot sector, partition tables, swap, all your apps, all your data, etc.).  It would mean changing your script from...

```
dd bs=15M if=/dev/sda4 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.$tdy.img.gz"
dd bs=15M if=/dev/sda7 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.$tdy.img.gz"
```To...

```
dd bs=15M if=/dev/sda conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/linux_system.$tdy.img.gz"
```Seriously think about it!!! 

If you are breaking them up to capture incremental changes on your /home partition then I would consider using  a tool like "Simple Backup Config" which is in the repos and can be installed by...

```

sudo apt-get install sbackup
```...this is a very easy to use backup tool and is much better at capturing daily incremental changes then taking images of the partition. 


That said.... Here's what you need would do to get your current script working. But seriously think about changing how you are going to image your system.  Just my 2 cents. =)

###############################

**Step 1** -  Create a scripts directory.

```
sudo mkdir /etc/scripts
```[B]

Step 2[/B] - Take the contents of your imaging script... 

```

####################
# set date variable
####################

tdy=`date +%m%d%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda4 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.$tdy.img.gz"
dd bs=15M if=/dev/sda7 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.$tdy.img.gz"


```.... and put them in a script file.


```
sudo nano /etc/scripts/image_backup.sh
```Consider adding a auto remove of oldest images to the bottom of your script. Something like...

```

####################
# set date variable
####################

tdy=`date +%m%d%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda4 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.$tdy.img.gz"
dd bs=15M if=/dev/sda7 conv=sync,noerror | "gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.$tdy.img.gz"

[B]#######################################
# Remove img.gz  files older than 21 days
#######################################

find /media/FreeAgentDesktop/Ubuntu/Backup/*.img.gz -type f -mtime +21 -exec rm {} \;[/B] 


```[B]

Step 3[/B] - Make script executable.

```
sudo chmod 700  /etc/scripts/image_backup.sh
```
[B]
Step 4[/B] - Add your script to roots crontab.

Change the default editor to nano if you don't like or don't know how to use vi.

```
export EDITOR=nano
```now edit the root crontab...

```
 sudo crontab -e
```...and  add line like...
```

0  23  * * 7 /path/to/script/server_imaging.sh  > /dev/null 2>&1
```This will run your image script at 11:00pm every Sunday.

This should do it!  

###############################

---

### Post by sionghua on 2008-11-11
Hi GrammatonCleric,

Thanks for your suggestions, but I don't want to image my windows partition and old data partitions which are also on the same harddisk. But thanks for the suggestion for auto-remove and the scrpt directory. I am using rsync to backup my data into daily/wekly/monthly/ folders so no need to use sbackup. BTW I think adding "" for the gzip command create problems.

Thanks again.

edit: by the way dunno why by running
> sudo kill -SIGUSR1 thepidofdd

it doesn't show the progress here. But not a big deal.

---

### Post by sionghua on 2008-11-11
Hi, anyone knows how to configure this to run by anacron? Because my computer is not always on. Thanks.

edit: found it at
[http://linux.die.net/man/8/anacron](http://linux.die.net/man/8/anacron)
[http://linux.die.net/man/5/anacrontab](http://linux.die.net/man/5/anacrontab)

can't find the option to delete this post so I edit instead.

---

### Post by sionghua on 2008-11-11
It appears that only the free space on sda4 is filled with zero, while sda7 is not, because the size of the backup file for sda7 is bigger than the size of used space in sda7.

my script as follows:

> ####################
# set date variable
####################

tdy=`date +%d-%m-%Y`

##################################
# consider zeroing unused space
# before imaging.  
#
# remove # in front of line below 
# enable this fuction
##################################

dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm rm -f /tmp/disk_zero_fill.tmp

#########################
# image server to
#########################

dd bs=15M if=/dev/sda4 conv=sync,noerror | gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda4.$tdy.img.gz
dd bs=15M if=/dev/sda7 conv=sync,noerror | gzip -9 > /media/FreeAgentDesktop/Ubuntu/Backup/sda7.$tdy.img.gz

#######################################
# Remove img.gz  files older than 90 days
#######################################

find /media/FreeAgentDesktop/Ubuntu/Backup/*.img.gz -type f -mtime +90 -exec rm {} \;

and running the script shows the following, but it was stopped before it complete.

> root@sionghua-desktop:/home/sionghua# sh ddbackup.sh
dd: writing `/tmp/disk_zero_fill.tmp': No space left on device
1339+0 records in
1338+0 records out
11229851648 bytes (11 GB) copied, 204.268 s, 55.0 MB/s
1365+1 records in
1366+0 records out
21485322240 bytes (21 GB) copied, 2365.57 s, 9.1 MB/s
^C2159+0 records in
2158+0 records out
33942405120 bytes (34 GB) copied, 7346.55 s, 4.6 MB/s


Is zero filling working in this case?

---

### Post by Zack McCool on 2008-11-14
Zero filling is working, but you need to pay more attention to the command...   ;)

In your case, /tmp is (apparently) located on /dev/sda4.  Therefore, the free space on /dev/sda4 is filled, then the file is deleted.  To do the same for /dev/sda7, you'll need to run the same command to fill some directory on that partition.  

So, if you add the following command, you should be all set: ```

dd if=/dev/zero of=/home/disk_zero_fill.tmp bs=8M; rm rm -f /home/disk_zero_fill.tmp 
```

Like you, I back up partitions instead of the drive.  

To the OP (thanks, BTW), there are several reasons for this type of image...   For instance, my sda is a 750GB Drive.  Much of the space is filled with files that are either not important enough for me to want to back up (torrents, virtual machines), or files that are already duplicated on my network (cd images and video files).  I keep all of those in their own partitions, and do not want large images of them that will eat space unnecessarily, especially since I send the images to a 500GB NAS drive.

So, I image the /, /var and /boot partitions, and backup any other needed information through other means (/home is backed up several times per day by rsnapshot).

Yes, it is much more complex.  But it makes restores a bit quicker and easier than a full reinstall, so I am happy with it.  Of course, I still use aptoncd as well, so if I do need a full reinstall, it can be done pretty easy, too.  You can never have too many backup methods...   ;)

---

### Post by solitaire on 2008-11-14
thanks [GrammatonCleric]("http://ubuntuforums.org/member.php?u=24155") for this easy how-to :D

have you considered using 'dcfldd' instead of 'dd'?
'dcfldd' automatically produces an output of Blocks and size of the wipe file. Might be a bit easier for newbies than running the  ' 			 				sudo kill -SIGUSR1 thepidofdd 			 		' command and looking for the output.


'dcfldd' is in the repos

---

### Post by Zack McCool on 2008-11-19
I like the looks of dcfldd.  I'll have to take a little time and see if it will do the job as a plug in replacement on those command lines, or if I'll have to add or modify any switches, but it looks good.

Thanks for pointing it out, as I'd never heard of it before.

---

### Post by xwang on 2009-06-20
Hi,
my hdd contains an ntfs partition, a fat32 partition and two ext3 partition. I would like to create an image of it and compress it with gzip, but, at the same time, I would like to be able to mount such an image to restore a single file. I'm wondering if it is necessary to decompress the image before mounting and how can I mount one partition from the image. Moreover I would like to know if I can use the zeroing command also on the ntfs and fat32 partitions which I suppose can create some problems due to the 4gb file dimension limitation.
Thank you,
Xwang

PS is it possible to automate it using a for cycle that reads how many sda partitions are mounted, zeroes each partitionb empty space and finally create a single image of the sda?

---

### Post by SoftwareExplorer on 2009-09-01
Nice tutorial. 
One question though: with the ssh, shouldn't you use ssh -e none user@server "command to run"? I was reading man ssh it sounds like the connection would be interrupted if some of the data that was being piped happens to have <newline>~

---

### Post by GrammatonCleric on 2009-09-01
Since DD is sending a bit for bit copy of the hard drive data to the ssh session I would think that there would not be any <newline> in the stream of data.

---

### Post by SoftwareExplorer on 2009-09-01
[QUOTE=Man ssh]If no pseudo-tty has been allocated, the session is transparent and can be used to reliably transfer binary data.  On most systems, setting the escape character to ``none'' will also make the session transparent even if a tty is used.[/QUOTE]
So when does ssh allocate a pseudo tty? Is it on by default or off by default. Second, what about a disk image prevents it from having a newline binary character?
Edit:By <newline> I meant the character that you get when you press enter, not literally '<newline>'

---

### Post by SoftwareExplorer on 2009-09-06
It seems like a pseudo-tty is the default because I logged into my backup computer and did ~. and the session closed and I was logged out of my backup computer. So my question is if there is anything that prevents a hard disk image from having something like ~ in the binary data. Would it interrupt the backup if a file had a line containing ~. by itself? 

Second, on my backup computer, I have a 1 TB drive. About 8 GB is for an ubuntu install, and the rest is a backup partition. I think I get how I would mount an uncompressed partition image, but is there a way to do that with one that is gzipped, without having to decompress the whole thing? The main reason I want to do this is to check the backups. (I heard a saying that says something to the effect of if you didn't check your backups, you didn't backup)

---

### Post by coppermine on 2009-10-05
Ressurecting dead thread may be not good idea but i wish to point out several things :
1) the block backups are quite risky because of low level information being manipulated;
2) filling the hard drive with zeros is not nice on operational system doing the work

---

### Post by jzacsh on 2009-11-25
> **coppermine said:**
> Ressurecting dead thread may be not good idea but i wish to point out several things :
1) the block backups are quite risky because of low level information being manipulated;
2) filling the hard drive with zeros is not nice on operational system doing the work

Can you elaborate exactly on "not nice on [*system*]"?

I'd imagine plenty of people are still finding this thread and benefiting from it (*including myself*) - so being an actively read thread, I can't think of a better place to talk about this...
[B]
That being said, I'm finding this thread to be [SIZE="4"]awesomely educational[/SIZE].[/B]
I think the ability to [just image an entire disk]("http://ubuntuforums.org/showpost.php?p=6155526&postcount=27") (*w/the whole partition map for all partitions*) is awesome.
[ _[http://ubuntuforums.org/showpost.php?p=6155526&postcount=27](http://ubuntuforums.org/showpost.php?p=6155526&postcount=27)_ ]

So, being kind of hazy about what actually occurs on my machine when I boot, I'm wondering if someone can relate that ^ to my situation:

**$ df**
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             11946532   6902144   4437536  61% /
udev                    254340       304    254036  awesome 1% /dev
none                    254340       188    254152   1% /dev/shm
none                    254340       336    254004   1% /var/run
none                    254340         0    254340   0% /var/lock
none                    254340         0    254340   0% /lib/init/rw
/dev/sda1             38464340  32025052   4485384  88% /multidrive
/dev/sdc5             75593540  34449904  37303704  49% /media/jzback
/dev/sdc6             78241284     53012  74213796   1% /media/jzstore

```

This extra 40GB "multidrive" is just another internal hard drive that wasn't being booted from...
**so I put the following in:**
_/etc/fstab_
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
*[COLOR="Red"]...all the stuff already in there...[/COLOR]*
#my line:
UUID=37e6f122-6cac-4096-bc11-834503d09540       /multidrive     ext4    defaults        0       0

```

[B][SIZE="4"]Correct me if I'm wrong:
[/SIZE][/B]I have a 40 GB hard drive being *[COLOR="Red"]mounted[/COLOR]*
ie
*[COLOR="Red"]given a directory as if it were part of my actual file system[/COLOR]* 
at boot time. This is really very neat, but still confusing to me.

**[SIZE="4"]The Main Question[/SIZE]**:
So now what happens if I image my hard drive, _the root_?.. **Do I get a disk image w/my multidrive??**

By "image the hard drive, or root", I mean w/specifying file path instead of the device path.. as follows:
```

dd bs=15M if=/ conv=sync,noerror | "gzip -9 > /media/jzback/test.img.gz"

```

I know that the above use of a file path (instead of device path) is acceptable to dd, because its currently running successfully (as I type this post) see:
```

dd if=/dev/zero of=/media/jzback/img/zero_fill.tmp bs=8M; rm -f /media/jzback/img/zero_fill.tmp

918+0 records in
918+0 records out
7700742144 bytes (7.7 GB) copied, 287.036 s, 26.8 MB/sthe

7657+0 records in
7657+0 records out
64231571456 bytes (64 GB) copied, 2463.04 s, 26.1 MB/s

```

**or is that use of the file system's path (*/media/<blah_blah>*) only acceptable as an output parameter?**

---

### Post by jzacsh on 2009-11-25
> **SoftwareExplorer said:**
> It seems like a pseudo-tty is the default because I logged into my backup computer and did ~. and the session closed and I was logged out of my backup computer. So my question is if there is anything that prevents a hard disk image from having something like ~ in the binary data. Would it interrupt the backup if a file had a line containing ~. by itself? 

Second, on my backup computer, I have a 1 TB drive. About 8 GB is for an ubuntu install, and the rest is a backup partition. I think I get how I would mount an uncompressed partition image, but is there a way to do that with one that is gzipped, without having to decompress the whole thing? The main reason I want to do this is to check the backups. (I heard a saying that says something to the effect of if you didn't check your backups, you didn't backup)

I'm not sure about your second question. But **if I'm understanding this entire thread about the dd utility at all**:
dd is actually writing bits (*binary digit - a zero, or one - an on or off*) to the drive.

the <new-line> character that you're referring to isn't being interpreted as a break symbol on by the dd utility because the dd utility is just "moving bits", a simple sequence of zeros and ones.

for example your computer stores an **ASCII line break** like this on the drive:
```
0000001010
```

So I believe GrammatonCleric is saying "bit for bit" as: dd is only sending 0's and 1's:
> **GrammatonCleric said:**
> Since DD is sending a bit for bit copy of the hard drive data to the ssh session I would think that there would not be any <newline> in the stream of data.

---

### Post by SoftwareExplorer on 2009-11-25
> **jzacsh said:**
> I'm not sure about your second question. But **if I'm understanding this entire thread about the dd utility at all**:
dd is actually writing bits (*binary digit - a zero, or one - an on or off*) to the drive.

the <new-line> character that you're referring to isn't being interpreted as a break symbol on by the dd utility because the dd utility is just "moving bits", a simple sequence of zeros and ones.

for example your computer stores an **ASCII line break** like this on the drive:
```
0000001010
```

So I believe GrammatonCleric is saying "bit for bit" as: dd is only sending 0's and 1's:

I was worried more about ssh seeing a ~. somewhere in the data (isn't all data, including what you type, binary) and thinking I typed it. It isn't really a pressing question; I back up with rysnc over ssh now. In fact it's more of a curiosity thing.  

Rsync is great for me because of the small time it takes to update a backup, that it handles symbolic links properly (I'm looking at you scp), and that it backs up at the file system level. That means that I can restore a single file from a backup if I need and that I can have different partition sizes when I restore.

---

### Post by electronico_nc on 2010-06-07
Hi all,

First thanks a lot for this good how-to !

I have a little question :
What if my system has a RAID1 system mounted as / in /dev/md0 (/boot is /dev/md1) ?```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc2[0] sda2[2](S) sdd2[1]
      3976000 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[0] sda1[2](S) sdd1[1]
      308592448 blocks [2/2] [UU]
      
unused devices: <none>

```Original backup line :```
if=/dev/sda conv=sync,noerror | ssh user@dest "gzip -9 > /path/to/image/ubuntu_linux.img.gz" 
```Should I use the RAID name :```
if=/dev/md0 ...
```or the hard drive : ```
if=/dev/sdc ...
```Thanks in advance for your time.

---

### Post by Matthaeus on 2011-07-04
> **electronico_nc said:**
> Hi all,

First thanks a lot for this good how-to !

I have a little question :
What if my system has a RAID1 system mounted as / in /dev/md0 (/boot is /dev/md1) ?```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc2[0] sda2[2](S) sdd2[1]
      3976000 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[0] sda1[2](S) sdd1[1]
      308592448 blocks [2/2] [UU]
      
unused devices: <none>

```Original backup line :```
if=/dev/sda conv=sync,noerror | ssh user "gzip -9 > /path/to/image/ubuntu_linux.img.gz" 
```Should I use the RAID name :```
if=/dev/md0 ...
```or the hard drive : ```
if=/dev/sdc ...
```Thanks in advance for your time.


I'm also very curious about this. I too run buntu from a mdadm raid1 setup.

/thread necromancy.

---

### Post by Jochus on 2011-09-07
Hi,

I just followed this tutorial, but I'm afraid something it isn't working very good in my case.

I have a SATA disk (/dev/sda) which has 3 partitions:

```

/dev/sda1               1        1992    15998976   82  Linux swap / Solaris
/dev/sda2   *        1992       26891   200000512   83  Linux
/dev/sda3           26891      121602   760761344   83  Linux
```

/dev/sda2 or / is my root partition
/dev/sda3 or /backup is my backup partition

I use the "zero" trick to clean all space. There's currently 135 GB used data in / (without /backup folder included).

I create a file from /dev/sda to /backup/image. But the image is becoming so large, so I'll run to the "out-of-disk-space" error. The image is now 450 GB big, but I only have 135 GB of data.

What could be I'm doing wrong?

---

### Post by dcsoldschool53 on 2011-09-07
Thank you very much for your tutorial.

---

### Post by SoftwareExplorer on 2011-09-07
I would recommend making a filesystem level backup, which actually works. I usually use rsync with the -avx options (-a = archive -v = verbose -x = don't go across filesystem boundaries, so you don't try to copy things like /dev/zero). 

I usually do something like this:
```
sudo rsync -avx / /media/Backup_drive/root/
```
This will store a backup of the currently running system's filesystem on backup drive in the root folder. To restore it, I do nearly the same thing from a LiveCD/USB:
```
sudo rsync -avx /media/Backup_drive/root/ /media/partition_to_restore_to/
```

To restore, after you run rsync, you need to edit /etc/fstab in the restored system to reflect any changes, especially if you restore to a different partition. You also need to update grub, usually using the Chroot method listed at [https://help.ubuntu.com/community/Grub2/#ChRoot]("https://help.ubuntu.com/community/Grub2/#ChRoot")

---

### Post by joof on 2011-09-10
^

SoftwareExplorer, thank you for this; it came just in time.

---

### Post by c-shadow on 2011-09-10
Another option for making a backup at filesystem level is fsarchiver (it's in the ubuntu repository):
[http://www.fsarchiver.org/](http://www.fsarchiver.org/)

For daily online backup sbackup is good, it's a really nice "fire and forget" program:
[http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)
Also in repos.

For restoring GRUB on a new system (for the people who don't like fiddling with the chroot ):
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)

I use sbackup for nightly backup of /home partition to another drive. fsarchiver for backing up /boot and /root partitions (both on soft raid arrays). The resulting compressed files are then transferred to removable drive, and less frequently (because of size) burned to optical media.

---

### Post by Forgonewarrior on 2013-02-14
Can you save this to a CD?

---

