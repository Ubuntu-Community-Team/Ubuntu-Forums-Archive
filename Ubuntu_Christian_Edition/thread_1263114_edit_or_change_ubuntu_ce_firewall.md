---
title: "edit or change ubuntu_ce_firewall?"
date: 2009-09-10
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2009-09-10
Ok, I have not been able to mount my nfs on this box since I installed Ubuntu-ce.  Today I started digging through everything, are removed tinyproxy, and DG, well, tried to.  I ran into an error. ```

sudo apt-get purge -f dansguardian dansguardian-gui 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dansguardian is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libtre4 python-ogg python-cddb libfltk1.1 python-pyvorbis python-gamin
  streamripper python-pyogg python-gpod libmpeg3-1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 227484 files and directories currently installed.)
Removing dansguardian-gui ...
[COLOR="Red"]update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)[/COLOR]
dpkg: error processing dansguardian-gui (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I did that, I noticed the  line I marked in red.  When I stopped that process (the ubuntu_ce_firewall) I was able to mount my nfs shared files!  
According to this post:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
ports 32771, 111 and 2049 should be left open for access to the NFS stuff.  I'm not sure how to do that with ubuntu_ce_firewall.  Any ideas?  I can just re-install ubuntu-ce and the tinyproxy and DG if I'm able to work with my NFS.  Any thoughts or ideas on this would be appreciated.

Shane

---

### Post by david_kt on 2009-09-10
> **shane2peru said:**
> Ok, I have not been able to mount my nfs on this box since I installed Ubuntu-ce.  Today I started digging through everything, are removed tinyproxy, and DG, well, tried to.  I ran into an error. ```

sudo apt-get purge -f dansguardian dansguardian-gui 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dansguardian is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libtre4 python-ogg python-cddb libfltk1.1 python-pyvorbis python-gamin
  streamripper python-pyogg python-gpod libmpeg3-1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 227484 files and directories currently installed.)
