---
title: "apt-get update doesn't work, no connectivity"
date: 2020-05-02
forum: Server Platforms
---

### Post by Robert_Boutin on 2020-05-02
My email server stopped working suddenly a few days ago.  It roughly coincided with an archive file that grew to fill up every spare corner of my hard drive.  I don't know if that's what caused it but I had to repair several VMs that were apparently impacted by a lack of any storage whatsoever.

Email server is a virtualbox Ubuntu 18.04 guest running on a Ubuntu 16.04 host. Below is the output from my aborted ping and from apt-get update.  I have internet connectivity from my other guests and the host.  I confirmed that my router is still NATing correctly from the email public ip to the private ip and back.

Any suggestions on what might be causing this?  I googled the message below, "Failed to connect to [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release). Check your Internet connection or proxy settings" but I couldn't find a solution to this, _really_ hoping someone here might be able to assist.

Thanks!


Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-99-generic x86_64)
 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
  System information as of Sat May  2 17:32:07 EDT 2020
  System load:  0.01               Processes:             121
  Usage of /:   34.9% of 52.42GB   Users logged in:       0
  Memory usage: 66%                IP address for enp0s3: 192.168.1.229
  Swap usage:   44%

 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)
0 packages can be updated.
0 updates are security updates.
Failed to connect to [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release). Check your Internet connection or proxy settings

Last login: Sat May  2 17:30:47 2020
[EMAIL="user@mail:~$"]user@mail:~$[/EMAIL] sudo su
[sudo] password for user:
[EMAIL="root@mail:/home/user"]root@mail:/home/user[/EMAIL]# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
66 packets transmitted, 0 received, 100% packet loss, time 66257ms
[EMAIL="root@mail:/home/user"]root@mail:/home/user[/EMAIL]# apt-get update
Err:1 [http://ppa.launchpad.net/certbot/certbot/ubuntu](http://ppa.launchpad.net/certbot/certbot/ubuntu) bionic InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic InRelease
  Temporary failure resolving 'de.archive.ubuntu.com'
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Temporary failure resolving 'de.archive.ubuntu.com'
Err:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Temporary failure resolving 'de.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://de.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'de.archive.ubuntu.com'
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://de.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Temporary failure resolving 'de.archive.ubuntu.com'
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://de.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Temporary failure resolving 'de.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://ppa.launchpad.net/certbot/certbot/ubuntu/dists/bionic/InRelease](http://ppa.launchpad.net/certbot/certbot/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'ppa.launchpad.net'
W: Some index files failed to download. They have been ignored, or old ones used instead.
[EMAIL="root@mail:/home/user"]root@mail:/home/user[/EMAIL]#

---

### Post by darkod on 2020-05-02
Does local connectivity work?

Can you ping the LAN router and other machines on the same LAN subnet?

If somehow the networking got messed up, it would behave like this. No ping to public 8.8.8.8, no dns if using public dns.

Errors in apt-get update say it couldn't complete even dns resolution. If you have local LAN dns (router or another dns server) it means it couldn't successfully even talk to that machine. But it's not just that. Because ping 8.8.8.8 should work even without dns if you have correct internet access.

---

### Post by Robert_Boutin on 2020-05-02
Thanks.  I'm sorry, I should stated in my original post.  Yes, it will talk to other machines locally, I've been rsync'ing files between it and other VMs.  Ping from mailserver to router is below, it's working.

[EMAIL="root@mail:/home/user"]root@mail:/home/user[/EMAIL]# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.596 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.450 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.617 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.641 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.511 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.417 ms
^C

I also checked my webserver (another VM on same network).  That pings 8.8.8.8.  Both use public ip's and are NATed in the identical manner to their private ip's so I don't have a reason to suspect the router (and the router has been rock solid for a couple years now).

[EMAIL="root@webhost:/home/user"]root@webhost:/home/user[/EMAIL]# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=16.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=16.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=52 time=19.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=52 time=18.8 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=52 time=16.2 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=52 time=17.8 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=52 time=17.0 ms
^C

I feel like it's inside the mailserver's networking configuration not wanting to talk to the public interface (I know what I'm thinking but I'm sure I didn't state that properly).  Any thoughts where to check next?  Thanks again!

---

### Post by volkswagner on 2020-05-03
You will need to diagnose the network connectivity/adapter.

Try the following commands and post results: 

```
traceroute 192.168.1.1
traceroute 8.8.8.8 
ip a
iptables -L
nslookup google.com

```

---

### Post by Robert_Boutin on 2020-05-03
Sorry, major change in direction for this issue, it is unquestionably something in my EdgeRouter-X.  I built a new email server yesterday with the goal of just restoring the data and databases to the new machine.  Everything was fine building the VM, no connectivity problems.  However, when I changed the NAT in my router to redirect to the public ip to the new private ip, everything stopped again.  With the old email server removed from NAT, it now connects and updates properly.  So there is something in my router that changed.  I upgraded the firmware a couple weeks ago, maybe that combined with a Ubuntu 18.04 Server update caused it, not sure. 

Not sure how but I will try to close this as apt-get update is working as it's supposed to.  Thanks for taking the time to respond, I'm sorry the problem was not as I thought.

---

