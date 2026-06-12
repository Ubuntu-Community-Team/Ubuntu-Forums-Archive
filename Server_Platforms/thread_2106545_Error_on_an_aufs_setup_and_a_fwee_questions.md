---
title: "Error on an aufs setup and a fwee questions"
date: 2013-01-19
forum: Server Platforms
---

### Post by macexx on 2013-01-19
Hi,

I just ventured into the world of ubuntu after many years of evilsoft. So pls use terms that a noob like me can understand my knowledge is very basic and moastly consists of reading guides.

And pls excuse my english.  

I´m running 12.04 server edition.

I have a setup with one main disk "sda", and two disks (sdb,sdc)that are pooled using aufs.

I have them mounted as /media/disk1 and 2
and with aufs as /storage

FSTAB:
----------------------------------------------------------------

#---------------------
# NAS DISKS
#---------------------
UUID=f56fcb72-f6f4-45ba-92fd-0e96a64f29a4 /media/disk1 ext4 defaults 0 0
UUID=9d98fcf5-c4b5-43da-bebb-980dca398415 /media/disk2 ext4 defaults 0 0
#---------------------
#Aufs Disk Pooling
#---------------------
none /storage br:/media/disk1=rw:/media/disk2=rw,sum,create=mfs 0 0

----------------------------------------------------------------


I´m running sab,sickbeard and couch potato on this and all was working great.

But i when i added another disk to the setup there was a fwee issues the new disk got named "sdb" and i thought this dosent mather since they are linked to uuid´s in fstab.

So i added the new disk in fstab to /media/disk3 and added it to aufs. anb all was working great i could see the space was added by running "df -k /storage"

But then there was some issues, when i download something useing sickbeard->sabnzbd  the "sabToSickBeard.py" takes forever and returns:

----------------------------------------------------------------
Traceback (most recent call last):
  File "/home/mace/.sickbeard/autoProcessTV/sabToSickBeard.py", line 29, in <module>
    autoProcessTV.processEpisode(sys.argv[1], sys.argv[2])
  File "/home/mace/.sickbeard/autoProcessTV/autoProcessTV.py", line 101, in processEpisode
    result = urlObj.readlines()
  File "/usr/lib/python2.7/socket.py", line 515, in readlines
    line = self.readline()
  File "/usr/lib/python2.7/socket.py", line 430, in readline
    data = recv(1)
socket.error: [Errno 104] Connection reset by peer
----------------------------------------------------------------

Removing the new disk from fstab and the computer dident solve the issues, anyone have any ideas.

And a question that might be related i´m useing putty to connect to the server, now my /media/disk1-2 and all the content is marked green in putty why is that?  

Pic of what i mean by marked:

[http://postimage.org/image/qcyela9sr/]("http://postimage.org/image/qcyela9sr/")

Hope someone can help me, since my budget dont allow be to buy new disks and go raid.

//Regards Marcus


Seems I solved the sickbeard part for some wierd reason the autoProcessTV.cfg keeps getting overwritten as soon as sickbeard starts, just changed it´s permissions to read only an no thats solevd.

However what does it mean when a disk is marked in terminal like the picture in the link??

//Marcus

---

### Post by rubylaser on 2013-01-19
Thos disks are green because there permissions are 777.  User, Group, and World can read, write, and execute anything on those drives.  In regards to AUFS, I have had better luck adding the mount for the AUFS to /etc/rc.local. I wrote about it in my [SnapRAID tutorial]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04").

---

### Post by macexx on 2013-01-19
Thanx a bunch for the explenation on the highlighted disks, well guess its time to change some permisions ;)

Aufs is working great now with my third drive, I acctually followed your guide to set up my system =P 

I have a question for ya, when i first set up my "aufs" it would only write to one drive I had "create=pmfs" but when i changed it to"create=mfs" it worked properly and wrote to the drive with moast space.


And thanx for a great guide mate!!

---

### Post by rubylaser on 2013-01-19
mfs and pmfs are very similar.  They both write to the drive with the most free space.  The difference is that pmfs writes to the drive with the most free space where the parent (folder exists).  Here's the explanation of all of the create modes from the man page.

> 	
create=tdp | top&#8722;down&#8722;parent

Selects the highest writable branch where the parent dir exists. If the parent dir does not exist on a writable branch, then the internal copyup will happen. The policy for this copyup is always &#8217;bottom-up.&#8217; This is the default policy.

create=rr | round&#8722;robin

Selects a writable branch in round robin. When you have two writable branches and creates 10 new files, 5 files will be created for each branch. mkdir(2) systemcall is an exception. When you create 10 new directories, all are created on the same branch.

create=mfs[:second] | most&#8722;free&#8722;space[:second]

Selects a writable branch which has most free space. In order to keep the performance, you can specify the duration (&#8217;second&#8217;) which makes aufs hold the index of last selected writable branch until the specified seconds expires. The first time you create something in aufs after the specified seconds expired, aufs checks the amount of free space of all writable branches by internal statfs call and the held branch index will be updated. The default value is 30 seconds.

create=mfsrr:low[:second]

Selects a writable branch in most-free-space mode first, and then round-robin mode. If the selected branch has less free space than the specified value &#8217;low&#8217; in bytes, then aufs re-tries in round-robin mode. Try an arithmetic expansion of shell which is defined by POSIX. For example, $((10 * 1024 * 1024)) for 10M. You can also specify the duration (&#8217;second&#8217;) which is equivalent to the &#8217;mfs&#8217; mode.

create=pmfs[:second]

Selects a writable branch where the parent dir exists, such as tdp mode. When the parent dir exists on multiple writable branches, aufs selects the one which has most free space, such as mfs mode.

I'm glad my guide was able to help you out.

---

