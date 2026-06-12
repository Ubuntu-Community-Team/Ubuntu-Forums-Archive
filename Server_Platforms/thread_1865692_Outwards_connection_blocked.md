---
title: "Outwards connection blocked"
date: 2011-10-20
forum: Server Platforms
---

### Post by tininho on 2011-10-20
I updated our Ubuntu server from 11.04 to 11.10 (should have stayaed with 10.04 originally, I know it now..). Every time the installation asked whether to overwrite or keep current the "keep current" action was chosen. Still, after the restart all sites worked (are accessible to all), but it seems the server does not allow the pages to make outside connections, since:

Litespeed error: [LICENSE] Failed to send registration request.
Magento: Magento downloader gives "host not available" when trying to install extensions, emails are not being sent and paypal payments do not get verified.

Iptables shows empty (iptables -L). I runned OUTPUT, INPUT , FORWARD ACCEPT commands plus -F but it did not help. Also runned the command sudo ufw disable. I cannot figure out what is blocking the connection. Can you guys help?

---

### Post by 2F4U on 2011-10-20
Is the server able to connect to the outside world, e.g. can you ping a web site such as [www.google.com?](www.google.com?)

---

### Post by tininho on 2011-10-20
Ping respond (had to use ip, address google.com did not work):

> virtual@*****:~$ ping -c 4 173.194.32.52
PING 173.194.32.52 (173.194.32.52) 56(84) bytes of data.
64 bytes from 173.194.32.52: icmp_req=1 ttl=58 time=8.64 ms
64 bytes from 173.194.32.52: icmp_req=2 ttl=58 time=8.57 ms
64 bytes from 173.194.32.52: icmp_req=3 ttl=58 time=8.52 ms
64 bytes from 173.194.32.52: icmp_req=4 ttl=58 time=8.53 ms

--- 173.194.32.52 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 8.529/8.570/8.640/0.079 ms

For example sudo apt-get update is not working though:

> virtual@****:~$ sudo apt-get update
[sudo] password for virtual:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease

Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) oneiric InRelease

Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) oneiric-updates InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) oneiric Release.gpg
  Could not resolve 'fi.archive.ubuntu.com'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) oneiric-updates Release.gpg
  Could not resolve 'fi.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://fi.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://fi.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'fi.archive.ubuntu.com'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'fi.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

I'm getting similiar "could not resolve" messages everywhere within this server (Magento extensions, wordpress, Litespeed admin panel etc etc.)

---

### Post by tininho on 2011-10-20
Oh, now I get it, the DNS servers got erased doing the update, should edit /etc/resolv.conf and give correct DNS server of the VPS provider. I use google nameservers untill they respond. The ping problem made it clear to me, so thanks :)

---

