---
title: "Open Source/Free Backup Solution"
date: 2016-04-02
forum: Security
---

### Post by biosboy4 on 2016-04-02
Hello,

I am about to implement a backup solution that is basically the following:

1) Ubuntu Server Disconnects/unmounts the backup drives. (the vault)
Note* Drives are encrypted and a goofy filesystem windows can't read.
2) Connects to directly to the servers and the core network.

Note* Server will be forced to use swap and will share it as windows
share so that if the ransomware is active, it will encrypt the swap and
freeze the server before it ever connects back to the vault.

3) Syncs all data to isolated partition while updating clamav (antivirus).
4) Disconnects from networks.
5) Runs Security Scan.
6) Connects to/mounts the vault and dumps data.
7) Disconnects from the vault.

I believe all of this can be done with Bash, correct?

I will be implementing this over the next 10 days, and pointers are welcome.

Thanks

---

### Post by TheFu on 2016-04-03
Seems overly complex.
Versioned backups should handle it, provided enough versions are retained.  I keep between 60 and 120 days of backups for each system here.

Bash is just glue. It doesn't actually do anything except glue other programs/tools together.  The "ABSG" is where I go to learn more about bash.  Search "ABSG bash" to find it.  If you don't already script or program already, the learning curve is steep.  For the stuff you want, I'd use a different language - python, perl, ruby would be the popular choices to look into. 

A few other notes:
* clamAV on a server should update daily, automatically. That shouldn't have **anything** to do with backups.
* Hard to do a network backup without the network. Don't see the point of that.
* "Security Scan" - what is that?  Seems a little vague.  Most of the scanners for Linux actually look for issues with Windows files.  The root-kit scanners aren't really useful - sorry to say that, but the output is full of useless data (not real information).  Install logwatch, setup daily email reports. Done.
* Mounting and unmounting backup disks is fine ... or just use automounter - autofs.

How do you plan to backup the Windows machines?  Bacula / Amanda? Something else?  Whatever you do, be certain it is versioned, not just a mirror.

---

### Post by biosboy4 on 2016-04-03
Thanks for your input, it is much appreciated.

Clamav would update daily, during the network connection. The reason for the limited connection (as needed basis) is to create an "isolation chamber" between the network and hard drive connections so that rasomware being executed from the windows network cannot reach the vault. 

The swap space will be shared as a windows share so that any active ransomware would freeze the server before it ever makes it back to the vault.

The vault is encrypted and also the goofiest fylsystem I can think of so that windows cant read it.

Its all about protecting the backup.

Edit: The windows machines will store to the "shared drive" via links and mapped drives. The shared drive will be synced by the ubuntu server daily. 

An isolated network is for the ubuntu server to grab large things like database files, server backups, snapshots, etc.

---

### Post by biosboy4 on 2016-04-04
I am currently trying to figure out how I am to backup all of the servers via images of the whole servers. Is there a way I can tell the Bash script to open up an SSH session to the ESXi hosts so that I can copy them directly from there? If not, I am working another angle where veeam free will (I hope) make images and place them on the shared drive or something where the backup server can access them from.

---

### Post by TheFu on 2016-04-04
We dumped all VMware software around 2011 and have never looked back.  KVM is the tool of choice for this stuff since 2010 and it part of the Ubuntu and Redhat solutions. It is also used by openstack for extremely large-scale virtualization deployments.  To backup ESX stuff, I think you need to pay $100 for backup tools.  I've deployed TriLead backup tools for ESX ... didn't really like them and how long they took.  For my company, we switched to using standard, Linux, backup tools which were 10,000x more efficient than anything designed to work for ESX.  Backups for most of our servers require 1-4 minutes daily.  

Images for backups?  We stopped doing that years/decades ago.  I suppose if we ran Windows servers, that would be necessary once a month, but only change data would be backed up daily.