Removing dansguardian-gui ...
[COLOR="Red"]update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)[/COLOR]
dpkg: error processing dansguardian-gui (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I did that, I noticed the  line I marked in red.  When I stopped that process (the ubuntu_ce_firewall) I was able to mount my nfs shared files!  
According to this post:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
ports 32771, 111 and 2049 should be left open for access to the NFS stuff.  I'm not sure how to do that with ubuntu_ce_firewall.  Any ideas?  I can just re-install ubuntu-ce and the tinyproxy and DG if I'm able to work with my NFS.  Any thoughts or ideas on this would be appreciated.

Shane

Thank you for your feedback. I will update ubuntu ce firewall shortly.

DK

---

### Post by david_kt on 2009-09-10
Please try attached deb package. If it is ok, I will update the repository.

DK

---

### Post by shane2peru on 2009-09-10
> **david_kt said:**
> Please try attached deb package. If it is ok, I will update the repository.

DK

Installation went fine.  I started DG, and Firefox wouldn't connect to any sites.  It could be a setting or something, I'm not that good with DG.  I'm not even sure I had it enabled before.  I use OpenDNS more so.  Perhaps I will mess around with it later.  It didn't disconnect my NFS connection.  I will see later if I'm still able to connect later.  I noticed it did start the firewall thing back up, so seems as though it is fixed, but I will let you know.

Shane

---

### Post by david_kt on 2009-09-10
> **shane2peru said:**
> Installation went fine.  I started DG, and Firefox wouldn't connect to any sites.  It could be a setting or something, I'm not that good with DG.  I'm not even sure I had it enabled before.  I use OpenDNS more so.  Perhaps I will mess around with it later.  It didn't disconnect my NFS connection.  I will see later if I'm still able to connect later.  I noticed it did start the firewall thing back up, so seems as though it is fixed, but I will let you know.

Shane

Launch dansguardian gui and make sure on top of the windows bar the status is all on, or all off.

If it could not connect to internet, try to stop dansguardian using dansguardian gui, just to test. But I thought it should not be a problem with OpenDNS.

DK

---

### Post by shane2peru on 2009-09-11
Right, it is all off now.  I think I didn't turn on the tinyproxy thing.  At any rate, back to the original problem.  I unmounted and tried to re-mount the NFS share, and it didn't work.  When I disabled the ubuntu_ce_firewall and tried to mount again, I was able to mount.  So I can confirm that the ubuntu_ce_firewall doesn't allow me to mount NFS.  FYI.  

Shane

---

### Post by david_kt on 2009-09-11
> **shane2peru said:**
> Right, it is all off now.  I think I didn't turn on the tinyproxy thing.  At any rate, back to the original problem.  I unmounted and tried to re-mount the NFS share, and it didn't work.  When I disabled the ubuntu_ce_firewall and tried to mount again, I was able to mount.  So I can confirm that the ubuntu_ce_firewall doesn't allow me to mount NFS.  FYI.  

Shane

You should change the status of dansguardian or firewall to make the new setting in effect (or simply restart the computer).

So, try enable ubuntu_ce_firewall, may be it is ok now. If still not ok, please give me the output of:

```
cat /etc/init.d/ubuntu_ce_firewall
```

DK

---

### Post by david_kt on 2009-09-11
Please also give me the out put of:

```
/etc/sysconfig/nfs
```

on your NSF server.

DK

---

### Post by shane2peru on 2009-09-12
Ok, here are the outputs:
```

cat /etc/init.d/ubuntu_ce_firewall 
#!/bin/bash
### BEGIN INIT INFO
# Provides:          ubuntu_ce_firewall
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall
# Description:       Start, stop or reload firewall.
### END INIT INFO

set -e

case "$1" in
  start)
    echo -e "\nStarting Ubuntu CE firewall .....\n"
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -t nat -F
/sbin/iptables -t nat -X
/sbin/iptables -t mangle -F
/sbin/iptables -t mangle -X
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT
# Open ports for NSF start
/sbin/iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
# Open ports for NSF end
/sbin/iptables -A INPUT -p icmp -j ACCEPT
/sbin/iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
/sbin/iptables -A INPUT -d 224.0.0.1 -j DROP
/sbin/iptables -A INPUT -j LOG
/sbin/iptables -A INPUT -j REJECT
	;;

  stop)
   echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"
	/sbin/iptables -F
	/sbin/iptables -X
	/sbin/iptables -t nat -F
	/sbin/iptables -t nat -X
	/sbin/iptables -t mangle -F
	/sbin/iptables -t mangle -X
	/sbin/iptables -P INPUT ACCEPT
	/sbin/iptables -P FORWARD ACCEPT
	/sbin/iptables -P OUTPUT ACCEPT
	;;

  status)
        /sbin/iptables -L
	;;

  restart|force-reload)
	$0 stop
	$0 start
;;
  *)
        echo "Usage: /etc/init.d/ubuntu_ce_firewall {start|stop|restart|force-reload|status}"
        exit 1
	;;
esac

```

And the other, I don't seem to have a /etc/sysconfig folder at all.  I located nfs, but there was a bunch of them, and nothing really close.  At any rate, I know it is the firewall, if I run ```
sudo /etc/init.d/ubuntu_ce_firewall stop
```  it flushes the ip tables, and I'm able to mount my nfs from my laptop to this computer.  If I run ```
sudo /etc/init.d/ubuntu_ce_firewall start
``` I cannot mount my nfs shared folder from the laptop to this computer.  To try and clarify, my Shared folder is on this computer and I have 2 others that connect to this, and neither can connect with the ubuntu_ce_firewall running.  I also have UFW running and installed GUFW to mess with it, it has a graphical way of allowing nfs shares.  When I run it, and set up my nfs shares, everything connects good.  If UFW, or GUFW cannot be implemented as a substitute, perhaps it would be helpful in setting things up?  Just a thought.  We must be on opposite ends of the world or time zones. :)  No prob though.

Shane

---

### Post by david_kt on 2009-09-12
What is the output of:

```
rpcinfo -p
```

DK

---

### Post by shane2peru on 2009-09-12
> **david_kt said:**
> What is the output of:

```
rpcinfo -p
```

DK

Here it is:
```

 program vers proto   port
    100000    2   tcp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  37918  nlockmgr
    100021    3   udp  37918  nlockmgr
    100021    4   udp  37918  nlockmgr
    100021    1   tcp  36079  nlockmgr
    100021    3   tcp  36079  nlockmgr
    100021    4   tcp  36079  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  43746  mountd
    100005    1   tcp  54702  mountd
    100005    2   udp  43746  mountd
    100005    2   tcp  54702  mountd
    100005    3   udp  43746  mountd
    100005    3   tcp  54702  mountd
    100000    2   udp    111  portmapper
    100024    1   udp  45821  status
    100024    1   tcp  50234  status

```
Hope you can make some sense of this ;)

Shane

---

### Post by david_kt on 2009-09-12
> **shane2peru said:**
> 
Hope you can make some sense of this ;)

Shane

Sure, but actually there is one problem. Unless you nail down the nfs port, it would be impossible for me as NFS port would be a moving target every restart.

From the above post, I could see which ports it is using. But next reboot, it might use different ports. The should be available on /etc/sysconfig/nfs

Could you configure your nfs server to use static ports? Or it is already using static ports?

DK

---

### Post by shane2peru on 2009-09-12
David,

Ok, I rebooted and here is the rpcinfo again:
```

rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  40393  status
    100024    1   tcp  37534  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  53205  nlockmgr
    100021    3   udp  53205  nlockmgr
    100021    4   udp  53205  nlockmgr
    100021    1   tcp  39969  nlockmgr
    100021    3   tcp  39969  nlockmgr
    100021    4   tcp  39969  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  59490  mountd
    100005    1   tcp  32839  mountd
    100005    2   udp  59490  mountd
    100005    2   tcp  32839  mountd
    100005    3   udp  59490  mountd
    100005    3   tcp  32839  mountd

```
It appears as though the nfs is the same port.  I don't think it changes all the time, or the other computers wouldn't know where to find the nfs shared file.  
Also after my reboot I tried again to mount the shared folder from the laptop to this computer (main box) and it didn't connect.  After stopping the ubuntu_ce_firewall it connected without a hitch.  Really you are over my head on most of this, but I'm helping out with what I can.  

Shane

---

### Post by shane2peru on 2009-09-14
ok, I was looking at this today, and found this link:
[http://pario.no/2008/01/15/allow-nfs-through-iptables-on-a-redhat-system/](http://pario.no/2008/01/15/allow-nfs-through-iptables-on-a-redhat-system/)
which seems to be what you were reading, or already know.  At any rate, it seems quite complex to run nfs through iptables firewall, without binding NFS to specific ports.  I don't really understand all of this, but that is basically what I have read.  So it seems my best option is to shutoff the firewall, or remove it.  Is tinyproxy or DG depending on the firewall?  I can probably safely remove delete the contents of the file and let it think it is running?  Or I could write a script to stop the firewall upon bootup, but my best setup would be to get rid of it.  Looking for options on this.  I mean I know how to stop it when I want to connect my NFS, but I don't want to have to remember to do that each time.  


Shane

---

### Post by david_kt on 2009-09-14
> **shane2peru said:**
> ok, I was looking at this today, and found this link:
[http://pario.no/2008/01/15/allow-nfs-through-iptables-on-a-redhat-system/](http://pario.no/2008/01/15/allow-nfs-through-iptables-on-a-redhat-system/)
which seems to be what you were reading, or already know.  At any rate, it seems quite complex to run nfs through iptables firewall, without binding NFS to specific ports.  I don't really understand all of this, but that is basically what I have read.  So it seems my best option is to shutoff the firewall, or remove it.  Is tinyproxy or DG depending on the firewall?  I can probably safely remove delete the contents of the file and let it think it is running?  Or I could write a script to stop the firewall upon bootup, but my best setup would be to get rid of it.  Looking for options on this.  I mean I know how to stop it when I want to connect my NFS, but I don't want to have to remember to do that each time.  


Shane

From your previous posts looks like the ports is dynamic (the the nlockmgr and mountd ports are different).  The best is to make the ports static, you could try the direction from the link above.

The dansguardian do not really rely on the firewall, but it is a good practice to have firewall on you computer, I guess. So, there two possibility (without removing dansguardian gui)

1. Make a permissive firewall (all ports are open, just redirect port 80 for transparent proxy) --> similar to firewall off

2. use static ports on NSF and only open those ports on firewall. --> Much safer than first option.

Which one do you want to do?

DK

---

### Post by shane2peru on 2009-09-15
> **david_kt said:**
> From your previous posts looks like the ports is dynamic (the the nlockmgr and mountd ports are different).  The best is to make the ports static, you could try the direction from the link above.

The dansguardian do not really rely on the firewall, but it is a good practice to have firewall on you computer, I guess. So, there two possibility (without removing dansguardian gui)

1. Make a permissive firewall (all ports are open, just redirect port 80 for transparent proxy) --> similar to firewall off

2. use static ports on NSF and only open those ports on firewall. --> Much safer than first option.

Which one do you want to do?

DK

Well, seems to be quite difficult to bind the NFS ports than I would have imagined.  I thought it would be easy, but there doesn't seem to be any instructions for Ubuntu anywhere.  On irc I was pointed to a bug report here:  [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/28706](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/28706)  I guess I will just cut off the ubuntu_ce_firewall when I want to connect, and let it run the rest of the time.  If you can figure out how to bind nfs to a port, that would be great.  Thanks for the help on this.

Shane

---

### Post by shane2peru on 2009-09-16
Ok, I got it!!!  Here is what needs done:
[B]1.  edit /etc/init.d/nfs-kernel-server:
[/B]```
sudo gedit /etc/init.d/nfs-kernel-server
```
when it opens look for this line:
> RPCMOUNTDOPTS= and change it to this: > RPCMOUNTDOPTS="-p [COLOR="DarkOrange"]32767[/COLOR]" the port number can be whatever you want, but it has to be opened in the ubuntu_ce_firewall.
**2.  edit /etc/modprobe.d/options.conf**
```
sudo gedit /etc/modprobe.d/options.conf
```
you need to add this line:
> options lockd nlm_udpport=[COLOR="Red"]4045[/COLOR] nlm_tcpport=[COLOR="Red"]4045[/COLOR]
again the port number can be whatever you want.
**3.  add lockd to the startup modules**
```
sudo gedit /etc/modules
``` and add this line, make sure it is on it's own line.> lockd   
**4.  Edit firewall**
```
sudo gedit /etc/init.d/ubuntu_ce_firewall
```
You will need to add this section or edit it if already exists:
> 
# Open ports for NSF start

/sbin/iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport [COLOR="Red"]4045[/COLOR] -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport [COLOR="Red"]4045[/COLOR] -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport [COLOR="DarkOrange"]32767[/COLOR] -m state --state NEW -j ACCEPT
/sbin/iptables -A INPUT -p udp --dport [COLOR="DarkOrange"]32767[/COLOR] -m state --state NEW -j ACCEPT

# Open ports for NSF end  The color coded numbers must match the numbers colored above.  You can edit these numbers to your liking, but there are some kind of restrictions, and I'm not sure what they are.  I assume it can't be a used port.  
**5.  Reboot**
Now simple reboot.  It is easier than trying to get all these services to restart.  

Hope this helps.

Shane

---

### Post by david_kt on 2009-09-16
Thank you for sharing the steps to lock those ports. May be you could start a new thread "How to install nfs server client".

May be I will include nfs server client by default for next release of ubuntu ce, following your instruction.

DK

---

### Post by shane2peru on 2009-09-17
> **david_kt said:**
> Thank you for sharing the steps to lock those ports. May be you could start a new thread "How to install nfs server client".

May be I will include nfs server client by default for next release of ubuntu ce, following your instruction.

DK

Actual installation of NFS isn't too difficult and setting it up is fairly simple too.  There is a how to here:  [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)   

I guess it would be possible to have it installed, or better yet, if you have the time and energy a gui nfs setup would be great.  I think it is less complex then Dans Guardian.  The hardest part was digging out the info above, but since that is done, perhaps it wouldn't be that difficult to setup.  It is very useful if you have more than one Linux computer running on a network.  

Shane

---

### Post by narnie on 2010-04-02
Wish I could say I could get this to work with this info.

Can connect to nfs when firewall down, but not when up.

I have a stock dansgui install on Karmic.

Here is a "proof" of what I have changed:

```
$ grep -i rpcmountdopts= /etc/init.d/nfs-kernel-server 
RPCMOUNTDOPTS="-p 32771"
		    RPCMOUNTDOPTS="$RPCMOUNTDOPTS --no-nfs-version 3"

```

```
$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  58448  status
    100024    1   tcp  57974  status
    100021    1   udp   4045  nlockmgr
    100021    3   udp   4045  nlockmgr
    100021    4   udp   4045  nlockmgr
    100021    1   tcp   4045  nlockmgr
    100021    3   tcp   4045  nlockmgr
    100021    4   tcp   4045  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  48163  mountd
    100005    1   tcp  33296  mountd
    100005    2   udp  48163  mountd
    100005    2   tcp  33296  mountd
    100005    3   udp  48163  mountd
    100005    3   tcp  33296  mountd

```

```
$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-02 21:28 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
631/tcp  open  ipp
2049/tcp open  nfs
3128/tcp open  squid-http
4045/tcp open  lockd
5900/tcp open  vnc
8080/tcp open  http-proxy

```

```
$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50505 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:sunrpc state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sunrpc state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nfs state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:nfs state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4045 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4045 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32771 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32771 state NEW 
ACCEPT     icmp --  anywhere             anywhere            
DROP       all  --  anywhere             0.0.0.255/0.0.0.255 
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```
$ cat /etc/init.d/ubuntu_ce_firewall 
#!/bin/bash
### BEGIN INIT INFO
# Provides:          ubuntu_ce_firewall
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall
# Description:       Start, stop or reload firewall.
### END INIT INFO

set -e

case "$1" in
  start)
    echo -e "\nStarting Ubuntu CE firewall .....\n"
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
## Open port for ssh server (22), web server (80), and mail server (25)
iptables -A INPUT -p tcp --dport 50505 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT
## Uncomment below to open NSF port, edit the port accoring actual setting
iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
## Open ports for NSF end

#Accept Ping request
iptables -A INPUT -p icmp -j ACCEPT

# Drop other packets, Logging, and closing firewall.
iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
iptables -A INPUT -d 224.0.0.1 -j DROP
iptables -A INPUT -j LOG
iptables -A INPUT -j REJECT
	;;

  stop)
   echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"
	iptables -F
	iptables -X
	iptables -t nat -F
	iptables -t nat -X
	iptables -t mangle -F
	iptables -t mangle -X
	iptables -P INPUT ACCEPT
	iptables -P FORWARD ACCEPT
	iptables -P OUTPUT ACCEPT
	;;

  status)
        iptables -L
	;;

  restart|force-reload)
	$0 stop
	$0 start
;;
  *)
        echo "Usage: /etc/init.d/ubuntu_ce_firewall {start|stop|restart|force-reload|status}"
        exit 1
	;;
esac

```

```


**FROM CLIENT COMPUTER**

$ nmap luke-netbook

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-02 21:29 CDT
Interesting ports on luke-netbook (192.168.1.62):
Not shown: 994 filtered ports
PORT      STATE  SERVICE
25/tcp    closed smtp
80/tcp    closed http
111/tcp   open   rpcbind
2049/tcp  open   nfs
4045/tcp  open   lockd
32771/tcp closed sometimes-rpc5
MAC Address: 0C:60:76:46:8A:3C (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 38.37 seconds
```

The closed 32771 has me puzzled. I only got this once. On running it with the same command, I get nothing about 32771, however with:

```
sudo nmap -PN -p 32771 192.168.1.62

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-02 22:11 CDT
Interesting ports on luke-netbook (192.168.1.62):
PORT      STATE  SERVICE
32771/tcp closed sometimes-rpc5
MAC Address: 0C:60:76:46:8A:3C (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.44 seconds
```

which shows the 32771 closed but as above from the excerpt from aboves ubuntu_ce_firewall 32771 should be open.

```
iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT

```

I also tried this with port 32767 (which shouldn't matter) and it didn't matter. Still no nfs with firewall up.

Would someone please give me guidance?

With thanks,
Narnie

---

### Post by shane2peru on 2010-04-03
> **narnie said:**
> Wish I could say I could get this to work with this info.

Can connect to nfs when firewall down, but not when up.

I have a stock dansgui install on Karmic.

Here is a "proof" of what I have changed:

```
$ grep -i rpcmountdopts= /etc/init.d/nfs-kernel-server 
RPCMOUNTDOPTS="-p 32771"
		    RPCMOUNTDOPTS="$RPCMOUNTDOPTS --no-nfs-version 3"

```

```
$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  58448  status
    100024    1   tcp  57974  status
    100021    1   udp   4045  nlockmgr
    100021    3   udp   4045  nlockmgr
    100021    4   udp   4045  nlockmgr
    100021    1   tcp   4045  nlockmgr
    100021    3   tcp   4045  nlockmgr
    100021    4   tcp   4045  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    [COLOR="Red"]100005    1   udp  48163  mountd
    100005    1   tcp  33296  mountd
    100005    2   udp  48163  mountd
    100005    2   tcp  33296  mountd
    100005    3   udp  48163  mountd
    100005    3   tcp  33296  mountd[/COLOR]

```



Would someone please give me guidance?

With thanks,
Narnie

Ok, some of those commands are over my head.  What it seems to me is that the RPCMOUNTS is not sticking.  I highlighted the numbers in red above that is indicating to me that it isn't sticking indeed.  I have updated to Karmic, and have yet to install UCE or the firewall, and at this point probably won't till after Lucid Lynx.  I had a real time figuring out how to make the rcpmountopts stick, and more than likely something else has changed causing my data to be 'outdated'  you seem to have a pretty good handle on this, so if you find anything out please post back here.  I bet if you reboot and re-run ```
rpcinfo -p
``` you can watch these numbers change, which means the a setting is not making them stick.  That would be the best route to test and troubleshoot it.

Shane

---

### Post by narnie on 2010-04-04
> **shane2peru said:**
> Ok, some of those commands are over my head.  What it seems to me is that the RPCMOUNTS is not sticking.  I highlighted the numbers in red above that is indicating to me that it isn't sticking indeed.  I have updated to Karmic, and have yet to install UCE or the firewall, and at this point probably won't till after Lucid Lynx.  I had a real time figuring out how to make the rcpmountopts stick, and more than likely something else has changed causing my data to be 'outdated'  you seem to have a pretty good handle on this, so if you find anything out please post back here.  I bet if you reboot and re-run ```
rpcinfo -p
``` you can watch these numbers change, which means the a setting is not making them stick.  That would be the best route to test and troubleshoot it.

Shane

Thanks, my thinking, too. For some reason, rpc.mountd is not following the setting in /etc/init.d/nfs-kernel-server

Honestly, I'm not sure where to go from here.

In researching, I've seen that statd may need to be tied as well (but perhaps not if mounting as tcp with 

```
mount -o proto=tcp 192.168.1.62:/home /mnt/mnt
```

Not sure where to go from here. Will keep checking.

Narnie

---

### Post by narnie on 2010-04-04
command line script to make all the above changes "automatically."

just untar it with:

```
tar -xvvpf dansguardian_nfs.tar.gz
```

then either do:

1)
```
$ chmod a+x dansguardian_nfs
```

then
```
$ ./dansguardian_nfs
```

or

2)
```
bash -c dansguardian_nfs
```

