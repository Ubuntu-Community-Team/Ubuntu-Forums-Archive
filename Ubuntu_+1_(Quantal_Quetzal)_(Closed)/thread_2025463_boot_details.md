---
title: "boot details"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lucazade on 2012-07-14
something new under the hood (upstart?) or just some glitches?

```
$ more /var/log/boot.log 
fsck da util-linux 2.20.1
/dev/sda1: clean, 118280/450560 files, 815660/1801984 blocks
 * Stopping Flush boot log to disk                                       [ OK ]
 * Starting Uncomplicated firewall                                       [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Stopping load fallback graphics devices                               [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting Mount network filesystems                                    [ OK ]
 * Starting Failsafe Boot Delay                                          [ OK ]
 * Stopping Mount network filesystems                                    [ OK ]
 * Starting Bridge socket events into upstart                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Stopping Failsafe Boot Delay                                          [ OK ]
 * Starting System V initialisation compatibility                        [ OK ]
 * Starting modem connection manager                                     [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting network connection manager                                   [ OK ]
 * Starting CUPS printing spooler/server                                 [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                            [ OK ]                                                                                                                                                                                              
 * Stopping System V initialisation compatibility                        [ OK ]                                                                                                                                                                                                
 * Starting System V runlevel compatibility                              [ OK ]                                                                                                                                                                                                
 *** Starting                                                              [ OK ]   **                                                                                                                                                                                             
 * Starting automatic crash report generation                            [ OK ]                                                                                                                                                                                                
 * Starting CPU interrupts balancing daemon                              [ OK ]                                                                                                                                                                                                
 *** Starting                                                              [ OK ]           **                                                                                                                                                                                     
 * Starting deferred execution scheduler                                 [ OK ]                                                                                                                                                                                                
 * Starting regular background program processing daemon                 [ OK ]                                                                                                                                                                                                
 * Starting LightDM Display Manager                                      [ OK ]                                                                                                                                                                                                
 * Starting ACPI daemon                                                  [ OK ]                                                                                                                                                                                                
 * Starting anac(h)ronistic cron                                         [ OK ]
[B] * Starting                                                              [ OK ]
 * Starting                                                              [ OK ][/B]
 * Starting save kernel messages                                         [ OK ]
[B] * Starting                                                              [ OK ]
 * Starting                                                              [ OK ][/B]
 * Stopping System PulseAudio sound server                               [ OK ]
 * Starting VirtualBox Additions                                         [ OK ] 
saned disabled; edit /etc/default/saned
 * Stopping save kernel messages                                         [ OK ]

```

there are some empty service lines, just an odd "Starting  [OK]"
maybe some ghost services ? :)

---

