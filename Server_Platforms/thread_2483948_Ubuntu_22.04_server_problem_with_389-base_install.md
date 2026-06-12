---
title: "Ubuntu 22.04 server problem with 389-base install"
date: 2023-02-13
forum: Server Platforms
---

### Post by odinn-burkni on 2023-02-13
Hi guys,
I've installed 389-ds on 22.04 server.
I installed it this way:
sudo apt install 389-ds
and then
sudo apt install cockpit-doc cockpit-pcp cockpit-sosreport xdg-utils udisks2-lvm2 sssd-dbus apache2 pcscd lm-sensors snmp-mibs-downloader m4-doc make-doc avahi-autoipd libteam-utils python-networkx-doc python3-gdal python3-matplotlib python3-pydot python3-pygraphviz python3-scipy gcc gfortran python-numpy-doc python3-dev subversion python-pygments-doc ttf-bitstream-vera setools-gui wpagui libengine-pkcs11-openssl


I then used this tutorial to create an instance: [https://documentation.suse.com/sles/15-SP3/html/SLES-all/cha-security-ldap.html#sec-security-ldap-server-template](https://documentation.suse.com/sles/15-SP3/html/SLES-all/cha-security-ldap.html#sec-security-ldap-server-template)
sudo dscreate create-template myInstance.txt
I then changed some things in the file, like giving my instance a name and put in the password and such.
sudo dscreate from-file myInstance.txt


This seemed to work fine and this command sudo dsctl myInstance status, shows that my instance is up and running.
When I go to the webgui, it comes up with the Apache2 Ubuntu Default Page: It works! 
Using :9830 or :3890 leads to nothing. I'm pretty sure I'm missing some step regarding setting up Apache. I blame it on tiredness. Can anyone point me in the right direction?


Thanks in advance...

---

### Post by odinn-burkni on 2023-02-13
Hi again,
I found, after a little more googling.... that the port is 9090, not 9830 or 3890.

---

### Post by ajgreeny on 2023-02-13
So can we presume that this is now  a solved problem?
If so please mark as SOLVED from the Thread Tools menu up-top. It is a great help to other users searching the forum with similar difficulties.

---

### Post by ziongate on 2023-05-15
Hi all,

I also have a issue with this install
Every installation is ok but in the GUI, there's no  389 Directory server anymore, so there's no gui to administer 389 DS.



cockpit:

ri  cockpit                               264-1ubuntu0.22.04.1                    all          Web Console for Linux servers
ri  cockpit-389-ds                        2.0.15-1                                all          Cockpit user interface for 389 Directory Server
ii  cockpit-bridge                        264-1ubuntu0.22.04.1                    amd64        Cockpit bridge server-side component
ii  cockpit-networkmanager                264-1ubuntu0.22.04.1                    all          Cockpit user interface for networking
ii  cockpit-packagekit                    264-1ubuntu0.22.04.1                    all          Cockpit user interface for packages
ii  cockpit-storaged                      264-1ubuntu0.22.04.1                    all          Cockpit user interface for storage
ii  cockpit-system                        264-1ubuntu0.22.04.1                    all          Cockpit admin interface for a system
ri  cockpit-ws                            264-1ubuntu0.22.04.1                    amd64        Cockpit Web Service



389-ds:

ii  389-ds                                2.0.15-1                                all          389 Directory Server suite - metapackage
ii  389-ds-base                           2.0.15-1                                amd64        389 Directory Server suite - server
ii  389-ds-base-libs:amd64                2.0.15-1                                amd64        389 Directory Server suite - libraries
ri  cockpit-389-ds                        2.0.15-1                                all          Cockpit user interface for 389 Directory Server
ii  libidm-console-framework-java         2.0.0-1                                 all          IDM Console Framework for the 389 Directory Server Console
ii  python3-lib389                        2.0.15-1                                all          Python3 module for accessing and configuring the 389 Directory Server


systemctl status [email]dirsrv@aaa.servic[/email]e
&#9679; [email]dirsrv@aaa.servic[/email]e - 389 Directory Server aaa.
     Loaded: loaded (/lib/systemd/system/dirsrv@.service; enabled; vendor preset: enabled)
    Drop-In: /usr/lib/systemd/system/dirsrv@.service.d
             &#9492;&#9472;custom.conf
     Active: active (running) since Fri 2023-05-12 16:45:30 UTC; 3 days ago
   Main PID: 15478 (ns-slapd)
     Status: "slapd started: Ready to process requests"


dsctl my_instance status
Instance "my_instance" is running





Best Regards

---

### Post by ziongate on 2023-05-16
The solution before a new deb package is there  [https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1854674.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1854674.html)

---

