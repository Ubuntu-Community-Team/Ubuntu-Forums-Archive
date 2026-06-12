---
title: "Strange network problems on a E250"
date: 2006-08-30
forum: Sun Sparc Users
---

### Post by Mr.Vanman on 2006-08-30
Hello,

    I'm new to ubuntu as a server so I'm sure I'm missing something here, (although I can't find the answer in forums) but I am experiencing strange networking issues.

     First off, I have a static IP set in <i>interfaces</i> with the proper gateway,netmask, etc.  I can ping other devices on my network with no problem, and I can ping IPs on the net, but I cannot seem to ssh to other known (and pingable) servers.  I also can't seem to look up dns (yes, I have working servers defined in <i>resolv.conf</i>) or indeed make any other types of connections. apt-get update cannot connect to any servers because of the lookup problems.

      I have also installed openssh server using apt-get from the cd, started the server and verified that I can connect via the local console.  From a remote machine I see that ssh is open, yet when I try to connect it times out.

    This is driving me nuts... I assume selinux in not in ubuntu? Are there default firewall rules in place I'm not aware of?? ](*,) 

Help!

Thanks,

-Van

---

### Post by xor007 on 2006-08-30
First make sure the hostname of the local machine is consitent. Do u see anything funny while running the `hostname` command? What is funny is that ssh times-out. It should connect after about 30 seconds. Have you installed any portmap services (NIS, NFS) and using NIS maybe as a name resolver? You have to track how name resolving works on your PC. I agree with you it is name resolving issue. Unfortunately my Linux networking is more RedHat and SuSE.

---

### Post by Mr.Vanman on 2006-08-30
Thanks for the reply, hostname returns normally and I didn't do any NIS/NFS configuration, unless that stuff is installed by default.  The strange thing is that I can ping the NS servers without a problem, and can even telnet to port 53 of them, yet lookups don't work.... ugh

---

### Post by Mr.Vanman on 2006-08-31
More information:  I can connect to an ftp host, but after entering my username is freezes - never asks for pass.

I can ping all devices on my network and net, including all gateways and dns servers.  From a remote machine all services appear up but just hang when connecting.  Netstat shows a connection established from the remote host just the same.  wth is going on?

:-({|= 

Any help would be appreciated..

---

### Post by Mr.Vanman on 2006-08-31
> **Mr.Vanman said:**
> More information:  I can connect to an ftp host, but after entering my username is freezes - never asks for pass.

I can ping all devices on my network and net, including all gateways and dns servers.  From a remote machine all services appear up but just hang when connecting.  Netstat shows a connection established from the remote host just the same.  wth is going on?


Any help would be appreciated..


I have solved it myself.  Apparently there ARE some firewall rules active on the default server install.  I used apt-get install shorewall and once shorewall was installed, shorewall clear did the trick.  \\:D/

---

