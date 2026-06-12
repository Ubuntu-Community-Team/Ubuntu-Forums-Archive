---
title: "Possible security breach?"
date: 2010-03-04
forum: Security
---

### Post by WinstonChurchill on 2010-03-04
I've noticed a couple things recently that I'm a little concerned about:

Thing #1: The 'w' command always shows that there are two users logged on, but only shows one in the list... which is weird. 'top' doesn't show any zombie processes, and I don't see anything that might be user-related... so why is it doing this?
```
user@host:~$ w
 22:41:24 up 12 days, 22:41,  2 users,  load average: 1.17, 0.86, 0.84
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user     pts/0    10.0.0.101       20:52    0.00s  0.25s  0.00s w
user@host:~$ who
user      pts/0        Mar  4 20:52 (10.0.0.101)
user@host:~$
```Thing #2: Snort has logged the following a couple times in the last few days: The server is 10.0.0.1, and 10.0.0.101 is my desktop.
```
[**] [122:1:0] (portscan) TCP Portscan [**]
[Priority: 3]
03/03-10:34:44.405435 10.0.0.1 -> 10.0.0.101
PROTO:255 TTL:0 TOS:0x0 ID:20 IpLen:20 DgmLen:152

[**] [122:1:0] (portscan) TCP Portscan [**]
[Priority: 3]
03/04-07:50:25.071711 10.0.0.1 -> 10.0.0.101
PROTO:255 TTL:0 TOS:0x0 ID:15 IpLen:20 DgmLen:152
```I know snort can be stupid sometimes, but this has happened twice, and during both instances I was not logged into the server at all, so I don't think it's anything I did. Both times were shortly after my desktop was turned on, so maybe it's DHCP related? But then why hasn't this shown up before?

---

### Post by iponeverything on 2010-03-05
Probably nothing with snort "PROTO: 255" looks like a bug.

with regard to w, it is strange. 

use apt-get to install debsums:

[http://www.digipedia.pl/man/doc/view/debsums.1.html](http://www.digipedia.pl/man/doc/view/debsums.1.html)

check the md5 of your w binary.

---

### Post by WinstonChurchill on 2010-03-05
I ran debsums - it reports:
```
root@host:/# debsums --silent
debsums: checksum mismatch bind9 file /usr/share/bind9/bind9-default.md5sum
debsums: no md5sums for binutils
debsums: no md5sums for g++
debsums: no md5sums for installation-report
debsums: no md5sums for libgdbm3
debsums: no md5sums for liblockfile1
debsums: no md5sums for lockfile-progs
debsums: no md5sums for mawk
debsums: no md5sums for netbase
debsums: no md5sums for squid
debsums: no md5sums for squid-common
debsums: no md5sums for ubuntu-keyring
debsums: no md5sums for update-inetd
```Should I be concerned about the bind9 mis-match? It only does DNS resolutions for my LAN - I've never exposed it to the internet...

It seems 'w' isn't the only command that's confused:
```
root@host:/# w
 01:03:54 up 13 days,  1:03,  2 users,  load average: 0.27, 0.46, 0.55
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user     pts/0    10.0.0.101       00:57    0.00s  0.49s  0.22s sshd: user [priv]
root@host:/# uptime
 01:03:55 up 13 days,  1:03,  2 users,  load average: 0.27, 0.46, 0.55
root@host:/# users
user     
root@host:/# who
user      pts/0        2010-03-05 00:57 (10.0.0.101)
root@host:/#
```Also, snort apparently always lists "Proto: 255" on those sorts of entries. I was checking a friend's server with nmap the other day, and this got logged:
```
[**] [122:3:0] (portscan) TCP Portsweep [**]
[Priority: 3]
02/27-16:15:58.711284 10.0.0.101 -> xxx.xxx.xxx.xxx
PROTO:255 TTL:0 TOS:0x0 ID:41141 IpLen:20 DgmLen:162 DF
```... so, any more ideas?

---

### Post by iponeverything on 2010-03-05
I think you should be concerned about bind, historically it has been security problem. 

I do this kind thing for a living, so I am not inclined to put too much effort into it as seems too much like work.. 

- Lookup recent bind exploits and see if the your flavour of Ubuntu was affected.

- Diff your bind binary (and for that matter w and ps as well) with ones inside the original version of the .deb installed on your machine. (from the Internet, not your machine)

If you find your machine has been compromised, it's very labour intensive to ensure that that a root-kit has been fully removed. In the majority of cases it is much easier to reinstall.

With the the amount what information that I have to work with (almost none)  and fact that your machine is on a private address - I put the likelihood that your machine was actually compromised, pretty low.

--

---

### Post by WinstonChurchill on 2010-03-05
All right, thanks for your help.

---

