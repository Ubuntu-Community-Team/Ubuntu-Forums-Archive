---
title: "Virtualbox web service won't start. 12.04 Headless ubuntu server"
date: 2013-03-08
forum: Virtualisation
---

### Post by naslaitis on 2013-03-08
It's been 2 days since I can't solve my problem.

I had a working copy of VirtualBox but something went wrong so I decided to start fresh.
Does this remove all the configuration as well?
```
sudo apt-get purge virtualbox-\*
```
And this is how I get new version of virtualbox
```
sudo echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
sudo wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.2
wget [http://download.virtualbox.org/virtualbox/4.2.8/Oracle_VM_VirtualBox_Extension_Pack-4.2.8-83876.vbox-extpack](http://download.virtualbox.org/virtualbox/4.2.8/Oracle_VM_VirtualBox_Extension_Pack-4.2.8-83876.vbox-extpack)
sudo VBoxManage extpack install *.vbox-extpack
```

And now the log that follows. I am really not sure what's wrong.
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/62.9 MB of archives.
After this operation, 137 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package virtualbox-4.2.
(Reading database ... 126340 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.8-83876~Ubuntu~precise_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox-4.2 (4.2.8-83876~Ubuntu~precise) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                                                            [ OK ]
 * Uninstalling old VirtualBox DKMS kernel modules                                                               [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                                                   [ OK ]
 * Starting VirtualBox kernel modules                                                                            [ OK ]
 * Starting VirtualBox web service
 *
invoke-rc.d: initscript vboxweb-service, action "start" failed.
dpkg: error processing virtualbox-4.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-4.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Whenever I run 
```

sudo /etc/init.d/vboxweb-service start
```

Virtualbox Web Service always fails to start.

---

### Post by Theodis on 2013-05-31
> **naslaitis said:**
> It's been 2 days since I can't solve my problem.


And now the log that follows. I am really not sure what's wrong.
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/62.9 MB of archives.
After this operation, 137 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package virtualbox-4.2.
(Reading database ... 126340 files and directories currently installed.)
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.8-83876~Ubuntu~precise_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox-4.2 (4.2.8-83876~Ubuntu~precise) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                                                            [ OK ]
 * Uninstalling old VirtualBox DKMS kernel modules                                                               [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                                                   [ OK ]
 * Starting VirtualBox kernel modules                                                                            [ OK ]
 * Starting VirtualBox web service
 *
invoke-rc.d: initscript vboxweb-service, action "start" failed.
dpkg: error processing virtualbox-4.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 virtualbox-4.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Whenever I run 
```

sudo /etc/init.d/vboxweb-service start
```

Virtualbox Web Service always fails to start.


comment out the entry to write a log file in /etc/default/virtualbox

---

