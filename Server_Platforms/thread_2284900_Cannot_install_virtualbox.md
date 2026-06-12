---
title: "Cannot install virtualbox"
date: 2015-07-02
forum: Server Platforms
---

### Post by FCNBYwP on 2015-07-02
Please help me with installing virtualbox on my 14.04.02 server.
```


ibrahim@UGSERVER:~/Downloads$ sudo dpkg -i virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb 
[sudo] password for ibrahim: 
(Reading database ... 62137 files and directories currently installed.)
Preparing to unpack virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb ...
Unpacking virtualbox-4.3 (4.3.28-100309~Ubuntu~raring) over (4.3.28-100309~Ubuntu~raring) ...
dpkg: dependency problems prevent configuration of virtualbox-4.3:
 virtualbox-4.3 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not installed.
  Package libgl1 is not installed.
 virtualbox-4.3 depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network is not installed.
 virtualbox-4.3 depends on libqt4-opengl (>= 4:4.7.2); however:
  Package libqt4-opengl is not installed.
 virtualbox-4.3 depends on libqtcore4 (>= 4:4.8.0); however:
  Package libqtcore4 is not installed.
 virtualbox-4.3 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not installed.
 virtualbox-4.3 depends on libvpx1 (>= 1.0.0); however:
  Package libvpx1 is not installed.
 virtualbox-4.3 depends on libxcursor1 (>> 1.1.2); however:
  Package libxcursor1 is not installed.
 virtualbox-4.3 depends on libxinerama1; however:
  Package libxinerama1 is not installed.
 virtualbox-4.3 depends on libxmu6; however:
  Package libxmu6 is not installed.
 virtualbox-4.3 depends on libxt6; however:
 
dpkg: error processing package virtualbox-4.3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Errors were encountered while processing:
 virtualbox-4.3
```

---

### Post by flocculant on 2015-07-02
Because you are using dpkg to install rather than one of the apt* methods, it's not grabbing any dependencies that it requires. 

If you have no need for the specific differences between the Oracle package and that in the repositories then try installing from them.

```
sudo apt-get install virtualbox 
```

That will also install any dependencies that VBox requires. 

Alternatively - install it's dependencies BEFORE trying to install with dpkg and the deb file.

---

### Post by FCNBYwP on 2015-07-02
I want to install the application from oracle because I want to use USB with the guest VM.
Please tell me how can I install the dependencies before trying to install with the dpkg and deb file?
thnx

---

### Post by westie457 on 2015-07-02
These commands might help. ```
sudo apt-get install --fix-missing
sudo dpkg --configure -a
```

---

### Post by SeijiSensei on 2015-07-02
Just follow the procedures for "Debian-based" distributions on the VirtualBox site.  You add the Oracle repository and its key to your system, then run "sudo apt-get update; sudo apt-get install virtualbox-4.3".  It will bring in any needed dependencies automatically.

The Extension Pack can be installed on the version of VirtualBox in the Ubuntu repositories.  You don't need Oracle's version of VB to install the Extension Pack.  That said, I always use the Oracle repository because it it usually more up-to-date.

---

### Post by v3.xx on 2015-07-02
> **SeijiSensei said:**
> Just follow the procedures for "Debian-based" distributions on the VirtualBox site.  You add the Oracle repository and its key to your system, then run "sudo apt-get update; sudo apt-get install virtualbox-4.3".  It will bring in any needed dependencies automatically.

The Extension Pack can be installed on the version of VirtualBox in the Ubuntu repositories.  You don't need Oracle's version of VB to install the Extension Pack.  That said, I always use the Oracle repository because it it usually more up-to-date.
Thats how its done +1

---

### Post by FCNBYwP on 2015-07-13
I am from Syria and Oracle will not allow me to download virtualbox, That is why i have to install the .deb package.

---

### Post by nerdtron on 2015-07-14
Are we talking about server with no GUI? Then the good virtualization is KVM and use virt-manager to remotely manage the VMs [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

---

### Post by SeijiSensei on 2015-07-15
> **FCNBYwP said:**
> I am from Syria and Oracle will not allow me to download virtualbox, That is why i have to install the .deb package.

Then install the missing dependencies manually.
```
virtualbox-4.3 depends on libgl1-mesa-glx | libgl1; however:
 virtualbox-4.3 depends on libqt4-network (>= 4:4.5.3); however:
 virtualbox-4.3 depends on libqt4-opengl (>= 4:4.7.2); however:
 virtualbox-4.3 depends on libqtcore4 (>= 4:4.8.0); however:
 virtualbox-4.3 depends on libqtgui4 (>= 4:4.8.0); however:
 virtualbox-4.3 depends on libvpx1 (>= 1.0.0); however:
 virtualbox-4.3 depends on libxcursor1 (>> 1.1.2); however:
 virtualbox-4.3 depends on libxinerama1; however:
 virtualbox-4.3 depends on libxmu6; however:
 virtualbox-4.3 depends on libxt6; however:

```

```
sudo apt-get install libgl1-mesa-glx libgl1 libqt4-network libqt4-opengl libqtcore4 libqtgui4 libvpx1 libxcursor1 libxinerama1 libxmu6 libxt6
```

---

