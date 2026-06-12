---
title: "Ubuntu 10.04"
date: 2010-04-18
forum: Ubuntu Christian Edition
---

### Post by calebyong on 2010-04-18
Ubuntu 10.04 is going to be released in a few days, i would like to know if i use the upgrade button in the update manager will i be able to still keep dansguardian gui? because i really need that nice filter.

---

### Post by david_kt on 2010-04-19
> **calebyong said:**
> Ubuntu 10.04 is going to be released in a few days, i would like to know if i use the upgrade button in the update manager will i be able to still keep dansguardian gui? because i really need that nice filter.

Yes, it should be. Please report here the result as it would be a good start to build the next release.

DK

---

### Post by calebyong on 2010-04-22
i installed ubuntu 10.04 beta 2 32 bit, i installed the dansguardian gui with command line, i didn't install the whole thing, it didn't work, filter was off.

---

### Post by david_kt on 2010-04-22
> **calebyong said:**
> i installed ubuntu 10.04 beta 2 32 bit, i installed the dansguardian gui with command line, i didn't install the whole thing, it didn't work, filter was off.

Could you try to:
1. autoconfigure dansguardian
2. stop dansguardian
3. start dansguardian.

DK

---

### Post by Deer Hunter on 2010-04-23
I'm assuming you are (or were) running 9.10 CE.  So, why not try this: 

To upgrade from Ubuntu 9.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.04' is available. Click Upgrade and follow the on-screen instructions. 

It's been working fine for me.  Of course, having done that, I now check the updates quite frequently, and download them all.  Just a thought.  Let us know if it works.

---

### Post by calebyong on 2010-04-29
I see, i'll try to install ubuntu 10.04 stable release via update manager after the peak downloads that will fill up the server this week.

---

### Post by doulos564 on 2010-05-01
Just upgraded to 10.04.  I didn't notice, but the filter was disabled during this.  I can use the dansguardian-gui to start the filter and reconfigure it, but FF continues to give me "connection reset" when the filter is running.

Linux luther 2.6.32-21-generic  (amd64)
dansguardian 2.10.1.1-1
tinyproxy 1.8.1-3
clamav  0.96+dfsg-2ubuntu1
clamav-freshclam 0.96+dfsg-2ubuntu1

I've tried reconfiguring, reboot, down grading to 2.9.9.7 (I'm back at the above).

Any ideas?

I am seeing this in the /var/log/syslog
May  1 07:51:04 luther dansguardian[4003]: Started sucessfully.
May  1 07:51:09 luther dansguardian[4006]: Error connecting to proxy

---

### Post by doulos564 on 2010-05-03
I also updated another PC (32-bit) to 10.04.
I ensured that DG was up and functioning prior to the upgrade.
When I rebooted, FH and TP were ON, but DG was OFF.
I continue to get the same errors as my 64-bit system.

Because this is my kids PC, I'll be downgrading back to 9.10 and the working DG.

However, I can work the issue on my 64-bit PC and provide whatever logs, traces, etc. that you need to help me get past the issue.

Thanks!

---

### Post by calebyong on 2010-05-03
can anyone resolve my issue, it seems that i'm unable to surf when i turn the filter on, i don't have an account with sudo rights( i had my password for the root account sent to my brother in another country so that i can't turn the filter off. I'm using Ubuntu 9.10 CE, with the improved dansguardian gui, google chrome the lastest build and firefox 3.5.9. Any help will do =)

---

### Post by david_kt on 2010-05-03
> **calebyong said:**
> can anyone resolve my issue, it seems that i'm unable to surf when i turn the filter on, i don't have an account with sudo rights( i had my password for the root account sent to my brother in another country so that i can't turn the filter off. I'm using Ubuntu 9.10 CE, with the improved dansguardian gui, google chrome the lastest build and firefox 3.5.9. Any help will do =)

Ubuntu 9.10 CE should have no problems. Could you post here:
```
 cat '/etc/apt/sources.list.d/ubuntuce.list' 

```

DK

---

### Post by calebyong on 2010-05-04
deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
 u mean this?

---