If you have changed /etc/init.d/ubuntu_ce_firewall, then it breaks the script as far as the mountd port.

This is more for a brand new install or starting with a fresh copy of it which I will include for your convenience.

```
#!/bin/bash
### BEGIN INIT INFO
# Provides:          ubuntu_ce_firewall
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall
# Description:       Start, stop or reload firewall.
### END INIT INFO

set -e

case "$1" in
  start)
    echo -e "\nStarting Ubuntu CE firewall .....\n"
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
## Open port for ssh server (22), web server (80), and mail server (25)
#iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT
## Uncomment below to open NSF port, edit the port accoring actual setting
#iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
## Open ports for NSF end

#Accept Ping request
iptables -A INPUT -p icmp -j ACCEPT

# Drop other packets, Logging, and closing firewall.
iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
iptables -A INPUT -d 224.0.0.1 -j DROP
iptables -A INPUT -j LOG
iptables -A INPUT -j REJECT
	;;

  stop)
   echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"
	iptables -F
	iptables -X
	iptables -t nat -F
	iptables -t nat -X
	iptables -t mangle -F
	iptables -t mangle -X
	iptables -P INPUT ACCEPT
	iptables -P FORWARD ACCEPT
	iptables -P OUTPUT ACCEPT
	;;

  status)
        iptables -L
	;;

  restart|force-reload)
	$0 stop
	$0 start
;;
  *)
        echo "Usage: /etc/init.d/ubuntu_ce_firewall {start|stop|restart|force-reload|status}"
        exit 1
	;;
esac

```

