---
title: "Partitioning of a ubuntu server for virtualization"
date: 2017-07-13
forum: Virtualisation
---

### Post by totla on 2017-07-13
I am in the process of installing latests LTS Ubuntu server on a new server hardware. The server will only serve as a platform for Virtualbox that will, in turn run several virtual servers.
Question is how should i be partitioning my "platform" Ubuntu. Should  i just partition /root, /swap /boot like normally or what?? Also I want to make a separate /home partition that will house all users data, that i can just mount on the virtual servers, so i can save space in the backups + makes things easier since all files are available for all users on all servers, at least thats the idea.

My plan for the setup was this:
8TB of space, in raid6 so i have 4TB of usable space
200gb /root
2gb /boot
32gb /swap
200GB /home
rest of the space goes for /virtualservers , that will have all the images for all virtual servers
Does this make sense?

Any suggestions how to best approach this?

---

### Post by TheFu on 2017-07-13
a)  Don't use virtualbox.  Use something with much greater performance, flexibility and capabilities - KVM/QEMU with libvirt.  **[virt-manager]("https://help.ubuntu.com/community/KVM/VirtManager")** is the GUI and it can be run from anywhere over an ssh connection to create/manage VMs.  With [Spice]("https://www.spice-space.org/spice-user-manual.html") for the graphics, performance is really excellent (for any desktops).
b) /root should be tiny.  Nothing should be stored in there beyond a few root-only scripts and perhaps some sensitive backup data. I don't bother making it separate from /.
c) / - this is the real root - I'd make it 25G which is overkill for most uses.  My primary desktop has only 17G total storage for reference.
d) Swap?  On a server?  No. Just ... no.  Buy enough RAM that swap isn't needed. RAM is cheap. Tune the workload.  The old rules about 2x RAM haven't applied in decades.  **Any** system with more than 8G of RAM shouldn't need more than 2G of swap. For desktops, swap becomes more important since popular browsers will expand to eat all available RAM and then some.
e) /boot - 700MB is 2x what most people need.  Just clean up old kernel monthly and it will be fine.
f) /var/lib/  - this is where VMs are placed when libvirt is used.  If you use QCOW2 storage, it should be fairly efficient.
g) RAID6 is highly inefficient - as in slow. Don't.  Use RAID1 or RAID10 if you want redundancy.  If you use enterprise SSDs, RAID0 is fine. Their failure rates are extremely low.

Use LVM for all physical storage.  LVM will let you resize things as needed even while the system is running.  LVM snapshots allow for consistent backups without downtime too.  Highly, highly, recommended.  Some people create LVM LVs for each VM, so the snapshots can be for a whole machine at a time, easily.  QCOW2 supports snapshots too.

Nothing replaces the requirement for excellent, automatic, daily, versioned, backups.  Not LVM, not RAID.

As for mounting user HOMEs - your plan is fine. Just use NFS.  Might want to have a FreeIPA server to manage user accounts across all the systems too.  NFS needs for the numeric uid/gid to match across systems.  With 5 users, it isn't a big deal to manually handle this. With more users, a central password/login solution based on LDAP really is best.  Just add the POSIX extensions to the LDAP server and configure PAM on each system.

Of course, there are lots of other redundant storage methods like [sheepdog clustering]("http://www.sheepdog-project.org/") across multiple servers that you may want to consider rather than any RAID with redundancy. Sheepdog makes KVM failover between different physical servers pretty easy.  Handy for a number of reasons.

---

