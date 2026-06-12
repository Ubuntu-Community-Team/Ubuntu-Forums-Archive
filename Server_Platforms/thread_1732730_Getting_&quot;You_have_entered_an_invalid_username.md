---
title: "Getting &quot;You have entered an invalid username or password&quot; - Netatalk/Avahi"
date: 2011-04-18
forum: Server Platforms
---

### Post by Slason on 2011-04-18
I followed this guide: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#volumes](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#volumes)

When I try to connect to my ubuntu server with my mac, I always get "You have entered an inncorrect username or password, please try again". 

The same problem occured when I tried to connect to another mac server at my school. Is this a mac wide problem? Anyone else experienced this problem?

So the big question is, is it the mac or ubuntu? Any suggestions?

---

### Post by usatonycuba on 2011-04-20
First of all, sorry if my post (it may) not help you...   my comments  are only from my own point of view to your issue... I have not read the full tutorial (of your above link) (too long), but I have some concerns, that may give you an starting point.

First, by default Ubuntu does not have the root user of the system set, ie .. whether you did to set up netatalk, (if) the system user that you entered (you set) was the sys-admin (Ubuntu admin) is very possible that your Ubuntu box, it may denied access because he takes it as root, and not as a regular user. .. the best way would set up a regular-user and give him the necessary privileges and permissions.

Second, what distro of Ubuntu did you installed for this tutorial ...? (I think an old one).. (if so) what's the point using an old Distro... wich has reaches his end-of-life?

Ubuntu, updated all packages and repositories on an ongoing basis, and you'll always be able to find new Distros, with BETTER implementation, most secure and complete .. on the other hand, why install a software package wich has "his own going on troubles"... ??
> 
**FROM 2008** :confused:

Apple will add some undocumented AFP commands with the Mac OS X 10.5.6 update which therefor won&#8217;t be supported by the current Netatalk package (and maybe never will). So be sure to check the latest comments on this article when the 10.5.6 update is out to see if this rumor is true and if there are problems caused by that.


Another thing I'm wondering..? ..Ubuntu has included a system called AppArmor wich is installed by default,... Do you have installed in your Ubuntu box >> AppArmor?... I guess you have .... So, you may wanna take look at it.. because AppArmor adds access control to specific system services.

---

### Post by wdpreez1 on 2011-05-19
> **Slason said:**
> I followed this guide: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#volumes](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#volumes)

When I try to connect to my ubuntu server with my mac, I always get "You have entered an inncorrect username or password, please try again". 


I had the same problem accessing netatalk on Ubuntu 11.04 from OS X 10.6.7. I followed the kremalicious guide too, except that in the end I realised the netatalk 2.1.4-1 in the Ubuntu repository now works too.

The problem in my case turned out to be the UAM (user authentication mechanism) used by afpd. The kremalicious guide counsels as follows on the configuration in /etc/netatalk/afpd.conf
```
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh

```

When I enabled substantial debugging on afpd on Ubuntu, I saw that it could not find uams_randnum.so or uams_dhx.so in /usr/lib/netatalk, so instead I used uams_dhx2.so, like so: 
```
- -transall -uamlist uams_dhx2.so -nosavepassword -advertise_ssh 
```

After a restart of afpd that worked!

---

### Post by tuwe on 2011-08-05
> **wdpreez1 said:**
> I had the same problem accessing netatalk on Ubuntu 11.04 from OS X 10.6.7. I followed the kremalicious guide too, except that in the end I realised the netatalk 2.1.4-1 in the Ubuntu repository now works too.

The problem in my case turned out to be the UAM (user authentication mechanism) used by afpd. The kremalicious guide counsels as follows on the configuration in /etc/netatalk/afpd.conf
```
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh

```

When I enabled substantial debugging on afpd on Ubuntu, I saw that it could not find uams_randnum.so or uams_dhx.so in /usr/lib/netatalk, so instead I used uams_dhx2.so, like so: 
```
- -transall -uamlist uams_dhx2.so -nosavepassword -advertise_ssh 
```

After a restart of afpd that worked!

thank you!

---

### Post by mattybe on 2012-01-03
Thanks! That just saved me as well!

---

### Post by Chadwick Crawford on 2012-03-10
Has anyone come up with another solution to this problem? That one hasn't worked for me.

---

### Post by xdracco on 2012-09-20
> **Chadwick Crawford said:**
> Has anyone come up with another solution to this problem? That one hasn't worked for me.

So what do your logs say? If you're not logging AFP, do so with the following in /etc/netatalk/afpd.conf:

```
# AFPd Logging
- -setuplog "AFPDaemon log_info /var/log/netatalk/afpd.log" \
  -setuplog "UAMSDaemon log_info /var/log/netatalk/uams.log" \
  -setuplog "Default log_info /var/log/netatalk/netatalk.log"
```

---

