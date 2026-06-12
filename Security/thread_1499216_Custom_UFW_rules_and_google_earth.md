---
title: "Custom UFW rules and google earth"
date: 2010-06-01
forum: Security
---

### Post by n1ght5t4lk3r on 2010-06-01
I have an issue that it seems quite a few people are having also with google earth in ubuntu 10.04, and google earth not being able to login to the google server as mentioned in the thread...

[http://ubuntuforums.org/showthread.php?t=1367651](http://ubuntuforums.org/showthread.php?t=1367651)

As i have mentioned in that thread this only came about after installing 10.04, I had zero problems running the exact same version of google earth under 9.04 (jaunty), the error message that GE gives points to a help article from google 

[http://earth.google.com/support/bin/answer.py?hl=en&answer=117452](http://earth.google.com/support/bin/answer.py?hl=en&answer=117452)

which is not really helpful at all, apart from mentioning about adding rules to your firewall to allow google earth to connect to certain servers on port 80. I thought I'd download GUFW to try an add rules but see no way to add rules on a per application basis unlike what I have been used to in windows with the likes of comodo (except for a few seemingly pre-defined torrent apps in a drop down in gufw). 
Is it possible, using the terminal, to add google earth to connect to

[LIST]
[*][http://kh.google.com/](http://kh.google.com/)
[*][http://geo.keyhole.com/](http://geo.keyhole.com/)
[*][http://auth.keyhole.com/](http://auth.keyhole.com/)
[/LIST]
on port 80
as google's help points out, and if so how do I do this?

---

### Post by cdenley on 2010-06-02
Unless you are filtering outbound connections, there is no reason for connections to those servers to be filtered by iptables, so there is no reason to allow it. Iptables cannot filter by application. There is no actively supported application firewall for linux that I know of. There is simply not much demand for such a tool, since linux users typically don't need to worry about malware or spyware.
```

nc -z -v -w 5 kh.google.com 80
nc -z -v -w 5 geo.keyhole.com 80
nc -z -v -w 5 auth.keyhole.com 80

```

Where did you install google earth from?

---

### Post by n1ght5t4lk3r on 2010-06-02
> **cdenley said:**
> There is simply not much demand for such a tool, since linux users typically don't need to worry about malware or spyware.
```

nc -z -v -w 5 kh.google.com 80
nc -z -v -w 5 geo.keyhole.com 80
nc -z -v -w 5 auth.keyhole.com 80

```Where did you install google earth from?

Basically thats exactly the impression I have always had, one of the reasons I've 95% dithched windows, but for some reason 10.04 will not initialize any connection to google earth servers, and the error message given points to the link I mentioned, which after going through the options given (even after selecting NO to "are you using windows") gives a useless answer. I looked into ufw manual, even created an app profile for google earth and gave it full, totally unrestricted inward or outward access and still get this issue (have since removed the rule).
the version of GE currently installed is the 5.1 from the software center, but have tried removing it (along with the folders in my home directory) and installing through package manager (same version), then uninstall/re-install from google directly, and also through the googleearth make package. basically i've installed via Every documented "official" method, and even given full 'allowed' (and of course since it didn't work revoked any rules) hasn't made any difference.
A few days ago I was running Ubuntu 9.04 on the SAME machine, running the SAME version of google-earth on the SAME internet connection with zero issues, and after doing a fresh install of Ubuntu 10.04 I cannot use google-earth, despite any others having this issue, even google don't have a solution

---

### Post by OpSecShellshock on 2010-06-02
Do you know for sure that the issue is on the client side? It seems to me that the connection should be allowed out with no problem, and especially so in the case where you created rules to allow it in and out no matter what. Is it possible that this is a server-side issue on Google's end? Does connection to the server require authentication?

---

### Post by cdenley on 2010-06-02
What version of googleearth-package are you using? Are you installing from a third party repository? If I can reproduce your problem, I might be able to fix it. It works fine for me, though. What is the output from the commands I gave? Have you attempted to configure a firewall? Are you using a web filter. Post the output for these commands as well.
```

echo -e "POST /geauth HTTP/1.0\nHost: kh.google.com\n"|nc -q 1 -w 5 kh.google.com 80|head
apt-cache policy googleearth-package
apt-cache policy googleearth

```

---

### Post by n1ght5t4lk3r on 2010-06-03
> **OpSecShellshock said:**
> Does connection to the server require authentication?

its the free version so no user inputed authentication required.




@ cdenley...

here are the outputs as you requested,


```
*****@*****:~$ echo -e "POST /geauth HTTP/1.0\nHost: kh.google.com\n"|nc -q 1 -w 5 kh.google.com 80|head
HTTP/1.0 411 Length Required
Content-Type: text/html; charset=UTF-8
Content-Length: 1363
Date: Thu, 03 Jun 2010 07:34:57 GMT
Server: GFE/2.0



<html><head>
<meta http-equiv="content-type" content="text/html;charset=utf-8">
*****@*****:~$ apt-cache policy googleearth-package
googleearth-package:
  Installed: 0.5.7
  Candidate: 0.5.7
  Version table:
 *** 0.5.7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Packages
        100 /var/lib/dpkg/status
*****@*****:~$ apt-cache policy googleearth
googleearth:
  Installed: 5.1.3533.1731-0medibuntu1
  Candidate: 5.1.3533.1731-0medibuntu1
  Version table:
 *** 5.1.3533.1731-0medibuntu1 0
        500 http://packages.medibuntu.org/ lucid/non-free Packages
        100 /var/lib/dpkg/status

```As I've said a couple of times the thing I don't get is the very same version worked fine for me a few days ago on Jaunty, on the same computer, same internet connection, the only one factor that has changed is I am now using Lucid (from a fresh install)

---

### Post by cdenley on 2010-06-03
Well, you can connect to their server fine, so messing with firewalls won't help. You don't seem to have the most current version, though. Either update your package index then upgrade googleearth from the medibuntu repo (if you have it enabled), or run
```

make-googleearth-package --download

```
(this will take longer)

---

### Post by Pablo Alonso on 2010-06-03
Hi Cdenley, I'm having same issue! so I leave my own output also to help investigation.

------------------------------------------
mfonticelli@ubpc-05:~$ echo -e "POST /geauth HTTP/1.0\nHost: kh.google.com\n"|nc -q 1 -w 5 kh.google.com 80|head
HTTP/1.0 411 Length Required
Content-Type: text/html; charset=UTF-8
Content-Length: 1363
Date: Thu, 03 Jun 2010 17:32:13 GMT
Server: GFE/2.0



<html><head>
<meta http-equiv="content-type" content="text/html;charset=utf-8">
mfonticelli@ubpc-05:~$ apt-cache policy googleearth-package
googleearth-package:
  Instalados: (ninguno)
  Candidato: 0.5.7
  Tabla de versión:
     0.5.7 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Packages
mfonticelli@ubpc-05:~$ apt-cache policy googleearth
googleearth:
  Instalados: 5.1.3533.1731-0medibuntu1
  Candidato: 5.1.3533.1731-0medibuntu1
  Tabla de versión:
 *** 5.1.3533.1731-0medibuntu1 0
        500 [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid/non-free Packages
        500 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Packages
        100 /var/lib/dpkg/status
--------------------------------------

It seems obvious that google earth in lucid dont work fine.
I tested downloading manual package from google directly and it never gets installed. It lasts too long to install and never finishes.
then installed from medibuntu repo and this same problem of this topic, cant connect to server kh.google.com:80 wich is not the case! I think, lucid has any firewall in the default installation that must be manually enable to grant access at this server???

thanks you!

regards,
Pablo alonso

---

### Post by cdenley on 2010-06-03
Ubuntu doesn't filter anything by default. I just noticed that the version built by googleearth-package is not the same as in the medibuntu repositories. I tried both, though, and they work fine for me. Are you using 32-bit or 64-bit?
```

uname -r -m

```

---

### Post by n1ght5t4lk3r on 2010-06-03
I'm running 32-bit.

as for my googleearth, the version I have at this moment is the one from the medibuntu repo , its not built through the make package (I had that installed because I was having this problem and tried installing google-earth via different means but reverted back to the repo version when I had zero luck, never removed the package maker after that)

---

### Post by n1ght5t4lk3r on 2010-06-04
well, at least I've had some replies on the ubuntu community but zero on google's googleearth community (despite a few there having the same issue), thanks for your efforts however unfruitful
I guess this is just another application I'll have to resort to booting into windows for (works fine there on the same machine under vista) along with Vue8

---

### Post by Pablo Alonso on 2010-06-10
Still nothing guys ??? I'm lost.

google earth is the only app that do not work here. everything else is fine.

---

### Post by cariboo on 2010-06-10
I'm running Google Earth from the Medibuntu repositories on Maverick (10.10) with zero problems.

Is anybody that is having problems connecting to Google connecting through a proxy? If so have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=195651&highlight=google+earth+proxy+server").

---

### Post by n1ght5t4lk3r on 2010-06-11
Nope, no proxies used here.

I also tried disabling ipv6 as someone suggested in another thread - 

[http://ubuntuforums.org/showthread.php?t=1367651&page=2](http://ubuntuforums.org/showthread.php?t=1367651&page=2)

It worked for some but still no luck for myself, the strange thing is I mounted my windows partition and ran the windows version of googleearth installed there through WINE and it worked fine, its just the linux version that refuses to connect to google. But since its not exactly a program I "need" to use for anything, or indeed use regularly, I am happy enough to use it via my workaround.

---

### Post by cdenley on 2010-06-11
I installed googlearth on a lucid 32-bit virtual machine, and I still could not reproduce your problem. If you can provide instructions for how to reproduce your problem, someone might be able to help. Perhaps you should see if it will work from a livecd.

---

### Post by sbin on 2010-11-11
I have discovered that GoogleEarth fails to connect to their  servers when my x64 workstation is assigned a static ip address, yet works fine with DHCP. (Other programs such as web browsers work fine with either configuration.)

Any thoughts on this?

---

### Post by cariboo on 2010-11-11
I always set a static ip address, and have no problems connecting to  the googleearth servers. How have you got your dsn addresses set when setting a static ip address?

---

### Post by sbin on 2010-11-13
I had "nameserver 192.168.1.254" on the first line of resolv.conf, using my ISP's dns servers (68.94.156.1 and 68.94.157.1). Then your comment led me to try reverting to a static ip address and then listing "nameserver 8.8.8.8" first in resolv.conf--now GoogleEarth can find its servers. I still don't understand why my other programs worked with the original setup, when GoogleEarth didn't.

---

### Post by sbin on 2010-11-13
I forgot to mention that 192.168.1.254 is the ip address of my gateway (router-modem), and that my ISP's nameservers are set in that device.

---

### Post by cariboo on 2010-11-13
I set the dns addresses on the ipv4 settings page in network manager, /etc/resolv.conf shows the manually set dns addresses.

---

### Post by sbin on 2010-11-13
I run network-manager on my laptop, because it works pretty well with wireless routers; but I seem to have better luck editing config files when it comes to cabled workstations and servers.

---

### Post by cariboo on 2010-11-14
Setting a static ip address using network-manager is not very intuitive. When entering the ip address, netmask and gateway, you have to press enter after each address eg:

[LIST]
[*]192.168.1.225 -> Press Enter
[*]255.255.255.0 -> Press Enter
[*]192.168.1.1 -> Press Enter
[/LIST]

---

