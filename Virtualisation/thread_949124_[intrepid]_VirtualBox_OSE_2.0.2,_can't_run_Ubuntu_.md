---
title: "[intrepid] VirtualBox OSE 2.0.2, can't run Ubuntu Hardy 8.04.1"
date: 2008-10-15
forum: Virtualisation
---

### Post by altonbr on 2008-10-15
Running VirtualBox OSE 2.0.2 on Intrepid 8.10, I can't run a Ubuntu Hardy 8.04.1 server guest.

```
$ lsb_release -a && apt-cache policy virtualbox-ose
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Codename:	intrepid
virtualbox-ose:
  Installed: 2.0.2-dfsg-0ubuntu3
  Candidate: 2.0.2-dfsg-0ubuntu3
  Version table:
 *** 2.0.2-dfsg-0ubuntu3 0
        500 http://archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status
```

I receive this error after installing Ubuntu Hardy 8.04.1 (server):
```
Starting up...
The kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU
```

It doesn't appear to like the 2.6.24-server kernel :/

---

### Post by AceRimmer on 2008-10-20
> **altonbr said:**
> Starting up...
The kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU[/code]It doesn't appear to like the 2.6.24-server kernel :/

I'm getting this same error under 8.04 desktop and on my Vista laptop.

---

### Post by Shaythong on 2008-10-20
I'm not sure but you can try this: [https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

[quote=Roborov]You can use server installation CD to boot into rescue mode.
After mount the root partition of installed harddisk and get the # prompt, run this command "apt-get install linux-virtual".

This will help you get the linux kernel customized for VM environment.
You might need to run this command if installation not success - "apt-get build-dep linux-virtual".

Grub menu won't be changed in some case so you have to edit /boot/grub/menu.lst to boot with the virtual customized kernel.[/quote]

---