Now if I could just find out what is preventing mine from working even with all the above changes!!

Regards,
Narnie

---

### Post by narnie on 2010-04-04
Problem semi-solved.

I don't know why it is behaving this way, but this is the problem portion out of /etc/init.d/nfs-kernel-server:

```

		start-stop-daemon --start --oknodo --quiet \
		    --exec $PREFIX/sbin/rpc.mountd -- $RPCMOUNTDOPTS


```

for some reason, $RPCMOUNTDOPTS is being substituted with "--manage-gids" rather than how it is defined earlier with "-p 32771 -g"

I changed the file to look like:

```
		start-stop-daemon --start --oknodo --quiet \
		    --exec $PREFIX/sbin/rpc.mountd -- "-p 32771 -g"

```

a nice run of rpcinfo -p shows:

```
$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  53057  status
    100024    1   tcp  36648  status
    100021    1   udp  53834  nlockmgr
    100021    3   udp  53834  nlockmgr
    100021    4   udp  53834  nlockmgr
    100021    1   tcp  52365  nlockmgr
    100021    3   tcp  52365  nlockmgr
    100021    4   tcp  52365  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  32771  mountd
    100005    1   tcp  32771  mountd
    100005    2   udp  32771  mountd
    100005    2   tcp  32771  mountd
    100005    3   udp  32771  mountd
    100005    3   tcp  32771  mountd
```