I wrote up a long, huge, response to your prior post and decided it was nice enough to be posted.  In short, I think you are trying to solve problems that Windows has from Linux. I think you are doing it wrong, but there could be unexplained reasons why that is necessary.  I've never run Windows servers and was only a Windows software developer for 5 yrs - but I've been on Unix for over 25 yrs and think in the Unix way (which is VERY different) from the Windows way.

In short, you should be using versioned backups to solve these issues and use a client/server backup model, not shared storage. Use bacula, duplicity, Amanda, or some other backup tool based on librsync to solve this.  If you plan to use something like synctoy to copy files over and only have 1 copy, that is a backup failure. You must have 30-120 "versions" of the backups. That solves all the issues you seem worried about that might occur. Versioned backups, not images.

Of course, dumping VMware isn't a trivial decision. We ran multiple systems on KVM for over a year before the final decision was made to switch completely. We used Xen as well.  KVM has **never** caused any issues, technical or otherwise.  Xen caused technical issues a few times a year - the hostOS would refuse to boot - that's an example. There were others.  With ESX and ESXi the issues were both technical and costs.  ESXi refused to boot on 80% of our hardware, the backup tools were all $1-5K and then there were the license costs (at the time, VMware corporate had decided to triple the license costs). They were greedy, IMHO.  All of this happened between 2009 and 2011, so things may have changed greatly since then. I don't know.  We are happy and don't have any plans to switch, though we are playing with containers for internal use only,. Don't have any plans to use containers for production and definitely NOT for anything internet facing for many years.  2020 is our next decision point. ;)

---

### Post by biosboy4 on 2016-04-04
Can I make versioned backups of vm images? I just figured out how to make vm images daily and copy them to a location that is accessible by the backup server. However, this means the backup server will be copying over the entire files everytime. Not the worst thing in the world since I have an isolated network for this, but I'm just wondering if there is a way to move only new data in the images. 

Also, I'm not using shared storage. I'm actually using HA-Lizard to get the vm clustering done with internal storage only. This whole Ubuntu/Zen backup box is internal storage only.

Thanks for your reply,

---

### Post by TheFu on 2016-04-04
I'm not plugged into the VMware ecosystem and simply don't know that answer.  

The key thing for versioned backups is that only data that has changed since the prior backup is transmitted, so the "versions" aren't large at all, but during the restore process, all the files, permissions, ACLs, etc. are put back for the specific version like you had created an image for each backup.  The efficiency of this method is 10,000x better than making image-based backups that are 20G every day.  It also means that backup storage doesn't need to be 30x larger than the actual production storage used to have 30 days of backups.  For our uses here, it is about 10% more storage for 30-60 days of backups.  So if a server uses 10G, then 30 days of backups would used less than 12G of storage.  Why wouldn't you want that?  Plus the old-school methods of weekly-fulls and daily incremental backups that old Unix admins have used for decades just isn't needed.

I treat VMs like they are physical machines and run backups from inside each VM - well - that isn't really true - I have a backup server that runs rdiff-backup and connects to each server which runs rdiff-backup on that side and transmits the backup data back to the server over the network through an ssh tunnel.  The server controls all of that. It also quiesce any DBs or other programs with open files so the backups are not corrupted. That is manually setup for each server. Using LVM and taking snapshots before the backup begins could avoid that.  ssh-keys are used for the authentication and tunnel.  The backup storage is only available to the backup server - the client machines don't know anything about it.  This is a "pull" backup method.   Something like this method is possible with duplicity and pretty much every other network-based backup tool on Unix systems.

[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) is the simplest/best explanation I've seen for it. Much better than any I've attempted on my blog. ;)

Anyway, hope this isn't confusing you too much, but showing alternative ways to accomplish things in a more efficient way.  If you aren't comfortable doing it this way - I wouldn't.  After all, the restore is the entire point of this effort. Without it, it is just wasted time.  I'm positive that these methods work. Once screwed up our email servers (actually not just once) and had to restore from the backup made 4 hrs earlier.  45 min later and everything was back and working.  If I'd had an image based backup, the restore could have been a little faster (maybe 30 min) with fewer commands, but at the cost of all the extra storage.  

