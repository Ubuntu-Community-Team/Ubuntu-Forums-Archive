---
title: "nfsd via udp"
date: 2007-03-06
forum: Server Platforms
---

### Post by hlynur on 2007-03-06
Does anyone know how i can force nfsd (nfs-user-server or nfs-kernel-server) to use udp not tcp without recompiling kernel and disabling CONFIG_NFSD_TCP.

cheers / Thor

---

### Post by Mr. C. on 2007-03-06
Its a mount option or an exports option.

$ man mount

MrC

---

### Post by hlynur on 2007-03-06
well no it is not an export option. You can specify it with mount but that is on the client side. What I'm looking for is a an option to the nfs-user-server so all 300+ clients or so will only use udp. I'm upgrading a file server from debian woody to ubuntu dapper.

But the nfs export is giving me a problems .. crashing or hanging 1-2 a week. Actually I've had this problem with all machines I've installed with dapper but they have been less loaded with nfs traffic so there i only had to restart (or just start) the nfs-user-server like once or every second mount.

---

### Post by Mr. C. on 2007-03-06
I'm sorry, hlynur, my mistake.  I actually meant fstab, not exports.  Man 5 nfs will give you this.

You want to disable advertising of TCP in the nfsd.  See:

man 8 nfsd

MrC.

---

### Post by Mr. C. on 2007-03-06
> **hlynur said:**
> But the nfs export is giving me a problems .. crashing or hanging 1-2 a week. Actually I've had this problem with all machines I've installed with dapper but they have been less loaded with nfs traffic so there i only had to restart (or just start) the nfs-user-server like once or every second mount.

What do your exports and fstab entries look like ?
Is this a heterogeneous client/server environment (Solaris requires a differnt rsize/wsize) ?

MrC

---

### Post by hlynur on 2007-03-06
The mount is done via autmount 

the /etc/exports on a nfsserver is typically like 

/exports *(rw,root_squash,insecure)


and then the client has in the /etc/auto.master

/home	auto.home
/net	/etc/auto.net

auto.home is then accessed from a yp nis server. 


The auto.home on the nis server then contains 

user1     -nosuid,nfs3,hard,intr  nfsserver:/export/home/user1
user2     -nosuid,nfs3,hard,intr  nfsserver:/export/home/user2


the clients typically also run an nfs export for exporting their /data which is mounted on a local hardrive. so on a client /etc/exports contains :

/data *(rw,root_squash)


This is done so you can from client1 access data on client2 with

client1$ cd /net/client2/data


Well all this works fine .. the /home is shared between 3 solaris and one old debian woddy and they all use nfs over udp. 

The clients are solaris ubuntu debian and some irix 


I’ve then installed some dapper client machines and noticed that export /net/client/data crashed like once in a month or less (never really more)  But on this new one which exports some  /home it is much worse .. chrashes like every third day (there is much more load here) 


The /etc/fstab looks typically like this:


/dev/hda2    /                 ext3    rw        0    1
none         /proc             proc    defaults  0    0
/dev/hda1    /boot             ext3    rw        0    2
/dev/hda5    /data             ext3    defaults,nodev,nosuid  0    2
/dev/hdd     /media/hdd        auto    ro,user,nodev,exec 0 0
/dev/fd0     /floppy    auto    defaults,user,nodev,nosuid,noauto 0 0
/data/swapfile    none         swap    rw        0    0


Cheers / Hlynur

---

### Post by Mr. C. on 2007-03-06
NFS crash / hang problems can be difficult.  I had a client who had the most ridiculous, unstable NFS setup ( which I was paid nicely to fix ).

You do know that you will get *much* better transfer rates and performance with solaris clients using a read/write blocksize of 32k ?

And you do know about noatime?

It is also important to tune the number of nfsd threads running.  This is critical.

Have you checked nfsstat ?  How do those stats look ?

I don't recall what version kernel / nsfd is in drapper; there were some *serious* nfs and interrupt issues (esp. on MP and/or certain RAID configurations ) for a long time; these were in the 2.4.17 and beyond kernels I think, but its been too long to recall.

MrC

---

### Post by hlynur on 2007-03-08
Yes the guy who installed it is banging is head for not installing solaris :-) .. normally
he installs solaris

I upgraded the kernel to an 2.6.17-11-server (edgy). I'm running dapper but I have to use 2.6.17 to be able to speek with the PERC 5 raid controller (DELL 2950). It hasn't given me any problems after that so I'm holdin my breath :-) ..

The previus kernel I was running was from edgy when it was still in the development phase a
nd i had CONFIG_NFS_FS compiled into the kernel .. now I load it as Module.

How do you tune the number of threads? I've been looking at man rpc.mountd and rpc.nfsd but I can't see it as an option.

my nfsstat looks like this:

Client rpc stats:
calls      retrans    authrefrsh
586        0          0
Client nfs v2:
null       getattr    setattr    root       lookup     readlink
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
read       wrcache    write      create     remove     rename
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%
link       symlink    mkdir      rmdir      readdir    fsstat
0       0% 0       0% 0       0% 0       0% 0       0% 0       0%

Client nfs v3:
null       getattr    setattr    lookup     access     readlink
0       0% 168    29% 13      2% 125    22% 96     16% 8       1%
read       write      create     mkdir      symlink    mknod
24      4% 11      1% 3       0% 0       0% 0       0% 0       0%
remove     rmdir      rename     link       readdir    readdirplus
3       0% 0       0% 3       0% 0       0% 0       0% 94     16%
fsstat     fsinfo     pathconf   commit
0       0% 19      3% 0       0% 0       0%


