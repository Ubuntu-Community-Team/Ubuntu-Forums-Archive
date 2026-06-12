---
title: "another way to test Unity8 = lxc"
date: 2014-12-13
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-12-13
Here is the link

[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

It installs fine on Vivid and at the LightDM login screen we get the additional option of Unity8 in LXC.

It downloads the ubuntu-desktop-next ISO from cdimage. That will take the usual time but installation is very fast and it uses the user name and password of the host Ubuntu install. When I installed this it was on a Ubuntu that was not connected to WiFi and Unity8 does not allow the setting up of a WiFi connection. An earlier hard disk install of desktop next did allow setting up WiFi. So, I do not know if this a bug or due to not having a WiFi connection to start with.

We cannot use apt-get to update/grade. We use this

```
sudo unity8-lxc-setup --update-lxc
```

That seems to upate whatever is in the LXC container from the standard Vivid repositories. And then there is this

```
sudo unity8-lxc-setup --rebuild-all --redownload
```

That seems to do a zsync with the latest cdimage ubuntu-desktop-next daily ISO image. Again installing is very fast as if it is not using the dpkg method. Or whatever usually happens.

By the way, the latest code put applications in their own resizable window. And the apps in the launcher are now top down instead of bottom up. It is starting to look more like a desktop UI than a phone UI.

Regards.

---

### Post by zika on 2014-12-13
Now, apart from (seemingly not (yet, until convergence ends) interested in) Unity8, You've made me start getting heightened level of interest in [LXC]("https://help.ubuntu.com/lts/serverguide/lxc.html") ... Thank You.
```
:~$ sudo apt-get install -s lxc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bridge-utils cloud-image-utils debootstrap distro-info distro-info-data
  euca2ools libaio1 libboost-thread1.55.0 liblxc1 librados2 librbd1
  libseccomp2 lxc-templates python-distro-info python-ndg-httpsclient
  python-requestbuilder python-requests python-setuptools python-support
  python-urllib3 python3-lxc qemu-utils sharutils uidmap
Suggested packages:
  shunit2 btrfs-tools lvm2 lxctl qemu-user-static bsd-mailx mailx
The following NEW packages will be installed:
  bridge-utils cloud-image-utils debootstrap distro-info distro-info-data
  euca2ools libaio1 libboost-thread1.55.0 liblxc1 librados2 librbd1
  libseccomp2 lxc lxc-templates python-distro-info python-ndg-httpsclient
  python-requestbuilder python-requests python-setuptools python-support
  python-urllib3 python3-lxc qemu-utils sharutils uidmap
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Inst libaio1 (0.3.110-1 Ubuntu:15.04/vivid [amd64])
Inst libboost-thread1.55.0 (1.55.0+dfsg-3ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst libseccomp2 (2.1.1-1 Ubuntu:15.04/vivid [amd64])
Inst liblxc1 (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst librados2 (0.87-0ubuntu2 Ubuntu:15.04/vivid [amd64])
Inst librbd1 (0.87-0ubuntu2 Ubuntu:15.04/vivid [amd64])
Inst python-urllib3 (1.9.1-3 Ubuntu:15.04/vivid [all])
Inst python-requests (2.4.3-5 Ubuntu:15.04/vivid [all])
Inst python-requestbuilder (0.2.3-1 Ubuntu:15.04/vivid [all])
Inst bridge-utils (1.5-7ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst distro-info-data (0.24 Ubuntu:15.04/vivid [all])
Inst distro-info (0.14 Ubuntu:15.04/vivid [amd64])
Inst python-setuptools (5.5.1-1 Ubuntu:15.04/vivid [all])
Inst euca2ools (3.1.0-1 Ubuntu:15.04/vivid [all])
Inst python3-lxc (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst lxc (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst lxc-templates (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Inst python-distro-info (0.14 Ubuntu:15.04/vivid [all])
Inst python-support (1.0.15 Ubuntu:15.04/vivid [all])
Inst python-ndg-httpsclient (0.3.2-1 Ubuntu:15.04/vivid [all])
Inst qemu-utils (2.1+dfsg-7ubuntu5 Ubuntu:15.04/vivid-proposed [amd64])
Inst sharutils (1:4.14-2 Ubuntu:15.04/vivid [amd64])
Inst uidmap (1:4.1.5.1-1.1ubuntu3 Ubuntu:15.04/vivid [amd64])
Inst cloud-image-utils (0.27-0ubuntu10 Ubuntu:15.04/vivid [all])
Inst debootstrap (1.0.66 Ubuntu:15.04/vivid [all])
Conf libaio1 (0.3.110-1 Ubuntu:15.04/vivid [amd64])
Conf libboost-thread1.55.0 (1.55.0+dfsg-3ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf libseccomp2 (2.1.1-1 Ubuntu:15.04/vivid [amd64])
Conf liblxc1 (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf librados2 (0.87-0ubuntu2 Ubuntu:15.04/vivid [amd64])
Conf librbd1 (0.87-0ubuntu2 Ubuntu:15.04/vivid [amd64])
Conf python-urllib3 (1.9.1-3 Ubuntu:15.04/vivid [all])
Conf python-requests (2.4.3-5 Ubuntu:15.04/vivid [all])
Conf python-requestbuilder (0.2.3-1 Ubuntu:15.04/vivid [all])
Conf bridge-utils (1.5-7ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf distro-info-data (0.24 Ubuntu:15.04/vivid [all])
Conf distro-info (0.14 Ubuntu:15.04/vivid [amd64])
Conf python-setuptools (5.5.1-1 Ubuntu:15.04/vivid [all])
Conf euca2ools (3.1.0-1 Ubuntu:15.04/vivid [all])
Conf python3-lxc (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf lxc (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf lxc-templates (1.1.0~alpha3-0ubuntu1 Ubuntu:15.04/vivid [amd64])
Conf python-distro-info (0.14 Ubuntu:15.04/vivid [all])
Conf python-support (1.0.15 Ubuntu:15.04/vivid [all])
Conf python-ndg-httpsclient (0.3.2-1 Ubuntu:15.04/vivid [all])
Conf qemu-utils (2.1+dfsg-7ubuntu5 Ubuntu:15.04/vivid-proposed [amd64])
Conf sharutils (1:4.14-2 Ubuntu:15.04/vivid [amd64])
Conf uidmap (1:4.1.5.1-1.1ubuntu3 Ubuntu:15.04/vivid [amd64])
Conf cloud-image-utils (0.27-0ubuntu10 Ubuntu:15.04/vivid [all])
Conf debootstrap (1.0.66 Ubuntu:15.04/vivid [all])
```tightly and neatly woven fabric without much (if any) stray fibers.

---

### Post by mc4man on 2014-12-13
Will have to try as no real interest in a standalone install.
The wireless thing seems like a bug, will give it a try.
(-  though on this laptop where I run ubuntu via a usb 3 ssd I only use ethernet now due to usb 3's  radiation/interference with the laptop's wireless

---

### Post by grahammechanical on 2014-12-13
> [COLOR=#000000]You've made me start getting heightened level of interest in [/COLOR][LXC]("https://help.ubuntu.com/lts/serverguide/lxc.html")[COLOR=#000000] [/COLOR]

Same here. Now wouldn't this be a useful way to run other distros? My machine has only 1GB RAM. So, a VM is next to useless. But these LXC containers are another thing entirely. No usability problems like I have with a VM.

Regards.

---

### Post by ventrical on 2014-12-14
[s]The other current unity8 next is opening now with Setup Session  after login. May give this a try. [/s]

Edit: Apologies . Belongs here.  
[http://ubuntuforums.org/showthread.php?t=2248940&page=6&p=13187556#post13187556](http://ubuntuforums.org/showthread.php?t=2248940&page=6&p=13187556#post13187556)
Regards..

---

### Post by grahammechanical on 2014-12-15
I am starting to think that the inability to set up WiFi access is not a bug but a security feature of Linux containers. 

> [COLOR=#333333][FONT=Ubuntu]It is possible to create a container without a private network namespace. In this case, _the container will have access to the host networking like any other application._ Note that this is particularly dangerous if the container is running a distribution with upstart, like Ubuntu, since programs which talk to init, like [/FONT][/COLOR][COLOR=#333333][FONT=monospace]shutdown[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu], will talk over the abstract Unix domain socket to the host's upstart, and shut down the host.[/FONT][/COLOR]

[https://help.ubuntu.com/lts/serverguide/lxc.html](https://help.ubuntu.com/lts/serverguide/lxc.html)

So, not wanting to take this thread off topic (testing unity8 in LXC on vivid) I will say that the image update method works well. Other than that, there is not much else to report, except that Browser does access the internet. Must be using the ethernet connection. The app store does not install apps (known bug) and there is no access to a tty/VT (known bug). so, at the moment it is hard power off to shutdown.

Regards.

---

### Post by ventrical on 2014-12-15
I looked at the link you have provided and this model had now descended to the unity8-desktop-next project. The only difference is that the ppa may provide earlier cutting edge gizzmos to test.

Regards..

---

### Post by grahammechanical on 2014-12-16
> [COLOR=#000000]this model had now descended to the unity8-desktop-next project.[/COLOR]

Yes, the unity8-lxc-setup command downloads from the daily live current image of ubuntu-desktop-next from cdimage.ubuntu. Likewise, the unity8-lxc-setup --rebuild-all --redownload command zsyncs from the same place.

I have been researching the LXC commands. a discussion of which would not be appropriate for this section of the forum, I do not think. But we can do work on Linux containers (LXC) using the terminal in the host Ubuuntu desktop.

I think there is a way to set up WiFi for an LXC container. Although it is not necessary in my case as I use ethernet most of the time. I guess having a WiFi connection for an LXC container is not considered necessary because LXC is usually used on servers not desktops. But there is a script that editing may solve the problem.

I am also tempted to try to install another LXC container running another version of Ubuntu. Again, a subject not applicable for this section. The usefulness of doing that will depend on whether we get a login session as we do with Unity8 in LXC. Or is that done through some special script? Which I am ignorant of.

Regards.

---

### Post by ventrical on 2014-12-16
Well .. we're here to test so I'll give this a spin.

Regards..

---

### Post by ventrical on 2014-12-16
It's downloading the desktop-next iso from daily-live/current. I don't get it. But maybe I will soon :)

edit:

Whats happening here? ...

```

ventrical@ventrical-MS-7798:~$ sudo unity8-lxc-setup
#################### 100.0% 266.8 kBps DONE     

open: No such file or directory
not using seed file /var/lib/lxc/unity8-lxc/ubuntu-next.iso
Read /var/lib/lxc/unity8-lxc/ubuntu-next.iso. Target 0.0% complete.      
No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/vivid-desktop-amd64.iso:
-------------------- 1.8% 15.6 kBps         TA   
-------------------- 3.9% 8.6 kBps         ETA   

```

---

### Post by ventrical on 2014-12-16
> **grahammechanical said:**
> Here is the link

[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

It installs fine on Vivid and at the LightDM login screen we get the additional option of Unity8 in LXC.

It downloads the ubuntu-desktop-next ISO from cdimage. That will take the usual time but installation is very fast and it uses the user name and password of the host Ubuntu install. 

Ahhh... ok.. so far so good.

---

### Post by ventrical on 2014-12-16
Epic fail. Will not accept password.

Regards..

---