### Post by david_kt on 2010-05-04
> **calebyong said:**
> deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
 u mean this?

Yes. If you are still using karmic, not upgraded to lucid yet, it should work. What is the error?

DK

---

### Post by calebyong on 2010-05-04
There is no error message, just blank pages, after some time it says it can't find the page like as if i don't have the internet on, but i can run pidgin.

---

### Post by doulos564 on 2010-05-04
I tried uninstalling:

```
sudo aptitude purge dansguardian tinyproxy firehol 
```

I also completely removed clamav, clamav-base, and clamav-freshclam using Synaptic.

Then, I reinstalled using the 9.10 thread - which gives this command:

```
wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O- | sudo apt-key add - && sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install dansguardian-gui 
```

Here is my install output:

```
doug@luther:~$ cd junk
doug@luther:~/junk$ wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O- | sudo apt-key add - && sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install dansguardian-gui
OK
--2010-05-04 16:03:18--  [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list)
Resolving ubuntuce.com... 66.40.7.42
Connecting to ubuntuce.com|66.40.7.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]
Saving to: `/etc/apt/sources.list.d/ubuntuce.list'

100%[======================================>] 223         --.-K/s   in 0s      

2010-05-04 16:03:19 (39.0 MB/s) - `/etc/apt/sources.list.d/ubuntuce.list' saved [223/223]

Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid Release.gpg
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main Translation-en_US           
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/restricted Translation-en_US     
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/universe Translation-en_US       
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/multiverse Translation-en_US     
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates Release.gpg                      
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/main Translation-en_US   
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security Release.gpg                     
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid Release                                  
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates Release                          
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security Release                         
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/main Packages                            
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/restricted Packages                      
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/main Sources                   
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/restricted Sources             
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/universe Packages                        
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/universe Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ubuntuce.com](http://ubuntuce.com) karmic_amd/ Release.gpg                                
Ign [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_amd/ Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/multiverse Packages            
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/multiverse Sources             
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/main Packages          
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/restricted Packages    
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/main Sources           
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/restricted Sources               
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/universe Packages                
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/universe Sources                 
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/multiverse Packages              
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/multiverse Sources               
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/main Packages                   
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/restricted Packages   
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/main Sources          
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/restricted Sources    
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net/alexandria-team/ppa/ubuntu/](http://ppa.launchpad.net/alexandria-team/ppa/ubuntu/) karmic/main Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/universe Sources                
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/multiverse Packages   
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-security/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ubuntuce.com](http://ubuntuce.com) karmic_amd/ Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu/](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu/) karmic/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ubuntuce.com](http://ubuntuce.com) karmic_amd/ Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav clamav-base clamav-freshclam dansguardian dhcp3-server tinyproxy
Suggested packages:
  clamav-docs squid dhcp3-server-ldap
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam dansguardian dansguardian-gui
  dhcp3-server tinyproxy
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,892kB of archives.
After this operation, 5,509kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  dansguardian dansguardian-gui
Install these packages without verification [y/N]? Y
Get:1 [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main clamav-base 0.96+dfsg-2ubuntu1 [288kB]
Get:2 [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_amd/ dansguardian 2.10.1.1-1really2.9.9.7-2ubuntu1 [481kB]
Get:3 [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main clamav-freshclam 0.96+dfsg-2ubuntu1 [300kB]
Get:4 [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main clamav 0.96+dfsg-2ubuntu1 [323kB]
Get:5 [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/universe tinyproxy 1.8.1-3 [85.5kB]
Get:6 [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main dhcp3-server 3.1.3-2ubuntu3 [398kB]
Get:7 [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_amd/ dansguardian-gui 2.4 [16.7kB]
Fetched 1,892kB in 3s (477kB/s)      
Preconfiguring packages ...
Selecting previously deselected package clamav-base.
(Reading database ... 196304 files and directories currently installed.)
Unpacking clamav-base (from .../clamav-base_0.96+dfsg-2ubuntu1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.96+dfsg-2ubuntu1_amd64.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.96+dfsg-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dansguardian.
Unpacking dansguardian (from .../dansguardian_2.10.1.1-1really2.9.9.7-2ubuntu1_amd64.deb) ...
Selecting previously deselected package tinyproxy.
Unpacking tinyproxy (from .../tinyproxy_1.8.1-3_amd64.deb) ...
Selecting previously deselected package dhcp3-server.
Unpacking dhcp3-server (from .../dhcp3-server_3.1.3-2ubuntu3_amd64.deb) ...
Selecting previously deselected package dansguardian-gui.
Unpacking dansguardian-gui (from .../dansguardian-gui_2.4_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up clamav-base (0.96+dfsg-2ubuntu1) ...

Setting up clamav-freshclam (0.96+dfsg-2ubuntu1) ...
 * Starting ClamAV virus database updater freshclam                      [ OK ] 

Setting up clamav (0.96+dfsg-2ubuntu1) ...
Setting up dansguardian (2.10.1.1-1really2.9.9.7-2ubuntu1) ...
Warning: The home dir /var/log/dansguardian you specified already exists.
Adding system user `dansguardian' (UID 115) ...
Adding new group `dansguardian' (GID 123) ...
Adding new user `dansguardian' (UID 115) with group `dansguardian' ...
The home directory `/var/log/dansguardian' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/log/dansguardian' does not belong to the user you are currently creating.
update-rc.d: warning: dansguardian start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 3 5)
update-rc.d: warning: dansguardian stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.

Setting up tinyproxy (1.8.1-3) ...
Starting tinyproxy: tinyproxy.

Setting up dhcp3-server (3.1.3-2ubuntu3) ...
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

Setting up dansguardian-gui (2.4) ...
 Adding system startup for /etc/init.d/ubuntu_ce_firewall ...
   /etc/rc0.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc1.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc6.d/K91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc2.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc3.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc4.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall
   /etc/rc5.d/S91ubuntu_ce_firewall -> ../init.d/ubuntu_ce_firewall

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB


```