### Post by totla on 2017-07-13
Good stuff. Thanks!
I will look into KVM/QEMU tommorrow, i inherited 2 physical servers which both run virtualbox with phpvirtualbox GUI for easy management, so i just figured i would do the same with the new servers.
I thought swap was required, so its there just for that, but yeah if its not required i think the 32gigs of ram our new server has will do just fine.
The raid6 wasnt my idea, my superior basicly ordered me to make it raid6, he wants the extra redundancy you get from raid6, so i have to go with that unfortunatly ( and yes we do have enterprise ssd, (SAS).
New plan is:
/ - 30 GB
/boot - 1 GB
/Home - 20 GB
/var/lib/ -- rest of the space? (3.9TB) (will house 4-5 seperate servers for starters ( 2xapache, dns, couple of svn servers)

Another reason i originally was going for virtualbox was so that i could use the new server as a backup server for the older servers by just copy/pasting the backup images on the new virtualbox.
Doubt i can just import vbox images to qemu? :)

---

### Post by TheFu on 2017-07-13
If you use LVM and sheepdog, your survivability and flexibility goes way up.  Don't underestimate storage architecture.

How can I say this nicely - virtualbox is a toy.  That's as nicely as I can say it.

You really don't want to migrate a vdi from vbox into a qcow2 for KVM.  It is possible, just a terrible idea.  The drivers you want are different and much better/more efficient under KVM.  You can rsync the files from 1 type of storage into the other, if you like, but I wouldn't use it directly or even use a translation tool.

I cannot imagine running 5 servers in 1 TB of storage, much less 4TB. That just seems crazy.  None of those require much storage.  Plus I don't get why having shared HOMEs across them is even a consideration.  No end users should have direct access to DNS/Apache systems.  I'd also push for using a git DVCS solution over SVN.  SVN is so, so, so ....  1990s.  For the git servers, if you go that way, force devs to use ssh, but only allow git commands to be used, not general logins.

You didn't say how many people.  Where's your POSIX LDAP server?

RAID5/6 is a really bad idea for HDDs over 2TB in size, especially if the storage is busy.  Ask any storage vendor.

virt-manager is a secure, remote, method, to manage up to about 50 physical VM servers.  Beyond that and you probably want an openstack-based solution with all the overhead that demands.

And don't forget that container-based services are much lighter than HVM solutions like KVM or vbox or ESX or Xen or ... all the others.  I wouldn't pause for 10 seconds to make git/svn servers container based.  You can use docker or LXD - doesn't really matter. Just run all the containers under a KVM VM to retain that separation.  Containers are usually about 10x more dense than VMs, but never treat container maintenance like you do physical or normal VMs.  A container that has ssh enabled is a failure. It should have only enough OS to perform the single service, nothing more.  When it is time to patch a container, that means rebuilding it from scratch using all new inputs for the OS, 3rd party tools, libraries, everything.

BTW, it is easy for me to say things. I don't have to do the work.  But I have been around a long time and have seen mistakes made over the years. Some whoppers are mine. 

Some really important things:
* use KVM
* use LVM
* use virt-manager / libvirt
* use virtio for network and disk drivers.
* don't convert the old storage (vdi) into the new storage.
* sheepdog is a nice-to-have. You won't regret it, but not mandatory, IMHO.
* Containers can be ignored. If you decide to move, that can happen later. 
* Use RAID1 or RAID10 for any HDDs over 2TB in size holding the VMs.

---

### Post by totla on 2017-07-13
Usually you wouldnt obviously need terabytes of space for servers, but our servers have to handle several hundred GB's of scientific data everyday from several locations and process that data, do plot etc.
After processing it obviously goes for storage on NAS drives. 

You clearly know your stuff and have been at this for much longer than i have (still a newbie here), so will for sure take notes and study up and learn to do this the right and better way, thank you.

Have you got any suggestions on a good backup solution, curretly running FSArchiver, automatic backup and snapshots every 3 days. 
I have been told to look for another backup system since you cant restore single files from FSArchive imges + our old server backups have grown over 2tb in size (restoring image of that size takes a couple of days...), mostly due to home directories being included in backups and those take a huge amout of space, since scientists like to store gigabytes of data there, thats one of the reasons for making seperate mounted /HOME directories for our new server

---

### Post by TheFu on 2017-07-13
Scientists will use every MB you let them.  Enabled quotas.  1GB per userid for their HOME.  Data shouldn't be allowed in HOME directories.  Make per-project data areas so the scientists working on the project all share it.  Anyone abusing it ... well that's politics for you.  I've seen people doing lots of foolish things because they didn't trust backups.  If you do your job correctly, they won't have a reason to keep 500MB of data "just in-case" they need it.  That is what a backup system does.  Having storage online is expensive. Backup storage is much more cost effective.

fsarchiver is NOT a backup solution. It is an imaging tool.  Snapshots are an LVM thing.  It freezes all the currently used blocks and all new/changed data are written to new blocks.  When the snapshot is removed under LVM, the new blocked created since the start of the snapshot become the primary and the old ones are freed.  This is instantaneous (both the create and remove).  The running OS doesn't notice.

I use **fsarchiver** only when moving boot drives.  Never for general data, home directories, etc.  Can't take the downtime.

Backup software should be taking versioned backups of the snapshot (frozen).  I use rdiff-backup.  30 days of versioned backups requires about 1.15x the original storage. It is fairly efficient.  Some of my systems have 120 days of versioned backups.  It isn't data centric. I actually don't even backup the OS. A few months ago, had a disk failure.  Recreating the OS with all the programs, settings, and minimal "data" took about 35 minutes.  My 120 days of versioned backups for that system are currently ... 
```
# du -sh spam2
149M    spam2
```
My main desktop (actually a VM running inside KVM in a private cloud) is using:
```
$ df
Filesystem           Size  Used Avail Use% Mounted on
/dev/vda1             17G   14G  1.9G  88% /

``` for the VM itself.
and
for backups:
```
# du -sh lubuntu
8.1G    lubuntu

``` I don't backup the OS. That can be trivially re-installed in 10-15 min, so why bother?  For the desktop, looks like 60 days of incremental backups are retained.
```
root@romulus:/Backups# rdiff-backup --list-increment-sizes  lubuntu
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Jul 13 01:15:09 2017         5.84 GB           5.84 GB   (current mirror)
Wed Jul 12 01:15:08 2017         26.9 MB           5.87 GB
Tue Jul 11 01:15:10 2017         12.3 MB           5.88 GB
Mon Jul 10 01:15:10 2017         7.59 MB           5.89 GB
Sun Jul  9 01:15:10 2017         7.03 MB           5.90 GB
...
Thu May 18 01:15:08 2017         7.24 MB           6.69 GB
Wed May 17 01:15:08 2017         7.33 MB           6.70 GB
Tue May 16 01:15:09 2017         7.21 MB           6.70 GB
Mon May 15 01:15:09 2017         11.1 MB           6.72 GB

```
Romulus is the backup server.  For the email gateway and my desktop, backups took:
```
=== Time for Backups to spam2 === 
StartTime 1499926264.00 (Thu Jul 13 02:11:04 2017)
EndTime 1499926273.85 (Thu Jul 13 02:11:13 2017)
ElapsedTime 9.85 (9.85 seconds)
TotalDestinationSizeChange 864 (864 bytes)


=== Time for Backups to lubuntu === 
StartTime 1499922909.00 (Thu Jul 13 01:15:09 2017)
EndTime 1499923979.99 (Thu Jul 13 01:32:59 2017)
ElapsedTime 1070.99 (17 minutes 50.99 seconds)
TotalDestinationSizeChange 24381802 (23.3 MB)
```
last night.  I need to look into why lubuntu took so long for 23MB.  Normally, it is 2-3 minutes for the backup.

Did I mention, zero downtime for backups AND they are all consistent?

I would NOT place storage inside a VM.  Use NFS for that.  Inside the VM should be the OS, programs and settings, not huge amounts of storage for data.  From the servers you've mentioned, I don't see any heavy processing or data use requirements.  Heavy CPU and RAM loads shouldn't be inside VMs, IMHO.  VMs are an exercise is sharing resources and that isn't what heavy scientific data processing is about.

But I could be wrong.

---

### Post by totla on 2017-08-02
Hi, i have been studying on LVM, KVM/QEMU, snapshots an rdiff for couple of weeks now, and have managed to create a acceptable server setup, just couple of question now.
Would you suggest running a seperate VM as a backup server, or should i just run backups from the host machine (im doing backups from host machine now)?
Would you suggest using LVM partitionin inside VM's, or just create a LV's for each VM and do normal partitioning inside it?

---

