---
title: "SystemD 227"
date: 2015-10-08
forum: Ubuntu Development Version
---

### Post by zika on 2015-10-08
[http://lists.freedesktop.org/archives/systemd-devel/2015-October/034509.html](http://lists.freedesktop.org/archives/systemd-devel/2015-October/034509.html)
**ppa: pitti/systemd**&#8203;
Off to reboot... ;)
Update&#8321;: Not for faint-hearted. A bunch of glitches but it could be used, after some sacrifices in comfort... Looks promising. Have alternative DM, UpStart and ppa-purge ready... ;)
Update: It &#8222;loves&#8220; kernel 4.3 a bit more than 4.2. As it does &#8222;love&#8220; LightDM more than GDM.
Hint: A bit of trouble here was caused by non-provoked weaking up of deja-dup daemon. Killed that with rename of appropriate .desktop file... ;) This is the first time it woke up.
Update: It settled so fast and it is now simply OK.
Joke (true):```
:~$ machinectl shell
The program 'machinectl' is currently not installed. You can install it by typing:
sudo apt-get install systemd
:~$ sudo apt-get install -s systemd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
systemd is already the newest version.
systemd set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$ dpkg -l|grep systemd
ii  libpam-systemd:amd64                                  227+upstream20151009-0.ubuntu                      amd64        system and service manager - PAM module
ii  libsystemd0:amd64                                     227+upstream20151009-0.ubuntu                      amd64        systemd utility library
ii  systemd                                               227+upstream20151009-0.ubuntu                      amd64        system and service manager
ii  systemd-gui                                           1:3-4                                              all          transitional package for systemd-ui
ii  systemd-shim                                          9-1bzr4                                            amd64        shim for systemd
ii  systemd-sysv                                          227+upstream20151009-0.ubuntu                      amd64        system and service manager - SysV links
ii  systemd-ui                                            3-4                                                amd64        graphical frontend for systemd
```

---

