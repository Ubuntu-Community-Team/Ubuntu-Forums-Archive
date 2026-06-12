---
title: "getting error after upgraded from 8.04 LTS server to 8.10 server"
date: 2008-11-02
forum: Server Platforms
---

### Post by kustomjs on 2008-11-02
Hi Guys
when I did a upgrade from 8.04LTS server to 8.10 server I got this error: 

dpkg: error processing rkhunter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
 bsd-mailx
 mailx
 rkhunter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lykwydchykyn on 2008-11-02
run aptitude -f install and post the complete output here.

---

### Post by kustomjs on 2008-11-02
here is the output of that:
xxx@xxxx sudo aptitude -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  enscript{u} fping{u} ghostscript{u} gsfonts{u} libart-2.0-2{u}
  libck-connector0{u} libcupsimage2{u} libcupsys2{u} libgs8{u} libltdl3{u}
  libpaper-utils{u} libpaper1{u} libphp-adodb{u} librrd2{u}
  libtiff-tools{u} metamail{u} nagios-plugins-extra{u} nagios2-common{u}
  nagios2-doc{u} openssh-blacklist{u} php5-snmp{u} qstat{u} rrdtool{u}
  sharutils{u}
The following partially installed packages will be configured:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx rkhunter
0 packages upgraded, 0 newly installed, 24 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 33.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 57849 files and directories currently installed.)
Removing enscript ...
Removing nagios-plugins-extra ...
Removing fping ...
Removing ghostscript ...
Purging font configuration of gs...
Purging category psprint..
Purging category cmap..
Purging category cid..
Purging category truetype..
Purging category gsfontderivative..
Purging category type3..
Purging category type1..
Removing gsfonts ...
Unregistering PostScript fonts...
Updating fontconfig cache for /usr/share/fonts/type1/gsfonts
done.
Removing rrdtool ...
Removing librrd2 ...
Removing libart-2.0-2 ...
Removing libck-connector0 ...
Removing libgs8 ...
Removing libcupsimage2 ...
Removing libcupsys2 ...
Removing libltdl3 ...
Removing libpaper-utils ...
Removing libpaper1 ...
Removing libphp-adodb ...
Removing libtiff-tools ...
Removing metamail ...
Removing nagios2-common ...
 * Reloading web server config apache2                                   [ OK ]
Removing nagios2-doc ...
Removing openssh-blacklist ...
Removing php5-snmp ...
Removing qstat ...
Removing sharutils ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up exim4-config (4.69-5ubuntu2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-dNo apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               aemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not installed.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rkhunter:
 rkhunter depends on exim4 | postfix | sendmail | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package postfix is not installed.
  Package sendmail is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing rkhunter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
 bsd-mailx
 mailx
 rkhunter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up exim4-config (4.69-5ubuntu2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-daemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not installed.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rkhunter:
 rkhunter depends on exim4 | postfix | sendmail | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package postfix is not installed.
  Package sendmail is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing rkhunter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
 rkhunter
 bsd-mailx
 mailx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

---

### Post by lykwydchykyn on 2008-11-02
The root of the problem is here:
> 
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting


Something has gone wrong with your exim4 configuration and it's causing the exim4 install to choke along with everything dependent on exim4. 

If exim4 isn't important to the functioning of this server (i.e. -- you don't have any special exim configs you need to keep), I'd try this:
```

sudo aptitude purge exim4 rkhunter mailx
sudo aptitude -f install
sudo aptitude install exim4 rkhunter mailx

```

See if that fixes you.

---

### Post by kustomjs on 2008-11-02
I still get that same error:



tim@server1:~$ sudo apt-get remove exim4 rkhunter mailx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  unhide
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  exim4 mailx rkhunter
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 860kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 56732 files and directories currently installed.)
Removing rkhunter ...
Removing exim4 ...
Removing mailx ...
Processing triggers for man-db ...
Setting up exim4-config (4.69-5ubuntu2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package eNo apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         xim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-common:
 nagios3-common depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing nagios3-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3:
 nagios3 depends on nagios3-common (= 3.0.2-1ubuntu1); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 bsd-mailx
 nagios3-common
 nagios3
E: Sub-process /usr/bin/dpkg returned an error code (1)
tim@server1:~$ sudo aptitude purge exim4 rkhunter mailx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  exim4{p} rkhunter{p} unhide{u}
The following partially installed packages will be configured:
  bsd-mailx exim4-base exim4-config exim4-daemon-light nagios3
  nagios3-common
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1626kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 56689 files and directories currently installed.)
Removing exim4 ...
Purging configuration files for exim4 ...
Removing rkhunter ...
Purging configuration files for rkhunter ...
(Reading database ... 56685 files and directories currently installed.)
Removing unhide ...
Processing triggers for man-db ...
Setting up exim4-config (4.69-5ubuntu2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package eNo apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         xim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-common:
 nagios3-common depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing nagios3-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3:
 nagios3 depends on nagios3-common (= 3.0.2-1ubuntu1); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 bsd-mailx
 nagios3-common
 nagios3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up exim4-config (4.69-5ubuntu2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-common:
 nagios3-common depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing nagios3-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3:
 nagios3 depends on nagios3-common (= 3.0.2-1ubuntu1); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 bsd-mailx
 nagios3-common
 nagios3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

---

### Post by lykwydchykyn on 2008-11-02
Ok, this time try:
```

sudo aptitude purge exim-config

```

use aptitude purge, not apt-get remove.  This will clear out any faulty configs you might have.

---

### Post by kustomjs on 2008-11-02
I think I got it fixed thanks for your help

---

