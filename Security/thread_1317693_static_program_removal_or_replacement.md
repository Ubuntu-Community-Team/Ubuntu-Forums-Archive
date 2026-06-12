---
title: "static program removal or replacement?"
date: 2009-11-06
forum: Security
---

### Post by logikz on 2009-11-06
static linked program removal..  How??

```
  PID TTY          TIME CMD                                                              
    1 ?        00:00:00 init                                                             
    2 ?        00:00:00 kthreadd                                                         
    3 ?        00:00:00 migration/0                                                      
    4 ?        00:00:05 ksoftirqd/0                                                      
    5 ?        00:00:00 **watchdog/0**                                                       
    6 ?        00:00:00 migration/1                                                      
    7 ?        00:00:05 ksoftirqd/1                                                      
    8 ?        00:00:00 **watchdog/1 **                                                      
    9 ?        00:00:00 migration/2                                                      
   10 ?        00:00:05 ksoftirqd/2                                                      
   11 ?        00:00:00 watchdog/2                                                       
   12 ?        00:00:00 migration/3                                                      
   13 ?        00:00:11 ksoftirqd/3                                                      
   14 ?        00:00:00 **watchdog/3 **                                                      
   15 ?        00:00:00 events/0                                                         
   16 ?        00:00:01 events/1                                                         
   17 ?        00:00:01 events/2                                                         
   18 ?        00:00:04 events/3                                                         
   19 ?        00:00:00 cpuset                                                           
   20 ?        00:00:00 khelper                                                          
   21 ?        00:00:00 netns                                                            
   22 ?        00:00:00 async/mgr                                                        
   23 ?        00:00:00 kintegrityd/0                                                    
   24 ?        00:00:00 kintegrityd/1                                                    
   25 ?        00:00:00 kintegrityd/2                                                    
   26 ?        00:00:00 kintegrityd/3                                                    
   27 ?        00:00:00 kblockd/0                                                        
   28 ?        00:00:00 kblockd/1                                                        
   29 ?        00:00:00 kblockd/2                                                        
   30 ?        00:00:00 kblockd/3                                                        
   31 ?        00:00:00 kacpid                                                           
   32 ?        00:00:00 **kacpi_notify**                                                     
   33 ?        00:00:00 **kacpi_hotplug**                                                    
   34 ?        00:00:00 ata/0                                                            
   35 ?        00:00:00 ata/1                                                            
   36 ?        00:00:00 ata/2                                                            
   37 ?        00:00:06 ata/3                                                            
   38 ?        00:00:00 ata_aux                                                          
   39 ?        00:00:00 **ksuspend_usbd **                                                   
   40 ?        00:00:00 khubd                                                            
   41 ?        00:00:00 **kseriod**                                                          
   42 ?        00:00:00 kmmcd                                                            
   43 ?        00:00:00 **bluetooth **                                                       
   44 ?        00:00:00 khungtaskd                                                       
   45 ?        00:00:00 pdflush                                                          
   46 ?        00:00:00 pdflush                                                          
   47 ?        00:00:00 **kswapd0**                                                          
   48 ?        00:00:00 aio/0                                                            
   49 ?        00:00:00 aio/1                                                            
   50 ?        00:00:00 aio/2                                                            
   51 ?        00:00:00 aio/3                                                            
   52 ?        00:00:00 ecryptfs-kthrea                                                  
   53 ?        00:00:00 crypto/0                                                         
   54 ?        00:00:00 crypto/1                                                         
   55 ?        00:00:00 crypto/2                                                         
   56 ?        00:00:00 crypto/3                                                         
   63 ?        00:00:00 scsi_eh_0                                                        
   64 ?        00:00:00 scsi_eh_1                                                        
   65 ?        00:00:00 scsi_eh_2                                                        
   66 ?        00:00:00 scsi_eh_3                                                        
   71 ?        00:00:12 scsi_eh_4                                                        
   72 ?        00:00:00 scsi_eh_5                                                        
   82 ?        00:00:00 **kstriped**                                                         
   83 ?        00:00:00 kmpathd/0                                                        
   84 ?        00:00:00 kmpathd/1                                                        
   85 ?        00:00:00 kmpathd/2                                                        
   86 ?        00:00:00 kmpathd/3                                                        
   87 ?        00:00:00 kmpath_handlerd                                                  
   88 ?        00:00:00 **ksnapd **                                                          
   89 ?        00:00:00 kondemand/0                                                      
   90 ?        00:00:00 kondemand/1                                                      
   91 ?        00:00:00 kondemand/2                                                      
   92 ?        00:00:00 kondemand/3                                                      
   93 ?        00:00:00 kconservative/0                                                  
   94 ?        00:00:00 kconservative/1                                                  
   95 ?        00:00:00 kconservative/2                                                  
   96 ?        00:00:00 kconservative/3                                                  
   97 ?        00:00:00 **krfcommd**                                                         
  259 ?        00:00:00 usbhid_resumer                                                   
  415 ?        00:00:01 kjournald2                                                       
  472 ?        00:00:00 upstart-udev-br                                                  
  704 ?        00:00:00 edac-poller                                                      
  943 ?        00:00:00 hd-audio0                                                        
 1039 ?        00:00:00 kjournald2                                                       
 1059 ?        00:00:00 dd                                                               
 1141 ?        00:00:05 dbus-daemon                                                      
 1178 ?        00:00:00 kdm                                                              
 1237 tty4     00:00:00 getty                                                            
 1242 tty5     00:00:00 getty                                                            
 1249 tty3     00:00:00 getty                                                            
 1251 tty6     00:00:00 getty                                                            
 1271 ?        00:00:00 cron                                                             
 1283 ?        00:00:00 atd                                                              
 1290 ?        00:00:00 console-kit-dae                                                  
 1384 ?        00:00:00 dhclient3                                                        
 1391 ?        00:00:00 cupsd                                                            
 1438 ?        00:00:00 wpa_supplicant                                                   
 1993 ?        00:00:00 polkitd                                                          
 2583 pts/2    00:00:00 ps                                                               
 3140 ?        00:00:01 devkit-disks-da                                                  
 3141 ?        00:00:08 devkit-disks-da                                                  
 5375 tty1     00:00:00 login                                                            
 5407 tty2     00:00:00 getty                                                            
 5486 tty1     00:00:00 bash                                                             
 7064 ?        00:00:02 wicd                                                             
 7074 ?        00:00:01 wicd-monitor                                                     
 7148 ?        00:00:00 dhclient <defunct>                                               
 7170 ?        00:00:00 dhclient                                                         
15087 tty1     00:00:00 startx                                                           
15104 tty1     00:00:00 xinit                                                            
15105 tty7     00:04:14 Xorg                                                             
15125 tty1     00:00:00 x-session-manag                                                  
15150 ?        00:00:00 ssh-agent                                                        
15151 ?        00:00:00 gpg-agent                                                        
15154 tty1     00:00:00 dbus-launch                                                      
15155 ?        00:00:02 dbus-daemon                                                      
15193 ?        00:00:00 kdeinit4                                                         
15194 ?        00:00:00 klauncher                                                        
15196 ?        00:00:01 kded4                                                            
15201 ?        00:00:00 kglobalaccel                                                     
15205 ?        00:00:01 knotify4                                                         
15206 tty1     00:00:00 kwrapper4                                                        
15207 ?        00:00:00 ksmserver                                                        
15209 ?        00:02:30 kwin                                                             
15223 ?        00:00:35 plasma-desktop                                                   
15234 ?        00:00:00 kaccess                                                          
15242 ?        00:00:00 nepomukserver                                                    
15245 ?        00:00:01 krunner                                                          
15251 ?        00:00:00 kmix                                                             
15252 ?        00:01:36 firefox                                                          
15260 ?        00:00:00 gconfd-2                                                         
15275 ?        00:00:02 konsole                                                          
15277 ?        00:00:01 kopete                                                           
15281 pts/1    00:00:00 bash                                                             
15288 pts/2    00:00:00 bash                                                             
15318 ?        00:00:00 kio_file                                                         
15320 ?        00:00:00 kwalletd                                                         
15326 ?        00:00:00 kate                                                             
15330 ?        00:00:00 polkit-gnome-au                                                  
15332 ?        00:00:00 python                                                           
15333 ?        00:00:00 wicd-client                                                      
15394 pts/1    00:00:00 bash                                                             
15414 pts/1    00:08:32 gnome-system-mo                                                  
15418 pts/1    00:00:00 dbus-launch                                                      
15419 ?        00:00:00 dbus-daemon                                                      
15421 ?        00:00:00 gconfd-2                                                         
19771 pts/2    00:00:00 bash                                                             
19870 ?        00:00:00 system-tools-ba                                                  
19872 ?        00:00:00 SystemToolsBack                                                  
21275 ?        00:00:00 rsyslogd                                                         
21313 ?        00:00:00 udevd                                                            
26762 ?        00:00:03 systemsettings                                                   
26863 ?        00:00:00 kdesu                                                            
26868 ?        00:00:00 sh                                                               
26871 ?        00:02:53 synaptic                                                         
27814 ?        00:00:00 master                                                           
27818 ?        00:00:00 pickup                                                           
27819 ?        00:00:00 qmgr                                                             
root@skittzl:~/Downloads/tzdata-2009o# ps -e                                             
  PID TTY          TIME CMD                                                              
    1 ?        00:00:00 init                                                             
    2 ?        00:00:00 kthreadd                                                         
    3 ?        00:00:00 migration/0                                                      
    4 ?        00:00:05 ksoftirqd/0                                                      
    5 ?        00:00:00 watchdog/0                                                       
    6 ?        00:00:00 migration/1                                                      
    7 ?        00:00:05 ksoftirqd/1                                                      
    8 ?        00:00:00 watchdog/1                                                       
    9 ?        00:00:00 migration/2                                                      
   10 ?        00:00:05 ksoftirqd/2                                                      
   11 ?        00:00:00 watchdog/2                                                       
   12 ?        00:00:00 migration/3                                                      
   13 ?        00:00:11 ksoftirqd/3                                                      
   14 ?        00:00:00 watchdog/3                                                       
   15 ?        00:00:00 events/0                                                         
   16 ?        00:00:01 events/1                                                         
   17 ?        00:00:01 events/2                                                         
   18 ?        00:00:04 events/3                                                         
   19 ?        00:00:00 cpuset                                                           
   20 ?        00:00:00 khelper                                                          
   21 ?        00:00:00 netns                                                            
   22 ?        00:00:00 async/mgr                                                        
   23 ?        00:00:00 kintegrityd/0                                                    
   24 ?        00:00:00 kintegrityd/1                                                    
   25 ?        00:00:00 kintegrityd/2                                                    
   26 ?        00:00:00 kintegrityd/3                                                    
   27 ?        00:00:00 kblockd/0                                                        
   28 ?        00:00:00 kblockd/1                                                        
   29 ?        00:00:00 kblockd/2                                                        
   30 ?        00:00:00 kblockd/3                                                        
   31 ?        00:00:00 kacpid                                                           
   32 ?        00:00:00 kacpi_notify                                                     
   33 ?        00:00:00 kacpi_hotplug                                                    
   34 ?        00:00:00 ata/0                                                            
   35 ?        00:00:00 ata/1                                                            
   36 ?        00:00:00 ata/2                                                            
   37 ?        00:00:06 ata/3                                                            
   38 ?        00:00:00 ata_aux                                                          
   39 ?        00:00:00 ksuspend_usbd                                                    
   40 ?        00:00:00 khubd                                                            
   41 ?        00:00:00 kseriod                                                          
   42 ?        00:00:00 kmmcd                                                            
   43 ?        00:00:00 bluetooth                                                        
   44 ?        00:00:00 khungtaskd                                                       
   45 ?        00:00:00 pdflush                                                          
   46 ?        00:00:00 pdflush                                                          
   47 ?        00:00:00 kswapd0                                                          
   48 ?        00:00:00 aio/0                                                            
   49 ?        00:00:00 aio/1                                                            
   50 ?        00:00:00 aio/2                                                            
   51 ?        00:00:00 aio/3                                                            
   52 ?        00:00:00 ecryptfs-kthrea                                                  
   53 ?        00:00:00 crypto/0                                                         
   54 ?        00:00:00 crypto/1                                                         
   55 ?        00:00:00 crypto/2                                                         
   56 ?        00:00:00 crypto/3                                                         
   63 ?        00:00:00 scsi_eh_0                                                        
   64 ?        00:00:00 scsi_eh_1                                                        
   65 ?        00:00:00 scsi_eh_2                                                        
   66 ?        00:00:00 scsi_eh_3                                                        
   71 ?        00:00:12 scsi_eh_4                                                        
   72 ?        00:00:00 scsi_eh_5                                                        
   82 ?        00:00:00 kstriped                                                         
   83 ?        00:00:00 kmpathd/0                                                        
   84 ?        00:00:00 kmpathd/1                                                        
   85 ?        00:00:00 kmpathd/2                                                        
   86 ?        00:00:00 kmpathd/3                                                        
   87 ?        00:00:00 kmpath_handlerd                                                  
   88 ?        00:00:00 ksnapd                                                           
   89 ?        00:00:00 kondemand/0                                                      
   90 ?        00:00:00 kondemand/1                                                      
   91 ?        00:00:00 kondemand/2                                                      
   92 ?        00:00:00 kondemand/3                                                      
   93 ?        00:00:00 kconservative/0                                                  
   94 ?        00:00:00 kconservative/1                                                  
   95 ?        00:00:00 kconservative/2                                                  
   96 ?        00:00:00 kconservative/3                                                  
   97 ?        00:00:00 krfcommd                                                         
  259 ?        00:00:00 usbhid_resumer                                                   
  415 ?        00:00:01 kjournald2                                                       
  472 ?        00:00:00 upstart-udev-br                                                  
  704 ?        00:00:00 edac-poller                                                      
  943 ?        00:00:00 hd-audio0                                                        
 1039 ?        00:00:00 kjournald2                                                       
 1059 ?        00:00:00 dd                                                               
 1141 ?        00:00:05 dbus-daemon                                                      
 1178 ?        00:00:00 kdm                                                              
 1237 tty4     00:00:00 getty                                                            
 1242 tty5     00:00:00 getty                                                            
 1249 tty3     00:00:00 getty                                                            
 1251 tty6     00:00:00 getty                                                            
 1271 ?        00:00:00 cron                                                             
 1283 ?        00:00:00 atd                                                              
 1290 ?        00:00:00 console-kit-dae                                                  
 1384 ?        00:00:00 dhclient3                                                        
 1391 ?        00:00:00 cupsd                                                            
 1438 ?        00:00:00 wpa_supplicant                                                   
 1993 ?        00:00:00 polkitd                                                          
 2639 pts/2    00:00:00 ps                                                               
 3140 ?        00:00:01 devkit-disks-da                                                  
 3141 ?        00:00:08 devkit-disks-da                                                  
 5375 tty1     00:00:00 login                                                            
 5407 tty2     00:00:00 getty                                                            
 5486 tty1     00:00:00 bash                                                             
 7064 ?        00:00:02 wicd                                                             
 7074 ?        00:00:01 wicd-monitor                                                     
 7148 ?        00:00:00 dhclient <defunct>                                               
 7170 ?        00:00:00 dhclient                                                         
15087 tty1     00:00:00 startx                                                           
15104 tty1     00:00:00 xinit                                                            
15105 tty7     00:04:23 Xorg                                                             
15125 tty1     00:00:00 x-session-manag                                                  
15150 ?        00:00:00 ssh-agent                                                        
15151 ?        00:00:00 gpg-agent                                                        
15154 tty1     00:00:00 dbus-launch                                                      
15155 ?        00:00:02 dbus-daemon                                                      
15193 ?        00:00:00 kdeinit4                                                         
15194 ?        00:00:00 klauncher                                                        
15196 ?        00:00:01 kded4                                                            
15201 ?        00:00:00 kglobalaccel                                                     
15205 ?        00:00:01 knotify4                                                         
15206 tty1     00:00:00 kwrapper4                                                        
15207 ?        00:00:00 ksmserver                                                        
15209 ?        00:02:34 kwin                                                             
15223 ?        00:00:35 plasma-desktop                                                   
15234 ?        00:00:00 kaccess                                                          
15242 ?        00:00:00 nepomukserver                                                    
15245 ?        00:00:01 krunner                                                          
15251 ?        00:00:00 kmix                                                             
15252 ?        00:01:45 firefox                                                          
15260 ?        00:00:00 gconfd-2
15275 ?        00:00:03 konsole
15277 ?        00:00:01 kopete
15281 pts/1    00:00:00 bash
15288 pts/2    00:00:00 bash
15318 ?        00:00:00 kio_file
15320 ?        00:00:00 kwalletd
15326 ?        00:00:00 kate
15330 ?        00:00:00 polkit-gnome-au
15332 ?        00:00:00 python
15333 ?        00:00:00 wicd-client
15394 pts/1    00:00:00 bash
15414 pts/1    00:08:49 gnome-system-mo
15418 pts/1    00:00:00 dbus-launch
15419 ?        00:00:00 dbus-daemon
15421 ?        00:00:00 gconfd-2
19771 pts/2    00:00:00 bash
19870 ?        00:00:00 system-tools-ba
19872 ?        00:00:00 SystemToolsBack
21275 ?        00:00:00 rsyslogd
21313 ?        00:00:00 udevd
26762 ?        00:00:03 systemsettings
26863 ?        00:00:00 kdesu
26868 ?        00:00:00 sh
26871 ?        00:02:53 synaptic
27814 ?        00:00:00 master
27818 ?        00:00:00 pickup
27819 ?        00:00:00 qmgr
root@skittzl:~/Downloads/tzdata-2009o#

```

