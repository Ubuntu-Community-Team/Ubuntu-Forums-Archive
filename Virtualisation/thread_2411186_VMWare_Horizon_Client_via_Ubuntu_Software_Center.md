---
title: "VMWare Horizon Client via Ubuntu Software Center"
date: 2019-01-26
forum: Virtualisation
---

### Post by herschen on 2019-01-26
I’ve followed the instructions below to install VMWare Horizon Client 4.10 via Ubuntu Software Center on Ubuntu 18.10:
[https://docs.vmware.com/en/VMware-Horizon-Client-for-Linux/4.6/linux-client-installation/GUID-E359F493-B6AF-4AAA-BAC3-E6DA87C57FC6.html](https://docs.vmware.com/en/VMware-Horizon-Client-for-Linux/4.6/linux-client-installation/GUID-E359F493-B6AF-4AAA-BAC3-E6DA87C57FC6.html)

However, even after I’ve enabled Canonical Partners, restarted Ubuntu Software Center and ran sudo apt-get update  from the terminal window I get nothing. I’ve searched for VMWare, VMWare Horizon Client and vmware-view-client. This is a brand new installation on an HP Pavilion 3168NGW dual-booting to Windows 10. Since I haven’t done anything crazy yet, I’m baffled why this simple procedure won’t work.

On a side note, I attempted to install via the bundle with similar luck:
[https://lts.lehigh.edu/services/stepwise-instructions/install-vmware-horizon-client-linux](https://lts.lehigh.edu/services/stepwise-instructions/install-vmware-horizon-client-linux)
[https://my.vmware.com/web/vmware/details?downloadGroup=CART19FQ4_LIN64_410&productId=578&rPId=29503](https://my.vmware.com/web/vmware/details?downloadGroup=CART19FQ4_LIN64_410&productId=578&rPId=29503)
(I obviously changed the name of the file from VMWare-Horizon-Client-4.5.0-5650368.x64.bundle to the version downloaded)

In that case, I got all the way up to the “sudo ./VMWare-Horizon-Client-4.5.0-5650368.x64.bundle” command, but it gave me an error that Python wasn’t installed. I confirmed that I have Python 3.2 so I’m super confused. Any help would be much appreciated. Thanks.

---

### Post by DuckHook on 2019-01-26
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by herschen on 2019-01-27
Shouldn’t this be moved back to General Help? I’m not requesting help with using VMWare, I’m having trouble installing it. It seems to me that this same problem could crop up with all types of software that I attempt to install since the issue is related to software showing up in Ubuntu Software Center and python not initiating properly. I’m pretty confident it’s user error on my behalf, but I’m all out of ideas. Thanks.

---

### Post by howefield on 2019-01-27
> **herschen said:**
> I’ve followed the instructions below to install VMWare Horizon Client 4.10 via Ubuntu Software Center on Ubuntu 18.10

The package was only available with Ubuntu 12.04 and 14.04

> ..I got all the way up to the “sudo ./VMWare-Horizon-Client-4.5.0-5650368.x64.bundle” command, but it gave me an error that Python wasn’t installed. I confirmed that I have Python 3.2 so I’m super confused. Any help would be much appreciated. Thanks.

Seems to have installed ok in a fresh 18.10

> hugh@cosmic:~/Downloads$  chmod a+x VMware-Horizon-Client-4.10.0-11053294.x64.bundle 
hugh@cosmic:~/Downloads$  sudo ./VMware-Horizon-Client-4.10.0-11053294.x64.bundle 
[sudo] password for hugh: 
Extracting VMware Installer...done.

Please copy/paste the terminal input/output ?

---

### Post by herschen on 2019-01-28
It seems that Python is installed but at the same time not installed:

I get this error message when I attempt to install VMWare Horizon:
[I]herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ chmod a+x VMware-Horizon-Client-4.10.0-11053294.x64.bundle
herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ sudo ./VMware-Horizon-Client-4.10.0-11053294.x64.bundle 
[sudo] password for herschen: 
Extracting VMware Installer...done.
/tmp/vmis.bSGvZQ/install/vmware-installer/vmware-installer: line 76: python: command not found[/I]

I looked to confirm if there was Python installed by typing in "type -a python" and got back "not found":
[I]herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ type -a python
bash: type: python: not found[/I]

However, I found that python is installed and when I tried to reinstall it, it told me that it's already installed:
[I]herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ ls -l /usr/bin/python*
lrwxrwxrwx 1 root root       9 Oct 25 04:11 /usr/bin/python3 -> python3.6
-rwxr-xr-x 2 root root 4534680 Oct 22 04:32 /usr/bin/python3.6
-rwxr-xr-x 2 root root 4534680 Oct 22 04:32 /usr/bin/python3.6m
lrwxrwxrwx 1 root root      10 Oct 25 04:11 /usr/bin/python3m -> python3.6m[/I]

[I]herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ sudo apt-get install python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3 is already the newest version (3.6.7-1~18.10).
python3 set to manually installed.
The following packages were automatically installed and are no longer required:
  libncursesw5 libtinfo5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
herschen@herschen-HP-Pavilion-Laptop-15-cc6xx:~/Downloads$ [/I]

I then ran *sudo apt-get install --reinstall python* and attempted the install again. Unfortunately with the same results. Since I literally just installed Ubuntu, I have no issue with attempting a fresh install if needed.

---

### Post by herschen on 2019-01-28
Problem solved! It looks like the soft link to Pythons&#8217;s executable was broken for some reason. The below command fixed everything. Your quick response helped me tremendously as I was way too focused on trying to install via "Ubuntu Software Center." Thanks.

*sudo ln -s /usr/bin/python3.6 /usr/bin/python*

---

