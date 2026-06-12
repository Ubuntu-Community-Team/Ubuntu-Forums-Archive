---
title: "Partition scheme for file server."
date: 2015-11-06
forum: Server Platforms
---

### Post by gardenair on 2015-11-06
hi,
          I need guidance regarding to setup a file server it should be either NFS or Samba server. For partitioning what partition scheme should i choose ? Normally a minimum partition scheme which i think is 

```
/boot    <-----500Mb size
/swap    <------Double of Ram
/var
/
/public-share

```
Is it a correct partition scheme for a file server which will dedicated for 500 users ? The public share is a separate partition for users to keep their files over the server.  please guide me what appropriate size should I keep for "/var " partition as well ? 

What is the recommended partition scheme for a linux file server ? 

thanks
gardenair

---

### Post by darkod on 2015-11-07
If the data on it will be on separate partition (mount point), and if users won't keep any large files in /home, then you don't need to make it so complicated. You don't need separate /boot, no need to separate /var either. You can have one single / partition, and it doesn't need to be big either. A 15-16GB is more than plenty. Remember that the basic ubuntu server install is only about 2GB. With no big data on it, only for OS and config files, 16GB is plenty.

If you do make separate /boot, I suggest 2GB at least. /boot gets filled with kernels if you don't clean it regularly (and most people seem not to do it), so it can get filled up which will make apt-get not work and it also complicates the clean-up process. 2GB gives you sufficient but you need to watch the use % anyway.

If you think you might need to resize partitions or to add more disks in the future and easily join them to the data partition, you can consider LVM. In such case you might use separate /boot but it is not necessary (earlier it was because the OS could not have the boot files on LVM). LVM gives you option for easy resize of LVs and adding more storage in the future. Again, in the LVM, make only single root LV and maybe /boot outside the LVM. But no need for var LV etc...

---

### Post by SeijiSensei on 2015-11-07
By the way you can have the server provide both NFS and CIFS via Samba at the same time.

---

### Post by gardenair on 2015-11-07
For "[COLOR=#000000]SeijiSensei" [/COLOR]it is a generic question. NFS  or samba both are file server and they need separate server for each other.

[COLOR=#000000]"darkod" thanks for your kind reply. Well using samba server the users will keep only there word,excel,power point files over the server ,no large file like videos,music over the network.
[/COLOR]Why we use /boot for 2GB ? Normally for other distributions if we use Fedora,cenos in that case we need only 500MB for /boot partition.In ubuntu case why we need tooo much big space ?
As u mentioned that** "[COLOR=#000000]/boot gets filled with kernels if you don't clean it regularly"[/COLOR]**[COLOR=#000000] _what is the purpose to clean up it_. In past i have worked on fedora and I have never been clean the /boot partition. I just assign 500 Mb to it ,only make separate partition for samba server data.

In ubuntu case what u suggest ? [/COLOR]

---

### Post by SeijiSensei on 2015-11-07
> **gardenair said:**
> For SeijiSensei"it is a generic question. NFS  or samba both are file server and they need separate server for each other.
It sounded from your original request that you thought NFS or CIFS was an either/or proposition.  It's not.  You can use both nfs-kernel-server and samba on the same machine and offer the same files using both protocols.

As for partitioning, I'd also suggest just using one partition for /.  If you had a small device to boot from and a separate data device, then I'd use the latter for /home.  Users should be saving their files to /home/username. 

Ubuntu has had a persistent issue with not cleaning up /boot correctly after kernel updates.  You can use "sudo apt-get autoremove" when you update the kernel.  On a server these updates will likely be pretty infrequent.  Even autoremove doesn't always clean out stale kernels from /boot correctly though 14.04 and later seem better in this regard.  I think 500 MB is sufficient for /boot myself.

Personally I always use CentOS for servers and Ubuntu for desktops.

---

### Post by gardenair on 2015-11-07
Thanks for your kind reply. What for /var partition ? Normally in server side we keep /var separate.

---

### Post by darkod on 2015-11-07
Yes, but having separate /var helps more in mysql or web servers for example, which use by default /var as location for the DB, web files, etc. Even in these cases you can always have modified path for DB etc... So /var will not fill up much.

In your case, for a file server, /var will not be filling up at all. So there is really no benefit having separate partition/LV for it. It just complicates the partitioning layout without any benefit.

---

### Post by SeijiSensei on 2015-11-07
Unless you have really large databases, I find /var/log takes up the most space in /var, especially if you maintain a few weeks' worth of rotations like I do.  For instance,

```

# cd /var
# du -sh *
4.0K    account
67M     cache
4.0K    crash
16K     db
8.0K    empty
4.0K    games
**3.1G    lib**
4.0K    local
8.0K    lock
**12G     log**
0       mail
864K    named
4.0K    nis
4.0K    opt
4.0K    preserve
168K    run
50M     spool
4.0K    tmp
1.6M    www
4.0K    yp

```
I have both MySQL and PostgreSQL databases on this machine.  The first is for WordPress, and the second is for the sites I build myself.  In my case most of that 3 GB belongs to a large PG database that contains all the postings for a bunch of listservers so they can be indexed with [Sphinx]("http://sphinxsearch.com/").

---

