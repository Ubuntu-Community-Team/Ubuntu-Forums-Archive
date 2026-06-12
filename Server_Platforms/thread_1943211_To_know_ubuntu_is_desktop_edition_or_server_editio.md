---
title: "To know ubuntu is desktop edition or server edition using terminal"
date: 2012-03-19
forum: Server Platforms
---

### Post by pavi_elex on 2012-03-19
command for knowing that Ubuntu is server edition or desktop edition.

---

### Post by WasMeHere on 2012-03-19
Hi pavi_elex,

Run
```
uname -a
```
At least it works with Ubuntu 10.04 LTS. The output line contains the string

- server
or
- generic (for the desktop version)

Having fun finding out :-)
Olle

---

### Post by Habitual on 2012-03-19
```
lsb_release -drc
```

---

### Post by Doug S on 2012-04-03
Please know that the kernels have been merged. There is no longer a difference.
The following is extracted from [here:]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel")
 
> As with Beta-1, the Beta-2 kernel no longer carries separate amd64 -server and -generic kernel flavors. These have been merged into a single -generic kernel flavor to help reduce the maintenance burden over the life of this LTS release. i386 systems have had their default kernel changed to PAE. We have also removed the non-SMP PowerPC kernel flavor to help reduce maintenance costs. Hardware coverage is essentially the same between both the SMP and non-SMP PowerPC flavors and any consumers of the non-SMP PowerPC flavor will be automatically upgraded/updated to the SMP PowerPC flavor. I think this was the case for 11.10 also.
 
For example on a 10.10 server computer:```
doug@doug-64:~$ uname -a
Linux doug-64 2.6.35-32-[COLOR=red]server[/COLOR] #66-Ubuntu SMP Mon Feb 13 21:21:41 UTC 2012 x86_64 GNU/Linux
```
 
And on a 12.04 (beta 2) server computer:```
doug@s15:~$ uname -a
Linux s15 3.2.0-21-[COLOR=red]generic[/COLOR] #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```
 
Actually, I no longer know of a command to tell me if I have a desktop installation or a server installation. Usually, I just know.

---

### Post by WasMeHere on 2012-04-03
> **Doug S said:**
> Please know that the kernels have been merged. There is no longer a difference.
The following is extracted from [here:]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel")
 
I think this was the case for 11.10 also.
 
For example on a 10.10 server computer:```
doug@doug-64:~$ uname -a
Linux doug-64 2.6.35-32-[COLOR=red]server[/COLOR] #66-Ubuntu SMP Mon Feb 13 21:21:41 UTC 2012 x86_64 GNU/Linux
```
 
And on a 12.04 (beta 2) server computer:```
doug@s15:~$ uname -a
Linux s15 3.2.0-21-[COLOR=red]generic[/COLOR] #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```
 
Actually, I no longer know of a command to tell me if I have a desktop installation or a server installation. Usually, I just know.
Thank you for this information. It is probably connected to the fact that the desktop version has 5 years of support (as is the case for the previous server LTS versions). So in practise, check if the are some server programs running (e.g. sshd)!
```
ps -A|grep " sshd$"
```
Because then it is a server, even if it was installed from the desktop flavour ;-)

---

### Post by jerome1232 on 2012-04-03
You can check sources.list for what cd they used to install, but the big question is why does it matter, the two are pretty much the same, the server edition just lets you install less during the installation process.

```
cat /etc/apt/sources.list | grep 'deb cdrom'
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

```

---

