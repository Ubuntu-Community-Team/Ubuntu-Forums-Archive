---
title: "apt-get update (connection refused) elp!!!"
date: 2005-09-25
forum: Repositories &amp; Backports
---

### Post by narmenia on 2005-09-25
last night i can still update but this afternoon i can't anymore...
the site can be pinged...
opning it on firefox also says connection refused...
using .uk or .us still has gives a connection refuse...
what gives???

> ws09@ws09:~$ ping ph.archive.ubuntu.com
PING ph.archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from 82.211.81.182: icmp_seq=1 ttl=51 time=360 ms
64 bytes from 82.211.81.182: icmp_seq=2 ttl=51 time=362 ms
64 bytes from 82.211.81.182: icmp_seq=3 ttl=51 time=358 ms
64 bytes from 82.211.81.182: icmp_seq=4 ttl=51 time=355 ms
64 bytes from 82.211.81.182: icmp_seq=5 ttl=51 time=356 ms
64 bytes from 82.211.81.182: icmp_seq=6 ttl=51 time=364 ms
64 bytes from 82.211.81.182: icmp_seq=7 ttl=51 time=357 ms

--- ph.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6004ms
rtt min/avg/max/mdev = 355.809/359.493/364.134/3.023 ms
ws09@ws09:~$ sudo apt-get update
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
52% [Connecting to ph.archive.ubuntu.com (82.211.81.182)] [Connecting to securi

---

### Post by reedlaw on 2005-09-25
I am having the same problem.  cn.archive.ubuntu.com is also refusing connections.

---

### Post by Xian on 2005-09-25
They seem to all be down. 
Since it is not a local problem there is nothing to be done but wait.

---

### Post by ghostintheshell on 2005-09-25
same problem here.

it's a catastrophic day x_X 
(see topic "breezy is very slow")

---

### Post by duminas on 2005-09-25
Same problem here. Juuuuuuuuuuuuuuuuuuuuuuuuuuuuust great.

Thanks a lot, Ubuntu. *kicks for something breaking again*

---

### Post by narmenia on 2005-09-25
waaaaaaaaaaaaaaaaaaa!!! OMG!!! i have to set-up 6 more PCs... T_T
ok i'll just wait a bit...  :roll:

---

### Post by heimo on 2005-09-25
For me changing http to ftp (in sources.list) did the trick.

---

### Post by jeffreyvergara.NET on 2005-09-25
[QUOTE=heimo]For me changing http to ftp (in sources.list) did the trick.[/QUOTE]
 yup! changing http to ftp works! thanks!!! 
btw, hello Kabayang narmenia!.. ehehehe...

---

### Post by Fed7 on 2005-09-25
same problem with it.archive.ubuntu.com :(

---

### Post by jpmcc on 2005-09-25
[QUOTE=narmenia]last night i can still update but this afternoon i can't anymore...
the site can be pinged...
opning it on firefox also says connection refused...
using .uk or .us still has gives a connection refuse...
what gives???[/QUOTE]

Yes, http is down, ftp is up:
```
$ **wget http://archive.ubuntu.com**
--09:56:27--  http://archive.ubuntu.com/
           => `index.html'
Resolving archive.ubuntu.com... 82.211.81.151, 82.211.81.182
Connecting to archive.ubuntu.com[82.211.81.151]:80... failed: Connection refused.
Connecting to archive.ubuntu.com[82.211.81.182]:80... failed: Connection refused.
$ **wget ftp://archive.ubuntu.com**
--09:58:24--  ftp://archive.ubuntu.com/
           => `.listing'
Resolving archive.ubuntu.com... 82.211.81.182, 82.211.81.151
Connecting to archive.ubuntu.com[82.211.81.182]:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> PASV ... done.    ==> LIST ... done.

    [ <=>                                 ] 64            --.--K/s

09:58:24 (48.75 KB/s) - `.listing' saved [64]

Removed `.listing'.
Wrote HTML-ized index to `index.html' [302].
$
```

---

### Post by Spleenie on 2005-09-25
[QUOTE=Fed7]same problem with it.archive.ubuntu.com :([/QUOTE]

Just reporting that the au one is down too.

Taking a wait and see approach and hoping its nothing catastrophic.

- Spleenie

---

### Post by Brad wilkinson on 2005-09-25
so would that be responsible for the error 

> W: Failed to fetch [http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla/libnspr4_1.7.12-0ubuntu05.04_i386.deb](http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla/libnspr4_1.7.12-0ubuntu05.04_i386.deb)
  503 Connect Error


W: Failed to fetch [http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla/libnss3_1.7.12-0ubuntu05.04_i386.deb](http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla/libnss3_1.7.12-0ubuntu05.04_i386.deb)
  503 Connect Error


W: Failed to fetch [http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb](http://192.168.1.100:9999/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb)
  503 Connect Error


or do I still have a problem with my apt-proxy settings?

---

### Post by Tiede on 2005-09-25
Nope. No need for all that. A solution's already been given by heimo. Change http to ftp in your sources.list

---

### Post by prosario_2000 on 2005-09-25
Today I installed Ubuntu for the very first time.  I thoght I did something wrong.  And just when I was making upgrades, it didn't want to download any upgrades :-S .  Thank goodness I'm not the problem of my inability to update and upgrade

---

### Post by funkenstein on 2005-09-25
also, http and ftp mirrormax backports server is  down. 
solution:
go to [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) and select the backports mirror closest to you. Then copy and paste the one you choose into /etc/apt/sources.list, remembering to leave the "hoary-extras main universe multiverse restrict" and "hoary-backports main universe multiverse restricted" after the linkys  [-X

---

### Post by minh on 2005-09-25
Hi guys,
Sorry if I have a stupid question cause i am a new bee. 
Still have the problem even when i change all the http to ftp
> 
Get:15 [ftp://ubuntu-backports.mirrormax.net](ftp://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Err [ftp://ubuntu-backports.mirrormax.net](ftp://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  Unable to fetch file, server said 'Can't open /dists/hoary-backports/main/binary-i386/Packages.gz: No such file or directory  '
Get:16 [ftp://ubuntu-backports.mirrormax.net](ftp://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Err [ftp://ubuntu-backports.mirrormax.net](ftp://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  Unable to fetch file, server said 'Can't open /dists/hoary-backports/universe/binary-i386/Packages.gz: No such file or directory  
Failed to fetch [ftp://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](ftp://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /dists/hoary-backports/restricted/binary-i386/Packages.gz: No such file or directory  '
' 
There is a reponse of  wget [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com)
So can someone tell me why it does that

---

### Post by minh on 2005-09-25
Ok, it fixe now, i've changed all us info for fr
ubuntu is back

---

### Post by ghostintheshell on 2005-09-25
[QUOTE=minh]Ok, it fixe now (...)[/QUOTE]

yes, for me tooooo

---

### Post by ghostintheshell on 2005-09-25
[QUOTE=funkenstein]also, http and ftp mirrormax backports server is  down. 
solution:
go to [http://backports.ubuntuforums.org/url.php]("http://backports.ubuntuforums.org/url.php") and select the backports mirror closest to you. Then copy and paste the one you choose into /etc/apt/sources.list, remembering to leave the "hoary-extras main universe multiverse restrict" and "hoary-backports main universe multiverse restricted" after the linkys  [-X[/QUOTE]

thank you for this info.
I'm now with:

 ```
#STABLE
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted

#STAGING
#deb http://acm.cs.umn.edu/ubp/ hoary-backports-staging main universe multiverse restricted
#deb http://acm.cs.umn.edu/ubp/ hoary-extras-staging main universe multiverse restricted
```

---

### Post by Tiede on 2005-09-27
OK, guys the https are backup again. Ubuntu-geek says it ways due to a hardware upgrade... Glad things are back on the runway! :)

---

