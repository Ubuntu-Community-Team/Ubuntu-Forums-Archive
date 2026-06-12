---
title: "Ubuntu Server 10.10 (x86) + LVM +"
date: 2010-12-10
forum: Server Platforms
---

### Post by i_am_lost on 2010-12-10
#OS: Ubuntu Server 10.10 (x86) 
I have tried to setup two nodes based on the example here: 
[[COLOR=Magenta]https://help.ubuntu.com/community/HighlyAvailableLAMP  [/COLOR]]("https://help.ubuntu.com/community/HighlyAvailableLAMP")

There are several problems that arise, but despite several tours on Google it is unclear if any solution exists.  Some suggest turning off fencing (I don't know how to do this properly yet)  
any input would be a great help, =)  


#the OS/swap is not on the LVM.
#and the two platforms have only about 3.8TB in a single group
#The 5 physical volumes in th Linux LVM group log volume were formatted ext4
/dev/lvmgrp/lvmvol 
  
#The only real difference is I am not using the bond0 adapter for several reasons.



#-----------------------------------------------------------------
#Created config file /etc/drbd.d/coconut.res

resource coconut {
        protocol C;
 
        handlers {
        pri-on-incon-degr "echo o > /proc/sysrq-trigger ; halt -f";
        pri-lost-after-sb "echo o > /proc/sysrq-trigger ; halt -f";
        local-io-error "echo o > /proc/sysrq-trigger ; halt -f";
        outdate-peer "/usr/lib/heartbeat/drbd-peer-outdater -t 5";      
        }

        startup {
        degr-wfc-timeout 120;
    become-primary-on redfish;
        }

        disk {
        on-io-error detach;
        }

        net {
        cram-hmac-alg sha1;
        shared-secret "password";
        after-sb-0pri disconnect;
        after-sb-1pri disconnect;
        after-sb-2pri disconnect;
        rr-conflict disconnect;
        }

        syncer {
        rate 10M;
        verify-alg sha1;
        al-extents 257;
        }


        on redfish {
        device  /dev/drbd0;
        disk    /dev/lvmgrp/lvmvol;
        address 10.10.10.250:7788;    
        meta-disk internal;
        }

        on bluefish {
        device  /dev/drbd0;
        disk    /dev/lvmgrp/lvmvol;
        address 10.10.10.240;7788; 
        meta-disk internal;
        }
}




#-----------------------------------------------------------------
#monkey@redfish:~$ sudo drbdadm create-md coconut

md_offset 3920231395328
al_offset 3920231362560
bm_offset 3920111726592
[U][B][COLOR=Black]
[/COLOR][COLOR=Black]Found ext3 filesystem[/COLOR][/B][/U]
  3828350976 kB data area apparently used
  3828234108 kB left usable by current configuration

Device size would be truncated, which
would corrupt data and result in
'access beyond end of device' errors.
You need to either
   * use external meta data (recommended)
   * shrink that filesystem first
   * zero out the device (destroy the filesystem)
Operation refused.

Command 'drbdmeta 0 v08 /dev/lvmgrp/lvmvol internal create-md' terminated with exit code 40
drbdadm create-md coconut: exited with code 40


#-----------------------------------------------------------------
#/etc/ha.d/haresources
redfish IPaddr::10.10.10.250/24/eth0 drbddisk::coconut Filesystem::/dev/drbd0::/mirrors/coconut::ext4 mysql-ndb-mgm mysql-ndb mysql apache2

](*,)](*,)](*,)](*,)

---

### Post by i_am_lost on 2010-12-10
meta data must be kept on a separate partition if 2TB+ disks are used.

---

