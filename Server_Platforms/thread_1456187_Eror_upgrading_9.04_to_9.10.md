---
title: "Eror upgrading 9.04 to 9.10"
date: 2010-04-16
forum: Server Platforms
---

### Post by orudie on 2010-04-16
Greetings. I need immediate assistance on the upgrade process off ubuntu server from version 9.04 to 9.10 . 


here is my output after running do-release-upgrade 

Note:* I first ran the release upgrade from 8.10 to 9.04, which ran really smoothely without errors and at the end pormpted a reboot. I have rebooted and decided to upgrade further - 9.04 to 9.10. And here is the result :( 

I saw this long into the upgrade process, somewhere 1.5 hours into the upgrade:
[http://www.pastebin.org/154139](http://www.pastebin.org/154139)

---

### Post by orudie on 2010-04-17
This is a Linode VPS. Here is what I see in Lish console after upgrade

NET: Registered protocol family 10                                                                  
lo: Disabled Privacy Extensions                                                                     
IPv6 over IPv4 tunneling driver                                                                     
ip6_tables: (C) 2000-2006 Netfilter Core Team                                                       
NET: Registered protocol family 17                                                                  
NET: Registered protocol family 15                                                                  
Bridge firewalling registered                                                                       
Ebtables v2.0 registered                                                                            
ebt_ulog: not logging via ulog since somebody else already registered for PF_BRIDGE                 
802.1Q VLAN Support v1.8 Ben Greear <greearb@candelatech.com>                                       
All bugs added by David S. Miller <davem@redhat.com>                                                
SCTP: Hash tables configured (established 65536 bind 65536)                                         
Using IPI Shortcut mode                                                                             
XENBUS: Device with no driver: device/console/0                                                     
md: Autodetecting RAID arrays.                                                                      
md: autorun ...                                                                                     
md: ... autorun DONE.                                                                               
kjournald starting.  Commit interval 5 seconds                                                      
EXT3-fs: mounted filesystem with ordered data mode.                                                 
VFS: Mounted root (ext3 filesystem) readonly.                                                       
Freeing unused kernel memory: 224k freed                                                            
init: hwclock main process (776) terminated with status 77                                          
init: ureadahead main process (777) terminated with status 5                                        
mountall:/proc: unable to mount: Device or resource busy                                            
mountall:/proc/self/mountinfo: No such file or directory                                            
mountall: root filesystem isn't mounted                                                             
init: mountall main process (780) terminated with status 1                                          
General error mounting filesystems.                                                                 
A maintenance shell will now be started.                                                            
CONTROL-D will terminate this shell and re-try.                                                     
Give root password for maintenance                                                                  
(or type Control-D to continue):     



--- I can login and see the file system if I provide root password.

---

