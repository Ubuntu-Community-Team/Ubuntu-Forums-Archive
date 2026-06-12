---
title: "No netplan on Ubuntu 20.04.4 LTS server edition?"
date: 2022-03-30
forum: Server Platforms
---

### Post by lucasge on 2022-03-30
So I am trying to install Home Assistant following this guide:

[Install Home Assistant OS with KVM on Ubuntu headless (CLI only) - Community Guides - Home Assistant Community (home-assistant.io)]("https://community.home-assistant.io/t/install-home-assistant-os-with-kvm-on-ubuntu-headless-cli-only/254941")

Everything was going great and got to the step where we create the bridge and edit the following file: 

```
nano /etc/netplan/00-installer-config.yaml
```

I edit it correctly and then to apply the changes I understand that like the guide explains, you must run "sudo netplan apply" but I am met with:

> sudo: netplan: command not found

I am able to install netplan using "sudo apt install netplan.io" but when I run "sudo netplan apply" I get the following:

> user@server:~$ sudo netplan applyTraceback (most recent call last):
  File "/usr/sbin/netplan", line 20, in <module>
    from netplan import Netplan
  File "/usr/share/netplan/netplan/__init__.py", line 18, in <module>
    from netplan.cli.core import Netplan
  File "/usr/share/netplan/netplan/cli/core.py", line 24, in <module>
    import netplan.cli.utils as utils
  File "/usr/share/netplan/netplan/cli/utils.py", line 23, in <module>
    import netifaces
ModuleNotFoundError: No module named 'netifaces'

Any ideas what could be going on? How do I update my networking configuration upon changing the /etc/netplan/00-installer-config.yaml file?

---

### Post by TheFu on 2022-03-30
Do you really have Ubuntu Server installed?  I've not seen 20.04 Server without netplan preinstalled.  Was the system migrated from a prior release. leaving cruft around?

Please prove that the file is edited correctly by posting the /etc/netplan/00-installer-config.yaml file. Use forum _code tags_ or indentation will be lost and we won't know anything more than now.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) code-tag how-to

Netplan commands support *--debug* options. Tried that?

Was 
```
sudo netplan generate
```
run first?

BTW, if it were me, I'd not use the same file "00-installer-config.yaml", since after modification, it is no longer the installer file. I use this:
```
/etc/netplan$ ll
total 20
drwxr-xr-x   2 root root  4096 Jun 23  2020 ./
drwxr-xr-x 163 root root 12288 Mar 26 12:59 ../
-rw-r--r--   1 root root   278 Jun 20  2020 **01-ens3-static.yaml**

```
It shows that ens3 is configured as a static IP on the system without extra effort. I made up the name. It just needs to be in the correct directory with the correct ending. I do 1 file per interface myself. Helps me stay organized on systems with multiple NICs. Plus, breaking 1 interface is better than breaking all of them due to an edit mistake.

Lastly, best to use **sudoedit** to edit system files. It honors the EDITOR environment variable and helps with security, though using **sudo nano** isn't a high risk ... besides that nano is a poor editor.


I'd use a netplan something like this:
```
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: [COLOR="#FF0000"]networkd[/COLOR]
  ethernets:
     eth0:
[COLOR="#FF0000"]       dhcp4: false
       dhcp6: false
[/COLOR]  bridges:
      br0:
        interfaces: [eth0]
[COLOR="#FF0000"]        dhcp4: false
        dhcp6: false
[/COLOR]        addresses: [192.168.1.15/24]
        gateway4: 192.168.1.1
        nameservers:
           addresses: [192.168.1.1]

```
and name the file 01-eth0-br0-static.yaml. Note how all DHCP is disabled and networkd is the renderer?  DHCP on a server is asking for problems in my decades of experience.  And I would rename any prior files in that directory to fail the .yaml extension pattern. Don't leave them as is. That would cause a conflict.

---

### Post by lucasge on 2022-03-31
It certainly wasn't installed and yes, it was Ubuntu Server, I guess because I didn't select any package during installation.

I've installed netplan with apt install netplan.io and made sure to select Python3.8 for Python3 exec and it's now working.

---

### Post by TheFu on 2022-03-31
Last month, I installed a new 20.04 server and didn't have any issues with netplan.  I usually allow it to download a new installer first, when that offer is made.  Something funny happened there. No clue what it may have been.

I only install ssh - never anything more.  A server without ssh is pretty useless to me.

---