This also shows the port open:

```
$ sudo nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-05 01:09 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 992 closed ports
PORT      STATE SERVICE
25/tcp    open  smtp
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
2049/tcp  open  nfs
5900/tcp  open  vnc
32771/tcp open  sometimes-rpc5
```

guess what? I CAN MOUNT MY NFS THROUGH THE FIREWALL NOW!!! YEA!!!

I have also modified my script to incorporate this change. It was a little tricky as sed wouldn't let me escape a $ (with \$, \\$,\\\$, nor \\\\$) so not sure what is wrong there.

At some point RPCMOUNTDOPTS is being redefined, but I can't see where on earth in the script this is happening. If I find it, I'll report back here. It is really odd behaviour.

Anyway, hopes this helps some people.

Yours,
Narnie

---

### Post by narnie on 2010-04-05
Problem solved. Bug found.

Traced the true source of the problem. Don't know why I didn't see it before. Here it is:

```
DEFAULTFILE=/etc/default/nfs-kernel-server
RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS="-p 32771 -g"
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=
PROCNFSD_MOUNTPOINT=/proc/fs/nfsd

if [ -f $DEFAULTFILE ]; then
    . $DEFAULTFILE
fi
```

Those initial variables are defined, including DEFAULTFILE which is the initial nfs-kernel-server variable definitions.

