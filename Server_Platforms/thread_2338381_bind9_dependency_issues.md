---
title: "bind9 dependency issues"
date: 2016-09-27
forum: Server Platforms
---

### Post by ghughes on 2016-09-27
Good afternoon, all! I have just run into an interesting dependency issue with updating bind9. Here is the error listing:

```
The following packages have unmet dependencies:
 bind9 : Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
         Depends: bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.16) but 1:9.8.1.dfsg.P1-4ubuntu0.17 is installed
E: Unmet dependencies. Try using -f.
root@www6:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-94 linux-headers-3.2.0-94-generic-pae
  linux-image-3.2.0-93-generic-pae libmonosgen-2.0-dev
  linux-image-3.2.0-94-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bind9
Suggested packages:
  resolvconf
The following packages will be upgraded:
  bind9
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/337 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 237, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in read_apt_pipeline
    return map(lambda pkg: filenames[pkg], order)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 83, in <lambda>
    return map(lambda pkg: filenames[pkg], order)
KeyError: 'bind9'
dpkg: dependency problems prevent configuration of bind9:
 bind9 depends on libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of libbind9-80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of libdns81 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of libisc83 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of libisccc80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of libisccfg82 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of liblwres80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
 bind9 depends on bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.16); however:
  Version of bind9utils on system is 1:9.8.1.dfsg.P1-4ubuntu0.17.
dpkg: error processing bind9 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I did find a possible way through this by installing the requested libraries by hand, but I wanted to check another possibility with the group. This installation is a 12.04 LTS and I get the "do-release-upgrade" prompt whenever I shell into the machine. Would that possibly solve this problem as well? I also need to see what packages depend on the updated libraries. I trawled through apt-cache rdepends but I'm not sure I got everything.
Any thoughts on a safe way to tackle this one?
Thanks to all for looking!
Gregg

---

### Post by Vegan on 2016-09-27
I found it was easier to use a new virtual machine with a new LTS release, then migration would be easier and less likely to be a problem

I have experimented with release upgrades and they usually fail which is why I use virtual machines galore

---

