---
title: "Upgrading a VM 4.3.34 to VirtualBox 5.0"
date: 2016-03-05
forum: Virtualisation
---

### Post by Lappert on 2016-03-05
Previously I was running a Windows 7 Virtual Machine on an Kubuntu 14.04 box and using VirtualBox 4.3.34_Ubuntu r104062.

I've set up a new box running Kubuntu 15.10 and installed VirtBox 5.0.14_Ubuntu r105127.

I tried to add the old VM and I've gotten the error message, "Failed to open VM located in ____"

Details:

Runtime error opening '/mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox' for reading: -38(Access denied.).
/build/virtualbox-JETMa8/virtualbox-5.0.14-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[480] (nsresult Machine::initFromSettings(VirtualBox*, const com::Utf8Str&, const com::Guid*)).


[TABLE]
[TR]
[TD]Result Code: 
[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
[TR]
[TD]Component: 
[/TD]
[TD]MachineWrap
[/TD]
[/TR]
[TR]
[TD]Interface: 
[/TD]
[TD]IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}
[/TD]
[/TR]
[TR]
[TD]Callee: 
[/TD]
[TD]IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}


[/TD]
[/TR]
[/TABLE]
[INDENT]
[/INDENT]

I'd also like to increase the size of the VM from 40GB to 80GB.

Help! Thank you.

---

### Post by MAFoElffen on 2016-03-05
Zip up the "VBoxStartup.log" file mentioned in the error message, and post as an attachment. (too long to post as code)

And when you reinstalled your versions of Virtual box, did you unistall previous before upgrading to 5.x or just upgrade. (both on Windows 7 right?)

That error has to do with the hypervisor being able to support guests on the host-- so about the host system... rather than something about the guest VM.

---

### Post by Lappert on 2016-03-05
Thanks for your reply.

There is no VBoxStartup.log mentioned in the error message (see above). There was a VBox.log from the old installation that I carried over with the old directory that contained the Win7-32.vbox file. But that log file hasn't been updated in a month (when it was last used on the old install).

Just to check, the .vbox file was root-root 600, so I changed it to user-user-777. But that didn't change anything.

---