It then allows the defining of varibales like RPCMOUNTDOPTS.

Then it "nicely" (er, cough, cough) resources the /etc/default/nfs-kernel-server. Guess what that file has in it as a definition!!! You guessed it:

```
RPCMOUNTDOPTS=--manage-gids
```

I'll be filing a bug report.

This can be fix by manually editing the code to look like this:

```
DEFAULTFILE=/etc/default/nfs-kernel-server

if [ -f $DEFAULTFILE ]; then
    . $DEFAULTFILE
fi

RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS="-p 32771 -g"
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=
PROCNFSD_MOUNTPOINT=/proc/fs/nfsd


```

This will allow the sourcing of /etc/default/nfs-kernel-server
and then modifying certain variables as needed and fix this issue.

As for me, I'm just going to use my script to code the changes, because shifting around lines like that is more work that I really want to do :)

As an afterthought, I could also modify /etc/default/nfs-kernel-server to patch it, but that doesn't fix real issue which is an error in the flow of the code.

That was fun!

Yours,
Narnie

bug already report. I posted the fix there.

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/423489]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/423489")

---

### Post by shane2peru on 2010-04-05
> **narnie said:**
> Problem solved. Bug found.

Traced the true source of the problem. Don't know why I didn't see it before. Here it is:

```
DEFAULTFILE=/etc/default/nfs-kernel-server
RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS="-p 32771 -g"
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=
PROCNFSD_MOUNTPOINT=/proc/fs/nfsd

if [ -f $DEFAULTFILE ]; then
    . $DEFAULTFILE
fi
```

