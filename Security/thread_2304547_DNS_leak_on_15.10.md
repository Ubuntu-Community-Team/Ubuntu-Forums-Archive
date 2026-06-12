---
title: "DNS leak on 15.10"
date: 2015-11-27
forum: Security
---

### Post by scu on 2015-11-27
I'm running PrivateInternetAccess VPN on Ubuntu 15.10 and now [http://dnsleak.com](http://dnsleak.com) is leaking my ISP's DNS addresses. I'm pretty sure on 15.04 I didn't have this leak. Any ideas what's wrong now?

Here is PIA's installation guide [https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn](https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn) and a straight link to the installation shell script [https://www.privateinternetaccess.com/installer/install_ubuntu.sh](https://www.privateinternetaccess.com/installer/install_ubuntu.sh)

Tried Firefox 42.0 and Chromium 45.0.2454.101. Also tried Firefox's safe mode (without add-ons) but it didn't help. Rebooting did not help either.[COLOR=#303942][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by matt_symes on 2015-11-27
I have moved your thread to the **Security** sub forum.

You are more likely to get help for your query here.

---

### Post by scu on 2015-11-27
Thank you matt_symes.

Tested now on another clean 15.10 install and same DNS leak. Then installed 15.04 and there was not DNS leak on any browser (FF 37.0, FF 42.0, Chromium 45.0.2454.101).

Installation on 15.10

```
$ sudo sh ./install_ubuntu.sh 
[sudo] password for XXX: 
Package python2.7 already installed
Package network-manager-openvpn required. Install? (y/n): y
Installing network-manager-openvpn..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpkcs11-helper1 network-manager-openvpn-gnome openvpn
Suggested packages:
  easy-rsa
The following NEW packages will be installed:
  libpkcs11-helper1 network-manager-openvpn network-manager-openvpn-gnome
  openvpn
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 627 kB of archives.
After this operation, 2 314 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libpkcs11-helper1 openvpn network-manager-openvpn
  network-manager-openvpn-gnome
Install these packages without verification? [y/N] y
Get:1 http://XXX.archive.ubuntu.com/ubuntu/ wily/main libpkcs11-helper1 amd64 1.11-4 [44,3 kB]
Get:2 http://XXX.archive.ubuntu.com/ubuntu/ wily/main openvpn amd64 2.3.7-1ubuntu1 [419 kB]
Get:3 http://XXX.archive.ubuntu.com/ubuntu/ wily/universe network-manager-openvpn amd64 0.9.10.0-1ubuntu2 [23,0 kB]
Get:4 http://XXX.archive.ubuntu.com/ubuntu/ wily/universe network-manager-openvpn-gnome amd64 0.9.10.0-1ubuntu2 [141 kB]
Fetched 627 kB in 0s (1 050 kB/s)                         
Preconfiguring packages ...
Selecting previously unselected package libpkcs11-helper1:amd64.
(Reading database ... 202315 files and directories currently installed.)
Preparing to unpack .../libpkcs11-helper1_1.11-4_amd64.deb ...
Unpacking libpkcs11-helper1:amd64 (1.11-4) ...
Selecting previously unselected package openvpn.
Preparing to unpack .../openvpn_2.3.7-1ubuntu1_amd64.deb ...
Unpacking openvpn (2.3.7-1ubuntu1) ...
Selecting previously unselected package network-manager-openvpn.
Preparing to unpack .../network-manager-openvpn_0.9.10.0-1ubuntu2_amd64.deb ...
Unpacking network-manager-openvpn (0.9.10.0-1ubuntu2) ...
Selecting previously unselected package network-manager-openvpn-gnome.
Preparing to unpack .../network-manager-openvpn-gnome_0.9.10.0-1ubuntu2_amd64.deb ...
Unpacking network-manager-openvpn-gnome (0.9.10.0-1ubuntu2) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (225-1ubuntu9) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Setting up libpkcs11-helper1:amd64 (1.11-4) ...
Setting up openvpn (2.3.7-1ubuntu1) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
Setting up network-manager-openvpn (0.9.10.0-1ubuntu2) ...
Setting up network-manager-openvpn-gnome (0.9.10.0-1ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Please enter your login: p9497738
Copying certificate..
Loading servers information..
Removing previous config files if existing..
Creating config files..
Restarting network manager..
Error: Object 'nm' is unknown, try 'nmcli help'.
Error: Object 'nm' is unknown, try 'nmcli help'.
Install successful!
```


Installation on 15.04

```
$ sudo sh ./install_ubuntu.sh
[sudo] password for XXX: 
Package python2.7 already installed
Package network-manager-openvpn required. Install? (y/n): y
Installing network-manager-openvpn..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpkcs11-helper1 network-manager-openvpn-gnome openvpn
Suggested packages:
  easy-rsa
The following NEW packages will be installed:
  libpkcs11-helper1 network-manager-openvpn network-manager-openvpn-gnome
  openvpn
0 upgraded, 4 newly installed, 0 to remove and 241 not upgraded.
Need to get 608 kB of archives.
After this operation, 2 666 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://XXX.archive.ubuntu.com/ubuntu/](http://XXX.archive.ubuntu.com/ubuntu/) vivid/main libpkcs11-helper1 amd64 1.11-2 [43,7 kB]
Get:2 [http://XXX.archive.ubuntu.com/ubuntu/](http://XXX.archive.ubuntu.com/ubuntu/) vivid/main openvpn amd64 2.3.2-9ubuntu4 [401 kB]
Get:3 [http://XXX.archive.ubuntu.com/ubuntu/](http://XXX.archive.ubuntu.com/ubuntu/) vivid/universe network-manager-openvpn amd64 0.9.10.0-1ubuntu1 [23,1 kB]
Get:4 [http://XXX.archive.ubuntu.com/ubuntu/](http://XXX.archive.ubuntu.com/ubuntu/) vivid/universe network-manager-openvpn-gnome amd64 0.9.10.0-1ubuntu1 [141 kB]
Fetched 608 kB in 0s (915 kB/s)                         
Preconfiguring packages ...
Selecting previously unselected package libpkcs11-helper1:amd64.
(Reading database ... 162448 files and directories currently installed.)
Preparing to unpack .../libpkcs11-helper1_1.11-2_amd64.deb ...
Unpacking libpkcs11-helper1:amd64 (1.11-2) ...
Selecting previously unselected package openvpn.
Preparing to unpack .../openvpn_2.3.2-9ubuntu4_amd64.deb ...
Unpacking openvpn (2.3.2-9ubuntu4) ...
Selecting previously unselected package network-manager-openvpn.
Preparing to unpack .../network-manager-openvpn_0.9.10.0-1ubuntu1_amd64.deb ...
Unpacking network-manager-openvpn (0.9.10.0-1ubuntu1) ...
Selecting previously unselected package network-manager-openvpn-gnome.
Preparing to unpack .../network-manager-openvpn-gnome_0.9.10.0-1ubuntu1_amd64.deb ...
Unpacking network-manager-openvpn-gnome (0.9.10.0-1ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (219-7ubuntu3) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Setting up libpkcs11-helper1:amd64 (1.11-2) ...
Setting up openvpn (2.3.2-9ubuntu4) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
Setting up network-manager-openvpn (0.9.10.0-1ubuntu1) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Setting up network-manager-openvpn-gnome (0.9.10.0-1ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (219-7ubuntu3) ...
Please enter your login: p9497738
Copying certificate..
Loading servers information..
Removing previous config files if existing..
Creating config files..
Restarting network manager..
Error: Object 'nm' is unknown, try 'nmcli help'.
Error: Object 'nm' is unknown, try 'nmcli help'.
Install successful!
```

I don't notice any big differences in the installation output. Both have the same object nm error in the end, but it does not have any affect on 15.04.

---

### Post by sammiev on 2015-11-30
Bump see this [Thread]("http://ubuntuforums.org/showthread.php?t=2304831").

Thanks

---

