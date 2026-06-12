---
title: "Kali Linux | apt-get fail (404  Not Found, failed to fetch etc) | No sound error"
date: 2016-10-09
forum: Ubuntu/Debian BASED
---

### Post by zedriv on 2016-10-09
Hello, I am new with this so please be patient.

I have Kali Linux (Dualboot Windows 8.1 64-bit) and I cant download any packages or update anything.
Since day one I have had problems downloading and there is no sound and since I cant download anything (in terminal) I am stuck.

I read another post with a smiliair problem and followed the command suggestions. I have tried to google some solutions and they have not solved my problem. 

```
root@localhost:~# cat /etc/apt/sources.list
deb http://http.kali.org/kali sana main non-free contrib
deb http://security.kali.org/kali-security/ sana/updates main contrib non-free
root@localhost:~# grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://http.kali.org/kali sana main non-free contrib
/etc/apt/sources.list:deb http://security.kali.org/kali-security/ sana/updates main contrib non-free
grep: /etc/apt/sources.list.d/*: No such file or directory
root@localhost:~# cat /etc/issue
Kali GNU/Linux Rolling \n \l
root@localhost:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Kali
Description:    Kali GNU/Linux Rolling
Release:    kali-rolling
Codename:    kali-rolling
root@localhost:~# ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=46 time=35.3 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=46 time=35.4 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=46 time=37.2 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 35.353/36.030/37.299/0.911 ms
root@localhost:~# apt-config dump | grep Architecture
APT::Architecture "amd64";
APT::Architectures "";
APT::Architectures:: "amd64";
root@localhost:~# uname -a
Linux localhost 4.6.0-kali1-amd64 #1 SMP Debian 4.6.4-1kali1 (2016-07-21) x86_64 GNU/Linux
root@localhost:~# 


```

---

### Post by howefield on 2016-10-09
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