I have bolded the statements im worried about.  I installed / uninstalled watchdog when i seen it there.  No effect on its being constantly going in 4 threads.  Compltely disabled bluetooth, doesnt stop that from starting, even on a minimal command line only system.  Any ideas?  

any boot params on a reinstall that would help?  Or possibly a different distro other than ubuntu?

also is this normal...  

frizzle@skittzl:/sbin$ w
 22:46:35 up 1 min,  2 users,  load average: 0.98, 0.32, 0.11
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
frizzle  :0       -                22:45   ?xdm?  15.55s  0.03s /bin/sh /usr/bin/x-sessio
frizzle  pts/0    :0               22:46   31.00s  0.00s  0.02s /usr/bin/kwrited
[B]
now killing kwrited, (kwrite is uninstalled)[/B]

frizzle@skittzl:/sbin$ w
 22:46:46 up 1 min,  2 users,  load average: 0.76, 0.30, 0.11
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
frizzle  :0       -                22:45   ?xdm?  16.85s  0.03s /bin/sh /usr/bin/x-sessio
frizzle@skittzl:/sbin$

---

### Post by cariboo on 2009-11-06
Do you know what watchdog actually does?

> 
A software watchdog

The watchdog program writes to /dev/watchdog every ten seconds. If the device is opened but not written to within a minute, the machine will reboot. This feature is available when the kernel is built with 'software watchdog' support (standard in Debian kernels).

The ability to reboot will depend on the state of the machine and interrupts. 

More on watchdog [here]("http://www.mjmwired.net/kernel/Documentation/watchdog/watchdog-api.txt").

---

### Post by logikz on 2009-11-07
why is there 4 instances of it?

---