Just to be clear "shared storage" was me trying to say that the client machines could see the storage where the backups were going. 
I've never heard of HA-Lizard.  Looked at many cluster solutions over the years, but not that one.  We generally just deployed either EMC or Netapp storage on SANs.  At home, I use NFS for non-local storage.  VMs run on RAID1 DAS.  After all, with the backups that I'm positive can be restored in less than 45 min (for any one of them), there isn't any need for clustering.  Our systems are NOT THAT critical where automatic failover of the VMs is needed.  I can spin up a clone of the email front-end server on an alternate system in less than 10 seconds, so that isn't a big deal, but it is manual.  We had a power outage for 6 hrs last weekend - I noticed (alarming told me), but nobody else did. ;)  One of our UPSes failed (within 10 sec of the power outage), so half the VMs were down.  The other UPS worked perfectly for 40 min, then shutdown the servers cleanly.  Think I got 7 yrs out of those batteries, so it isn't the end of the world.  I know they are only rated for 3 yrs. Not bad.  Power came back up before 2am, when all our backups start running.  Didn't miss a beat. I love it when a plan comes together and everything works as it should ... er ... unless there is a failure in the backup electricity. ;)   No generators or gas-turbines here. ;)

---

### Post by biosboy4 on 2016-04-06
I have 1 big question: 

How can I gain visibility to the .vhd files from the Ubuntu server? Please help me find a way
.
Thank you,

---

### Post by TheFu on 2016-04-06
Option:
a) Connect to the VM using normal file sharing tools.
b) Or find a driver - but mounting a file system that is already mounted natively by another running OS is asking for data corruption.  Unix/Linux will let you do it, but that doesn't mean it is a good idea.

With Linux as the hostOS, most enterprises use a dedicated LV for each VM.  Makes taking snapshots (for backups) and mounting those much easier.  1 LV for each VM. Removes the need to have DBMS dumped or shutdown during backups if you do it this way.  If you need a networked based VM file system store, use NFS. It will be a little slower, however.  LVM can do some amazing things.

