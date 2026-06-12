---
title: "NFS and OpenLDAP guidance"
date: 2011-12-05
forum: Server Platforms
---

### Post by brianmills on 2011-12-05
BACKGROUND: Hi, I'm in the process of trying to teach myself Ubuntu  (particularly in the server space). I've been a long time Windows guy,  but felt it was time to widen my experience. I've been fideling with  various aspects of Ubuntu Server (and desktop) and really like it. But  I've just ventured into trying to run multiple servers and that's where I  think I'm missing something. This is my first Ubuntu Forum post, so  feel free to point out the obvious thing I've missed, I wont be  offended. 

ENVIRONMENT: My current main issue is NFS sharing. I  have a server running Virtual Box (I run Windows Guests too).  Essentially I'm trying everything on Virtual hosts before I apply  anything to the physical host. I'm running it all on a i7 desktop (or  two) with 16GB RAM and a Raid 5 MDADM array. 

ISSUE 1: I was  trying to work out how to setup NFS server and mount's but I can't see  the exports from the client, it just times out. I can however see the  exports I setup on the physical host. I can't for the life of me work  out what's missing on the virtual server compared to the physical  server. I can ping the server from the client, but "shomount -e  [server]" or rpcinfo -p [server] just timeout after 60 seconds or so. 

ISSUE 2: I also dont get how file permissions in an NFS mounted directory will work. 
(Currently  I have not hooked up Kerberos, or OpenLDAP to NFS, as my NFS shares  will really only be exported to other servers, most clients are  Windows/Mac and can use the SAMBA system which I will hook up to  OpenLDAP). 
If Client Server A has a big data directory that an  application uses, will it be able to write files to the NFS mounted  directory with correct permissions for the local users? When I tried to  rsync -av the files onto the NFS mount, I recieved some error's and the  file user/group information was lost (sorry, dont remeber the error, I'm  at work now). 

- So, what could be blocking my NFS exports from VM to VM? (UFW is not active)
- And what should I do about permissions for my NFS exports?
-  I started using 11.04, but I've since noticed a few comments around  suggesting I should probably stick with 10.04 LTS, not least of which is  that LDAP change significantly in 11.04. Should I go back to 10.04, or  not worry about it. 
- Is it worth using Zentyal to get up and  running quickly with LDAP and samba shares, and PDC? It seemed very easy  to get Zentyal up and running, but I lost the LDAP attribute "mail"  when I had a quick go, however when I have done it manually, I dont get  how all the parts fit togeather to provide end to end auth, and are  having trouble finding a site that does more than a step by step how to  with any decent explanation of the parts (as I'd like to understand it,  not just get it working). 

Any help and guideance would be appreciated.

---

### Post by 2F4U on 2011-12-06
Did you try setting the network adapter in the VM in bridge mode?

[http://ubuntuforums.org/showthread.php?t=1180823](http://ubuntuforums.org/showthread.php?t=1180823)

With respect to the question of 10.04 vs. 11.04, this is mostly a question of your personal preferences. My server runs on 10.04 since that is the LTS version. My server has to be stable and reliable and I don't need the latest bits of software. I would always recommend running a LTS release on a server. The only exception maybe if you really need newer software and if that newer software is not available on the older release.

---

### Post by brianmills on 2011-12-06
Yes. I run all the adapters in bridge mode, as I'm running some services the client PC's use on Virtual Box VM's. I can also ping from each side. 

I've now also tried viewing the mount's using "showmount -e [serverip]" from a client linux server on another physical host (which can also ping the IP and DNS entry for the server). 

Could IP Tables be blocking by default? or something not configured properly in AppArmor? (I've not looked into either of these much, I tend to use ufw when I want to turn on the firewall so far). 

Any other thoughts?

---

### Post by brianmills on 2011-12-06
From the local machine (NFS server that is) I get these results:

$ showmount -e 10.1.1.36
Export list for pdc.example.net:
/export/test 10.1.1.0/24

And 

~$ rpcinfo -p 10.1.1.36
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  39133  status
    100024    1   tcp  46235  status
    100021    1   udp  33856  nlockmgr
    100021    3   udp  33856  nlockmgr
    100021    4   udp  33856  nlockmgr
    100021    1   tcp  41799  nlockmgr
    100021    3   tcp  41799  nlockmgr
    100021    4   tcp  41799  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  39094  mountd
    100005    1   tcp  33744  mountd
    100005    2   udp  39094  mountd
    100005    2   tcp  33744  mountd
    100005    3   udp  39094  mountd
    100005    3   tcp  33744  mountd
    100011    1   udp    948  rquotad
    100011    2   udp    948  rquotad
    100011    1   tcp    949  rquotad
    100011    2   tcp    949  rquotad

Which seems to cover what it needs to.

---

### Post by brianmills on 2011-12-06
Ok. I worked out why I could not see them remotly, Fatal error between the keyboard and the chair. As suspected at some point I had enabled the port filter/firewall without realising it. 

I'm just left wondering about the permissions on NFS mounted directories, and how that all fits togeather. 

AND what do people think about using Zentyal/eBox to get a PDC up and running for CIFS shares? (It seemed webmin has fallen out of favor for what ever reason I'm not sure).

---

### Post by brianmills on 2011-12-06
So I have more detail. When I copy files from one machine to the other (which have root as the user/group) I end up with the uid/gui 4294967294. Which sounds like the nobody user I've seen mentioned. 

I do have the nfs exopor option no_root_squash which I would have thought would have prevented this from occuring. 

Any ideas?

---

