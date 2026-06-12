---
title: "Installing Latest Version of qemu-kvm on Ubuntu 9.10"
date: 2010-07-23
forum: Virtualisation
---

### Post by Ubi on 2010-07-23
Hi,
  Are there any instructions on how to update qemu-kvm to 0.12.4.  Unfortunately, Ubuntu 9.10 comes with 0.11.0.  Thanks.

PS.  I tried downloading the source and successfully compiled it.  Using the version that comes with the OS, my virtual machine works fine using virt-manager.  However, when I make kvm point to the new qemu-system-x86_64, the virtual machine would not start (using virt-manager).  It would give me the following error: ```
"Error starting domain: internal error unable to start guest: qemu: could not open disk image : No such file or directory"
``` with the following details: ```
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 493, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 558, in startup
    self.vm.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 293, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error unable to start guest: qemu: could not open disk image : No such file or directory


```

Thanks.

---

### Post by sh1ny on 2010-07-24
Use this PPA :

[https://launchpad.net/~dnjl/+archive/virtualization](https://launchpad.net/~dnjl/+archive/virtualization)

in console , execute :

```
sudo apt-add-repository ppa:dnjl/virtualization
```

Then update your packages. Should be working fine.

---

### Post by Ubi on 2010-07-24
Thanks.  However, when trying to install libvirt-bin, I get the following error.  Any ideas?  Thanks.

```

# apt-get install libvirt-bin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libvirt-bin: Depends: libparted0debian1 (>= 2.2-1) but it is not installable
E: Broken packages

```

Of course, libparted0debian1 is Debian-specific (not Ubuntu specific) and manually installing it results in other dependency issues.  Thanks.

---

### Post by sh1ny on 2010-07-24
You might have to install other of dnjl's ppa's, i think it's this one :

[https://launchpad.net/~dnjl/+archive/ppa](https://launchpad.net/~dnjl/+archive/ppa)

---

### Post by yngens on 2012-05-03
I've been trying to achieve the same result only for Ubuntu 10.04 LTS. So after adding all the packages listed on [https://launchpad.net/~dnjl/+archive/virtualization](https://launchpad.net/~dnjl/+archive/virtualization), namely the following ones:

```
    sudo add-apt-repository ppa:dnjl/virtualization
    sudo add-apt-repository ppa:dnjl/ppa
    sudo add-apt-repository ppa:dnjl/network
    sudo add-apt-repository ppa:dnjl/kernel
    sudo add-apt-repository ppa:dnjl/multimedia
```

and running 

```
apt-get update && apt-get upgrade && apt-get dist-upgrade
```

I have finally:

```
kvm -version
QEMU emulator version 0.14.0 (qemu-kvm-0.14.0), Copyright (c) 2003-2008 Fabrice Bellard
```

Everything seems to be working just fine. The only thing that disturbs me that during the installation I got lot's of warning messages like the ones listed below and I really hope this update won't have terrible consequences for my system.

By the way what about additionally added repositories - is it safe to delete them or I need to keep them to have qemu-kvm-0.14.0?

```
Hit http://software.virtualmin.com virtualmin-lucid Release.gpg
Ign http://software.virtualmin.com/gpl/ubuntu/ virtualmin-lucid/main Translation-en_US        
Hit http://software.virtualmin.com virtualmin-universal Release.gpg                           
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                  
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US         
Get:2 http://us.archive.ubuntu.com lucid Release.gpg [189B]                                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Get:3 http://ppa.launchpad.net lucid Release.gpg [316B]              
Ign http://ppa.launchpad.net/dnjl/kernel/ubuntu/ lucid/main Translation-en_US                 
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]              
Ign http://software.virtualmin.com/gpl/ubuntu/ virtualmin-universal/main Translation-en_US    
Hit http://software.virtualmin.com virtualmin-lucid Release                                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                   
Get:5 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]                           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US           
Get:6 http://us.archive.ubuntu.com lucid Release [57.2kB]                                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US              
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US            
Get:7 http://security.ubuntu.com lucid-security Release [57.3kB]                              
Ign http://ppa.launchpad.net/dnjl/multimedia/ubuntu/ lucid/main Translation-en_US             
Get:8 http://ppa.launchpad.net lucid Release.gpg [316B]                                       
Ign http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main Translation-en_US                
Get:9 http://ppa.launchpad.net lucid Release.gpg [316B]                                       
Ign http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main Translation-en_US                    
Hit http://ppa.launchpad.net lucid Release.gpg                                                
Ign http://ppa.launchpad.net/dnjl/virtualization/ubuntu/ lucid/main Translation-en_US         
Get:10 http://ppa.launchpad.net lucid Release [13.9kB]                                        
Hit http://software.virtualmin.com virtualmin-universal Release                               
Get:11 http://ppa.launchpad.net lucid Release [14.0kB]                                        
Hit http://software.virtualmin.com virtualmin-lucid/main Packages                             
Hit http://software.virtualmin.com virtualmin-universal/main Packages                         
Get:12 http://ppa.launchpad.net lucid Release [13.9kB]                                        
Get:13 http://ppa.launchpad.net lucid Release [13.9kB]                                        
Hit http://ppa.launchpad.net lucid Release                                                    
Get:14 http://ppa.launchpad.net lucid/main Packages [4,789B]                                  
Get:15 http://us.archive.ubuntu.com lucid-updates Release [57.3kB]                            
Get:16 http://ppa.launchpad.net lucid/main Packages [38.7kB]                                  
Get:17 http://security.ubuntu.com lucid-security/main Packages [415kB]                 
Get:18 http://ppa.launchpad.net lucid/main Packages [34.8kB]                                  
Get:19 http://us.archive.ubuntu.com lucid/main Packages [1,383kB]                             
Get:20 http://ppa.launchpad.net lucid/main Packages [45.0kB]                                  
Hit http://ppa.launchpad.net lucid/main Packages                                              
Get:21 http://security.ubuntu.com lucid-security/restricted Packages [2,840B]          
Get:22 http://security.ubuntu.com lucid-security/main Sources [122kB]
Get:23 http://security.ubuntu.com lucid-security/restricted Sources [1,259B]           
Get:24 http://security.ubuntu.com lucid-security/universe Packages [142kB]               
Get:25 http://security.ubuntu.com lucid-security/universe Sources [38.9kB]           
Get:26 http://security.ubuntu.com lucid-security/multiverse Packages [5,335B]           
Get:27 http://security.ubuntu.com lucid-security/multiverse Sources [2,349B]              
Get:28 http://us.archive.ubuntu.com lucid/restricted Packages [6,193B]                    
Get:29 http://us.archive.ubuntu.com lucid/main Sources [659kB]
Get:30 http://us.archive.ubuntu.com lucid/restricted Sources [3,775B]                         
Get:31 http://us.archive.ubuntu.com lucid/universe Packages [5,430kB]                         
Get:32 http://us.archive.ubuntu.com lucid/universe Sources [3,165kB]                          
Get:33 http://us.archive.ubuntu.com lucid/multiverse Packages [176kB]                         
Get:34 http://us.archive.ubuntu.com lucid/multiverse Sources [119kB]                          
Get:35 http://us.archive.ubuntu.com lucid-updates/main Packages [608kB]                       
Get:36 http://us.archive.ubuntu.com lucid-updates/restricted Packages [4,638B]                
Get:37 http://us.archive.ubuntu.com lucid-updates/main Sources [221kB]                        
Get:38 http://us.archive.ubuntu.com lucid-updates/restricted Sources [2,194B]                 
Get:39 http://us.archive.ubuntu.com lucid-updates/universe Packages [286kB]                   
Get:40 http://us.archive.ubuntu.com lucid-updates/universe Sources [98.0kB]                   
Get:41 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [11.3kB]                
Get:42 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,565B]                 
Fetched 13.3MB in 29s (445kB/s)                                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gettext iptables libcap2-bin libsdl1.2debian libsdl1.2debian-alsa python-launchpadlib
The following packages will be upgraded:
  apt-cacher-ng autotools-dev devscripts gconf2 gconf2-common gettext-base libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libgconf2-4 libgl1-mesa-dri libgl1-mesa-glx libnl1 libpcap0.8
  libpcre3 libpixman-1-0 libpython2.6 python python-lazr.restfulclient python-lazr.uri
  python-libvirt python-minimal python2.6 python2.6-minimal rsync ubuntu-keyring virt-manager
32 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 25.5MB of archives.
After this operation, 6,951kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libpython2.6 2.6.6-5ubuntu1~lucid0 [1,076kB]
Get:2 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main python2.6 2.6.6-5ubuntu1~lucid0 [2,458kB]
Get:3 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main python2.6-minimal 2.6.6-5ubuntu1~lucid0 [1,522kB]
Get:4 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main python 2.6.6-5ubuntu1~lucid2 [171kB]
Get:5 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main python-minimal 2.6.6-5ubuntu1~lucid2 [34.8kB]
Get:6 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libpcre3 8.02-1~lucid1 [234kB]     
Get:7 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main ubuntu-keyring 2010.+09.30 [11.6kB]
Get:8 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main gettext-base 0.18.1.1-3ubuntu1~lucid0 [167kB]
Get:9 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main apt-cacher-ng 0.6.3-1~lucid0 [401kB]
Get:10 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main autotools-dev 20110511.1 [44.7kB] 
Get:11 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main devscripts 2.11.0ubuntu1+dnjl0~lucid0 [689kB]
Get:12 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main gconf2-common 2.28.1-3ubuntu1 [28.7kB]
Get:13 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libgconf2-4 2.28.1-3ubuntu1 [200kB]
Get:14 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main gconf2 2.28.1-3ubuntu1 [61.2kB]   
Get:15 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libavahi-common-data 0.6.30-3ubuntu3+dnjl2~lucid0 [133kB]
Get:16 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libavahi-common3 0.6.30-3ubuntu3+dnjl2~lucid0 [54.4kB]
Get:17 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libavahi-client3 0.6.30-3ubuntu3+dnjl2~lucid0 [58.5kB]
Get:18 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libavahi-glib1 0.6.30-3ubuntu3+dnjl2~lucid0 [37.7kB]
Get:19 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libdrm2 2.4.26~glasen~lucid~ppa2 [22.8kB]
Get:20 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libdrm-intel1 2.4.26~glasen~lucid~ppa2 [24.3kB]
Get:21 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libdrm-nouveau1 2.4.26~glasen~lucid~ppa2 [13.1kB]
Get:22 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libdrm-radeon1 2.4.26~glasen~lucid~ppa2 [13.8kB]
Get:23 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libgl1-mesa-dri 7.8~really7.10.3~glasen~ppa1 [16.0MB]
Get:24 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libgl1-mesa-glx 7.8~really7.10.3~glasen~ppa1 [150kB]
Get:25 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libnl1 1.1-6ubuntu1~lucid0 [143kB]
Get:26 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main libpcap0.8 1.1.1-6~lucid0 [123kB]
Get:27 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main libpixman-1-0 0.21.8-1~lucid0 [205kB]
Get:28 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main python-lazr.restfulclient 0.11.2-2+dnjl0~lucid0 [55.8kB]
Get:29 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main python-lazr.uri 1.0.2-5~lucid0 [14.6kB]
Get:30 http://ppa.launchpad.net/dnjl/virtualization/ubuntu/ lucid/main python-libvirt 0.9.2-5ubuntu0+dnjl0~lucid0 [729kB]
Get:31 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main rsync 3.0.8-1ubuntu1~lucid0 [367kB]
Get:32 http://ppa.launchpad.net/dnjl/virtualization/ubuntu/ lucid/main virt-manager 0.8.7-1ubuntu2 [304kB]
Fetched 25.5MB in 59s (429kB/s)                                                               
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 123855 files and directories currently installed.)
Preparing to replace libpython2.6 2.6.5-1ubuntu6 (using .../libpython2.6_2.6.6-5ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement libpython2.6 ...
Preparing to replace python2.6 2.6.5-1ubuntu6 (using .../python2.6_2.6.6-5ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement python2.6 ...
Preparing to replace python2.6-minimal 2.6.5-1ubuntu6 (using .../python2.6-minimal_2.6.6-5ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement python2.6-minimal ...
Processing triggers for man-db ...
Setting up python2.6-minimal (2.6.6-5ubuntu1~lucid0) ...

(Reading database ... 123856 files and directories currently installed.)
Preparing to replace python 2.6.5-0ubuntu1 (using .../python_2.6.6-5ubuntu1~lucid2_all.deb) ...
Unpacking replacement python ...
Preparing to replace python-minimal 2.6.5-0ubuntu1 (using .../python-minimal_2.6.6-5ubuntu1~lucid2_all.deb) ...
Unpacking replacement python-minimal ...
Processing triggers for man-db ...
Setting up python-minimal (2.6.6-5ubuntu1~lucid2) ...

(Reading database ... 123874 files and directories currently installed.)
Preparing to replace libpcre3 7.8-3build1 (using .../libpcre3_8.02-1~lucid1_amd64.deb) ...
Unpacking replacement libpcre3 ...
Preparing to replace ubuntu-keyring 2010.11.09 (using .../ubuntu-keyring_2010.+09.30_all.deb) ...
Unpacking replacement ubuntu-keyring ...
Preparing to replace gettext-base 0.17-8ubuntu3 (using .../gettext-base_0.18.1.1-3ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement gettext-base ...
Preparing to replace apt-cacher-ng 0.4.6-1ubuntu1 (using .../apt-cacher-ng_0.6.3-1~lucid0_amd64.deb) ...
 * Stopping apt-cacher-ng apt-cacher-ng
   ...done.
Unpacking replacement apt-cacher-ng ...
Preparing to replace autotools-dev 20090611.1 (using .../autotools-dev_20110511.1_all.deb) ...
Unpacking replacement autotools-dev ...
Preparing to replace devscripts 2.10.61ubuntu5.1 (using .../devscripts_2.11.0ubuntu1+dnjl0~lucid0_amd64.deb) ...
Unpacking replacement devscripts ...
Preparing to replace gconf2-common 2.28.1-0ubuntu1 (using .../gconf2-common_2.28.1-3ubuntu1_all.deb) ...
Unpacking replacement gconf2-common ...
Preparing to replace libgconf2-4 2.28.1-0ubuntu1 (using .../libgconf2-4_2.28.1-3ubuntu1_amd64.deb) ...
Unpacking replacement libgconf2-4 ...
Preparing to replace gconf2 2.28.1-0ubuntu1 (using .../gconf2_2.28.1-3ubuntu1_amd64.deb) ...
Unpacking replacement gconf2 ...
Preparing to replace libavahi-common-data 0.6.25-1ubuntu6.2 (using .../libavahi-common-data_0.6.30-3ubuntu3+dnjl2~lucid0_amd64.deb) ...
Unpacking replacement libavahi-common-data ...
Preparing to replace libavahi-common3 0.6.25-1ubuntu6.2 (using .../libavahi-common3_0.6.30-3ubuntu3+dnjl2~lucid0_amd64.deb) ...
Unpacking replacement libavahi-common3 ...
Preparing to replace libavahi-client3 0.6.25-1ubuntu6.2 (using .../libavahi-client3_0.6.30-3ubuntu3+dnjl2~lucid0_amd64.deb) ...
Unpacking replacement libavahi-client3 ...
Preparing to replace libavahi-glib1 0.6.25-1ubuntu6.2 (using .../libavahi-glib1_0.6.30-3ubuntu3+dnjl2~lucid0_amd64.deb) ...
Unpacking replacement libavahi-glib1 ...
Preparing to replace libdrm2 2.4.18-1ubuntu3 (using .../libdrm2_2.4.26~glasen~lucid~ppa2_amd64.deb) ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm-intel1 2.4.18-1ubuntu3 (using .../libdrm-intel1_2.4.26~glasen~lucid~ppa2_amd64.deb) ...
Unpacking replacement libdrm-intel1 ...
Preparing to replace libdrm-nouveau1 2.4.18-1ubuntu3 (using .../libdrm-nouveau1_2.4.26~glasen~lucid~ppa2_amd64.deb) ...
Unpacking replacement libdrm-nouveau1 ...
Preparing to replace libdrm-radeon1 2.4.18-1ubuntu3 (using .../libdrm-radeon1_2.4.26~glasen~lucid~ppa2_amd64.deb) ...
Unpacking replacement libdrm-radeon1 ...
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu3 (using .../libgl1-mesa-dri_7.8~really7.10.3~glasen~ppa1_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu3 (using .../libgl1-mesa-glx_7.8~really7.10.3~glasen~ppa1_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: warning: unable to delete old directory '/usr/lib/xorg': Directory not empty
Preparing to replace libnl1 1.1-5build1 (using .../libnl1_1.1-6ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement libnl1 ...
Preparing to replace libpcap0.8 1.0.0-6 (using .../libpcap0.8_1.1.1-6~lucid0_amd64.deb) ...
Unpacking replacement libpcap0.8 ...
Preparing to replace libpixman-1-0 0.16.4-1ubuntu2 (using .../libpixman-1-0_0.21.8-1~lucid0_amd64.deb) ...
Unpacking replacement libpixman-1-0 ...
Preparing to replace python-lazr.restfulclient 0.9.11-1ubuntu1.3 (using .../python-lazr.restfulclient_0.11.2-2+dnjl0~lucid0_all.deb) ...
Unpacking replacement python-lazr.restfulclient ...
Preparing to replace python-lazr.uri 1.0.2-1 (using .../python-lazr.uri_1.0.2-5~lucid0_all.deb) ...
Unpacking replacement python-lazr.uri ...
Preparing to replace python-libvirt 0.7.5-5ubuntu27.22 (using .../python-libvirt_0.9.2-5ubuntu0+dnjl0~lucid0_amd64.deb) ...
Unpacking replacement python-libvirt ...
Preparing to replace rsync 3.0.7-1ubuntu1.1 (using .../rsync_3.0.8-1ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement rsync ...
Preparing to replace virt-manager 0.8.2-2ubuntu8 (using .../virt-manager_0.8.7-1ubuntu2_all.deb) ...
Unpacking replacement virt-manager ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2-nspkg.pth is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/PKG-INFO is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/SOURCES.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/dependency_links.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/namespace_packages.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/not-zip-safe is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/requires.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/top_level.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_browser.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_json.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/resource.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/oauth.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/docs/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/example.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/_uri.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_uri.py is linked but does not belong to any package.
Setting up python2.6 (2.6.6-5ubuntu1~lucid0) ...

Setting up libpython2.6 (2.6.6-5ubuntu1~lucid0) ...

Setting up python (2.6.6-5ubuntu1~lucid2) ...

Setting up libpcre3 (8.02-1~lucid1) ...

Setting up ubuntu-keyring (2010.+09.30) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

Setting up gettext-base (0.18.1.1-3ubuntu1~lucid0) ...

Setting up apt-cacher-ng (0.6.3-1~lucid0) ...
Installing new version of config file /etc/logrotate.d/apt-cacher-ng ...
Installing new version of config file /etc/apt-cacher-ng/acng.conf ...
Installing new version of config file /etc/init.d/apt-cacher-ng ...
 * Starting apt-cacher-ng apt-cacher-ng
   ...done.

Setting up autotools-dev (20110511.1) ...
Setting up devscripts (2.11.0ubuntu1+dnjl0~lucid0) ...
Installing new version of config file /etc/bash_completion.d/devscripts.chdist ...
Installing new version of config file /etc/cowpoke.conf ...

Setting up gconf2-common (2.28.1-3ubuntu1) ...

Setting up libgconf2-4 (2.28.1-3ubuntu1) ...

Setting up gconf2 (2.28.1-3ubuntu1) ...

Setting up libavahi-common-data (0.6.30-3ubuntu3+dnjl2~lucid0) ...
Setting up libavahi-common3 (0.6.30-3ubuntu3+dnjl2~lucid0) ...

Setting up libavahi-client3 (0.6.30-3ubuntu3+dnjl2~lucid0) ...

Setting up libavahi-glib1 (0.6.30-3ubuntu3+dnjl2~lucid0) ...

Setting up libdrm2 (2.4.26~glasen~lucid~ppa2) ...

Setting up libdrm-intel1 (2.4.26~glasen~lucid~ppa2) ...

Setting up libdrm-nouveau1 (2.4.26~glasen~lucid~ppa2) ...

Setting up libdrm-radeon1 (2.4.26~glasen~lucid~ppa2) ...

Setting up libgl1-mesa-dri (7.8~really7.10.3~glasen~ppa1) ...
Setting up libgl1-mesa-glx (7.8~really7.10.3~glasen~ppa1) ...

Setting up libnl1 (1.1-6ubuntu1~lucid0) ...

Setting up libpcap0.8 (1.1.1-6~lucid0) ...

Setting up libpixman-1-0 (0.21.8-1~lucid0) ...

Setting up python-lazr.restfulclient (0.11.2-2+dnjl0~lucid0) ...

Setting up python-lazr.uri (1.0.2-5~lucid0) ...

Setting up python-libvirt (0.9.2-5ubuntu0+dnjl0~lucid0) ...

Setting up rsync (3.0.8-1ubuntu1~lucid0) ...
Installing new version of config file /etc/init.d/rsync ...
 Removing any system startup links for /etc/init.d/rsync ...
   /etc/rc1.d/K20rsync
   /etc/rc2.d/S50rsync
   /etc/rc3.d/S50rsync
   /etc/rc4.d/S50rsync
   /etc/rc5.d/S50rsync

Setting up virt-manager (0.8.7-1ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libnfnetlink0 libunistring0 python-crypto python-keyring
The following packages have been kept back:
  libcap2-bin libsdl1.2debian libsdl1.2debian-alsa
The following packages will be upgraded:
  gettext iptables python-launchpadlib
3 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 3,225kB of archives.
After this operation, 2,089kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libnfnetlink0 1.0.0-1 [14.3kB]
Get:2 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main iptables 1.4.10-1ubuntu1~lucid0 [423kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libunistring0 0.9.1-1 [433kB]
Get:4 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main gettext 0.18.1.1-3ubuntu1~lucid0 [2,097kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-crypto 2.0.1+dfsg1-4ubuntu2 [187kB]
Get:6 http://ppa.launchpad.net/dnjl/ppa/ubuntu/ lucid/main python-keyring 0.5.1-2+dnjl0~lucid0 [24.8kB]
Get:7 http://ppa.launchpad.net/dnjl/network/ubuntu/ lucid/main python-launchpadlib 1.9.8-2~lucid0 [46.3kB]
Fetched 3,225kB in 6s (467kB/s)                                                               
Selecting previously deselected package libnfnetlink0.
(Reading database ... 124057 files and directories currently installed.)
Unpacking libnfnetlink0 (from .../libnfnetlink0_1.0.0-1_amd64.deb) ...
Preparing to replace iptables 1.4.4-2ubuntu2 (using .../iptables_1.4.10-1ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement iptables ...
Selecting previously deselected package libunistring0.
Unpacking libunistring0 (from .../libunistring0_0.9.1-1_amd64.deb) ...
Preparing to replace gettext 0.17-8ubuntu3 (using .../gettext_0.18.1.1-3ubuntu1~lucid0_amd64.deb) ...
Unpacking replacement gettext ...
Selecting previously deselected package python-crypto.
Unpacking python-crypto (from .../python-crypto_2.0.1+dfsg1-4ubuntu2_amd64.deb) ...
Selecting previously deselected package python-keyring.
Unpacking python-keyring (from .../python-keyring_0.5.1-2+dnjl0~lucid0_all.deb) ...
Preparing to replace python-launchpadlib 1.6.0-0ubuntu1 (using .../python-launchpadlib_1.9.8-2~lucid0_all.deb) ...
Unpacking replacement python-launchpadlib ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2-nspkg.pth is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/apps.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/credentials.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/launchpad.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/uris.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/tests/test_launchpad.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/testing/helpers.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/PKG-INFO is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/SOURCES.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/dependency_links.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/namespace_packages.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/not-zip-safe is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/requires.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/top_level.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_browser.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_json.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/resource.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/oauth.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/docs/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/example.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/_uri.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_uri.py is linked but does not belong to any package.
Setting up libnfnetlink0 (1.0.0-1) ...

Setting up iptables (1.4.10-1ubuntu1~lucid0) ...

Setting up libunistring0 (0.9.1-1) ...

Setting up gettext (0.18.1.1-3ubuntu1~lucid0) ...

Setting up python-crypto (2.0.1+dfsg1-4ubuntu2) ...

Setting up python-keyring (0.5.1-2+dnjl0~lucid0) ...

Setting up python-launchpadlib (1.9.8-2~lucid0) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...

```

---

### Post by yngens on 2012-05-03
Particularly I am worried by occurrence of these two blocks of warning messages:

```

Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2-nspkg.pth is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/PKG-INFO is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/SOURCES.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/dependency_links.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/namespace_packages.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/not-zip-safe is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/requires.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/top_level.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_browser.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_json.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/resource.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/oauth.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/docs/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/example.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/_uri.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_uri.py is linked but does not belong to any package.
Setting up python2.6 (2.6.6-5ubuntu1~lucid0) ...

```

```

Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2-nspkg.pth is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/apps.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/credentials.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/launchpad.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/uris.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/tests/test_launchpad.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/launchpadlib/testing/helpers.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/PKG-INFO is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/SOURCES.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/dependency_links.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/namespace_packages.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/not-zip-safe is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/requires.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr.uri-1.0.2.egg-info/top_level.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_browser.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/_json.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/errors.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/resource.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/authorize/oauth.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/docs/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/example.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/restfulclient/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/_uri.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/version.txt is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/__init__.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_docs.py is linked but does not belong to any package.
WARNING: WARNING: /usr/share/pyshared/lazr/uri/tests/test_uri.py is linked but does not belong to any package.
Setting up libnfnetlink0 (1.0.0-1) ...

```

Googling on the name of the packages gives nothing: [https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=WARNING%3A+WARNING%3A+%2Fusr%2Fshare%2Fpyshared%2Flazr.uri-1.0.2-nspkg.pth+is+linked+but+does+not+belong+to+any+package.#hl=en&sclient=psy-ab&q=lazr.uri-1.0.2-nspkg.pth+&oq=lazr.uri-1.0.2-nspkg.pth+&aq=f&aqi=&aql=&gs_l=serp.3...41920.42381.3.42613.2.1.1.0.0.0.175.175.0j1.1.0...0.0.l9w04k_Pa6Y&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=8316e992ae23057e&biw=1135&bih=1083](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=WARNING%3A+WARNING%3A+%2Fusr%2Fshare%2Fpyshared%2Flazr.uri-1.0.2-nspkg.pth+is+linked+but+does+not+belong+to+any+package.#hl=en&sclient=psy-ab&q=lazr.uri-1.0.2-nspkg.pth+&oq=lazr.uri-1.0.2-nspkg.pth+&aq=f&aqi=&aql=&gs_l=serp.3...41920.42381.3.42613.2.1.1.0.0.0.175.175.0j1.1.0...0.0.l9w04k_Pa6Y&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=8316e992ae23057e&biw=1135&bih=1083)

Am I alone in hitting this wall?

---