Thanks ..  / Hlynur

---

### Post by Mr. C. on 2007-03-08
To set the number of worker threads:

man rpc.nfsd

See the variable RPCNFSDCOUNT in /etc/init.d/nfs-kernel-server, which defaults to 8.  This is far to low for larger environments.  You may need 16, 20, or or more.  It depends on your usage, number of clients, etc.  There is a rule of thumb for working this out, but those are only approximations and benchmarking is required to tune optimally for situation. Start searching the web for tuning NFS servers.

Learn to use the NFS stat tools - they will tell you when you have too many threads, by nature of some threads essentially doing little to nothing.

Configured in the kernel, or as a module - no difference.

Your nfsstats show a) you're not using any NFS v2 (good!), and that your NFS load is fairly well spread over various operations (meaning, for example, your clients are not heavy writers, which is beneficial to your raid-5 environment.

Tune away!

MrC

---

### Post by hlynur on 2007-03-09
Ok thanks I'll try the nfs-kernel-server .. and to tune it 

the /usr/sbin/rpc.nfsd for my nfs-user-server just died again :-(

cheers / Thor

---

### Post by Mr. C. on 2007-03-09
hlynur,

I'm sorry to say, that the Linux NFS server, while good, in my experience is not yet a robust enterprise solution.  In my opinion, if reliability and performance are high on your priority list, you should look for dedicated NFS or file serving solutions.

If this is not within your budget, be prepared to spend a significant amount of time evaluating various kernel versions, and this will likely require you to build your own tuned kernels.

Best of luck,
MrC

---

### Post by jmac99 on 2007-03-11
> **hlynur said:**
> Ok thanks I'll try the nfs-kernel-server .. and to tune it 

the /usr/sbin/rpc.nfsd for my nfs-user-server just died again :-(

cheers / Thor


try disabling nfsv2 on the server.     I know it sounds
silly, but its worth trying even though nfsstat says your
not using it.   

Also worth disabling the solaris clients.  Move them
somplace else, or something.  Just till you can isolate
whats causing the hangs.

---

### Post by hlynur on 2007-03-14
\\

---

### Post by hlynur on 2007-03-14
I have not tried to disable nfs v 2 with the user-server. I'm trying the kernel-server at the moment but it is also giving me some weird behavioral. 

It hasn't crashed yet so it seems more stable than when I ran the user server. 

But when I try to access folder like 
.mozilla-thunderbird/2tp4y4v1.default/ or 
.mozilla/firefox/iii9wfwt.Default User

over NFS i get Permission denied around 50% of the time.

First I thought this was a problem with this user mail .. but now I see that every user on this server has this problem. I tried removing the folder completely and configure thunderbird again to the imap server. But same problem again. 

 Thunderbird is also affected that it can't read its index files so sometimes the mailfolders seam empty .. and click again and then you get see the mai.

I've tested this a lot with other users and other files ... but it only affects these 2 folders and subfolders. 
.mozilla-thunderbird/2tp4y4v1.default/ or 
.mozilla/firefox/iii9wfwt.Default User

I've also tried to moving these folders on a solaris nfs server .. where it gives me no problem. Also I didn't have this problem running the user-server ...


cheers Hlynur

---

### Post by Mr. C. on 2007-03-14
Disabling nfsv2 is a red herring.  It is not being used - your diagnostics show this.

The permissions issue is likely due to having different user IDs on the various systems.  Your UID/GID's must be in sync across all systems that use NFS.  Review week 4 lecture and lab:  [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by hlynur on 2007-03-14
hi hi red-hering ;-)

well I thought it was wourth the while because after I installed kernel-server it is using nfs2 

here is my nfsstat 


Server rpc stats:
calls      badcalls   badauth    badclnt    xdrcall
123619     41         1          40         0
Server nfs v2:
null       getattr    setattr    root       lookup     readlink
16      0% 2092   82% 7       0% 0       0% 387    15% 0       0%
read       wrcache    write      create     remove     rename
21      0% 0       0% 0       0% 0       0% 0       0% 0       0%
link       symlink    mkdir      rmdir      readdir    fsstat
0       0% 0       0% 0       0% 0       0% 0       0% 10      0%

Server nfs v3:
null       getattr    setattr    lookup     access     readlink
31      0% 101034 83% 407     0% 9537    7% 6999    5% 0       0%
read       write      create     mkdir      symlink    mknod
50      0% 670     0% 429     0% 120     0% 0       0% 0       0%
remove     rmdir      rename     link       readdir    readdirplus
429     0% 120     0% 167     0% 0       0% 0       0% 903     0%
fsstat     fsinfo     pathconf   commit
15      0% 8       0% 0       0% 167     0%

thanks for the link .. cheers / Hlynur

---

### Post by Mr. C. on 2007-03-14
The red-herring was trying to resolve your *previous* problems, which showed nfsv2 was not being used at all.  It therefore, would not have played a factor in your issues.

You have since changed your configuration, so my tip is no longer valid.

It sounds like you have everything under control,
MrC

---

### Post by hlynur on 2007-03-16
Well It is working now .. I had to set  no_subtree_check exports option for the nfs-kernel-server to work properly.

so in /etc/exports

/priv_1 *(rw,root_squash,no_subtree_check,insecure,sync)

cheers  / Thor

---

### Post by Mr. C. on 2007-03-16
Excellent.  Thanks for the follow up.

MrC

---