I assume VHD files are from some other virtualization technology?  Is it a specific file extension or a generic term?  
[https://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk/359852](https://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk/359852) covers most of the commonly used VHDs that I know.
[http://ubuntuforums.org/showthread.php?t=2299701](http://ubuntuforums.org/showthread.php?t=2299701) - post #5 seems like a good start for the microsoft file stuff.  I've never used it. Looks like FUSE, so it will be slow - good to rescue data, not to run a VM.

---

### Post by biosboy4 on 2016-04-06
I'm trying to reach into our VMware cluster to incrementally backup the hard disk files.

---

### Post by TheFu on 2016-04-06
> **biosboy4 said:**
> I'm trying to reach into our VMware cluster to incrementally backup the hard disk files.

>     I'm not plugged into the VMware ecosystem and simply don't know that answer.  

For VMware backups, I think you either need to pay for a solution or backup from inside the VM.  Years ago, I looked at F/LOSS stuff to backup VMware stuff - it wasn't good and didn't seem to be moving forward in the 4 yrs that I watched.  Decided to spend $1000 and move on.  That was before we dropped VMware; a big decision.

---

### Post by biosboy4 on 2016-04-06
How do I backup from inside the vm's? They are windows server.

---

### Post by biosboy4 on 2016-04-06
I just found this:


[http://blog.magiksys.net/run-rsync-i...on-vmware-esxi](http://blog.magiksys.net/run-rsync-i...on-vmware-esxi)

[http://www.virtuallyghetto.com/2011/...ked-rsync.html](http://www.virtuallyghetto.com/2011/...ked-rsync.html)

[https://damiendebin.net/blog/2013/12...t-1-and-rsync/](https://damiendebin.net/blog/2013/12...t-1-and-rsync/)



I'm going to do it. Wish me luck.

---

### Post by biosboy4 on 2016-04-07
Ok when I try this:

[root@esxi02-b:~] cp -r  /vmfs/volumes/54ef4c22-27a271ae-b5c4-000af77e3720/ASTRABESSVEEAM /AKRYPT-LINUX/bakhak

I get the following:

cp: write error: no space left on device

What am I doing wrong? I shared the location with Samba and gave write permissions to everyone.

---

### Post by biosboy4 on 2016-04-26
I finally got everything working!

I used a pull script to pull backup all FILES from the network. Then I used a second script that runs from the ESXi host to push the vms over. I used XSIbackup (open source/free) for this, which supports many things including hot backups.

Here's what ended up working:

#Hardware: x86 box with a good raid config (like raid 1 or 10).
#I used 4 partitions for this deployment: OS(small), Dir1"sdd1" (big), Dir2 "sdd2" (bigger), and vault"sdc" (biggest).
#Software: Debian, dependencies are pretty much met out of the box. You will need Rsync and Samba if you made a minimal install.
#XSi-Backup, a respected open source backup solution that supports hot-running vm backups. Installation is spelled out in this script.
#Connect the server to the network via a static IP, make sure it can ping everything it needs to reach.
#make sure sdc is umounted by default, sdd1 is mounted to /backup/Dir1, and sdd2 is mounted to /backup/Dir2
#run the script:

mount -t cifs //serverip/sharedir/ /backup/dir1 -o credentials=/credentialslocation
#this mounts the entire shared drive using a root read only credentials file
sleep 10s

rsync -avz /backup/dir1/ /backup/dir2
#backs up the data from dir1 to dir2
sleep 10s

umount /backup/dir1
#unmounts windows share
sleep 10s

mount -t //server/"share with spaces"/ backup/dir1 -o credentials=/credentialslocation
#Mount the PLC share
sleep 10s

rsync -avz /backup/dir1 /backup/dir2
#syncs share to dir2
#note* an "infinite" amount of directories can be backed up this way
sleep 10s

umount /backup/dir1
#unmounts share
sleep 20s

freshclam
#antivirus update
sleep 10s

clamscan -r --bell -i /
#scan entire filesystem and hault/ring a bell (alert) upon threat detection, stopping the script.
sleep 10s


mount /dev/sdc /backup/vault
#mounts the backup vault
sleep 10s

rsync -avz /backup/dir2/ /mnt/bak8
#syncs temp dir2 to the vault
sleep 10s

umount /mnt/bak8
#unmounts vault
sleep 10s

#end of script.

Here's how I got the vms backed up:

install XSibackup:
cd /vmfs/volumes/datastore1/xsi-dir 2>/dev/null || mkdir /vmfs/volumes/datastore1/xsi-dir && \
cd /vmfs/volumes/datastore1/xsi-dir && \
esxcli network firewall unload && \
wget [http://33hops.com/downloads/?key=ojW...ziaiJYXquxoIaR](http://33hops.com/downloads/?key=ojW...ziaiJYXquxoIaR) -O xsibackup.zip && \
unzip -o xsibackup.zip && \
chmod 0700 xsibackup* && \
rm -rf xsibackup.zip && \
esxcli network firewall load

Now set up Dir2 on the server as an NFS share to be mounted via the ESXi cli or vsphere.

Now we cron this script:

./xsibackup --backup-point=/vmfs/volumes/newnfsdatastore --backup-type=ALL
#this pushes clones of the hot and cold vms directly to the backup server where it will pick them up from Dir2 and drop them into the vault automatically.

This is the rough draft/launch of this little project. I have a lot of cleaning up to do and many improvements to make. Any help is greatly appreciated.

Thanks,

---

