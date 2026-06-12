---
title: "NFS4 server deployment and tuning up"
date: 2011-08-31
forum: Server Platforms
---

### Post by monkeyMonk on 2011-08-31
Hello,
  Recently I had reconstructed my home computer network, I have about 20 computers/devices connected to my home network, including 12 Desktop/laptops, most of them running Ubuntu and few Windows; Also I have iPhones, iPads, appleTV and HP touchPad recently joined in the network. Since there are more and more devices added into the network, I thought it will be good to tuning up the network for better performance. One of those efforts is tuning up the server deployed on Ubuntu platform. 

  In this tread, I like to bring up a discussion on the NFS version 4 server deployment on Ubuntu. I like to have this opportunity to practice and learning. I wish that all we have fun here.

  I have one of NFS sever set up on an Ubuntu 10.04 platform, the clients all running Ubuntu 11.04.  I had searched on the Internet and the forum, there are two references that help me in the first. They are:
[INDENT][https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)   and
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
[/INDENT]  They are good help in the first place, however, still there many necessary details are missing. I would like peoples can post good references here, so we will be able to put all useful together.

  Thanks in advance for everyone contributing.

---

### Post by monkeyMonk on 2011-08-31
The default NFS server  start/stop script is 
```
 /etc/init.d/nfs-kernel-serve 
```The default parameter will be in 
```
 /etc/default/nfs-kernel-server 
```The out of box  NFS server script will staring NFSD daemon to support NFS server on version 2,3,4 simultaneously, which by my opinion is over killing, waist resource and increasing security risk. 

Since I don't have any NFS client has to running early NFS version, my first tuning up effort is to turn off NFSD on version 2 and 3. Check ```
man rpc.nfsd
```  for more details. What needed is to pass 
  " -N  or  --no-nfs-version version_number" when execute "rpc.nfsd".

The hack could be like this,
```
  sudo nano /etc/init.d/nfs-kernel-server
```Find the part of 
```
                log_daemon_msg "Starting $DESC"
                log_progress_msg "nfsd"
                start-stop-daemon --start --oknodo --quiet \
                    --nicelevel $RPCNFSDPRIORITY \
                    --exec $PREFIX/sbin/rpc.nfsd --  $RPCNFSDCOUNT
                RET=$?
```change it to be 
```
                log_daemon_msg "Starting $DESC"
                log_progress_msg "nfsd"
                start-stop-daemon --start --oknodo --quiet \
                    --nicelevel $RPCNFSDPRIORITY \
                    --exec $PREFIX/sbin/rpc.nfsd -- [COLOR=Red] -N 2 -N 3[/COLOR]  $RPCNFSDCOUNT
                RET=$?
```Of course, this is a hack, a better change could be introduce a new parameter into ```
 /etc/default/nfs-kernel-server 
``` and use it in ```
 /etc/init.d/nfs-kernel-serve 
```.

---

### Post by monkeyMonk on 2011-09-01
It is an interesting question to the relationship between RPC and NFS version 4.

As early version of NFS until version 3, NFS largely relies on RPC functions to complete the interactive between the server and client.  Many PRC protocols be called as NFS side protocol.  However, for NFS version 4, many functions originally been defined in RPCs have been included into NFS main body directly, and the NFS v4 has the default port on 2049, which makes NFS not necessary to rely on portmapper to provide initial information.  The other side protocols have been merged into NFS version 4 main body were rpc.mountd and rpc.lockd.  I had read from somewhere said that on NFS version 4, rpc.mountd does not involve any interactive over the wire, and rpc.lockd to be removed from newer Linux distribution.  

On Ubuntu 10.04 and 11.04, I observed that individual rpc.lockd program has been removed, and a kernel thread named "nlockmgr" (NFS Lock Manager) has been started when rpc.nfsd has been invoked. This is OK, but I confused on this, from ```
rpcinfo -p
```, it indicated that "nlockmgr" listens on a TCP port and a UDP port, and support version 1,3,and 4. The related part shows as below, 
 
```
    100021    1   udp  54702  nlockmgr
    100021    3   udp  54702  nlockmgr
    100021    4   udp  54702  nlockmgr
    100021    1   tcp  55273  nlockmgr
    100021    3   tcp  55273  nlockmgr
    100021    4   tcp  55273  nlockmgr
```I don't know what versions the nlockmgr here means, if it is equivalent to NFS version, then I have no idea how come the version 1 , since the NFS package on Linux has no NFS version 1 supported on nfsd. 

The another interesting RPC prpgram is " rpc.mountd " .  The " man rpc.mountd"  says it support NFS version 2 and 3, there no mention to NFS version 4. Theoretically NFS version 4 has handle the mount interactive in the nfsd4 main body, there no need for rpc.mountd to be involved when NFS version 4 sever <-> client interactive. However, if remove " rpc.mountd"  from script of "/etc/init.d/nfs-kernel-server", the NFS v4 client would be failed or hanging on the mount request. The interesting thing is, as long as the server side has a rpc.mound daemon started, no matter what options to give either ```
sudo  rpc.mountd  --no-nfs-version 3
``` or ```
sudo  rpc.mountd   -no-nfs-version 2
```, the NFS 4 client would be able go through the mount request onto NFS server exported. 

The new RPC introduced into NFS version 4 is " rpc.idmapd" , from ```
ps -eaf | grep idmap
``` , I can see it runs by root, however, ```
rpcinfo -p
``` has nothing reveal about rpc.idmap.  

Anyone can provide references to address these questions? I will be interested to know. :p

---

### Post by monkeyMonk on 2011-09-05
Anyone could provide comments or links to discussion of the relationship between  NFSv4 and RPC ?

I'm be very interested to this.

By my limited knowledge, many of functions that defined in RPC had been included in NFSv4 main body. So as result, NFSv4 will possible to work properly without RPC. 
I had tested the case on deploying NFSv4, the NFSv4 server and NFSv4 client worked properly when I turned off rpc.portmapper.  Of course, the RPCs would be useful in diagnostic/analysis NFS problem, though, as matter of security concern, unnecessary used ports should be closed.

---

