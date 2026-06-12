---
title: "Update problem with broken package"
date: 2011-02-01
forum: Server Platforms
---

### Post by onehitxzibit on 2011-02-01
When I try to do "apt-get upgrade" and/or "apt-get dist-upgrade" I get > The following packages have been kept back: upstart

I tried installing upstart manually and it says the package is broken. 

> root@server:/home/onehitxzibit# apt-get install upstart
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2-mpm-prefork : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
 apache2.2-common : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
                    Depends: apache2-utils but it is not going to be installed
                    Depends: lsb-base but it is not going to be installed
                    Depends: procps but it is not going to be installed
                    Depends: perl but it is not going to be installed
                    Recommends: ssl-cert but it is not going to be installed
 libc6 : Depends: libgcc1 but it is not going to be installed
         Depends: findutils (>= 4.4.0-2ubuntu2) but it is not going to be installed
 libgssapi-krb5-2 : Depends: libkeyutils1 but it is not going to be installed
                    Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not going to be installed
 libk5crypto3 : Depends: libkeyutils1 but it is not going to be installed
                Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not going to be installed
 libkrb5-3 : Depends: libkeyutils1 but it is not going to be installed
             Depends: libkrb5support0 (= 1.8.1+dfsg-5ubuntu0.2) but it is not going to be installed
 libssl0.9.8 : Depends: debconf (>= 0.5) but it is not going to be installed or
                        debconf-2.0
 php5-common : Depends: sed (>= 4.1.1-1) but it is not going to be installed
 tzdata : Depends: debconf (>= 0.5) but it is not going to be installed or
                   debconf-2.0
 ucf : Depends: debconf (>= 1.5.19) but it is not going to be installed
       Depends: coreutils (>= 5.91) but it is not going to be installed
 upstart : Depends: libdbus-1-3 (>= 1.2.16) but it is not going to be installed
           Depends: libnih-dbus1 (>= 1.0.0) but it is not going to be installed
           Depends: libnih1 (>= 1.0.0) but it is not going to be installed
           Depends: libudev0 (>= 151) but it is not going to be installed
           Depends: sysvinit-utils but it is not going to be installed
           Depends: sysv-rc but it is not going to be installed
           Depends: initscripts but it is not going to be installed
           Depends: mountall but it is not going to be installed
           Depends: ifupdown (>= 0.6.8ubuntu29)
           Breaks: libc6 (< 2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu10.1 is to be installed
E: Broken packages


Running Ubuntu Server Edition 10.10. Does anyone know a solution to this problem?

---

### Post by bapoumba on 2011-02-01
Have you checked your /etc/apt/sources.list ?

---

### Post by onehitxzibit on 2011-02-01
> **bapoumba said:**
> Have you checked your /etc/apt/sources.list ?

I haven't modified anything here.

---

### Post by bapoumba on 2011-02-01
Hmm. If you are using a repository close to your location, please try the main repositories, reload the sources.list (update) and run the dist-upgrade again.

---

### Post by onehitxzibit on 2011-02-01
Changed to main repositories, ran update and then dist-upgrade but the problem remains. Same thing with trying to manually install "upstart". Apparently there's a conflict with libc6 package. 
> Breaks: libc6 (< 2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu10.1 is to be installed

---

### Post by bapoumba on 2011-02-01
[http://ubuntuforums.org/showthread.php?t=1679862](http://ubuntuforums.org/showthread.php?t=1679862)
Thanks for the error. Looks like there are some problems with today's updates.
If I look here with update-manager (I understand you may not have a graphic interface) upstart is in the list but is unchecked.

I would check the other thread as well and probably wait the repos and packages get straiten up. You are not alone, a google search gives several similar situations.

Edit, I have not found any bug report. You may want to fill a new one.

---

### Post by stmiller on 2011-02-01
[https://launchpad.net/ubuntu/+source/upstart/0.6.6-4](https://launchpad.net/ubuntu/+source/upstart/0.6.6-4)

Looks like an update was pushed to prevent this horrible bug:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/672177](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/672177)

...but is now causing a conflict in 10.10.

---

### Post by stmiller on 2011-02-02
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/711601](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/711601)

Update - looks like a fix should be hitting the mirrors soon.

> The problem appears to have been caused by a delay in the required libc6 update moving from maverick-proposed to maverick-updates. This issue has been resolved, so please retry the upgrade to ensure it works as expected for you.


:)

---

### Post by onehitxzibit on 2011-02-02
I can confirm it's fixed. Works like a charm after newest update. :)

---

### Post by bapoumba on 2011-02-02
> **onehitxzibit said:**
> I can confirm it's fixed. Works like a charm after newest update. :)

Glad to see you got it sorted out :)

---