Those initial variables are defined, including DEFAULTFILE which is the initial nfs-kernel-server variable definitions.

It then allows the defining of varibales like RPCMOUNTDOPTS.

Then it "nicely" (er, cough, cough) resources the /etc/default/nfs-kernel-server. Guess what that file has in it as a definition!!! You guessed it:

```
RPCMOUNTDOPTS=--manage-gids
```

I'll be filing a bug report.

This can be fix by manually editing the code to look like this:

```
DEFAULTFILE=/etc/default/nfs-kernel-server

if [ -f $DEFAULTFILE ]; then
    . $DEFAULTFILE
fi

RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS="-p 32771 -g"
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=
PROCNFSD_MOUNTPOINT=/proc/fs/nfsd


```

This will allow the sourcing of /etc/default/nfs-kernel-server
and then modifying certain variables as needed and fix this issue.

As for me, I'm just going to use my script to code the changes, because shifting around lines like that is more work that I really want to do :)

As an afterthought, I could also modify /etc/default/nfs-kernel-server to patch it, but that doesn't fix real issue which is an error in the flow of the code.

That was fun!

Yours,
Narnie

bug already report. I posted the fix there.

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/423489]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/423489")

Glad you got it!  I love nfs as it is fast and easy to use, and I love the security of the firewall, and working through it.  I also enjoy ssh.  I'm sure I will be referring back to this when I get stuck on this when I upgrade, provided it isn't fixed.

Shane

---

