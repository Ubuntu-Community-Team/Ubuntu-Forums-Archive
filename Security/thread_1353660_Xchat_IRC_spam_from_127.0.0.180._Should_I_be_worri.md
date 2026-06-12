---
title: "Xchat IRC spam from 127.0.0.1:80. Should I be worried?"
date: 2009-12-13
forum: Security
---

### Post by KIAaze on 2009-12-13
Hi,

Today I got spam through IRC for the second time (The first time made me set the default preferences for "auto-accept file offers" from "Browse for save folder everytime" to 'No").

I'm using Xchat.

I checked the details about the file offers and apparently some come from 69.73.253.37:28061 and others from **127.0.0.1:80**!!!

Should I be worried?

P.S.: 69.73.253.37 is not my outside IP address.

The file offers came from Tex on the #esperanto channel on freenode this time (could just be because that was the active channel). I don't know where they came from last time.
I tried sending myself a file and it showed my outside IP address as source.

---

### Post by schauerlich on 2009-12-13
LOL WUT

No really.

---

### Post by -grubby on 2009-12-13
Yeah, that looks fishy. Just don't accept the transfers and you'll be fine.

---

### Post by KIAaze on 2009-12-13
But how can they come from 127.0.0.1?
Is there a trick to change the IP source address or could my PC be compromised?

I tried sending a file to myself and it shows my outside IP address. How can it even show 127.0.0.1?

---

### Post by FuturePilot on 2009-12-13
Are you running a webserver or proxy or something?

---

### Post by KIAaze on 2009-12-13
No, not that I know of.
I even deactivated samba file-sharing a while ago (it was not running when the file offers happened and is still not running). That's the only server like thing I can think of.

```
&#9484;&#9472;(~)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9492;&#9472;(^_^)(15)&#9472;> dpkg -l *server*                                                                                                                                                                                                              
Desired=Unknown/Install/Remove/Purge/Hold                                                                                                                                                                                                   
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend                                                                                                                                                              
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)                                                                                                                                                                                  
||/ Name                                                  Version                                               Description                                                                                                                 
+++-=====================================================-=====================================================-==========================================================================================================================  
ii  akonadi-server                                        1.2.1-0ubuntu4                                        Akonadi PIM storage service                                                                                                 
un  dict-server                                           <none>                                                (no description available)                                                                                                  
ii  evolution-data-server                                 2.28.1-0ubuntu1                                       evolution database backend server                                                                                           
ii  evolution-data-server-common                          2.28.1-0ubuntu1                                       architecture independent files for Evolution Data Server                                                                    
un  evolution-data-server-dbg                             <none>                                                (no description available)                                                                                                  
un  evolution-data-server1.2                              <none>                                                (no description available)                                                                                                  
un  inet-superserver                                      <none>                                                (no description available)                                                                                                  
un  ksmserver                                             <none>                                                (no description available)                                                                                                  
ii  libedataserver1.2-11                                  2.28.1-0ubuntu1                                       Utility library for evolution data servers                                                                                  
ii  libedataserverui1.2-8                                 2.28.1-0ubuntu1                                       GUI utility library for evolution data servers                                                                              
ii  libhttp-server-simple-perl                            0.38-1                                                simple stand-alone HTTP server                                                                                              
ii  libmissioncontrol-server1                             4.67-1ubuntu1                                         Telepathy mission control plugin library                                                                                    
un  libvncserver0                                         <none>                                                (no description available)                                                                                                  
un  libvncserver0-dbg                                     <none>                                                (no description available)                                                                                                  
un  mysql-server-5.1                                      <none>                                                (no description available)                                                                                                  
un  mysql-server-core                                     <none>                                                (no description available)                                                                                                  
un  mysql-server-core-5.0                                 <none>                                                (no description available)                                                                                                  
ii  mysql-server-core-5.1                                 5.1.37-1ubuntu5                                       MySQL database core server files                                                                                            
un  mysql-server-data-5.1                                 <none>                                                (no description available)                                                                                                  
ii  obex-data-server                                      0.4.4-2build1                                         D-Bus service for OBEX client and server side functionality                                                                 
un  openarena-server                                      <none>                                                (no description available)                                                                                                  
un  openssh-server                                        <none>                                                (no description available)                                                                                                  
un  rsh-server                                            <none>                                                (no description available)                                                                                                  
ii  x11-xserver-utils                                     7.4+2ubuntu3                                          X server utilities                                                                                                          
un  xserver                                               <none>                                                (no description available)                                                                                                  
ii  xserver-common                                        2:1.6.4-2ubuntu4.1                                    common files used by various X servers                                                                                      
ii  xserver-xephyr                                        2:1.6.4-2ubuntu4.1                                    nested X server                                                                                                             
un  xserver-xfree86                                       <none>                                                (no description available)                                                                                                  
un  xserver-xfree86-dbg                                   <none>                                                (no description available)                                                                                                  
ii  xserver-xorg                                          1:7.4+3ubuntu10                                       the X.Org X server                                                                                                          
ii  xserver-xorg-core                                     2:1.6.4-2ubuntu4.1                                    Xorg X server - core server                                                                                                 
un  xserver-xorg-driver-all                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-apm                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-ark                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-chips                             <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-cirrus                            <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-fbdev                             <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-i128                              <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-i810                              <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-mga                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-neomagic                          <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-nv                                <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-rendition                         <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-s3                                <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-s3virge                           <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-savage                            <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-siliconmotion                     <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-sis                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-sisusb                            <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-tdfx                              <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-trident                           <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-tseng                             <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-v4l                               <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-vesa                              <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-vmware                            <none>                                                (no description available)                                                                                                  
un  xserver-xorg-driver-voodoo                            <none>                                                (no description available)                                                                                                  
un  xserver-xorg-input                                    <none>                                                (no description available)                                                                                                  
un  xserver-xorg-input-2                                  <none>                                                (no description available)                                                                                                  
un  xserver-xorg-input-2.1                                <none>                                                (no description available)                                                                                                  
un  xserver-xorg-input-4                                  <none>                                                (no description available)                                                                                                  
ii  xserver-xorg-input-all                                1:7.4+3ubuntu10                                       the X.Org X server -- input driver metapackage                                                                              
ii  xserver-xorg-input-evdev                              1:2.2.5-1ubuntu6                                      X.Org X server -- evdev input driver                                                                                        
ii  xserver-xorg-input-kbd                                1:1.3.2-3                                             X.Org X server -- keyboard input driver                                                                                     
ii  xserver-xorg-input-mouse                              1:1.4.0-2                                             X.Org X server -- mouse input driver                                                                                        
ii  xserver-xorg-input-synaptics                          1.1.2-1ubuntu7                                        Synaptics TouchPad driver for X.Org server                                                                                  
ii  xserver-xorg-input-vmmouse                            1:12.6.4-1ubuntu3                                     X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                              1:0.8.4.1-0ubuntu4                                    X.Org X server -- Wacom input driver
un  xserver-xorg-video                                    <none>                                                (no description available)
un  xserver-xorg-video-1.0                                <none>                                                (no description available)
un  xserver-xorg-video-1.9                                <none>                                                (no description available)
un  xserver-xorg-video-2                                  <none>                                                (no description available)
un  xserver-xorg-video-4                                  <none>                                                (no description available)
un  xserver-xorg-video-5                                  <none>                                                (no description available)
ii  xserver-xorg-video-all                                1:7.4+3ubuntu10                                       the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-apm                                1:1.2.1-2                                             X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                                1:0.7.1-2                                             X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                                1:6.12.99+git20090929.7968e1fb-0ubuntu1               X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                              1:1.2.1-3                                             X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                             1:1.3.1-1ubuntu2                                      X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                              1:0.4.0-4                                             X.Org X server -- fbdev display driver
ii  xserver-xorg-video-i128                               1:1.3.2-1                                             X.Org X server -- i128 display driver
un  xserver-xorg-video-i810                               <none>                                                (no description available)
un  xserver-xorg-video-i810-modesetting                   <none>                                                (no description available)
ii  xserver-xorg-video-intel                              2:2.9.0-1ubuntu2                                      X.Org X server -- Intel i8xx, i9xx display driver
un  xserver-xorg-video-intel-modesetting                  <none>                                                (no description available)
ii  xserver-xorg-video-mach64                             6.8.2-1                                               X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                                1:1.4.11.dfsg-1                                       X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                           1:1.2.3-1                                             X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nv                                 1:2.1.14-2ubuntu3                                     X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome                         1:0.2.903+svn758-0ubuntu1                             X.Org X server -- VIA display driver
un  xserver-xorg-video-psb                                <none>                                                (no description available)
ii  xserver-xorg-video-r128                               6.8.1-1                                               X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                             1:6.12.99+git20090929.7968e1fb-0ubuntu1               X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-rendition                          1:4.2.1-1                                             X.Org X server -- Rendition display driver
un  xserver-xorg-video-riva128                            <none>                                                (no description available)
ii  xserver-xorg-video-s3                                 1:0.6.2-1                                             X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                            1:1.10.2-2                                            X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                             1:2.3.0-1ubuntu1                                      X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion                      1:1.7.2-1                                             X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                                1:0.10.1-2                                            X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                             1:0.9.1-1                                             X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                               1:1.4.1-1                                             X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                            1:1.3.1-1                                             X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                              1:1.2.1-1                                             X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                                1:0.2.0-3ubuntu1                                      X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa                               1:2.2.1-1                                             X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                             1:10.16.7-1                                           X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                             1:1.2.2-1                                             X.Org X server -- Voodoo display driver
&#9484;&#9472;(~)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9492;&#9472;(^_^)(16)&#9472;> dpkg -l *apache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
un  apache2.2-common                                      <none>                                                (no description available)
un  libapache-mod-auth-kerb                               <none>                                                (no description available)
un  libapache2-mod-auth-kerb                              <none>                                                (no description available)
un  libapache2-mod-perl2                                  <none>                                                (no description available)

```

rkhunter log:
```
[08:24:36] Running Rootkit Hunter version 1.3.4 on kiaaze-desktop
[08:24:36]
[08:24:36] Info: Start date is Sun Dec 13 08:24:36 CET 2009
[08:24:37]
[08:24:37] Checking configuration file and command-line options...
[08:24:37] Info: Detected operating system is 'Linux'
[08:24:37] Info: Found O/S name: Ubuntu 9.10
[08:24:37] Info: Command line is /usr/bin/rkhunter -c -sk
[08:24:37] Info: Environment shell is /bin/bash; rkhunter is using dash
[08:24:37] Info: Using configuration file '/etc/rkhunter.conf'
[08:24:37] Info: Installation directory is '/usr'
[08:24:37] Info: Using language 'en'
[08:24:37] Info: Using '/var/lib/rkhunter/db' as the database directory
[08:24:37] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[08:24:37] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[08:24:37] Info: Using '/' as the root directory by default
[08:24:37] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[08:24:37] Info: No mail-on-warning address configured
[08:24:37] Info: X will be automatically detected
[08:24:37] Info: Using second color set
[08:24:37] Info: Found the 'diff' command: /usr/bin/diff
[08:24:37] Info: Found the 'file' command: /usr/bin/file
[08:24:37] Info: Found the 'find' command: /usr/bin/find
[08:24:37] Info: Found the 'ifconfig' command: /sbin/ifconfig
[08:24:37] Info: Found the 'ip' command: /sbin/ip
[08:24:37] Info: Found the 'ldd' command: /usr/bin/ldd
[08:24:37] Info: Found the 'lsattr' command: /usr/bin/lsattr
[08:24:37] Info: Found the 'lsmod' command: /sbin/lsmod
[08:24:37] Info: Found the 'lsof' command: /usr/bin/lsof
[08:24:37] Info: Found the 'mktemp' command: /bin/mktemp
[08:24:37] Info: Found the 'netstat' command: /bin/netstat
[08:24:37] Info: Found the 'perl' command: /usr/bin/perl
[08:24:37] Info: Found the 'ps' command: /bin/ps
[08:24:37] Info: Found the 'pwd' command: /bin/pwd
[08:24:37] Info: Found the 'readlink' command: /bin/readlink
[08:24:37] Info: Found the 'sort' command: /usr/bin/sort
[08:24:37] Info: Found the 'stat' command: /usr/bin/stat
[08:24:37] Info: Found the 'strings' command: /usr/bin/strings
[08:24:37] Info: Found the 'uniq' command: /usr/bin/uniq
[08:24:37] Info: System is not using prelinking
[08:24:37] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[08:24:37] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[08:24:37] Info: Stored hash values did not use a package manager
[08:24:37] Info: The hash function field index is set to 1
[08:24:37] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[08:24:38] Info: Previous file attributes were stored
[08:24:38] Info: Enabled tests are: all
[08:24:38] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[08:24:38] Info: Found ksym file '/proc/kallsyms'
[08:24:38]
[08:24:38] Checking if the O/S has changed since last time...
[08:24:38] Info: Nothing seems to have changed
[08:24:38]
[08:24:38] Starting system checks...
[08:24:38]
[08:24:38] Checking system commands...
[08:24:38] Info: Starting test name 'system_commands'
[08:24:38]
[08:24:38] Performing 'strings' command checks
[08:24:38] Info: Starting test name 'strings'
[08:24:38] Scanning for string /usr/sbin/ntpsx               [ OK ]
[08:24:38] Scanning for string /usr/lib/.../ls               [ OK ]
[08:24:38] Scanning for string /usr/lib/.../netstat          [ OK ]
[08:24:38] Scanning for string /usr/lib/.../lsof             [ OK ]
[08:24:38] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[08:24:38] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[08:24:38] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[08:24:38] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[08:24:38] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[08:24:38] Scanning for string /usr/lib/.../psr              [ OK ]
[08:24:38] Scanning for string /usr/lib/.../find             [ OK ]
[08:24:38] Scanning for string /usr/lib/.../pstree           [ OK ]
[08:24:38] Scanning for string /usr/lib/.../slocate          [ OK ]
[08:24:38] Scanning for string /usr/lib/.../du               [ OK ]
[08:24:39] Scanning for string /usr/lib/.../top              [ OK ]
[08:24:39] Scanning for string /usr/lib/...                  [ OK ]
[08:24:39] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[08:24:39] Scanning for string /usr/lib/.bkit-               [ OK ]
[08:24:39] Scanning for string /tmp/.bkp                     [ OK ]
[08:24:39] Scanning for string /tmp/.cinik                   [ OK ]
[08:24:39] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[08:24:39] Scanning for string /lib/.sso                     [ OK ]
[08:24:39] Scanning for string /lib/.so                      [ OK ]
[08:24:39] Scanning for string /var/run/...dica/clean        [ OK ]
[08:24:39] Scanning for string /var/run/...dica/xl           [ OK ]
[08:24:39] Scanning for string /var/run/...dica/xdr          [ OK ]
[08:24:39] Scanning for string /var/run/...dica/psg          [ OK ]
[08:24:39] Scanning for string /var/run/...dica/secure       [ OK ]
[08:24:39] Scanning for string /var/run/...dica/rdx          [ OK ]
[08:24:39] Scanning for string /var/run/...dica/va           [ OK ]
[08:24:39] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[08:24:39] Scanning for string /usr/bin/.etc                 [ OK ]
[08:24:39] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[08:24:39] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[08:24:40] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[08:24:40] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[08:24:40] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[08:24:40] Scanning for string /bin/sysback                  [ OK ]
[08:24:40] Scanning for string /usr/local/bin/sysback        [ OK ]
[08:24:40] Scanning for string /usr/lib/.tbd                 [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[08:24:40] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[08:24:41] Scanning for string /usr/info/.torn/sh*           [ OK ]
[08:24:41] Scanning for string /usr/src/.****/.1addr         [ OK ]
[08:24:41] Scanning for string /usr/src/.****/.1file         [ OK ]
[08:24:41] Scanning for string /usr/src/.****/.1proc         [ OK ]
[08:24:41] Scanning for string /usr/src/.****/.1logz         [ OK ]
[08:24:41] Scanning for string /usr/info/.t0rn               [ OK ]
[08:24:41] Scanning for string /dev/.lib                     [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib                 [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib             [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[08:24:41] Scanning for string /dev/.lib/lib/scan            [ OK ]
[08:24:41] Scanning for string /usr/src/.****                [ OK ]
[08:24:41] Scanning for string /usr/man/man1/man1            [ OK ]
[08:24:42] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[08:24:42] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[08:24:42] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[08:24:42]
[08:24:42] Performing 'shared libraries' checks
[08:24:42] Info: Starting test name 'shared_libs'
[08:24:42] Checking for preloading variables                 [ None found ]
[08:24:42] Checking for preload file                         [ Not found ]
[08:24:42] Info: Starting test name 'shared_libs_path'
[08:24:42] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[08:24:42]
[08:24:42] Performing file properties checks
[08:24:42] Info: Starting test name 'properties'
[08:24:42] Checking for prerequisites                        [ OK ]
[08:24:42] /bin/bash                                         [ OK ]
[08:24:42] /bin/cat                                          [ OK ]
[08:24:43] /bin/chmod                                        [ OK ]
[08:24:43] /bin/chown                                        [ OK ]
[08:24:43] /bin/cp                                           [ OK ]
[08:24:43] /bin/date                                         [ OK ]
[08:24:43] /bin/df                                           [ OK ]
[08:24:43] /bin/dmesg                                        [ OK ]
[08:24:43] /bin/echo                                         [ OK ]
[08:24:44] /bin/ed                                           [ OK ]
[08:24:44] /bin/egrep                                        [ OK ]
[08:24:44] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[08:24:44] /bin/fgrep                                        [ OK ]
[08:24:44] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[08:24:44] /bin/fuser                                        [ OK ]
[08:24:44] /bin/grep                                         [ OK ]
[08:24:44] /bin/ip                                           [ OK ]
[08:24:45] /bin/kill                                         [ OK ]
[08:24:45] /bin/less                                         [ OK ]
[08:24:45] /bin/login                                        [ OK ]
[08:24:45] /bin/ls                                           [ OK ]
[08:24:45] /bin/lsmod                                        [ OK ]
[08:24:45] /bin/mktemp                                       [ OK ]
[08:24:46] /bin/more                                         [ OK ]
[08:24:46] /bin/mount                                        [ OK ]
[08:24:46] /bin/mv                                           [ OK ]
[08:24:46] /bin/netstat                                      [ OK ]
[08:24:46] /bin/ps                                           [ OK ]
[08:24:46] /bin/pwd                                          [ OK ]
[08:24:46] /bin/readlink                                     [ OK ]
[08:24:47] /bin/sed                                          [ OK ]
[08:24:47] /bin/sh                                           [ OK ]
[08:24:47] /bin/su                                           [ OK ]
[08:24:47] /bin/touch                                        [ OK ]
[08:24:47] /bin/uname                                        [ OK ]
[08:24:48] /bin/which                                        [ OK ]
[08:24:48] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[08:24:48] /bin/dash                                         [ OK ]
[08:24:48] /usr/bin/awk                                      [ OK ]
[08:24:48] /usr/bin/basename                                 [ OK ]
[08:24:48] /usr/bin/chattr                                   [ OK ]
[08:24:48] /usr/bin/curl                                     [ OK ]
[08:24:49] /usr/bin/cut                                      [ OK ]
[08:24:49] /usr/bin/diff                                     [ OK ]
[08:24:49] /usr/bin/dirname                                  [ OK ]
[08:24:49] /usr/bin/dpkg                                     [ OK ]
[08:24:49] /usr/bin/dpkg-query                               [ OK ]
[08:24:49] /usr/bin/du                                       [ OK ]
[08:24:49] /usr/bin/env                                      [ OK ]
[08:24:50] /usr/bin/file                                     [ OK ]
[08:24:50] /usr/bin/find                                     [ OK ]
[08:24:50] /usr/bin/GET                                      [ OK ]
[08:24:50] /usr/bin/groups                                   [ OK ]
[08:24:50] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[08:24:50] /usr/bin/head                                     [ OK ]
[08:24:50] /usr/bin/id                                       [ OK ]
[08:24:50] /usr/bin/killall                                  [ OK ]
[08:24:51] /usr/bin/last                                     [ OK ]
[08:24:51] /usr/bin/lastlog                                  [ OK ]
[08:24:51] /usr/bin/ldd                                      [ OK ]
[08:24:51] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[08:24:51] /usr/bin/less                                     [ OK ]
[08:24:51] /usr/bin/links                                    [ OK ]
[08:24:51] /usr/bin/locate                                   [ OK ]
[08:24:51] /usr/bin/logger                                   [ OK ]
[08:24:52] /usr/bin/lsattr                                   [ OK ]
[08:24:52] /usr/bin/lsof                                     [ OK ]
[08:24:52] /usr/bin/mail                                     [ OK ]
[08:24:52] /usr/bin/md5sum                                   [ OK ]
[08:24:52] /usr/bin/mlocate                                  [ OK ]
[08:24:52] /usr/bin/newgrp                                   [ OK ]
[08:24:53] /usr/bin/passwd                                   [ OK ]
[08:24:53] /usr/bin/perl                                     [ OK ]
[08:24:53] /usr/bin/pstree                                   [ OK ]
[08:24:53] /usr/bin/rkhunter                                 [ OK ]
[08:24:53] /usr/bin/rpm                                      [ OK ]
[08:24:53] /usr/bin/runcon                                   [ OK ]
[08:24:53] /usr/bin/sha1sum                                  [ OK ]
[08:24:54] /usr/bin/size                                     [ OK ]
[08:24:54] /usr/bin/sort                                     [ OK ]
[08:24:54] /usr/bin/stat                                     [ OK ]
[08:24:54] /usr/bin/strace                                   [ OK ]
[08:24:54] /usr/bin/strings                                  [ OK ]
[08:24:54] /usr/bin/sudo                                     [ OK ]
[08:24:54] /usr/bin/tail                                     [ OK ]
[08:24:55] /usr/bin/test                                     [ OK ]
[08:24:55] /usr/bin/top                                      [ OK ]
[08:24:55] /usr/bin/touch                                    [ OK ]
[08:24:55] /usr/bin/tr                                       [ OK ]
[08:24:55] /usr/bin/uniq                                     [ OK ]
[08:24:55] /usr/bin/users                                    [ OK ]
[08:24:55] /usr/bin/vmstat                                   [ OK ]
[08:24:56] /usr/bin/w                                        [ OK ]
[08:24:56] /usr/bin/watch                                    [ OK ]
[08:24:56] /usr/bin/wc                                       [ OK ]
[08:24:56] /usr/bin/wget                                     [ OK ]
[08:24:56] /usr/bin/whatis                                   [ OK ]
[08:24:56] /usr/bin/whereis                                  [ OK ]
[08:24:56] /usr/bin/which                                    [ OK ]
[08:24:56] /usr/bin/who                                      [ OK ]
[08:24:57] /usr/bin/whoami                                   [ OK ]
[08:24:57] /usr/bin/gawk                                     [ OK ]
[08:24:57] /usr/bin/lwp-request                              [ OK ]
[08:24:57] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[08:24:57] /usr/bin/heirloom-mailx                           [ OK ]
[08:24:57] /usr/bin/w.procps                                 [ OK ]
[08:24:57] /sbin/depmod                                      [ OK ]
[08:24:58] /sbin/ifconfig                                    [ OK ]
[08:24:58] /sbin/ifdown                                      [ OK ]
[08:24:58] /sbin/ifup                                        [ OK ]
[08:24:58] /sbin/init                                        [ OK ]
[08:24:58] /sbin/insmod                                      [ OK ]
[08:24:58] /sbin/ip                                          [ OK ]
[08:24:59] /sbin/lsmod                                       [ OK ]
[08:24:59] /sbin/modinfo                                     [ OK ]
[08:24:59] /sbin/modprobe                                    [ OK ]
[08:24:59] /sbin/rmmod                                       [ OK ]
[08:25:00] /sbin/runlevel                                    [ OK ]
[08:25:00] /sbin/sulogin                                     [ OK ]
[08:25:00] /sbin/sysctl                                      [ OK ]
[08:25:00] /usr/sbin/adduser                                 [ OK ]
[08:25:00] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[08:25:01] /usr/sbin/chroot                                  [ OK ]
[08:25:01] /usr/sbin/cron                                    [ OK ]
[08:25:01] /usr/sbin/groupadd                                [ OK ]
[08:25:01] /usr/sbin/groupdel                                [ OK ]
[08:25:01] /usr/sbin/groupmod                                [ OK ]
[08:25:01] /usr/sbin/grpck                                   [ OK ]
[08:25:02] /usr/sbin/nologin                                 [ OK ]
[08:25:02] /usr/sbin/pwck                                    [ OK ]
[08:25:02] /usr/sbin/rsyslogd                                [ OK ]
[08:25:02] /usr/sbin/sestatus                                [ OK ]
[08:25:03] /usr/sbin/tcpd                                    [ OK ]
[08:25:03] /usr/sbin/unhide                                  [ OK ]
[08:25:03] /usr/sbin/useradd                                 [ OK ]
[08:25:03] /usr/sbin/userdel                                 [ OK ]
[08:25:03] /usr/sbin/usermod                                 [ OK ]
[08:25:03] /usr/sbin/vipw                                    [ OK ]
[08:25:04] /usr/sbin/unhide-linux26                          [ OK ]
[08:25:08]
[08:25:08] Checking for rootkits...
[08:25:08] Info: Starting test name 'rootkits'
[08:25:08]
[08:25:08] Performing check of known rootkit files and directories
[08:25:08] Info: Starting test name 'known_rkts'
[08:25:08]
[08:25:08] Checking for 55808 Trojan - Variant A...
[08:25:08]   Checking for file '/tmp/.../r'                  [ Not found ]
[08:25:09]   Checking for file '/tmp/.../a'                  [ Not found ]
[08:25:09] 55808 Trojan - Variant A                          [ Not found ]
[08:25:09]
[08:25:09] Checking for ADM Worm...
[08:25:09]   Checking for string 'w0rm'                      [ Not found ]
[08:25:09] ADM Worm                                          [ Not found ]
[08:25:09]
[08:25:09] Checking for AjaKit Rootkit...
[08:25:09]   Checking for file '/dev/tux/.addr'              [ Not found ]
[08:25:09]   Checking for file '/dev/tux/.proc'              [ Not found ]
[08:25:09]   Checking for file '/dev/tux/.file'              [ Not found ]
[08:25:09]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[08:25:09]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[08:25:09]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[08:25:09]   Checking for directory '/dev/tux'               [ Not found ]
[08:25:09]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[08:25:09] AjaKit Rootkit                                    [ Not found ]
[08:25:09]
[08:25:09] Checking for aPa Kit...
[08:25:09]   Checking for file '/usr/share/.aPa'             [ Not found ]
[08:25:09] aPa Kit                                           [ Not found ]
[08:25:09]
[08:25:09] Checking for Apache Worm...
[08:25:09]   Checking for file '/bin/.log'                   [ Not found ]
[08:25:09] Apache Worm                                       [ Not found ]
[08:25:09]
[08:25:09] Checking for Ambient (ark) Rootkit...
[08:25:09]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[08:25:09]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[08:25:10]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[08:25:10]   Checking for directory '/dev/ptyxx'             [ Not found ]
[08:25:10] Ambient (ark) Rootkit                             [ Not found ]
[08:25:10]
[08:25:10] Checking for Balaur Rootkit...
[08:25:10]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[08:25:10]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[08:25:10]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[08:25:10]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[08:25:10] Balaur Rootkit                                    [ Not found ]
[08:25:10]
[08:25:10] Checking for BeastKit Rootkit...
[08:25:10]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[08:25:10]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[08:25:10]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[08:25:10]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[08:25:10] BeastKit Rootkit                                  [ Not found ]
[08:25:10]
[08:25:10] Checking for beX2 Rootkit...
[08:25:10]   Checking for directory '/usr/include/bex'       [ Not found ]
[08:25:11] beX2 Rootkit                                      [ Not found ]
[08:25:11]
[08:25:11] Checking for BOBKit Rootkit...
[08:25:11]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../find'           [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../du'             [ Not found ]
[08:25:11]   Checking for file '/usr/lib/.../top'            [ Not found ]
[08:25:11]   Checking for directory '/usr/lib/...'           [ Not found ]
[08:25:11]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[08:25:11]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[08:25:11]   Checking for directory '/tmp/.bkp'              [ Not found ]
[08:25:11] BOBKit Rootkit                                    [ Not found ]
[08:25:12]
[08:25:12] Checking for CiNIK Worm (Slapper.B variant)...
[08:25:12]   Checking for file '/tmp/.cinik'                 [ Not found ]
[08:25:12]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[08:25:12] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[08:25:12]
[08:25:12] Checking for Danny-Boy's Abuse Kit...
[08:25:12]   Checking for file '/dev/mdev'                   [ Not found ]
[08:25:12]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[08:25:12] Danny-Boy's Abuse Kit                             [ Not found ]
[08:25:12]
[08:25:12] Checking for Devil RootKit...
[08:25:12]   Checking for file '/var/lib/games/.src'         [ Not found ]
[08:25:12]   Checking for file '/dev/dsx'                    [ Not found ]
[08:25:12]   Checking for file '/dev/caca'                   [ Not found ]
[08:25:12] Devil RootKit                                     [ Not found ]
[08:25:12]
[08:25:12] Checking for Dica-Kit Rootkit...
[08:25:12]   Checking for file '/lib/.sso'                   [ Not found ]
[08:25:12]   Checking for file '/lib/.so'                    [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[08:25:12]   Checking for file '/var/run/...dica/va'         [ Not found ]
[08:25:13]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[08:25:13]   Checking for file '/usr/bin/.etc'               [ Not found ]
[08:25:13]   Checking for directory '/var/run/...dica'       [ Not found ]
[08:25:13]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[08:25:13]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[08:25:13] Dica-Kit Rootkit                                  [ Not found ]
[08:25:13]
[08:25:13] Checking for Dreams Rootkit...
[08:25:13]   Checking for file '/dev/ttyoa'                  [ Not found ]
[08:25:13]   Checking for file '/dev/ttyof'                  [ Not found ]
[08:25:13]   Checking for file '/dev/ttyop'                  [ Not found ]
[08:25:13]   Checking for file '/usr/bin/sense'              [ Not found ]
[08:25:13]   Checking for file '/usr/bin/sl2'                [ Not found ]
[08:25:13]   Checking for file '/usr/bin/logclear'           [ Not found ]
[08:25:13]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[08:25:13]   Checking for file '/usr/bin/snfs'               [ Not found ]
[08:25:13]   Checking for file '/usr/lib/libsss'             [ Not found ]
[08:25:13]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[08:25:13] Dreams Rootkit                                    [ Not found ]
[08:25:13]
[08:25:13] Checking for Duarawkz Rootkit...
[08:25:13]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[08:25:13]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[08:25:13] Duarawkz Rootkit                                  [ Not found ]
[08:25:13]
[08:25:13] Checking for Enye LKM...
[08:25:14]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[08:25:14] Enye LKM                                          [ Not found ]
[08:25:14]
[08:25:14] Checking for Flea Linux Rootkit...
[08:25:14]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[08:25:14]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[08:25:14]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[08:25:14]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[08:25:14]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[08:25:14]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[08:25:14]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[08:25:14]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[08:25:14]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[08:25:14]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[08:25:14]   Checking for directory '/dev/..0'               [ Not found ]
[08:25:14]   Checking for directory '/dev/..0/backup'        [ Not found ]
[08:25:14] Flea Linux Rootkit                                [ Not found ]
[08:25:14]
[08:25:14] Checking for FreeBSD Rootkit...
[08:25:14]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[08:25:14]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[08:25:14]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[08:25:14]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[08:25:14]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[08:25:14]   Checking for file '/bin/sysback'                [ Not found ]
[08:25:15]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[08:25:15]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[08:25:15]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[08:25:15] FreeBSD Rootkit                                   [ Not found ]
[08:25:15]
[08:25:15] Checking for ****`it Rootkit...
[08:25:15]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[08:25:15]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[08:25:15] ****`it Rootkit                                   [ Not found ]
[08:25:15]
[08:25:15] Checking for GasKit Rootkit...
[08:25:15]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[08:25:15]   Checking for directory '/dev/dev'               [ Not found ]
[08:25:15]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[08:25:15]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[08:25:15] GasKit Rootkit                                    [ Not found ]
[08:25:15]
[08:25:15] Checking for Heroin LKM...
[08:25:16]   Checking for kernel symbol 'heroin'             [ Not found ]
[08:25:16] Heroin LKM                                        [ Not found ]
[08:25:16]
[08:25:16] Checking for HjC Kit...
[08:25:16]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[08:25:16] HjC Kit                                           [ Not found ]
[08:25:16]
[08:25:16] Checking for ignoKit Rootkit...
[08:25:16]   Checking for file '/lib/defs/p'                 [ Not found ]
[08:25:16]   Checking for file '/lib/defs/q'                 [ Not found ]
[08:25:16]   Checking for file '/lib/defs/r'                 [ Not found ]
[08:25:16]   Checking for file '/lib/defs/s'                 [ Not found ]
[08:25:16]   Checking for file '/lib/defs/t'                 [ Not found ]
[08:25:16]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[08:25:16]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[08:25:16]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[08:25:16]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[08:25:16]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[08:25:16]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[08:25:16]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[08:25:16]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[08:25:16]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[08:25:16] ignoKit Rootkit                                   [ Not found ]
[08:25:16]
[08:25:16] Checking for ImperalsS-FBRK Rootkit...
[08:25:16]   Checking for directory '/dev/fd/.88'            [ Not found ]
[08:25:17]   Checking for directory '/dev/fd/.99'            [ Not found ]
[08:25:17] ImperalsS-FBRK Rootkit                            [ Not found ]
[08:25:17]
[08:25:17] Checking for IntoXonia-NG Rootkit...
[08:25:17]   Checking for kernel symbol 'funces'             [ Not found ]
[08:25:17]   Checking for kernel symbol 'ixinit'             [ Not found ]
[08:25:17]   Checking for kernel symbol 'tricks'             [ Not found ]
[08:25:17]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[08:25:17]   Checking for kernel symbol 'rootme'             [ Not found ]
[08:25:17]   Checking for kernel symbol 'hide_module'        [ Not found ]
[08:25:17]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[08:25:17] IntoXonia-NG Rootkit                              [ Not found ]
[08:25:18]
[08:25:18] Checking for Irix Rootkit...
[08:25:18]   Checking for directory '/dev/pts/01'            [ Not found ]
[08:25:18]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[08:25:18]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[08:25:18]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[08:25:18] Irix Rootkit                                      [ Not found ]
[08:25:18]
[08:25:18] Checking for Kitko Rootkit...
[08:25:18]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[08:25:18] Kitko Rootkit                                     [ Not found ]
[08:25:18]
[08:25:18] Checking for Knark Rootkit...
[08:25:18]   Checking for file '/proc/knark/pids'            [ Not found ]
[08:25:18]   Checking for directory '/proc/knark'            [ Not found ]
[08:25:18] Knark Rootkit                                     [ Not found ]
[08:25:18]
[08:25:18] Checking for Li0n Worm...
[08:25:18]   Checking for file '/bin/in.telnetd'             [ Not found ]
[08:25:18]   Checking for file '/bin/mjy'                    [ Not found ]
[08:25:18]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[08:25:18]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[08:25:18]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[08:25:18]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[08:25:18]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[08:25:18]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[08:25:18]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[08:25:18]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[08:25:19]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[08:25:19] Li0n Worm                                         [ Not found ]
[08:25:19]
[08:25:19] Checking for Lockit / LJK2 Rootkit...
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[08:25:19]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[08:25:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[08:25:21]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[08:25:21] Lockit / LJK2 Rootkit                             [ Not found ]
[08:25:21]
[08:25:21] Checking for Mood-NT Rootkit...
[08:25:21]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[08:25:21]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[08:25:21]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[08:25:21]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[08:25:21]   Checking for directory '/_cthulhu'              [ Not found ]
[08:25:21] Mood-NT Rootkit                                   [ Not found ]
[08:25:21]
[08:25:21] Checking for MRK Rootkit...
[08:25:21]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[08:25:21]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[08:25:21]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[08:25:21]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[08:25:21]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[08:25:21]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[08:25:21] MRK Rootkit                                       [ Not found ]
[08:25:21]
[08:25:21] Checking for Ni0 Rootkit...
[08:25:21]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[08:25:21]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[08:25:21]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[08:25:21]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[08:25:21]   Checking for directory '/tmp/waza'              [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[08:25:22]   Checking for directory '/usr/sbin/es'           [ Not found ]
[08:25:22] Ni0 Rootkit                                       [ Not found ]
[08:25:22]
[08:25:22] Checking for Ohhara Rootkit...
[08:25:22]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[08:25:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[08:25:22] Ohhara Rootkit                                    [ Not found ]
[08:25:22]
[08:25:22] Checking for Optic Kit (Tux) Worm...
[08:25:22]   Checking for directory '/dev/tux'               [ Not found ]
[08:25:22]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[08:25:22]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[08:25:22]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[08:25:22] Optic Kit (Tux) Worm                              [ Not found ]
[08:25:22]
[08:25:22] Checking for Oz Rootkit...
[08:25:22]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[08:25:22]   Checking for directory '/dev/.oz'               [ Not found ]
[08:25:22] Oz Rootkit                                        [ Not found ]
[08:25:23]
[08:25:23] Checking for Phalanx Rootkit...
[08:25:23]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[08:25:23]   Checking for file '/etc/host.ph1'               [ Not found ]
[08:25:23]   Checking for file '/bin/host.ph1'               [ Not found ]
[08:25:23]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[08:25:23]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[08:25:23] Phalanx Rootkit                                   [ Not found ]
[08:25:23]
[08:25:23] Checking for Phalanx Rootkit (strings)...
[08:25:23]   Checking for string 'phalanx'                   [ Not found ]
[08:25:23] Phalanx Rootkit (strings)                         [ Not found ]
[08:25:23]
[08:25:23] Checking for Phalanx2 Rootkit...
[08:25:23]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[08:25:23]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[08:25:23]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[08:25:23]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[08:25:23]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[08:25:23]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[08:25:23]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[08:25:23]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[08:25:23]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[08:25:23]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[08:25:23] Phalanx2 Rootkit                                  [ Not found ]
[08:25:23]
[08:25:23] Checking for Phalanx2 Rootkit (extended tests)...
[08:25:24]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[08:25:24]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[08:25:24] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[08:25:24]
[08:25:24] Checking for Portacelo Rootkit...
[08:25:24]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../.p'             [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../getty'          [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../show'           [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[08:25:24]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[08:25:24]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[08:25:24] Portacelo Rootkit                                 [ Not found ]
[08:25:24]
[08:25:24] Checking for R3dstorm Toolkit...
[08:25:24]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[08:25:24]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[08:25:24]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[08:25:24]   Checking for file '/bin/.../see_all'            [ Not found ]
[08:25:25]   Checking for directory '/var/log/tk02'          [ Not found ]
[08:25:25]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[08:25:25]   Checking for directory '/bin/...'               [ Not found ]
[08:25:25] R3dstorm Toolkit                                  [ Not found ]
[08:25:25]
[08:25:25] Checking for RH-Sharpe's Rootkit...
[08:25:25]   Checking for file '/bin/lps'                    [ Not found ]
[08:25:25]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[08:25:25]   Checking for file '/usr/bin/ltop'               [ Not found ]
[08:25:25]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[08:25:25]   Checking for file '/usr/bin/ldu'                [ Not found ]
[08:25:25]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[08:25:25]   Checking for file '/usr/bin/wp'                 [ Not found ]
[08:25:25]   Checking for file '/usr/bin/shad'               [ Not found ]
[08:25:25]   Checking for file '/usr/bin/vadim'              [ Not found ]
[08:25:25]   Checking for file '/usr/bin/slice'              [ Not found ]
[08:25:25]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[08:25:25]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[08:25:25] RH-Sharpe's Rootkit                               [ Not found ]
[08:25:25]
[08:25:25] Checking for RSHA's Rootkit...
[08:25:25]   Checking for file '/bin/kr4p'                   [ Not found ]
[08:25:25]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[08:25:25]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[08:25:25]   Checking for file '/usr/bin/slice2'             [ Not found ]
[08:25:26]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[08:25:26]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[08:25:26]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[08:25:26]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[08:25:26] RSHA's Rootkit                                    [ Not found ]
[08:25:26]
[08:25:26] Checking for Scalper Worm...
[08:25:26]   Checking for file '/tmp/.a'                     [ Not found ]
[08:25:26]   Checking for file '/tmp/.uua'                   [ Not found ]
[08:25:26] Scalper Worm                                      [ Not found ]
[08:25:26]
[08:25:26] Checking for Sebek LKM...
[08:25:26]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[08:25:26] Sebek LKM                                         [ Not found ]
[08:25:27]
[08:25:27] Checking for Shutdown Rootkit...
[08:25:27]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[08:25:27]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[08:25:27]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[08:25:27]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[08:25:27]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[08:25:27]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[08:25:27]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[08:25:27]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[08:25:27] Shutdown Rootkit                                  [ Not found ]
[08:25:27]
[08:25:27] Checking for SHV4 Rootkit...
[08:25:27]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[08:25:27]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[08:25:27]   Checking for file '/lib/lidps1.so'              [ Not found ]
[08:25:27]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[08:25:27]   Checking for directory '/lib/security/.config'  [ Not found ]
[08:25:27]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[08:25:27] SHV4 Rootkit                                      [ Not found ]
[08:25:27]
[08:25:27] Checking for SHV5 Rootkit...
[08:25:27]   Checking for file '/etc/sh.conf'                [ Not found ]
[08:25:27]   Checking for file '/dev/srd0'                   [ Not found ]
[08:25:27]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[08:25:27] SHV5 Rootkit                                      [ Not found ]
[08:25:28]
[08:25:28] Checking for Sin Rootkit...
[08:25:28]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[08:25:28]   Checking for file '/dev/ttyoa'                  [ Not found ]
[08:25:28]   Checking for file '/dev/ttyof'                  [ Not found ]
[08:25:28]   Checking for file '/dev/ttyop'                  [ Not found ]
[08:25:28]   Checking for file '/dev/ttyos'                  [ Not found ]
[08:25:28]   Checking for file '/usr/lib/.lib'               [ Not found ]
[08:25:28]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[08:25:28]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[08:25:28]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[08:25:28]   Checking for file '/usr/man/man1/...'           [ Not found ]
[08:25:28]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[08:25:28]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[08:25:28]   Checking for directory '/usr/lib/sn'            [ Not found ]
[08:25:28]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[08:25:28]   Checking for directory '/dev/.haos'             [ Not found ]
[08:25:28] Sin Rootkit                                       [ Not found ]
[08:25:28]
[08:25:28] Checking for Slapper Worm...
[08:25:28]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[08:25:28]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[08:25:28]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[08:25:28]   Checking for file '/tmp/httpd'                  [ Not found ]
[08:25:28]   Checking for file '/tmp/.unlock'                [ Not found ]
[08:25:29]   Checking for file '/tmp/update'                 [ Not found ]
[08:25:29]   Checking for file '/tmp/.cinik'                 [ Not found ]
[08:25:29]   Checking for file '/tmp/.b'                     [ Not found ]
[08:25:29] Slapper Worm                                      [ Not found ]
[08:25:29]
[08:25:29] Checking for Sneakin Rootkit...
[08:25:29]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[08:25:29] Sneakin Rootkit                                   [ Not found ]
[08:25:29]
[08:25:29] Checking for Suckit Rootkit...
[08:25:29]   Checking for file '/sbin/initsk12'              [ Not found ]
[08:25:29]   Checking for file '/sbin/initxrk'               [ Not found ]
[08:25:29]   Checking for file '/usr/bin/null'               [ Not found ]
[08:25:29]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[08:25:29]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[08:25:29]   Checking for directory '/etc/.MG'               [ Not found ]
[08:25:29]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[08:25:30]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[08:25:30] Suckit Rootkit                                    [ Not found ]
[08:25:30]
[08:25:30] Checking for SunOS Rootkit...
[08:25:30]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[08:25:30]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[08:25:30]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[08:25:30]   Checking for file '/bin/xlogin'                 [ Not found ]
[08:25:30]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[08:25:30]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[08:25:30]   Checking for file '/sbin/login'                 [ Not found ]
[08:25:30]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[08:25:30]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[08:25:30]   Checking for file '/dev/kmod'                   [ Not found ]
[08:25:30]   Checking for file '/dev/dos'                    [ Not found ]
[08:25:30] SunOS Rootkit                                     [ Not found ]
[08:25:30]
[08:25:30] Checking for SunOS / NSDAP Rootkit...
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[08:25:30]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[08:25:31]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[08:25:31]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[08:25:31]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[08:25:31]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[08:25:31]   Checking for file '/usr/lib/lpset'              [ Not found ]
[08:25:31]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[08:25:31] SunOS / NSDAP Rootkit                             [ Not found ]
[08:25:31]
[08:25:31] Checking for Superkit Rootkit...
[08:25:31]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[08:25:31] Superkit Rootkit                                  [ Not found ]
[08:25:31]
[08:25:31] Checking for TBD (Telnet BackDoor)...
[08:25:31]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[08:25:31] TBD (Telnet BackDoor)                             [ Not found ]
[08:25:31]
[08:25:31] Checking for TeLeKiT Rootkit...
[08:25:31]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[08:25:31]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[08:25:31]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[08:25:31]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[08:25:31]   Checking for file '/dev/ptyr'                   [ Not found ]
[08:25:31]   Checking for file '/dev/ptyp'                   [ Not found ]
[08:25:31]   Checking for file '/dev/ptyq'                   [ Not found ]
[08:25:31]   Checking for file '/dev/hda06'                  [ Not found ]
[08:25:31]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[08:25:32]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[08:25:32]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[08:25:32]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[08:25:32] TeLeKiT Rootkit                                   [ Not found ]
[08:25:32]
[08:25:32] Checking for T0rn Rootkit...
[08:25:32]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[08:25:32]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[08:25:33]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[08:25:33]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[08:25:33]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[08:25:33]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[08:25:33]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[08:25:33]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[08:25:33]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[08:25:33]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[08:25:33]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[08:25:33]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[08:25:33]   Checking for directory '/dev/.lib'              [ Not found ]
[08:25:33]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[08:25:33]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[08:25:33]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[08:25:33]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[08:25:33]   Checking for directory '/usr/src/.****'         [ Not found ]
[08:25:33]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[08:25:33]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[08:25:33]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[08:25:33]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[08:25:33] T0rn Rootkit                                      [ Not found ]
[08:25:33]
[08:25:33] Checking for Trojanit Kit...
[08:25:34]   Checking for file '/bin/.ls'                    [ Not found ]
[08:25:34]   Checking for file '/bin/.ps'                    [ Not found ]
[08:25:34]   Checking for file '/bin/.netstat'               [ Not found ]
[08:25:34]   Checking for file '/usr/bin/.nop'               [ Not found ]
[08:25:34]   Checking for file '/usr/bin/.who'               [ Not found ]
[08:25:34] Trojanit Kit                                      [ Not found ]
[08:25:34]
[08:25:34] Checking for Tuxtendo Rootkit...
[08:25:34]   Checking for file '/dev/tux/.addr'              [ Not found ]
[08:25:34]   Checking for file '/dev/tux/.cron'              [ Not found ]
[08:25:34]   Checking for file '/dev/tux/.file'              [ Not found ]
[08:25:34]   Checking for file '/dev/tux/.log'               [ Not found ]
[08:25:34]   Checking for file '/dev/tux/.proc'              [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[08:25:34]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[08:25:35]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[08:25:35]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[08:25:35]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[08:25:35]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[08:25:35]   Checking for directory '/dev/tux'               [ Not found ]
[08:25:35]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[08:25:35]   Checking for directory '/dev/tux/backup'        [ Not found ]
[08:25:35] Tuxtendo Rootkit                                  [ Not found ]
[08:25:35]
[08:25:35] Checking for URK Rootkit...
[08:25:35]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[08:25:35]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[08:25:35]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[08:25:35]   Checking for file '/tmp/conf.inf'               [ Not found ]
[08:25:35]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[08:25:35] URK Rootkit                                       [ Not found ]
[08:25:35]
[08:25:35] Checking for Vampire Rootkit...
[08:25:35]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[08:25:35]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[08:25:36]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[08:25:36]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[08:25:36] Vampire Rootkit                                   [ Not found ]
[08:25:36]
[08:25:36] Checking for VcKit Rootkit...
[08:25:36]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[08:25:36]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[08:25:36] VcKit Rootkit                                     [ Not found ]
[08:25:36]
[08:25:36] Checking for Volc Rootkit...
[08:25:36]   Checking for directory '/var/spool/.recent'     [ Not found ]
[08:25:36]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[08:25:36]   Checking for directory '/usr/lib/volc'          [ Not found ]
[08:25:36]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[08:25:36] Volc Rootkit                                      [ Not found ]
[08:25:36]
[08:25:36] Checking for X-Org SunOS Rootkit...
[08:25:36]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[08:25:36]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[08:25:36]   Checking for file '/usr/bin/srload'             [ Not found ]
[08:25:36]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[08:25:36]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[08:25:36]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[08:25:36]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[08:25:37]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[08:25:37]   Checking for directory '/usr/share/man...'      [ Not found ]
[08:25:37] X-Org SunOS Rootkit                               [ Not found ]
[08:25:37]
[08:25:37] Checking for zaRwT.KiT Rootkit...
[08:25:37]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[08:25:37]   Checking for file '/dev/ttyf'                   [ Not found ]
[08:25:37]   Checking for file '/dev/ttyp'                   [ Not found ]
[08:25:37]   Checking for file '/dev/ttyn'                   [ Not found ]
[08:25:37]   Checking for file '/rk/tulz'                    [ Not found ]
[08:25:37]   Checking for directory '/rk'                    [ Not found ]
[08:25:37]   Checking for directory '/dev/rd/s'              [ Not found ]
[08:25:37] zaRwT.KiT Rootkit                                 [ Not found ]
[08:25:37]
[08:25:37] Performing additional rootkit checks
[08:25:37] Info: Starting test name 'additional_rkts'
[08:25:37]
[08:25:37]   Performing Suckit Rookit additional checks
[08:25:37]     Checking hard link count on '/sbin/init'      [ OK ]
[08:25:37]     Checking for hidden file extensions           [ None found ]
[08:25:37]     Running skdet command                         [ Skipped ]
[08:25:37] Info: Unable to find the 'skdet' command
[08:25:37]   Suckit Rookit additional checks                 [ OK ]
[08:25:37]
[08:25:37]   Performing check of possible rootkit files and directories
[08:25:37] Info: Starting test name 'possible_rkt_files'
[08:25:37]     Checking for file '/dev/sdr0'                 [ Not found ]
[08:25:38]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[08:25:38]     Checking for file '/tmp/.bash_history'        [ Not found ]
[08:25:38]     Checking for file '/usr/info/.clib'           [ Not found ]
[08:25:38]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[08:25:38]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[08:25:38]     Checking for file '/sbin/create'              [ Not found ]
[08:25:38]     Checking for file '/dev/ttypz'                [ Not found ]
[08:25:38]     Checking for directory '/usr/bin/take'        [ Not found ]
[08:25:38]     Checking for directory '/usr/src/.lib'        [ Not found ]
[08:25:38]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[08:25:38]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[08:25:38]     Checking for directory '/usr/sbin/...'        [ Not found ]
[08:25:38]     Checking for directory '/usr/share/.gun'      [ Not found ]
[08:25:38]   Checking for possible rootkit files and directories [ None found ]
[08:25:38]
[08:25:38]   Performing check for possible rootkit strings
[08:25:38] Info: Starting test name 'possible_rkt_strings'
[08:25:38] Info: Using system startup paths: /etc/rc.local /etc/init.d
[08:25:38]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[08:25:39]     Checking for string '****'                    [ Not found ]
[08:25:39]     Checking for string 'backdoor'                [ Not found ]
[08:25:39]     Checking for string 'vt200'                   [ Not found ]
[08:25:39]     Checking for string '/usr/bin/xstat'          [ Not found ]
[08:25:39]     Checking for string '/bin/envpc'              [ Not found ]
[08:25:39]     Checking for string 'L4m3r0x'                 [ Not found ]
[08:25:39]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[08:25:39]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[08:25:39]     Checking for string '/dev/sgk'                [ Not found ]
[08:25:39]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[08:25:39]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[08:25:39]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[08:25:39]     Checking for string '/lib/.sso'               [ Not found ]
[08:25:39]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[08:25:40]     Checking for string '/dev/caca'               [ Not found ]
[08:25:40]     Checking for string '/dev/ttyoa'              [ Not found ]
[08:25:40]     Checking for string 'syg'                     [ Not found ]
[08:25:40]     Checking for string '/dev/pts/01'             [ Not found ]
[08:25:40]     Checking for string 'tw33dl3'                 [ Not found ]
[08:25:40]     Checking for string 'psniff'                  [ Not found ]
[08:25:40]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[08:25:40]     Checking for string '/dev/xdta'               [ Not found ]
[08:25:40]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[08:25:41]     Checking for string 'in.inetd'                [ Not found ]
[08:25:41]     Checking for string '#<HIDE_.*>'              [ Not found ]
[08:25:41]     Checking for string 'bin/xchk'                [ Not found ]
[08:25:42]     Checking for string 'bin/xsf'                 [ Not found ]
[08:25:42]   Checking for possible rootkit strings           [ None found ]
[08:25:42]
[08:25:42] Performing malware checks
[08:25:42] Info: Starting test name 'malware'
[08:25:42]
[08:25:42] Info: Test 'deleted_files' disabled at users request.
[08:25:42] Info: Starting test name 'running_procs'
[08:25:42]   Checking running processes for suspicious files [ None found ]
[08:25:42]
[08:25:42] Info: Test 'hidden_procs' disabled at users request.
[08:25:42]
[08:25:42] Info: Test 'suspscan' disabled at users request.
[08:25:42]
[08:25:42]   Performing check for login backdoors
[08:25:42] Info: Starting test name 'other_malware'
[08:25:42]     Checking for '/bin/.login'                    [ Not found ]
[08:25:42]     Checking for '/sbin/.login'                   [ Not found ]
[08:25:42]   Checking for login backdoors                    [ None found ]
[08:25:42]
[08:25:42]   Performing check for suspicious directories
[08:25:42]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[08:25:43]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[08:25:43]   Checking for suspicious directories             [ None found ]
[08:25:43]
[08:25:43]   Checking for software intrusions                [ Skipped ]
[08:25:43] Info: Check skipped - tripwire not installed
[08:25:43]
[08:25:43]   Performing check for sniffer log files
[08:25:43]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[08:25:43]   Checking for sniffer log files                  [ None found ]
[08:25:43]
[08:25:43] Performing trojan specific checks
[08:25:43] Info: Starting test name 'trojans'
[08:25:43] Info: Using inetd configuration file '/etc/inetd.conf'
[08:25:43]   Checking for enabled inetd services             [ OK ]
[08:25:43]
[08:25:43]   Performing check for enabled xinetd services
[08:25:43]   Checking for enabled xinetd services            [ Skipped ]
[08:25:43] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[08:25:43] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[08:25:43]
[08:25:43] Performing Linux specific checks
[08:25:43] Info: Starting test name 'os_specific'
[08:25:43]   Checking loaded kernel modules                  [ OK ]
[08:25:43] Info: Using modules pathname of '/lib/modules/2.6.31-17-generic'
[08:25:43]   Checking kernel module names                    [ OK ]
[08:25:43]
[08:25:43] Checking the network...
[08:25:43] Info: Starting test name 'network'
[08:25:43] Info: Starting test name 'ports'
[08:25:43]
[08:25:43] Performing check for backdoor ports
[08:25:44]   Checking for TCP port 1524                      [ Not found ]
[08:25:44]   Checking for TCP port 1984                      [ Not found ]
[08:25:44]   Checking for UDP port 2001                      [ Not found ]
[08:25:44]   Checking for TCP port 2006                      [ Not found ]
[08:25:44]   Checking for TCP port 2128                      [ Not found ]
[08:25:44]   Checking for TCP port 6666                      [ Not found ]
[08:25:44]   Checking for TCP port 6667                      [ Not found ]
[08:25:44]   Checking for TCP port 6668                      [ Not found ]
[08:25:45]   Checking for TCP port 6669                      [ Not found ]
[08:25:45]   Checking for TCP port 7000                      [ Not found ]
[08:25:45]   Checking for TCP port 13000                     [ Not found ]
[08:25:45]   Checking for TCP port 14856                     [ Not found ]
[08:25:45]   Checking for TCP port 25000                     [ Not found ]
[08:25:45]   Checking for TCP port 29812                     [ Not found ]
[08:25:45]   Checking for TCP port 31337                     [ Not found ]
[08:25:45]   Checking for TCP port 33369                     [ Not found ]
[08:25:46]   Checking for TCP port 47107                     [ Not found ]
[08:25:46]   Checking for TCP port 47018                     [ Not found ]
[08:25:46]   Checking for TCP port 60922                     [ Not found ]
[08:25:46]   Checking for TCP port 62883                     [ Not found ]
[08:25:46]   Checking for TCP port 65535                     [ Not found ]
[08:25:46]
[08:25:46] Performing checks on the network interfaces
[08:25:46] Info: Starting test name 'promisc'
[08:25:46]   Checking for promiscuous interfaces             [ None found ]
[08:25:46]
[08:25:46] Info: Test 'packet_cap_apps' disabled at users request.
[08:25:46]
[08:25:46] Checking the local host...
[08:25:46] Info: Starting test name 'local_host'
[08:25:46]
[08:25:46] Performing system boot checks
[08:25:46] Info: Starting test name 'startup_files'
[08:25:46]   Checking for local host name                    [ Found ]
[08:25:47] Info: Starting test name 'startup_malware'
[08:25:47]   Checking for system startup files               [ Found ]
[08:25:47]   Checking system startup files for malware       [ None found ]
[08:25:47]
[08:25:47] Performing group and account checks
[08:25:48] Info: Starting test name 'group_accounts'
[08:25:48]   Checking for passwd file                        [ Found ]
[08:25:48] Info: Found password file: /etc/passwd
[08:25:48]   Checking for root equivalent (UID 0) accounts   [ None found ]
[08:25:48] Info: Found shadow file: /etc/shadow
[08:25:48]   Checking for passwordless accounts              [ None found ]
[08:25:48] Info: Starting test name 'passwd_changes'
[08:25:48]   Checking for passwd file changes                [ None found ]
[08:25:48] Info: Starting test name 'group_changes'
[08:25:48]   Checking for group file changes                 [ None found ]
[08:25:48]   Checking root account shell history files       [ OK ]
[08:25:48]
[08:25:48] Performing system configuration file checks
[08:25:48] Info: Starting test name 'system_configs'
[08:25:48]   Checking for SSH configuration file             [ Not found ]
[08:25:48]   Checking for running syslog daemon              [ Found ]
[08:25:48]   Checking for syslog configuration file          [ Found ]
[08:25:48] Info: Found syslog configuration file: /etc/rsyslog.conf
[08:25:48]   Checking if syslog remote logging is allowed    [ Not allowed ]
[08:25:48]
[08:25:48] Performing filesystem checks
[08:25:48] Info: Starting test name 'filesystem'
[08:25:48] Info: SCAN_MODE_DEV set to 'THOROUGH'
[08:25:49]   Checking /dev for suspicious file types         [ Warning ]
[08:25:49] Warning: Suspicious file types found in /dev:
[08:25:49]          /dev/shm/pulse-shm-109180131: data
[08:25:49]          /dev/shm/pulse-shm-2142357409: data
[08:25:49]   Checking for hidden files and directories       [ Warning ]
[08:25:49] Warning: Hidden directory found: /etc/.java
[08:25:49] Warning: Hidden directory found: /dev/.udev
[08:25:49] Warning: Hidden directory found: /dev/.initramfs
[08:25:49]
[08:25:49] Checking application versions...
[08:25:49] Info: Starting test name 'apps'
[08:25:51]   Checking version of Exim MTA                    [ Warning ]
[08:25:51] Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.
[08:25:51]   Checking version of GnuPG                       [ Warning ]
[08:25:51] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
[08:25:51] Info: Application 'httpd' not found.
[08:25:51] Info: Application 'named' not found.
[08:25:51]   Checking version of OpenSSL                     [ Warning ]
[08:25:51] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
[08:25:51] Info: Application 'php' not found.
[08:25:51] Info: Application 'procmail' not found.
[08:25:51] Info: Application 'proftpd' not found.
[08:25:51] Info: Application 'sshd' not found.
[08:25:51] Info: Applications checked: 3 out of 9
[08:25:51]
[08:25:51] System checks summary
[08:25:51] =====================
[08:25:51]
[08:25:51] File properties checks...
[08:25:51] Files checked: 132
[08:25:51] Suspect files: 0
[08:25:51]
[08:25:51] Rootkit checks...
[08:25:51] Rootkits checked : 111
[08:25:51] Possible rootkits: 0
[08:25:52]
[08:25:52] Applications checks...
[08:25:52] Applications checked: 3
[08:25:52] Suspect applications: 3
[08:25:52]
[08:25:52] The system checks took: 1 minute and 13 seconds
[08:25:52]
[08:25:52] Info: End date is Sun Dec 13 08:25:52 CET 2009

```

---

### Post by KIAaze on 2009-12-13
In Xchat, setting 127.0.0.1 in "Settings->Preferences->File transfers" as DCC IP address and deactivating "Get my address from the IRC server" seems to work to spoof the IP.

However, downloads don't seem to work that way, which would make the spam pretty pointless.

---

### Post by KIAaze on 2009-12-15
Got spammed again.
Got a solution from "leaf-sheep" on the ubuntu channel:
```
/ignore *!*@* DCC
```

This will ignore DCC offers from all users.

Syntax:
```
/IGNORE <mask> <types..> <options..>
mask = nick!userid@host.com

```

Here's more info:
[http://t0x.in/xchatignore.html](http://t0x.in/xchatignore.html) (Can also be done through "Window->Ignore list" in Xchat.)

If you suffer from disconnect/reconnect problems (DCC exploit), try this:
[https://help.ubuntu.com/community/FixDCCExploit](https://help.ubuntu.com/community/FixDCCExploit)
(found it while trying to block the DCC spam)

---

