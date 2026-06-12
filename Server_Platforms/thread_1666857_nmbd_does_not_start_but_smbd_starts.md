---
title: "nmbd does not start but smbd starts"
date: 2011-01-14
forum: Server Platforms
---

### Post by Felipesm on 2011-01-14
The time the server smbd and nmbd functioned normally but when I restart the service he returned smbd nmbd not normal but when I try to start it the following error occurs:

```
 service nmbd start
start: Job failed to start

 service nmbd status
nmbd stop/waiting


```

and when I try one of the most testparm an error:

```

Traceback (most recent call last):
   File "/ usr / bin / testparm", line 43, in <module>
     import samba
ImportError: No module named samba
```

Anyone know the solution?
Thanks for help

---

### Post by Felipesm on 2011-01-14
I solved the problem removing all dependencies of samba and reinstall the samba,I think the samba is conflicting with other versions.

---

### Post by roadrawts on 2011-03-09
I have the same problem "nmbd failed to start".  Removed and apt-get install samba again did not solve the problem.  I am using ubuntu 10.10.  Any suggestions.  Using webmin to setup samba.

---

### Post by patrik_peki on 2011-05-28
I got similar problem when i installed swat,

I removed all dependencies and openbsd_inetd and cleaned aptitude then I installed samba and it works now

Hope I help :)

---

### Post by papibe on 2011-05-28
It's a bug: [nmbd doesn't start because of missing testparm]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410").

This solve it:
```
$ sudo dpkg-reconfigure samba-common-bin
```

Regards.

---

### Post by vista.tec on 2011-12-03
HI,
I removed nmbd @ BOOT and now SAMBA works @ boot

> sudo update-rc.d -f nmbd removebsa

:D

---

### Post by bab1 on 2011-12-03
> **vista.tec said:**
> HI,
I removed nmbd @ BOOT and now SAMBA works @ boot

bsa

:D
You need both **smbd** and **nmbd** for Samba to work correctly.  At minimum you should have 2 instances of **smbd** and 1 of **nmbd**.

```
root       939     1  0 Dec02 ?        00:00:00 smbd -F
root      1063     1  0 Dec02 ?        00:00:00 nmbd -D
root      1085   939  0 Dec02 ?        00:00:00 smbd -F

```

---

### Post by vista.tec on 2011-12-05
> **bab1 said:**
> You need both **smbd** and **nmbd** for Samba to work correctly.  At minimum you should have 2 instances of **smbd** and 1 of **nmbd**.

```
root       939     1  0 Dec02 ?        00:00:00 smbd -F
root      1063     1  0 Dec02 ?        00:00:00 nmbd -D
root      1085   939  0 Dec02 ?        00:00:00 smbd -F

```

:confused: u are correct ... I was drunk or may be Saturday ...

so ... start again

---

### Post by vista.tec on 2011-12-05
Followed this link

[http://ubuntuforums.org/archive/index.php/t-1663668.html](http://ubuntuforums.org/archive/index.php/t-1663668.html)

it seems now it works 

bsa

---

### Post by vista.tec on 2011-12-05
Ah ! now it works really
not drunk or stupid (I hope as this is last chance )
> 
Thus, /etc/init/nmbd.conf content should be:
 description "NetBIOS name server"
author      "Steve Langasek <email address hidden>"
 start on (local-filesystems)
stop on runlevel [!2345]
 expect fork
respawn
 pre-start script
 **mkdir -p /var/run/samba**
  [ -f /etc/samba/smb.conf ] || { stop; exit 0; }
  install -o root -g root -m 755 -d /var/run/samba
 NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null`
  [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }
  exit 0
end script
 exec nmbd -D

Link

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/750786](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/750786)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/823878](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/823878)
[https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/596064](https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/596064)


Hope this help someone



Bsa

---

### Post by bab1 on 2011-12-05
> **vista.tec said:**
> Ah ! now it works really
not drunk or stupid (I hope as this is last chance )
Link

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/750786](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/750786)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/823878](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/823878)
[https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/596064](https://bugs.launchpad.net/ubuntu/lucid/+source/samba/+bug/596064)


Hope this help someone



Bsa
That is what I did and it works for me,

---