I'm not sure why dhcpd is installed, but it FAILS and this is what is in the syslog for output:

```
May  4 16:03:46 luther kernel: [  673.018810] type=1505 audit(1273003426.086:17):  operation="profile_replace" pid=9830 name="/usr/bin/freshclam"
May  4 16:03:54 luther kernel: [  681.097180] type=1505 audit(1273003434.167:18):  operation="profile_replace" pid=10058 name="/usr/sbin/dhcpd3"
May  4 16:03:54 luther dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May  4 16:03:54 luther dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May  4 16:03:54 luther dhcpd: All rights reserved.
May  4 16:03:54 luther dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  4 16:03:54 luther dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May  4 16:03:54 luther dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May  4 16:03:54 luther dhcpd: All rights reserved.
May  4 16:03:54 luther dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  4 16:03:54 luther dhcpd: Wrote 0 leases to leases file.
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for vmnet8 (192.168.173.1).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on vmnet8.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface vmnet8 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for vmnet1 (172.16.143.1).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on vmnet1.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface vmnet1 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for eth0 (192.168.2.9).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on eth0.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface eth0 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: Not configured to listen on any interfaces!
doug@luther:~/junk$ 
May  4 16:03:46 luther kernel: [  673.018810] type=1505 audit(1273003426.086:17):  operation="profile_replace" pid=9830 name="/usr/bin/freshclam"
May  4 16:03:54 luther kernel: [  681.097180] type=1505 audit(1273003434.167:18):  operation="profile_replace" pid=10058 name="/usr/sbin/dhcpd3"
May  4 16:03:54 luther dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May  4 16:03:54 luther dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May  4 16:03:54 luther dhcpd: All rights reserved.
May  4 16:03:54 luther dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  4 16:03:54 luther dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May  4 16:03:54 luther dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May  4 16:03:54 luther dhcpd: All rights reserved.
May  4 16:03:54 luther dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  4 16:03:54 luther dhcpd: Wrote 0 leases to leases file.
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for vmnet8 (192.168.173.1).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on vmnet8.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface vmnet8 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for vmnet1 (172.16.143.1).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on vmnet1.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface vmnet1 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: No subnet declaration for eth0 (192.168.2.9).
May  4 16:03:54 luther dhcpd: ** Ignoring requests on eth0.  If this is not what
May  4 16:03:54 luther dhcpd:    you want, please write a subnet declaration
May  4 16:03:54 luther dhcpd:    in your dhcpd.conf file for the network segment
May  4 16:03:54 luther dhcpd:    to which interface eth0 is attached. **
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: 
May  4 16:03:54 luther dhcpd: Not configured to listen on any interfaces!
doug@luther:~/junk$ 

```

