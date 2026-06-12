---
title: "[Pop_OS] Boot takes 90 seconds longer than it should"
date: 2021-04-06
forum: Ubuntu/Debian BASED
---

### Post by buckeyeback101 on 2021-04-06
I just finished fixing my bootloader after migrating my install over to a new ssd and hard drive (I had mistakenly tried to install GRUB). Everything seems to be working now, but my boot is taking over a minute and a half, and I can't figure out why. Here're the outputs of some commands:

```
systemd-analyze time

    Startup finished in 17.576s (firmware) + 481ms (loader) + 4.865s (kernel) + 1min 33.629s (userspace) = 1min 56.552s 
    graphical.target reached after 1min 33.614s in userspace
```

```
systemd-analyze blame

    3.006s plymouth-quit-wait.service                                               
    1.823s NetworkManager-wait-online.service                                       
     456ms accounts-daemon.service                                                  
     442ms systemd-logind.service                                                   
     346ms system76-power.service                                                   
     324ms networkd-dispatcher.service                                              
     297ms fwupd.service                                                            
     275ms udisks2.service                                                          
     260ms vmware-USBArbitrator.service                                             
     256ms dev-sdb2.device                                                          
     240ms home.mount                                                               
     175ms polkit.service                                                           
     171ms avahi-daemon.service                                                     
     170ms bluetooth.service                                                        
     166ms NetworkManager.service                                                   
     151ms switcheroo-control.service                                               
     148ms thermald.service                                                         
     145ms wpa_supplicant.service                                                   
     125ms gdm.service                                                              
     123ms gpu-manager.service                                                      
     115ms lvm2-monitor.service                                                     
     112ms ModemManager.service                                                     
     105ms user@1000.service                                                        
     101ms apparmor.service                                                         
      98ms upower.service                                                           
      93ms systemd-udevd.service                                                    
      81ms systemd-journal-flush.service                                            
      80ms rsyslog.service                                                          
      74ms systemd-resolved.service                                                 
      68ms dev-disk-by\x2duuid-8336a597\x2de014\x2d47aa\x2d980b\x2dd7ead594b5ee.swap
      64ms systemd-timesyncd.service                                                
      64ms systemd-udev-trigger.service                                             
      61ms colord.service                                                           
      57ms systemd-journald.service                                                 
      57ms apport.service                                                           
      53ms binfmt-support.service                                                   
      47ms proc-sys-fs-binfmt_misc.mount                                            
      44ms keyboard-setup.service                                                   
      40ms e2scrub_reap.service                                                     
      36ms vmware.service                                                           
      29ms networking.service                                                       
      26ms systemd-modules-load.service                                             
      26ms geoclue.service                                                          
      22ms packagekit.service                                                       
      21ms systemd-tmpfiles-setup.service                                           
      20ms boot-efi.mount                                                           
      16ms plymouth-start.service                                                   
      15ms grub-common.service                                                      
      14ms systemd-remount-fs.service                                               
      13ms setvtrgb.service                                                         
      13ms systemd-sysusers.service                                                 
      12ms resolvconf-pull-resolved.service                                         
      11ms plymouth-read-write.service
```

That output repeats one and a half times, for some reason. And, lastly:

```
systemd-analyze critical-chain

    The time when unit became active or started is printed after the "@" character.
    The time the unit took to start is printed after the "+" character.
    
    graphical.target @1min 33.614s
    &#9492;&#9472;multi-user.target @1min 33.614s
      &#9492;&#9472;plymouth-quit-wait.service @1min 30.607s +3.006s
        &#9492;&#9472;systemd-user-sessions.service @1min 30.601s +4ms
          &#9492;&#9472;network.target @1min 30.599s
            &#9492;&#9472;NetworkManager.service @1min 30.433s +166ms
              &#9492;&#9472;dbus.service @1min 30.430s
                &#9492;&#9472;basic.target @1min 30.422s
                  &#9492;&#9472;sockets.target @1min 30.422s
                    &#9492;&#9472;uuidd.socket @1min 30.422s
                      &#9492;&#9472;sysinit.target @1min 30.419s
                        &#9492;&#9472;apparmor.service @892ms +101ms
                          &#9492;&#9472;local-fs.target @892ms
                            &#9492;&#9472;home.mount @651ms +240ms
                              &#9492;&#9472;dev-sda1.device @651ms
```

From my primitive understanding of the *critical-chain* output, the system appears to be doing nothing for 90 seconds between *apparmor.service* and *sysinit.target*. Does anyone have an idea of what could be going on here? Any help would be appreciated. Thanks!

---

### Post by oldfred on 2021-04-06
Some things to review. Not sure if same as Ubuntu.

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) 

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by buckeyeback101 on 2021-04-06
Found the problem. Pressing ESC I was able to switch from Plymouth to the verbose boot. There I saw the message:

    *A start job is running for /dev/disk/by-uuid/...*

It turns out */etc/crypttab* still had an entry for my old hard drive. Which is strange, because that drive wasn't encrypted. Anyways, I commented out the line and now the machine boots in about 20 seconds.

Thanks!

---

