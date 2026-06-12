---
title: "pre-testing auto upgrader for point release- ubuntu-gnome fails"
date: 2016-07-09
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-09
I am trying to auto-upgrade an install of ubuntu-gnome 15.10 to 16.04 and I get the pop up window and select  'upgrade' but nothing happens. 

 I have full upgraded wily install and rebooted.
1. What package do I file the  bug against?
2. What is terminal command  to auto-upgrade to xenial?

Regards..

---

### Post by kansasnoob on 2016-07-09
Did you fully update Wily? It should just offer the upgrade after updating and then rebooting because the update-mangler should run again after boot ................ I think?????

I'm not sure if this command will offer an upgrade to Xenial or Yakkety:

```
update-manager -d -c
```

Bugs would be filed against the proper version of ubuntu-release-upgrader. In fact this might be enough:

```
ubuntu-bug ubuntu-release-upgrader
```

If not you might have to use apt to see what specific packages are used in that flavor. Like right now I'm in Xenial Ubuntu MATE:

```
lance@lance-amd-desktop:~$ apt-cache policy ubuntu-release-upgrader*
ubuntu-release-upgrader-qt:
  Installed: (none)
  Candidate: 1:16.04.14
  Version table:
     1:16.04.14 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     1:16.04.12 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
ubuntu-release-upgrader-core:
  Installed: 1:16.04.14
  Candidate: 1:16.04.14
  Version table:
 *** 1:16.04.14 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:16.04.12 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
ubuntu-release-upgrader-gtk:
  Installed: 1:16.04.14
  Candidate: 1:16.04.14
  Version table:
 *** 1:16.04.14 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:16.04.12 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages

```

---

### Post by ventrical on 2016-07-09
OK kansasnoob. I'll try that.

Thanks ! 

Regards..

---

### Post by ventrical on 2016-07-09
Before I could get it to work I had to set it in software&updates to 'notify LTS versions only' and so now it tells me that I modified the upgrades... so there is the circular bug.

edit:  [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1600495](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1600495)

---

### Post by ventrical on 2016-07-09
> **kansasnoob said:**
> Did you fully update Wily? It should just offer the upgrade after updating and then rebooting because the update-mangler should run again after boot ................ I think?????

I'm not sure if this command will offer an upgrade to Xenial or Yakkety:

```
update-manager -d -c
```



And I get the circular pop-up fail.

---

### Post by ventrical on 2016-07-09
Ok.. wait .. wait ... I have the mkusb ppa installed. I will add msg to bug report. I will disable mkusb ppa and try again.

Ok.. still mangled up . Not mkusb ppa.

---

### Post by kansasnoob on 2016-07-09
I subscribed to that bug report. I'll try to test that this weekend yet. This could be a really huge deal because Wily is almost EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ventrical on 2016-07-09
I have another install of wily ubuntu-gnome 15.10. I fully updated , rebooted but no upgrader greeter  so I am going ot try the command you suggested and see if this one will upgrade.

regards..

---

### Post by ventrical on 2016-07-09
Ok.. now got a totally different icon and alterter. (theme) 
edit: ok .. here goes..

---

### Post by ventrical on 2016-07-09
@kansasnoob

gimmee about an hour and a half and I'll try out those trustys.

regards..

---

### Post by kansasnoob on 2016-07-09
> **ventrical said:**
> Ok.. now got a totally different icon and alterter. (theme) 
edit: ok .. here goes..

Did that pop-up on its own or did you have to manually start it?

---

### Post by ventrical on 2016-07-09
On other install the gdm greeter/login locks up and will not let you log on although you can get to terminal. Since it has downloaded all files and is installing now I'll have to wait a while until I shut down. This is two fails now with ubuntu-gnome upgrades from 15.10 to 16.04 using the automated update-manager. Looks like gnome got thrown under the bus as far as upgrading from wily version.

regards..

---

### Post by ventrical on 2016-07-09
> **kansasnoob said:**
> Did that pop-up on its own or did you have to manually start it?

Used ..
```

update-manager -d -c

```

---

### Post by ventrical on 2016-07-09
With a great degree of work in the terminal I was able to fix broken upgrade of install from 15.10 to 16.04. ubuntu-gnome desktop. When new, younger users try this process ( or are prompted to try it by wily EOL) it will be a great disappointment I am afraid.

Regards..

---

### Post by ventrical on 2016-07-14
Unfortunately I had  upgraded with nVidia driver installed. (gotta test the nvidia drivers .. right? ) 

it resulted in relics in plymouth followed by the huge nVida logo. I removed nVidia drivers and install nouveau-frimware, rebooted and after login the desktop screen presented itself with an inverted screen, held for 2 seconds and then reset to to normal desktop. I removed nouveau and re-install nvidia. The relics are still there during bootup but the logo is gone.

Regards..

---