After running the Autoconfigure in dansguardians-gui, then stop/start - DG continues to show down, even though the other two components are up.

Syslog has this:
```
May  4 16:09:26 luther dansguardian[13087]: Error connecting to parent proxy
May  4 16:09:39 luther dansguardian[13537]: Error connecting to parent proxy
```


Any ideas?

---

### Post by david_kt on 2010-05-04
> **doulos564 said:**
> 
I'm not sure why dhcpd is installed, but it FAILS and this is 

After running the Autoconfigure in dansguardians-gui, then stop/start - DG continues to show down, even though the other two components are up.

Syslog has this:
```
May  4 16:09:26 luther dansguardian[13087]: Error connecting to parent proxy
May  4 16:09:39 luther dansguardian[13537]: Error connecting to parent proxy
```

Any ideas?

DHCPD is installed for internet connection sharing, to give ip address automatically for LAN computers connected to ubuntu ce. It fails because it is not configured yet, but will not have any effect as it is only for internect connection sharing, not for filtering.

I am not sure why it could not connect to parent proxy as I have not tried Lucid yet so far. You could try restart your computer to see if it help. Failing that. you should try to configure the proxy and dansguardian manually, make sure it use the same port.

DK

---

### Post by doulos564 on 2010-05-06
Restarts don't help, unfortunately.
Initially, I found no tinyproxy.conf (just the *.original).
I created the tinyproxy.conf from this.
They both reference 3128.
Restarts of the DG and the system with DG enabled don't solve the issue.

How can I troubleshoot tinyproxy?
Does DG authenticate to TP?
If so, what is the mechanism (e.g. http post)?
Are there log/debug levels that can be set to give more information?

The problem symptoms seems similar to those that I experienced when 9.10 first came out.  The solution then was what dansguardian_install brought:
.10.1.1-1really2.9.9.7-2ubuntu1

But this is what's installed on my 10.04 system.

---

### Post by doulos564 on 2010-05-06
Well!  I found something significant!

/etc/init.d/tinyproxy has this line:
CONFIG=/etc/tinyproxy.conf

instead of this line on my working 9.10 system:
CONFIG=/etc/tinyproxy/tinyproxy.conf

This explains why the latter didn't exist until I created it - only the *.original.

The /etc/tinyproxy.conf had the following lines in it:
User nobody
Group nogroup
Port 8888

This explains why DG couldn't connect.
When I fixed these - root, root, and 3128, DG started working.

