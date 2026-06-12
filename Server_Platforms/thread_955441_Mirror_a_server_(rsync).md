---
title: "Mirror a server (rsync?)"
date: 2008-10-22
forum: Server Platforms
---

### Post by TheGameAh on 2008-10-22
Howdy guys.

Soon, I'm going to have a server with the following:

Samba (for Windows users)
NFS (rarely used, but possibly for VMWare testing)
VMWare (4-5 VMs, Windows based)

Regular backups to tape, of course.  But what I'd also like to do is take a spare server and mirror this one to have a close up to date copy of everything.  Obviously if the server really crashes, I can just change IP addresses, and not have to worry too much about downtime and fumbling with tape.

I've studied up on heartbeat.  That's a little overkill to be honest.  I don't mind a little downtime while I change IP addresses (so high availability isn't really necessary).

So is rsync the way to go here?

And if rsync is the answer, I'm assuming it can handle samba and nfs shares no problem.  But what about VMWare images?  I can't see rsync working very well on a running VMWare image.

---

### Post by jonabyte on 2008-10-22
I use rsync to backup files to an external drive nightly and it works great that way. I am not sure about using it to mirror or in a sense clone your server.
If you setup the mirror already and just rysnc the data, it should work well, but not sure how rysnc handles services running such as samba.

---

### Post by dotkam on 2008-10-22
@TheGameAh,

   Check out the howto forge article: [http://www.howtoforge.com/mirroring_with_rsync]("http://www.howtoforge.com/mirroring_with_rsync") on how to keep mirrors via rsync.

   As far as VMWare images, I am not sure what the nature of your server is but, you're right, it does not make sense to mirror "several moving pieces" in one sync :-k. Hence, the logical way, would be to mirror its static pieces.

   :arrow: So, let's say your rsync process is scheduled on 4:00 A.M.. Then schedule another process at 2:00 A.M. that takes snapshots from all the VMWare images. By the time 4:00 A.M. comes you have your static VMWare images ready to be synced.

   Yes, you might loose (only in case the first server crashes with no HD restore) these "2 hours of off-peak fun", but you'll always know you have stable images on your mirror(s).

Let me know what you think,

-- dotkam

---

### Post by MJN on 2008-10-23
For what it's worth I use rsync to make nightly backups of my entire system (the whole shebang, whilst it's running) to an external drive.
 
I have simulated a total hardware failure by restoring this backup to another machine (of almost identical hardware) and bar having to make a couple of tweaks (to accomodate the different hardware, e.g. network mappings, fstab mount points etc) was up-and-running in no time at all.
 
Hence, I can confirm that a snapshot of a running system can be done with rsync, however as the others have said it's likely the virtual machine aspects could be what trip you up.
 
Unfortunately I have no virtual experience (do you put that on your CV? ;-)) and so perhaps it may well be the case that it's no different than a real machine and requires no specific attention.
 
Give it a go. What have you got to lose (apart form your system ;-))? I'm a great supporter of rsync - once you get to grips with it it is extremely powerful, robust and yet simple at the same time. You cannot beat having a backup existing in exactly the same format as the source.
 
Mathew

---

### Post by TheGameAh on 2008-10-23
Thanks for the replies guys.  I did a ton of studying yesterday.  Here's what I came up with, for anyone interested.

Rsync will indeed be fine for the NFS and Samba shares (was actually more concerned about the Samba shares, and how rsync would react to ACL).  This is going to be a RAID10 system, so hopefully this spare server will be kinda a last resort thing, only if the motherboard or power supply dies.  It's just to have another step before going to tape.

The VMWare images will be the rough part, as was said above.  You can't Rsync a running Vmware image, unless you incorporate LVM for snapshots (I'm a total newbie to LVM, and have only had bad things happen with it from the little bit of experience I do have).  And if I suspend/shut down the VMWare images, I could rsync them.  However, it looks like typically Rsync will do the entire image, and not just the changes.  So it's a huge transfer.

So for the VMWare part.  I'm just going to write a script to shutdown the images, tar and compress them, and those tarred files will be what I rsync.

Should be a fun project.  Basically I'm pulling all of my Windows 2003 files shares out of Windows, putting them on Samba, and virtualizing everything else.  Since I'm going to have so much data on this one server, I figured a spare in another building that was basically a clone of it would be a good idea.

---

### Post by ezacon on 2008-10-23
I have a ubuntu server with vmware server and 2 virtual machines.
I backup the server to a big network drive (everithing gigabyte) the virtual machines are backed up by pausing them with a script and tar.
I back up vm's on week end because they have relatively static data.

Here is an example script for 1 vm (im not a programer):

#!/bin/sh
ISMOUNT=$(cat /proc/mounts|grep /media/copias)
if [ -z "${ISMOUNT}" ];
        then
                echo Montando disco de copias
                mount /media/copias
                if [ $? -ge 1 ]
                        then
                                echo ERROR mounting disk
                                exit
                fi
        else
                echo Disk is mounted
fi
# Copia maquina virtual windows 2003 server
/usr/bin/vmware-cmd "/var/lib/vmware/Virtual Machines/win2k3/Windows Server 2003 Enterprise Edition.vmx" suspend
/bin/tar \
        --create \
        --verbose \
        --preserve \
        --gzip \
        --ignore-failed-read \
        --file=/media/copias/win2k3.tar \
        /var/lib/vmware/Virtual\ Machines/win2k3/
/usr/bin/vmware-cmd "/var/lib/vmware/Virtual Machines/win2k3/Windows Server 2003 Enterprise Edition.vmx" start


If your is beter, let me have a look

---

