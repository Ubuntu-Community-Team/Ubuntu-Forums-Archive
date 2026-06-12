---
title: "VM Server 2.0 eating memory/processor"
date: 2011-07-23
forum: Virtualisation
---

### Post by wazhapen on 2011-07-23
I'm seeking some assistance with an issue I'm currently having with VMWare Server 2.0...

I recently partitioned my drive for Ubuntu 11.0.4 Natty. For the longest time I have been using Windows 7. My Windows 7 image had VMWare Server installed with Windows Server 2008. 

After setting up my Ubuntu I successfully installed VMWare Server 2.0 and because lack of drive space I didn't move over my VMWare Windows Server 08' image to Ubuntu instead I changed the directory in the config file for VMWare and setup the data store to pull from my Windows 7 directory. 

My issue is when I now boot that server it takes FOREVER to even get to the login screen and even once it does it is extremely slow. Eventually I was able to uninstall/reinstall the VMWare tools but that didn't do anything. Also when looking at my processors and memory they are spiking well over what is allocated for this server. 

If you need any additional information please feel free to let me know. Thanks for any help I am exhausted from searching on forums... I had the thought that maybe since I'm pulling my VMWare from the same drive as my Ubuntu and it is NTFS that it might be causing extreme drag on the IO of the disk? 

My host is ...
AMD x86 - 6 core 3.2ghz
DDR2 8gb RAM

Allocated to Windows Server 2008 ...
x2 core
4gb RAM

---

### Post by HermanAB on 2011-07-24
Yeah, well, VMware Server 2.0 is best avoided.  Either use VMware Player or VMware Workstation.

---

