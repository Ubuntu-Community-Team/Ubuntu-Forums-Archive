---
title: "cobbler install fails"
date: 2012-05-19
forum: Server Platforms
---

### Post by airtonix on 2012-05-19
Fresh system with Zentyal 2.3 and ZFS.

Trying to get orchestra, juju and cobbler installed... but it fails to install.

```
$ sudo apt-get install cobbler
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cobbler is already the newest version.
The following packages were automatically installed and are no longer required:
  samba4 libdcerpc-server0 python-samba zentyal-dns samba4-common-bin libregistry0 libsamba-policy0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cobbler (2.2.2-0ubuntu33) ...
Usage: ip addr {add|change|replace} IFADDR dev STRING [ LIFETIME ]
                                                      [ CONFFLAG-LIST ]
       ip addr del IFADDR dev STRING
       ip addr {show|flush} [ dev STRING ] [ scope SCOPE-ID ]
                            [ to PREFIX ] [ FLAG-LIST ] [ label PATTERN ]
IFADDR := PREFIX | ADDR peer PREFIX
          [ broadcast ADDR ] [ anycast ADDR ]
          [ label STRING ] [ scope SCOPE-ID ]
SCOPE-ID := [ host | link | global | NUMBER ]
FLAG-LIST := [ FLAG-LIST ] FLAG
FLAG  := [ permanent | dynamic | secondary | primary |
           tentative | deprecated | dadfailed | temporary |
           CONFFLAG-LIST ]
CONFFLAG-LIST := [ CONFFLAG-LIST ] CONFFLAG
CONFFLAG  := [ home | nodad ]
LIFETIME := [ valid_lft LFT ] [ preferred_lft LFT ]
LFT := forever | SECONDS
dpkg: error processing cobbler (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 cobbler
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```

```

$ sudo apt-get purge cobbler
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bind9 bind9utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cobbler*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 252 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133262 files and directories currently installed.)
Removing cobbler ...
Purging configuration files for cobbler ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
administrator@edge:~$ sudo apt-get purge orchestra 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bind9 bind9utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  orchestra*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 35.8 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133228 files and directories currently installed.)
Removing orchestra ...
administrator@edge:~$ sudo apt-get purge juju 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bind9 bind9utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  juju*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 2,930 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133225 files and directories currently installed.)
Removing juju ...
Purging configuration files for juju ...
Processing triggers for man-db ...


```


```

$ sudo rm /etc/cobbler/ -rf

```

```

$ sudo rm /etc/orchestra/ -rf

```


```

$ sudo apt-get install cobbler
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  createrepo bind9 debmirror genisoimage
The following NEW packages will be installed:
  cobbler
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/37.4 kB of archives.
After this operation, 252 kB of additional disk space will be used.
Preconfiguring packages ...
Usage: ip addr {add|change|replace} IFADDR dev STRING [ LIFETIME ]
                                                      [ CONFFLAG-LIST ]
       ip addr del IFADDR dev STRING
       ip addr {show|flush} [ dev STRING ] [ scope SCOPE-ID ]
                            [ to PREFIX ] [ FLAG-LIST ] [ label PATTERN ]
IFADDR := PREFIX | ADDR peer PREFIX
          [ broadcast ADDR ] [ anycast ADDR ]
          [ label STRING ] [ scope SCOPE-ID ]
SCOPE-ID := [ host | link | global | NUMBER ]
FLAG-LIST := [ FLAG-LIST ] FLAG
FLAG  := [ permanent | dynamic | secondary | primary |
           tentative | deprecated | dadfailed | temporary |
           CONFFLAG-LIST ]
CONFFLAG-LIST := [ CONFFLAG-LIST ] CONFFLAG
CONFFLAG  := [ home | nodad ]
LIFETIME := [ valid_lft LFT ] [ preferred_lft LFT ]
LFT := forever | SECONDS
cobbler failed to preconfigure, with exit status 255
Selecting previously unselected package cobbler.
(Reading database ... 132434 files and directories currently installed.)
Unpacking cobbler (from .../cobbler_2.2.2-0ubuntu33_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up cobbler (2.2.2-0ubuntu33) ...
Usage: ip addr {add|change|replace} IFADDR dev STRING [ LIFETIME ]
                                                      [ CONFFLAG-LIST ]
       ip addr del IFADDR dev STRING
       ip addr {show|flush} [ dev STRING ] [ scope SCOPE-ID ]
                            [ to PREFIX ] [ FLAG-LIST ] [ label PATTERN ]
IFADDR := PREFIX | ADDR peer PREFIX
          [ broadcast ADDR ] [ anycast ADDR ]
          [ label STRING ] [ scope SCOPE-ID ]
SCOPE-ID := [ host | link | global | NUMBER ]
FLAG-LIST := [ FLAG-LIST ] FLAG
FLAG  := [ permanent | dynamic | secondary | primary |
           tentative | deprecated | dadfailed | temporary |
           CONFFLAG-LIST ]
CONFFLAG-LIST := [ CONFFLAG-LIST ] CONFFLAG
CONFFLAG  := [ home | nodad ]
LIFETIME := [ valid_lft LFT ] [ preferred_lft LFT ]
LFT := forever | SECONDS
dpkg: error processing cobbler (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 cobbler
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

