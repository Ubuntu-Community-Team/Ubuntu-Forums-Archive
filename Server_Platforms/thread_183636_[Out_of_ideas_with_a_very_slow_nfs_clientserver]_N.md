---
title: "[Out of ideas with a very slow nfs client/server] Needs expert !!"
date: 2006-05-28
forum: Server Platforms
---

### Post by patrick295767 on 2006-05-28
SOO, since long time, this slow nfs occurs with my breezy boxes: 
  
I am out of ideas... It's 2 days now ... and absolutely no way ! 
I need help of an expert ! :-)
  
My server 192.168.123.100 config   :
===========
at the startup I mount the folder in /home
this is working greatly !!
with in rc2.d : mount IP:/mnt/hda5/home    ; 
/etc/fstab:
> 
192.168.123.100:/mnt/hda5/home  /home   nfs     hard,rsize=8192,wsize=8192,timeo=14,sync,nolock,intr    0   0
  
/etc/hosts.allow:
> 
portmap: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103




lockd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103
rquotad: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103
mountd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103
statd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103
nfs: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103
nfsd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103



 
/etc/hosts.deny:
> 
portmap:ALL

lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
nfs:ALL

   
my rpcinfo:
> 
  program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    679  status
    100024    1   tcp    682  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32772  nlockmgr
    100021    3   udp  32772  nlockmgr
    100021    4   udp  32772  nlockmgr
    100021    1   tcp  32769  nlockmgr
    100021    3   tcp  32769  nlockmgr
    100021    4   tcp  32769  nlockmgr
    100005    1   udp    823  mountd
    100005    1   tcp    826  mountd
    100005    2   udp    823  mountd
    100005    2   tcp    826  mountd
    100005    3   udp    823  mountd
    100005    3   tcp    826  mountd


  
nfs pkg installed: 
> dpkg -l | grep nfs
ii  libnfsidmap1                           0.8-1                                An nfs idmapping library
ii  nfs-common                             1.0.7-3ubuntu1                       NFS support files common to client and serve
ii  nfs-kernel-server                      1.0.7-3ubuntu1                       Kernel NFS server support
rc  nfs-user-server                        2.2beta47-20                         User space NFS server

   
mount nfo: $mount
> /dev/hda5 on /mnt/hda5 type ext3 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
192.168.123.100:/mnt/hda5/home on /home type nfs (rw,sync,hard,rsize=8192,wsize=8192,timeo=14,nolock,intr,addr=192.168.123.100)


/etc/auto.master:
> cat /etc/auto.master
#
# $Id: auto.master,v 1.3 2003/09/29 08:22:35 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/misc  /etc/auto.misc
#/net   /etc/auto.net

My Client 192.168.123.101 config :
==========
 /etc/fstab
> 192.168.123.100:/mnt/hda5/home  /home   nfs     hard,nolock,rsize=8192,wsize=8192,timeo=14,intr 0       0
  
/etc/hosts.allow
> portmap: 192.168.123.100 , 192.168.123.101 , 192.168.123.102



lockd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103 , 192.168.123.104 , 192.168.123.105
rquotad: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103 , 192.168.123.104 , 192.168.123.105
mountd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103 , 192.168.123.104 , 192.168.123.105
statd: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103 , 192.168.123.104 , 192.168.123.105

nfs: 192.168.123.100 , 192.168.123.101 , 192.168.123.102 , 192.168.123.103 , 192.168.123.104 , 192.168.123.105



  
rpcinfo -p
> winwood@laptop06:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    691  status
    100024    1   tcp    694  status
    100005    1   udp    690  mountd
    100005    1   tcp    693  mountd
    100005    2   udp    690  mountd
    100005    2   tcp    693  mountd
    100005    3   udp    690  mountd
    100005    3   tcp    693  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32768  nlockmgr
    100021    3   udp  32768  nlockmgr
    100021    4   udp  32768  nlockmgr
    100021    1   tcp  32769  nlockmgr
    100021    3   tcp  32769  nlockmgr
    100021    4   tcp  32769  nlockmgr

  
/etc/hosts.deny
> 
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

portmap:ALL

lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

  
My nfs-installed pkg: 
> winwood@laptop06:~$ cat /etc/autonfs.master
cat: /etc/autonfs.master: No such file or directory
winwood@laptop06:~$ dpkg -l |grep nfs
ii  libnfsidmap1                           0.8-1                                An nfs idmapping library
ii  nfs-common                             1.0.7-3ubuntu1                       NFS support files common to client and serve
ii  nfs-kernel-server                      1.0.7-3ubuntu1                       Kernel NFS server support
winwood@laptop06:~$ mount --vers
mount: mount-2.12p
winwood@laptop06:~$

  
I need help :-( 
I would like to have this linux server working ... 
  
Thank you very much !!

---

### Post by cvmiller on 2006-05-29
What is slow about the NFS client/server relationship? For example, is the mount slow? The mount is fast, but the data transfers are slow? 

I was having a problem with slow mount (by client) with dapper drake, Turned out I needed to run portmapper on the client machine, then mounts were almost instantaneous.

I hope this helps,

Craig...

---

### Post by patrick295767 on 2006-05-30
Thank you first for your intentions for helping !!
  
Soo, the mounting is rather ok (15sec) (for me less important)
  
Data sharing is very very slow !
about 2 minutes to open one files, the /home/user session hangs.... 
cos amazingly slow data nfs sharing from server  
  
//
portmap: 
I did on both machines client & server : 
> apt-get -f -y install portmap

---

### Post by patrick295767 on 2006-05-31
bump

---

### Post by joshrobinson on 2006-05-31
[QUOTE=patrick295767]Someone has any ideas maybe ?? 
  
I still stuck with it ... :-(

Thank you !![/QUOTE]

i got your pm. sorry i cant be of any help.. i used my linux server using samba, because a few windows computers would also connect to it

but i thought i would reply here and give your thread a bump while i was at it.. at least i can help you out with a bump :-D

---

### Post by patrick295767 on 2006-05-31
[QUOTE=joshrobinson]i got your pm. sorry i cant be of any help.. i used my linux server using samba, because a few windows computers would also connect to it

but i thought i would reply here and give your thread a bump while i was at it.. at least i can help you out with a bump :-D[/QUOTE]
  
Thank you joshrobinson !
I'll try again a bit more this evening to see what can be done !
  
Ahhh if Linus Torvald was there sometimes !! :-) 
  
Sunny Greetings !!

---

### Post by patrick295767 on 2006-06-11
I think I have found the problem 

1/I read that server/client non identical  FULL / HALF duplex can be the reason ??

2/ that I have to measure my ethernet line 
when i did : 

ping -s 8192 192.168.123.100   
(server)
i get no bytes !! nothing
 
 ping -s 256 192.168.123.100   
i get 1ms

 ping -s 48 192.168.123.100   
i get 0.48ms
  
What should I do ??

 Thank you for you help

---

### Post by patrick295767 on 2006-08-04
Ohhh, 
I forgot to say. I solved it since long time. 
Everything works fine, this thread can be then an how to.
 
The crazy thing came from a HUB and 1 cable. I could ping, but but all sharing type connections were really bad. 
 
I removed the old HUB (robotics) and this old ethernet cable, and everthg is workign ddddamn fast for all the connected computer. 
Go to explain this ?

It works !!

---

### Post by acope on 2006-09-01
Hi,

I had a very slow mounting NFS and very, very slow access. 

Thanks to cvmiller for the portmapper suggestion, that solved it instantly.
:D 

Cheers
Andrew

---

### Post by acope on 2006-09-05
As a follow up, I also had to install the nfs-common package to avoid tons of these in /var/log/messages :

Sep  4 08:08:43 localhost kernel: [17416462.068000] lockd: cannot monitor 192.168.0.5
Sep  4 08:08:43 localhost kernel: [17416462.068000] lockd: failed to monitor 192.168.0.5

Cheers
Andrew
-- 
DIRECTOR
Evergreen Computing Ltd
Websites - Excellent Quality, Excellent Value

Email:    [email]andrew@evergreencomputing.com[/email]
Website:  [http://evergreencomputing.com](http://evergreencomputing.com)
Phone:    +44 (0)1454 269 087 
Fax:      +44 (0)8707 515 596

---

### Post by patrick295767 on 2006-12-16
> **acope said:**
> As a follow up, I also had to install the nfs-common package to avoid tons of these in /var/log/messages :

Sep  4 08:08:43 localhost kernel: [17416462.068000] lockd: cannot monitor 192.168.0.5
Sep  4 08:08:43 localhost kernel: [17416462.068000] lockd: failed to monitor 192.168.0.5

Cheers
Andrew
-- 
DIRECTOR
Evergreen Computing Ltd
Websites - Excellent Quality, Excellent Value

Email:    [email]andrew@evergreencomputing.com[/email]
Website:  [http://evergreencomputing.com](http://evergreencomputing.com)
Phone:    +44 (0)1454 269 087 
Fax:      +44 (0)8707 515 596


The portmap is very needed indeed. 
and you can use my config above. It is working very very well ( of course with portmap )

Enjoy NFS

---

