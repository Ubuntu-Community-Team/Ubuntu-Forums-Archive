---
title: "apt-get update not working......"
date: 2010-03-15
forum: Server Platforms
---

### Post by ggerules on 2010-03-15
Hi,

I have a farily new install of 8.04.3 server and I am having trouble with getting the following command to work. 

sudo apt-get update

It is saying that apt-get "could not resolve" the server. The error text is below.

Here is my sources.list and after that are the error messages I am getting.

Thanks in advance!

--------- sources.list ---------------------------

# 
# deb cdrom:[Ubuntu-Server 8.04.3 _Hardy Heron_ - Release i386 (20090709)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.3 _Hardy Heron_ - Release i386 (20090709)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

----------------- error messages ----------------------
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists...

---

### Post by solar george on 2010-03-15
You need to check your internet connection is working;
Post the output of the following commands;
```

cat /etc/resolv.conf
ifconfig
nslookup google.com

```

---

### Post by ggerules on 2010-03-15
Hi Solar,

Thanks for the response!

Here is a the output requested....... 

This is smelling like a nameserver dns configuration issue......

------- resolve.conf -----------
search gerules.com
nameserver 151.167.1.8

Note: The 151 address above was the name server address I had for yahoo's dns server. This is an old entry. I use to be running debian and I copied it from that system.

The interesting thing is that I can get to [www.gerules.com](www.gerules.com) and the name resolves to my static ip address.

------- ifconfig -----------
eth0      Link encap:Ethernet  HWaddr 00:10:5a:5b:a8:34  
          inet addr:216.63.57.169  Bcast:216.63.57.175  Mask:255.255.255.248
          inet6 addr: fe80::210:5aff:fe5b:a834/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620496 errors:1 dropped:0 overruns:0 frame:2
          TX packets:703458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160350883 (152.9 MB)  TX bytes:501352510 (478.1 MB)
          Interrupt:16 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:358911 (350.4 KB)  TX bytes:358911 (350.4 KB)

nslookup google.com responded with a 
;; connection timed out; no servers could be reached

---

### Post by solar george on 2010-03-15
Odd i can resolve us.archive.ubuntu.com using that namesever (so thats fine) and ping your ip address (so doesn't seem to be a routing problem).
Are you allowed to be using that server or may they have blocked your ip for using their servers without permission.
Can you try;
```
nslookup google.com - 4.2.2.2
```

---

### Post by ggerules on 2010-03-15
Thanks for the reply.

Here is the response from the 
nslookup google.com - 4.2.2.2

Server:		4.2.2.2
Address:	4.2.2.2#53

Non-authoritative answer:
Name:	google.com
Address: 209.85.225.103
Name:	google.com
Address: 209.85.225.104
Name:	google.com
Address: 209.85.225.105
Name:	google.com
Address: 209.85.225.106
Name:	google.com
Address: 209.85.225.147
Name:	google.com
Address: 209.85.225.99

---

### Post by solar george on 2010-03-15
Maybe try changing you dns providers then - you could try 4.2.2.1, 4.2.2.2, 4.2.2.3 and 4.2.2.4

---

### Post by ggerules on 2010-03-15
Thanks Solar!

The problem was with my dns. The 151 address described above didn't work anymore. I changed it to the 4.2.2.2 address and things worked like a charm.

Thanks again for taking the time to help.

---

