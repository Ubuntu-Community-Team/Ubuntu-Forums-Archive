---
title: "When I change my ip address from DHCP to static i can no longer update package list."
date: 2013-04-15
forum: Server Platforms
---

### Post by unclepeanuts159 on 2013-04-15
I am kind of new to the server environment, I have previously been using Ubuntu desktop and running my game and other servers off that but I wanted a change so i thought I would change to Ubuntu server which is at 12.10. 
I followed the steps on the Ubuntu website/manual of the server as to change from Dynamic ip to Static and I have gone over my work more then once. I get this error after i have rebooted the server with the IP set to Static and entered apt-get update:
[TABLE="width: 500"]
[TR]
[TD]Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) quantal Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) quantal-updates Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) quantal-backports Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg)                            
  Temporary failure resolving 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg)
   Temporary failure resolving 'au.archive.ubuntu.com'

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg)
 Temporary failure resolving 'au.archive.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)
 Temporary failure resolving 'security.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.[/TD]
[/TR]
[/TABLE]
[HR][/HR]So simply I ask how do I fix this problem? 
any help would be wonderful :).

---

### Post by gdi2k on 2013-04-15
This could be a DNS related issue I think. Did you add:
```
dns-nameservers xxx.xxx.xxx.xxx
```

to your /etc/network/interfaces file? 

Like: 
```
auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
```

---

### Post by unclepeanuts159 on 2013-04-15
I havn't tried that i shall try that now and get back to you

---

### Post by unclepeanuts159 on 2013-04-15
Thank you very much , it fixed my problem.

---

### Post by Hexxus on 2013-04-15
Excellent! Could you please mark this as "Solved" unclepeanuts159.

---

### Post by unclepeanuts159 on 2013-04-15
How?? I can't find it and I'm only new to these forums and I'm still
Getting my head round it

---

### Post by Iowan on 2013-04-15
I changed it for you but here's how:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)
As a sidenote, I have a couple of servers set for DHCP. The DHCP Server is configured to issue them a static lease (AKA reserved address).

---