HOWEVER, FF started acting oddly.  Namely, any click on a menu (e.g., Bookmarks) or anything that had to pop up something (like >> on the links under the menus, and there was a 30-60sec lag for the action to complete.  And while the system lagged, sometimes FF darkened (like a hung process).

During this behavior, nothing was produced in the DG access log, but the tinyproxy.log had these lines coincidentally:

```

CONNECT   May 06 22:06:40 [3959]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:40 [3959]: Request (file descriptor 6): POST http://sync.xmarks.com/sync/bookmarks/getchanges HTTP/1.0
INFO      May 06 22:06:40 [3959]: No proxy for sync.xmarks.com
CONNECT   May 06 22:06:40 [3959]: Established connection to host "sync.xmarks.com" using file descriptor 7.
INFO      May 06 22:06:40 [3959]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:41 [3962]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:41 [3962]: Request (file descriptor 6): POST http://ocsp.thawte.com/ HTTP/1.0
INFO      May 06 22:06:41 [3962]: No proxy for ocsp.thawte.com
CONNECT   May 06 22:06:41 [3962]: Established connection to host "ocsp.thawte.com" using file descriptor 7.
INFO      May 06 22:06:41 [3962]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:41 [4212]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:41 [4212]: Request (file descriptor 6): POST http://sync.xmarks.com/sync/bookmarks/getchanges HTTP/1.0
INFO      May 06 22:06:41 [4212]: No proxy for sync.xmarks.com
CONNECT   May 06 22:06:42 [4212]: Established connection to host "sync.xmarks.com" using file descriptor 7.
INFO      May 06 22:06:42 [4212]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:54 [3963]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:54 [3963]: Request (file descriptor 6): POST http://safebrowsing.clients.google.com/safebrowsing/downloads?client=Firefox&appver=3.6.3&pver=2.2&wrkey=AKEgNitBdAofe3hIbNk_6hYaCFj-FlsZN1GfQ6MA-QTFYXBhjzh5zsIHBg8MfR6TwGKq5aihseeZqX0PCMAQAYJ3-gCouzu5YA== HTTP/1.0
INFO      May 06 22:06:54 [3963]: No proxy for safebrowsing.clients.google.com
CONNECT   May 06 22:06:54 [3963]: Established connection to host "safebrowsing.clients.google.com" using file descriptor 7.
INFO      May 06 22:06:54 [3963]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:54 [3960]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:54 [3960]: Request (file descriptor 6): GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGOzvBSDw7wUyBex3AQAf HTTP/1.0
INFO      May 06 22:06:54 [3960]: No proxy for safebrowsing-cache.google.com
CONNECT   May 06 22:06:54 [3960]: Established connection to host "safebrowsing-cache.google.com" using file descriptor 7.
INFO      May 06 22:06:54 [3960]: Closed connection between local client (fd:6) and remote client (fd:7)


```

Hope this helps as you work toward a 10.04 version of dansguardian_install.

Any ideas about the latter behavior?

Doug

---

### Post by doulos564 on 2010-05-06
BTW - I have the Xmarks add on installed in FF the reference to sync.xmarks is the periodic sync of my bookmarks with the server.

---

### Post by doulos564 on 2010-05-07
FF seems to be back to it's normal behavior tonight.  No noticable slowness whatsoever.  I don't understand it, but it's all working well!

---

### Post by marius_brkt on 2010-05-09
> **doulos564 said:**
> Well!  I found something significant!

/etc/init.d/tinyproxy has this line:
CONFIG=/etc/tinyproxy.conf

instead of this line on my working 9.10 system:
CONFIG=/etc/tinyproxy/tinyproxy.conf

This explains why the latter didn't exist until I created it - only the *.original.

The /etc/tinyproxy.conf had the following lines in it:
User nobody
Group nogroup
Port 8888

This explains why DG couldn't connect.
When I fixed these - root, root, and 3128, DG started working.

HOWEVER, FF started acting oddly.  Namely, any click on a menu (e.g., Bookmarks) or anything that had to pop up something (like >> on the links under the menus, and there was a 30-60sec lag for the action to complete.  And while the system lagged, sometimes FF darkened (like a hung process).

During this behavior, nothing was produced in the DG access log, but the tinyproxy.log had these lines coincidentally:

```

CONNECT   May 06 22:06:40 [3959]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:40 [3959]: Request (file descriptor 6): POST http://sync.xmarks.com/sync/bookmarks/getchanges HTTP/1.0
INFO      May 06 22:06:40 [3959]: No proxy for sync.xmarks.com
CONNECT   May 06 22:06:40 [3959]: Established connection to host "sync.xmarks.com" using file descriptor 7.
INFO      May 06 22:06:40 [3959]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:41 [3962]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:41 [3962]: Request (file descriptor 6): POST http://ocsp.thawte.com/ HTTP/1.0
INFO      May 06 22:06:41 [3962]: No proxy for ocsp.thawte.com
CONNECT   May 06 22:06:41 [3962]: Established connection to host "ocsp.thawte.com" using file descriptor 7.
INFO      May 06 22:06:41 [3962]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:41 [4212]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:41 [4212]: Request (file descriptor 6): POST http://sync.xmarks.com/sync/bookmarks/getchanges HTTP/1.0
INFO      May 06 22:06:41 [4212]: No proxy for sync.xmarks.com
CONNECT   May 06 22:06:42 [4212]: Established connection to host "sync.xmarks.com" using file descriptor 7.
INFO      May 06 22:06:42 [4212]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:54 [3963]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:54 [3963]: Request (file descriptor 6): POST http://safebrowsing.clients.google.com/safebrowsing/downloads?client=Firefox&appver=3.6.3&pver=2.2&wrkey=AKEgNitBdAofe3hIbNk_6hYaCFj-FlsZN1GfQ6MA-QTFYXBhjzh5zsIHBg8MfR6TwGKq5aihseeZqX0PCMAQAYJ3-gCouzu5YA== HTTP/1.0
INFO      May 06 22:06:54 [3963]: No proxy for safebrowsing.clients.google.com
CONNECT   May 06 22:06:54 [3963]: Established connection to host "safebrowsing.clients.google.com" using file descriptor 7.
INFO      May 06 22:06:54 [3963]: Closed connection between local client (fd:6) and remote client (fd:7)
CONNECT   May 06 22:06:54 [3960]: Connect (file descriptor 6): localhost [127.0.0.1]
CONNECT   May 06 22:06:54 [3960]: Request (file descriptor 6): GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGOzvBSDw7wUyBex3AQAf HTTP/1.0
INFO      May 06 22:06:54 [3960]: No proxy for safebrowsing-cache.google.com
CONNECT   May 06 22:06:54 [3960]: Established connection to host "safebrowsing-cache.google.com" using file descriptor 7.
INFO      May 06 22:06:54 [3960]: Closed connection between local client (fd:6) and remote client (fd:7)


```Hope this helps as you work toward a 10.04 version of dansguardian_install.

Any ideas about the latter behavior?

Doug


So, I've configured tinyproxy.conf ( from /etc/tinyproxy.conf) as follows:
User root
Group root
Port 3128

all is OK, danguardian filter, but some pages ( including this one and all pages of ubuntuforums) are blank..withe..nothing appear, alltough is connected

To post this, I had to stop dansguardian..I am abble to open some other pages..

keep you posted for some other bugs..

maybe u can help me...

I run 10.04 32bytes

---

### Post by calebyong on 2010-05-10
is there a fix for the blank pages? i hate restarting every time i get this problem.

---

### Post by david_kt on 2010-05-10
> **calebyong said:**
> is there a fix for the blank pages? i hate restarting every time i get this problem.

I have not tried it myself as I am still busy with other things. But what I understand is we could use other proxy instead of tinyproxy, to solve this issue.

DK

---

### Post by doulos564 on 2010-05-18
calebyong,

What versions of dansguardian and tinyproxy are you running?
I had this issue when I first upgraded to 9.10, but it was solved for almost all URLs later.

---

### Post by calebyong on 2010-05-20
How to check it if i'm not an admin?

---

### Post by doulos564 on 2010-05-20
Goto Applications > Accessories > Terminal

In the terminal window:
apptitude show dansguardian

The output will have a line like this:
Version: 2.10.1.1-1really2.9.9.7-2ubuntu1

---

### Post by Eutaw on 2010-06-03
I upgraded using the package manager, everything I'm trying seems to be working. 2 minor issues I'd like to change. I don't like the splash image (pic of the statue) but I can't seem to change it. I tried following the instructions in the forum, but the text is not exactly the same. any advice would be appreciated.
Also, switching the Close/Minimize/Maximize buttons from top right of screen to top left? I'd prefer it the original way, if there's an easy way to toggle it back.
Thanks

---

### Post by david_kt on 2010-06-04
> **Eutaw said:**
> I upgraded using the package manager, everything I'm trying seems to be working. 2 minor issues I'd like to change. I don't like the splash image (pic of the statue) but I can't seem to change it. I tried following the instructions in the forum, but the text is not exactly the same. any advice would be appreciated.
Also, switching the Close/Minimize/Maximize buttons from top right of screen to top left? I'd prefer it the original way, if there's an easy way to toggle it back.
Thanks

1 Splash image: after change the image, run:
sudo update-initramfs -u

2. Move back to top right: System > Preferences > Appearance >
Choose the theme that provide the button on the right.

DK

---

### Post by Eutaw on 2010-06-05
Thanks David. I appreciate your patience and help.

---

### Post by ekhansen on 2010-06-10
I have tried the above to no avail.  I am running Ubuntu 10.04 64 bit.  Karmic was running just fine with DG GUI.  I use Mozilla Firefox.

/etc/tinyproxy/tinyproxy.conf
user root
group root
port 3128

/etc/init.d/tinyproxy 
CONFIG=/etc/tinyproxy/tinyproxy.conf 
(I edited it to read this, it originally read just /etc/tinyproxy.conf)

If I run Firefox without a proxy but with DG active the connection times out, which IIRC is what it should do.  If I manually configure Firefox to use HTTP proxy 127.0.0.1 and port 8080, as used to work with DG, I get a proxy server error even if DG is up and running.

When I fire up DG GUI I get a dialog that tinyproxy and DG are starting, but only redirection is listed as on.  DG and tinyproxy are both still listed as off in the GUI.  But when I try to start DG again or lock tinyproxy individually in the GUI it tells me they are already up and running or locked.

I think this is the same thing the others on this thread have had problems with.  But things aren't working out for me as it appears to have for others.  I don't know why.  What am I doing wrong?

---

### Post by doulos564 on 2010-06-10
When I dealt with the problem, I also tried this, but tinyproxy did not start correctly.

You need to change /etc/init.d/tinyproxy back to 
CONFIG=/etc/tinyproxy.conf

Then edit /etc/tinyproxy.conf to have:
user root
group root
port 3128

Things then started correctly for me.
I'm not sure why yet, but it worked.

Awaiting His Shout,
Doug
Romans 8:28-31

---

### Post by doulos564 on 2010-06-10
I just tried this, and it also worked.
Copy /etc/tinyproxy.conf to /etc/tinyproxy/tinyproxy.conf
sudo cp -p /etc/tinyproxy/tinyproxy.conf /etc/tinyproxy/tinyproxy.conf.old
sudo cp -p /etc/tinyproxy.conf /etc/tinyproxy/tinyproxy.conf.old

without changing the CONFIG line back, and tinyproxy work.
HOWEVER, the DEB install package doesn't know that the location of the config file has changed.  So, this may effect updated a patch may make to the file.

Doug

---

### Post by david_kt on 2010-06-10
> **ekhansen said:**
> I have tried the above to no avail.  I am running Ubuntu 10.04 64 bit.  Karmic was running just fine with DG GUI.  I use Mozilla Firefox.

/etc/tinyproxy/tinyproxy.conf
user root
group root
port 3128

/etc/init.d/tinyproxy 
CONFIG=/etc/tinyproxy/tinyproxy.conf 
(I edited it to read this, it originally read just /etc/tinyproxy.conf)

If I run Firefox without a proxy but with DG active the connection times out, which IIRC is what it should do.  If I manually configure Firefox to use HTTP proxy 127.0.0.1 and port 8080, as used to work with DG, I get a proxy server error even if DG is up and running.

When I fire up DG GUI I get a dialog that tinyproxy and DG are starting, but only redirection is listed as on.  DG and tinyproxy are both still listed as off in the GUI.  But when I try to start DG again or lock tinyproxy individually in the GUI it tells me they are already up and running or locked.

I think this is the same thing the others on this thread have had problems with.  But things aren't working out for me as it appears to have for others.  I don't know why.  What am I doing wrong?

Please follow the instruction on below thread:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

You could replace sudo apt-get install ubuntu-ce with sudo apt-get install dansguardian-gui if you only want dansguardian, not ubuntu ce.

DK

---

### Post by ekhansen on 2010-06-11
A big thank you to both doulos and david_kt.  I followed your first instructions doulos, and it works like old times again.

david_kt, the instructions you give in the other thread are exactly how I first installed DG GUI under Karmic Koala.  In future I won't upgrade to a new release until Ubuntu CE is ready with DG running smoothly.  I love DG and can't live without it.

---

