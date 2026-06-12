---
title: "NFS server very slow"
date: 2009-07-01
forum: Server Platforms
---

### Post by ymai on 2009-07-01
Hello all

My server: Ubuntu 8.04 / 100 Mbits/s Ethernet / 240GB Sata HD / NFS server for the users of the workstations
The workstations in my classroom: 20 brand new mixed Ubuntu 8.10 / 9.04 Dual Core 100 Mbits/s LDAP authentification 
I have more than 1000 possible users (all the students of the school). Their files (and .profiles) are saved on the NFS server. They can work from any workstation in the school with their personnal username and pwd.

My problem:
A standalone workstation with local authenfication and local user files works perfectly good, fully reactive.
The problem arises when 10 -> 20 users log at the begin of a lesson on the LDAP/NFS server.
The server's HD works continuously, sometimes more than one hour; the workstations are very, very slow: totally unusable, sometimes freezing during about 2 minutes. After one hour hyper-activity of the server's HD (and revolution among the students), the users get progressively normal service of their workstations. All their files are normally accessible on the NFS server.

The "top" command just show a few % CPU activity on the server.
The Desktop Visual Effects have been disabled on the workstations.
Tracker has been disabled on the workstations (I read on this forum that Beagle could be problematic).

The server software was renewed in december 2008. Ubuntu 8.04 took the place of an old Fedora 5 distribution. Old PIV 382 Mo RAM workstations were replaced by the DualCore stations.
Nothing has been changed on the network.
Before the renewal, I've never noticed that slowness problem.

My questions:
1. Do someone here successfully use a similar configuration ?
2. What can I still do to make the workstations usable in september, when the students come back (our present "solution" is to use local users on the stations with a "on-demand" Samba connexion to the NFS server).

Any answer really appreciated.

---

### Post by trundlenut on 2009-07-02
could this be a problem with the network, you say that the server has a 100mbit connection, how is it connected to the workstations?  Could it be a problem with suddenly trying to supply all the students profile information at the same time and there being some kind of bottleneck in the network?

---

### Post by netztier on 2009-07-02
> **ymai said:**
> 

240GB Sata HD 


Single harddisk? a RAID-1 (mirror) might help quite a bit to increase total throughput here, so that simultaneous access (resulting in more or lesse random reads) can be distributed to different disks.

> 
NFS server for the users of the workstations


That's "NFS mounted home directories", right?

> 
The problem arises when 10 -> 20 users log at the begin of a lesson on the LDAP/NFS server.


Well, during logon, a good many files of a user's homedir are read  - which can bring considerable load on the server, because a lot of the files are small.

> 
The "top" command just show a few % CPU activity on the server.


A good tool is saidar, install it on the server, it shows you CPU, Network and I/O activity in a terminal window.

> 
2. What can I still do to make the workstations usable in september, when the students come back (our present "solution" is to use local users on the stations with a "on-demand" Samba connexion to the NFS server).


Just for the sake of saneness, check that your 100Mbps Ethernet performs well. Use iPerf to measure raw TCP throughput between a number of workstations and the server; a single, exclusive connection between one workstation and the server should deliver 10-11MByte/s of througput at least, in either direction.

Worth considering: 1Gbps connection for the server; PCIe Gbit NICs are affordable nowadays, and chances to find a LAN switch with a number of 100Mbps and a few Gbit ports shouldn't be that bad either.

regards

Marc

---

### Post by ymai on 2009-07-04
Hello trundlenut
Thanks for answering
> **trundlenut said:**
> could this be a problem with the network, you say that the server has a 100mbit connection, how is it connected to the workstations?  Could it be a problem with suddenly trying to supply all the students profile information at the same time and there being some kind of bottleneck in the network?

The server is connected through a 100 Mbits/s Switch.
Till december 2008, I had to use a 100 Mbits/s Hub. Without any problem.

The bottleneck lays in the server, not in the network...
Huge file transfers through the network give good results -after the slow time.
As the HD works really hard during all the slow time, I guess the problem must lay in the NFS server.
I even think *the* problem is the huge .mozilla directory. One trial was to ask all users to log in without launching Firefox.
No extraordinary slowlyness was noticed.

Each user has (say) a 50 MB .mozilla . 
With 20 users coming all together, I'll have a 1 GB demand on the server.
$ atop
shows that my HD sometimes gives up to 18 MB/s. For 1 GB, that's around 1 minute hard work for the server. Isn't it?

Do you confirm you use (or know about) a similar configuration without any problem?

---

### Post by ymai on 2009-07-04
Hello netztier
> **netztier said:**
> Single harddisk? a RAID-1 (mirror) might help quite a bit to increase total throughput here, so that simultaneous access (resulting in more or lesse random reads) can be distributed to different disks.
Do you really mean my server is really under-powered? :o(
Maybe it's true... But I can't figure how the same server worked just fine with that old Fedora 5 and a faulty HD (strange noises were heard). The HD has been changed.
> **netztier said:**
> 
That's "NFS mounted home directories", right?

yes
> **netztier said:**
> 
Well, during logon, a good many files of a user's homedir are read  - which can bring considerable load on the server, because a lot of the files are small.

A good tool is saidar, install it on the server, it shows you CPU, Network and I/O activity in a terminal window.

Just for the sake of saneness, check that your 100Mbps Ethernet performs well. Use iPerf to measure raw TCP throughput between a number of workstations and the server; a single, exclusive connection between one workstation and the server should deliver 10-11MByte/s of througput at least, in either direction.

I didn't know those tools. I'll give a try as soon as possible. Unfortunately not in the next (holly)days.

Many thanks for your advices.

---