### Post by Lappert on 2016-03-05
The admin at virtualbox.org said the version installed via Ubuntu Software Center is [COLOR=#333333][FONT=Lucida Grande]5.0.14-dfsg-0ubuntu1.15.10.1  and not supported there. They said my choices are to remove the Ubuntu version and install the "official" version from virtualbox.org, or see if a fix may be got here. So that's where I am at the moment. Before I take the radical approach, I'm hoping the Ubuntu version I already have can be fixed.

As I said above, there is no log file, but I did find some info that might help the diagnostics.

The new version I installed is essentially a virgin copy of 5.0.14. The problem comes from trying to add the old 4.x version of the .vbox file ... I pulled that .vbox from an archive of the old ubuntu 14.04 install.

See the attached message.txt
[/FONT][/COLOR][ATTACH]267664[/ATTACH]

---

### Post by MAFoElffen on 2016-03-06
Sorry, I got that backwards then. I was going out the door when I saw this. Just back now. 

I thought your host was Windows. Actually easier to fix in Linux. What that error is saying is that the kernel module is not loading. I looked up the error at Oracle: VirtualBox. They say that that error has to do with the hypervisor. If it were a Windows host it has to do with one of the dll's. On a Linux Host, it has to do with the kernel module not being compiled and installed for the current kernel. So:
```

 sudo /etc/init.d/vboxdrv setup

```
That setup should recompile the kernel module and reinstall it. If it doesn't then reinstall that version.

---

### Post by MAFoElffen on 2016-03-06
Sorry, I got that backwards then. I was going out the door when I saw this. Just back now. 

I thought your host was Windows. Actually easier to fix in Linux. What that error is saying is that the kernel module is not loading. I looked up the error at Oracle: VirtualBox. They say that that error has to do with the hypervisor. If it were a Windows host it has to do with one of the dll's. On a Linux Host, it has to do with the kernel module not being compiled and installed for the current kernel. So:
```

 sudo /etc/init.d/vboxdrv setup

```
That setup should recompile the kernel module and reinstall it. Pay attention for errors when it goes to build the module. One common error is if there is no kernel header file present for the kernel you are running on. If you see that error. then:
```

sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-(uname -r)

```
Then try it again...

If you see no errors and it still does not work, then reinstall VirtualBox.

---

### Post by howefield on 2016-03-06
Just for infomation, if you do end up reinstalling Virtualbox note that a new version (5.0.16) was released a couple of days ago. Likely to appear in the repositories over the next few days or available from virtualbox.org.

---

### Post by Lappert on 2016-03-06
I get nothing from the suggested commands:

> root@mybox:/home/user# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory

root@mybox:/home/user# apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.

root@mybox:/home/user# apt-get install linux-headers-(uname -r)
bash: syntax error near unexpected token `('

root@mybox:/home/user# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory
root@corsair:/home/lance# 


---

### Post by MAFoElffen on 2016-03-06
In that case, since it says that vboxdrv is not there, then that is why the kernel module is not there:
```

sudo apt-get install linux-headers-'uname -r'
sudo apt-get install virtualbox-dkms

```

---

### Post by Lappert on 2016-03-06
*Note: I didn't see your most recent reply above. Here's what I've done in the meantime:*


OK, so now I have installed the newer version of VB 5.0.16 via apt-get (see below). Then I installed the extension pack. But I'm still getting the same error message:

Failed to open virtual machine located in /mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox.
Runtime error opening **'/mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox'** for reading: -38(Access denied.).
/home/vbox/vbox-5.0.16/src/VBox/Main/src-server/MachineImpl.cpp[480] (nsresult Machine::initFromSettings(VirtualBox*, const com::Utf8Str&, const com::Guid*)).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]MachineWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}[/TD]
[/TR]
[TR]
[TD]Callee:[/TD]
[TD]IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}[/TD]
[/TR]
[/TABLE]


**Before that I updated the sources.list with**
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wiley contrib**Then I ran apt-get update:**

```
root@mybox:/etc/apt# apt-get update
Get:1 [http://download.virtualbox.org]("http://download.virtualbox.org/") wily InRelease [7,138 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily InRelease                                                                                                                                                                   
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") wily InRelease                                                                                                                                                                 
Ign [http://dl.google.com]("http://dl.google.com/") stable InRelease                                                                                                                                                                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates InRelease                                                                                                                                                           
Get:2 [http://download.virtualbox.org]("http://download.virtualbox.org/") wily/contrib amd64 Packages [983 B]                                                                                                                                          
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports InRelease                                                                                                                                                         
Hit [http://dl.google.com]("http://dl.google.com/") stable Release.gpg                                                                                                                                                                       
Get:3 [http://download.virtualbox.org]("http://download.virtualbox.org/") wily/contrib i386 Packages [979 B]                                                                                                                                           
Hit [http://dl.google.com]("http://dl.google.com/") stable Release                                                                                                                                     
Ign [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge InRelease                                                                                 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security InRelease                                                   
Hit [http://dl.google.com]("http://dl.google.com/") stable/main amd64 Packages                                                                                                     
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") wily/contrib Translation-en_US                                                              
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") wily/contrib Translation-en                                                                 
Hit [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge Release.gpg                                                         
Hit [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge Release                 
Hit [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge/contrib amd64 Packages                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/main Sources                                                                      
Hit [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge/contrib i386 Packages                                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/restricted Sources                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/multiverse Sources                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/restricted amd64 Packages                                                
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/multiverse amd64 Packages                                                
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/restricted i386 Packages                                                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/multiverse i386 Packages                                                                  
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/multiverse Translation-en                                                                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/restricted Translation-en                                        
Ign [http://download.webmin.com]("http://download.webmin.com/") sarge InRelease                                                                   
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/restricted Sources                                             
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/universe Sources                                                                                   
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/multiverse Sources                                                                                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/main amd64 Packages                           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/restricted amd64 Packages                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/universe amd64 Packages                           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/multiverse amd64 Packages                         
Hit [http://download.webmin.com]("http://download.webmin.com/") sarge Release.gpg                                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/main i386 Packages                                                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/restricted i386 Packages                                                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/universe i386 Packages                                                           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/multiverse i386 Packages                                                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/main Translation-en                                                              
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/multiverse Translation-en                                                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/restricted Translation-en                                               
Ign [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge/contrib Translation-en_US                          
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily/universe Translation-en                           
Hit [http://download.webmin.com]("http://download.webmin.com/") sarge Release                                            
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/main Sources                                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/restricted Sources                                                       
Ign [http://webmin.mirror.somersettechsolutions.co.uk]("http://webmin.mirror.somersettechsolutions.co.uk/") sarge/contrib Translation-en                                      
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/universe Sources                                                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/multiverse Sources                                                       
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/restricted amd64 Packages                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/multiverse amd64 Packages                          
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/main i386 Packages                                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/restricted i386 Packages                                              
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/universe i386 Packages                                                
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/main Translation-en   
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/restricted Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/main Sources                                          
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-updates/universe Translation-en                              
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/main Sources                                                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/universe Sources                                                    
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/main amd64 Packages                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/universe amd64 Packages                           
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/restricted Sources    
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/main i386 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/universe Sources                                     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/main Translation-en                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") wily-backports/universe Translation-en                           
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/multiverse Sources    
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/main amd64 Packages   
Hit [http://download.webmin.com]("http://download.webmin.com/") sarge/contrib amd64 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/restricted amd64 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/universe amd64 Packages        
Hit [http://download.webmin.com]("http://download.webmin.com/") sarge/contrib i386 Packages                  
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/main i386 Packages              
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/restricted i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/universe i386 Packages         
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/main Translation-en            
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/multiverse Translation-en      
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/restricted Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") wily-security/universe Translation-en                                
Ign [http://download.webmin.com]("http://download.webmin.com/") sarge/contrib Translation-en_US                                      
Ign [http://download.webmin.com]("http://download.webmin.com/") sarge/contrib Translation-en
Fetched 9,100 B in 3s (2,728 B/s)
W: GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/") wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
[B]
Then a dist-upgrade:
[/B]
```
root@mybox:/etc/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

[B]Then installed VB 5.0
[/B]
```
root@mybox:/etc/apt# apt-get install virtualbox-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsdl-ttf2.0-0
The following NEW packages will be installed:
  libsdl-ttf2.0-0 virtualbox-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.1 MB of archives.
After this operation, 163 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  virtualbox-5.0
Install these packages without verification? [y/N] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/universe libsdl-ttf2.0-0 amd64 2.0.11-3 [15.0 kB]
Get:2 [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) wily/contrib virtualbox-5.0 amd64 5.0.16-105871~Ubuntu~wily [65.1 MB]
Fetched 65.1 MB in 6s (9,433 kB/s)                                                                                                                                                                                
Preconfiguring packages ...
Selecting previously unselected package libsdl-ttf2.0-0:amd64.
(Reading database ... 192558 files and directories currently installed.)
Preparing to unpack .../libsdl-ttf2.0-0_2.0.11-3_amd64.deb ...
Unpacking libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Selecting previously unselected package virtualbox-5.0.
Preparing to unpack .../virtualbox-5.0_5.0.16-105871~Ubuntu~wily_amd64.deb ...
Unpacking virtualbox-5.0 (5.0.16-105871~Ubuntu~wily) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Setting up virtualbox-5.0 (5.0.16-105871~Ubuntu~wily) ...
Adding group `vboxusers' (GID 130) ...
Done.
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
root@mybox:/etc/apt#
```

---

### Post by Lappert on 2016-03-06
from your latest suggestion (I'll let you know if it works):


```
root@mybox:/home/user# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory
```

```
root@mybox:/home/user# apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
root@mybox:/home/user# apt-get install linux-headers-(uname -r)
bash: syntax error near unexpected token `('
```

```
root@mybox:/home/user# apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-uname -r
```

```
root@mybox:/home/user# apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libgsoap7 libvncserver1 virtualbox virtualbox-qt
Suggested packages:
  vde2 virtualbox-guest-additions-iso
The following packages will be REMOVED:
  virtualbox-5.0
The following NEW packages will be installed:
  libgsoap7 libvncserver1 virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
Need to get 318 kB/22.2 MB of archives.
After this operation, 68.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/universe libgsoap7 amd64 2.8.22-1 [196 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/main libvncserver1 amd64 0.9.10+dfsg-3 [122 kB]
Fetched 318 kB in 0s (1,341 kB/s)      
(Reading database ... 193333 files and directories currently installed.)
Removing virtualbox-5.0 (5.0.16-105871~Ubuntu~wily) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Selecting previously unselected package libgsoap7:amd64.
(Reading database ... 192567 files and directories currently installed.)
Preparing to unpack .../libgsoap7_2.8.22-1_amd64.deb ...
Unpacking libgsoap7:amd64 (2.8.22-1) ...
Selecting previously unselected package libvncserver1:amd64.
Preparing to unpack .../libvncserver1_0.9.10+dfsg-3_amd64.deb ...
Unpacking libvncserver1:amd64 (0.9.10+dfsg-3) ...
Selecting previously unselected package virtualbox-dkms.
Preparing to unpack .../virtualbox-dkms_5.0.14-dfsg-0ubuntu1.15.10.1_all.deb ...
Unpacking virtualbox-dkms (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Selecting previously unselected package virtualbox.
Preparing to unpack .../virtualbox_5.0.14-dfsg-0ubuntu1.15.10.1_amd64.deb ...
Unpacking virtualbox (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Selecting previously unselected package virtualbox-qt.
Preparing to unpack .../virtualbox-qt_5.0.14-dfsg-0ubuntu1.15.10.1_amd64.deb ...
Unpacking virtualbox-qt (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (225-1ubuntu9) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Setting up libgsoap7:amd64 (2.8.22-1) ...
Setting up libvncserver1:amd64 (0.9.10+dfsg-3) ...
Setting up virtualbox-dkms (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Loading new virtualbox-5.0.14 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-30-generic
Building initial module for 4.2.0-30-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up virtualbox (5.0.14-dfsg-0ubuntu1.15.10.1) ...
vboxweb.service is a disabled or a static unit, not starting it.
Setting up virtualbox-qt (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...
root@mybox:/home/user#
```

---

### Post by Lappert on 2016-03-06
And still getting the latest error:

Failed to open virtual machine located in /mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox.
Runtime error opening **'/mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox'** for reading: -38(Access denied.).
/build/virtualbox-JETMa8/virtualbox-5.0.14-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[480] (nsresult Machine::initFromSettings(VirtualBox*, const com::Utf8Str&, const com::Guid*)).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]MachineWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IMachine {f30138d4-e5ea-4b3a-8858-a059de4c93fd}[/TD]
[/TR]
[TR]
[TD]Callee:[/TD]
[TD]IVirtualBox {0169423f-46b4-cde9-91af-1e9d5b6cd945}[/TD]
[/TR]
[/TABLE]

---

### Post by SeijiSensei on 2016-03-06
This looks like a permissions problem to me "(Access denied)".  Are you sure you have full read/write permissions on /mnt/sdb/VirtualBox VMs/ and its subdirectories? 

Also I noticed that you omitted the space in "VirtualBox VMs."  Are you sure that "VirtualBoxVMs" is correct on your installation?

---

### Post by MAFoElffen on 2016-03-07
Strange things is that I can see all the pieces are there and they installed correctly. VirtualBox says that error is from a module not loading, but I can see it compiled and installed without error.(???). 

Where is /mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox? (Physically describe)

Can you check permissions on (from you userid, not from sudo...)
```

ls -la /mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox

```

---

### Post by SeijiSensei on 2016-03-07
I don't think it's a problem with a module.  VirtualBox can't open the virtual machine.

```
Runtime error opening '/mnt/sdb/VirtualBoxVMs/Win7-32/Win7-32.vbox' for reading: -38(Access denied.).
```

---

### Post by MAFoElffen on 2016-03-08
At first I thought it was a run-time problem from a module. That "IS" what Oracle said his error was all about. His previous install was missing vboxdrv, so that sort of confirmed my suspicion on that. But now?

With this version, I see his machine building and installing the modules. 

*** What is curious is the "permission denied" error on path "/mnt/sdb/VirtualBoxVMs/". It is not "/dev/sdb/", so it is a mount... If this path were mounted via Nautilus, it should carry user rights, but that path would start with "/media/"... On a path starting with "/mnt/", that is usually referring to an elevated mount from root... Usually with VirtualBox, default VM paths for a user is in the "/home/" directory, where they have read/write/execution rights and permissions.

So wondering if he can't access the VM image as a user, because of user permissions in that path... ego, the request for output of permissions on that path...

---

### Post by Lappert on 2016-03-14
Thank you to all who have replied, and sorry about the delay in responding (I had to deal with work issues).

Made some progress, but not there yet. I added the space in the "VirtualBox VMs" directory as suggested.

The application starts up, and I go to Machine > New > Add and pick the old Win7-32.vbox file. The icon shows that the VM is powered off.

I select that and click Start. A box comes up stating "Failed to open a session for the virtual machine Win7-32."

Under Details, I see:

Failed to open a session for the virtual machine **Win7-32**.
The device helper structure version has changed.
If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[/TABLE]


The VirtualBox is 5.0.16 and I added an extension pack from the VB website, so all should be the latest. The Win7 VB file is from the old VB 4.x install. Could that be the latest issue?

FYI, I've uploaded the /var/log/[COLOR=#000000]vbox-install.log file as a .txt file.

I also uploaded (as a zip file) the text from Machine > Show Log
This - I expect - will show the versions of VB and the extension file.[/COLOR]

---

### Post by MAFoElffen on 2016-03-15
Looks like either the vboxmanager-dkms package is not installed (which would install the vbox kernel module) or the newer package was not installed because...

Did you remove the 4.x version before installing the new 5.x version? If not then there is mixed versions present. If that is true, then remove both versions and install the 5.0 version.

If you did remove it before installing, then 
```

sudo apt-get install vboxmanager-dkms

```

---

### Post by Lappert on 2016-03-15
I had to rebuild the computer due to a crash. This time I installed Kubuntu 15.10. The old install was 14.04 LTS. I did not reinstall the old 4.x version of VB. I did install the 5.0.14 version, but then removed that (along with apt-get purge) and then installed the 5.0.16 version, where I am now. So AFAIK there are not mixed versions present.

I don't know what vboxmanager is, but I'll try your suggestion....

> root@mybox:/home/user# apt-get install vboxmanager-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vboxmanager-dkms
root@mybox:/home/user# 


also
> 
# apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.


and
> 
# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory


---

### Post by Lappert on 2016-03-15
I also just tried

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

```[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]```
# apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-dkms
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
Need to get 616 kB of archives.
After this operation, 4,948 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates/multiverse virtualbox-dkms all 5.0.14-dfsg-0ubuntu1.15.10.1 [616 kB]
Fetched 616 kB in 0s (3,796 kB/s)       
Selecting previously unselected package virtualbox-dkms.
(Reading database ... 195204 files and directories currently installed.)
Preparing to unpack .../virtualbox-dkms_5.0.14-dfsg-0ubuntu1.15.10.1_all.deb ...
Unpacking virtualbox-dkms (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Setting up virtualbox-dkms (5.0.14-dfsg-0ubuntu1.15.10.1) ...
Loading new virtualbox-5.0.14 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-30-generic
Building initial module for 4.2.0-30-generic
Done.


vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/


vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/


vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/


vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-30-generic/updates/dkms/


depmod....


DKMS: install completed.

```

But no change.

---

### Post by Lappert on 2016-03-15
Getting very frustrated here and I very much need to get this up and running. 

I appreciate the help, but it doesn't seem like progress is being made. Any suggestions? 

Should I uninstall everything and start over? (I did that before). What about these side programs that I didn't know even existed? Or should I get rid of the ubuntu version and use the version that is on the virtualbox website?

---

### Post by MAFoElffen on 2016-03-16
IMHO: Well worth a try. It's been down a week already, right?

I can confirm that I uninstalled mine previous version and installed 5.0 from what I dl'ed from Oracle... and it works on mine. I cannot guaranty that it will work on yours, but it it doesn't, you are no worse off than now, right?

---

### Post by Lappert on 2016-03-17
I think I'll do that - and report back.

But one question - in addition to removing and purging virtualbox and the extension, what other programs should also be removed (and reinstalled).
I think one is the VB-manager, the DKMS (whatever that is). others?

---

### Post by MAFoElffen on 2016-03-17
dl the Oracle vb extension pack. When you get VB installed. Then open the extension pack. If you go into Nautilus (file manager), right click on it, open with Virtual box... VB will install it.

The Extension pack is the replacement for the Guest additions. The biggest failure on trying to run old VM guests on a newer version is that is has USB extensions in the VM, which where handled by... now with the extensions pack. I don't know why they just don't include that as "part" of VB itself... and turn it on or off as an option of the program. It seems like it would save people a lot of headaches if they did. But that just makes too much sense right?

---

### Post by Lappert on 2016-03-19
OK, I removed the old VB install and reinstalled using the Oracle VB binary. I also installed the extension pack.

To recap, I have an old VM Windows 7 host that contains vital programs and data that I need to be able to access, so I can't just install a new Win7 host. 

The structure I'm using is /mnt/sdb/VirtualBox VMs/Win7-32/Win7-32.vbox. Note this file was from a 4.x VB install.

So I boot up. I get warnings about shared directories having changed and auto capture keyboard. I was able to adjust the settings so I'm not getting those alerts anymore. I set up the old 4.x host file with Machine > Add and navigate to the Win7-32.vbox file. Then I hit 'start.'

I get the Oracle splash screen, then the message "FATAL: Could not read from the boot medium! System halted."

What boot medium? Doesn't the Win7-32.vbox and .vdi files contain the entire Windows OS in some sort of virtual drive? I'm very confused here. HELP!!

---

### Post by Lappert on 2016-03-20
Answering my own question. I think I have a solution here. I found a small tutorial on Youtube that addresses just this issue. 

[https://www.youtube.com/watch?v=S8j1Fo2KRZM](https://www.youtube.com/watch?v=S8j1Fo2KRZM)

One must attach the *.vdi file as if it's a hard drive.

So now VB is booting up. I think I'll have to spend time tweaking it for USB devices, audio, printers and scanners. Last time it took some time as well.

In any case, to those that responded, thank you very much for your efforts. I appreciate your help.

---

### Post by MAFoElffen on 2016-03-21
Great. So since this is solve now... Correct? If so, then please return to this thread and go to link to the top left of your first post that says "Thread Tools" > "Mark thread as Solved"... so that others may find a solution to their similar problems.

---

