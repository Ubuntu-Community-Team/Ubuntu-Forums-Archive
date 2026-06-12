---
title: "Request: K3B 0.12 and wget 1.10"
date: 2005-06-14
forum: Ubuntu Backports
---

### Post by abandoned_hussam on 2005-06-14
Is it possible to make these two packages for Hoary?
- K3B 0.12 ( I'm sure i'm not the only one who wants this one :) )
- Wget 1.10 ( it's already in debian unstable )

Thanks in advance :)

---

### Post by jdong on 2005-06-14
Neither are in Breezy yet. Let's wait.

---

### Post by Mez on 2005-06-15
I'll update to k3b 0.11.24 (the latest stable version) which I built for Breezy

---

### Post by _MiniMe_ on 2005-06-15
Hi,

I tried to update to 0.11.24 today, but it doesn't work because of failed dependency:

k3blibs needs kdelibs4 (>=4:3.4.1) but there is just 4:3.4.0-0ubuntu3.2 available...

I cannot find any version of kdelibs4 in one of the backport-mirrors

---

### Post by man.life on 2005-06-15
**Maybe** this will help:

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

---

### Post by Mez on 2005-06-15
[QUOTE=_MiniMe_]Hi,

I tried to update to 0.11.24 today, but it doesn't work because of failed dependency:

k3blibs needs kdelibs4 (>=4:3.4.1) but there is just 4:3.4.0-0ubuntu3.2 available...

I cannot find any version of kdelibs4 in one of the backport-mirrors[/QUOTE]

I may have uploaded the wrong deb - I'll check this in a mo

---

### Post by whatever on 2005-06-15
[QUOTE=_MiniMe_]Hi,

I tried to update to 0.11.24 today, but it doesn't work because of failed dependency:

k3blibs needs kdelibs4 (>=4:3.4.1) but there is just 4:3.4.0-0ubuntu3.2 available...

I cannot find any version of kdelibs4 in one of the backport-mirrors[/QUOTE]
same problem here

---

### Post by dlpfmVfH on 2005-06-15
checked the recommend packages...movixmaker...
but inside k3b it still says no emovix found...

how can I change that??

---

### Post by Mez on 2005-06-15
Seeing as I'm using kubuntu - I built with the latest version of KDe (3.4.1) that's why

I'll edit my pbuild and change it so it doesnt use the latest kde version.

---

### Post by Mez on 2005-06-15
fixed - and uploded to staging

---

### Post by _MiniMe_ on 2005-06-16
Installation now works! Thx man!

But there is another problem: it crashes. Even after a reboot it hangs when scanning for devices. The last version had the same problem only when starting for the first time. After a reboot it worked perfectly. But this one doesn't even start. Maybe you should leave it in staging till some more testing is done?

---

### Post by _MiniMe_ on 2005-06-16
OK, there seems to be a serious problem. I always end up with a running k3b process that doesn't work and is impossible to kill.

I've made a downgrade back to 0.11.23 (which worked fine before) but now even that version hangs everytime. I haven't changed anything else. Really no good...

---

### Post by _MiniMe_ on 2005-06-16
It works again! At least version 0.11.23. But I got no idea what was wrong. Just went out, got something to eat, came back, turned the computer on and it started as normal.  I've rebooted the system before at least 5 times... ](*,)

The only output I get now is this:

DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-remrot"
Link points to "/tmp/kde-remrot"
kbuildsycoca running...
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!

I really look forward to the day when projects like gnomebaker or graveman get more stable (and some more functionality) so I can get rid of this confusing k3b...

---

### Post by Mez on 2005-06-16
I suggest adding the following line to your /etc/apt/sources.list - this will make sure you can have the latest version of things like k3b

```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
```

---

### Post by _MiniMe_ on 2005-06-16
[QUOTE=Mez]I suggest adding the following line to your /etc/apt/sources.list - this will make sure you can have the latest version of things like k3b

```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
```[/QUOTE]

Do you really think that it's a good idea to mix ubuntu and kubuntu packages? I just ask because I tried mixing debian and ubuntu .debs a few weeks ago (I had to, cause I couldnt find another solutionat that time) and ended up with some strange problems. They are almost gone now (after many downgrades), but I don't want similar problems again...

Has anyone tried this?

---

### Post by Mez on 2005-06-16
kubuntu = the KDE stuff of ubuntu.

It's quite safe to do... kubuntu IS ubuntu - the only diffeence is what it installs by default - it uses the exact same packages etc etc.

I'm using this perfectly well... all that that deb line does is let you use the latest kde libs... which you need to run things like k3b

debain and ubuntu are completely different. It's perfectly safe to mix kubuntu and ubuntu - as they are the same thing, but to mix ubuntu asnd debian can be sdangerous (hence why we strongly adivse to use backports instead of marillat

---

### Post by jdong on 2005-06-16
[QUOTE=_MiniMe_]Do you really think that it's a good idea to mix ubuntu and kubuntu packages? I just ask because I tried mixing debian and ubuntu .debs a few weeks ago (I had to, cause I couldnt find another solutionat that time) and ended up with some strange problems. They are almost gone now (after many downgrades), but I don't want similar problems again...

Has anyone tried this?[/QUOTE]

One second. I'll consult #ubuntu-devel about this.

---

### Post by dlpfmVfH on 2005-06-17
I'm running ubuntu and kubuntu at the same time...
have the kubuntu repository in my sources.list...

Haven't had a problem yet...even k3b installs perfectly...
Only problem that is that the emovix package isn't found...

tried the movixmaker package...but it wasn't recognized...

---

