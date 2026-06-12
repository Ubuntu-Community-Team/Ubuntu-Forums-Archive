---
title: "Shutdown problem after upgrading to Karmic 9.10"
date: 2010-06-23
forum: Server Platforms
---

### Post by lindevox on 2010-06-23
Hi, 

I set my server (Specs:P4-2GHz, 2GB RAM, NICs: eth0 and linksys WUSBF-54G(USB WIFI)) as NFS and ROUTER for my internal network and able to connect to internet thru the second NIC (USB WIFI)

I just upgraded my ubuntu server edition from jaunty to karmic successfully I thought.. 

command issued for upgrade: 
   #sudo apt-get install update-manager-core
   #sudo do-release-upgrade


Before and after the upgrade, everything still well functioning. It still function as NFS and ROUTER except was experiencing problem when shutting it down by issuing the command which I usually use without a problem : 

   # shutdown -h now

This time my server produces message below :

     [9960:132004] EIP: [<c0170bfd>] clockevents_notify+0xfd/0x110
     SS:ESP 0068:f5cf1dd0
     [9960:132004] ---[ end trace ee2baa08003ad8b7 ]---
     [9964:100011] wlan0: no probe response from AP xx:xx:xx:xx:xx:xx 
     - disassociating
     [9965:100074] zd1211rw 1-3:1.0: error
     [12727.492074] zd1211rw 1-3:1/0: error ioread(CR_REG1): -110  
     .
     . <just HANG and PC won't Power off>
    

     sometimes it produces message like this:

     usb_id[384]:unable to access '/devices/pci0000:00/0000:00:1d.2
     /usb4/4-2'
     starting up ...
     fsck from util-linux-ng 2.16
     /dev/mapper/myserver-root: clean, 45/62248 files, 53267/248976 
     blocks (check in 3 mounts)
     fsck from util
     /dev/mapper/myserver-root:clean, 95492/13230080 files, 
     3558527/52910080 blocks (
     * Reloading /etc/samba/smb.conf smbd only
       .
       .
      <cursor blinking for a very long time and pc won't power off>

It won't power off the server (which it usually did before the upgrade). I've got manually bring it down by switch it off.

I try to examine the /var/log message (dmesg, daemon,messages,...etc) but couldn't find a line pointing to the problem I'm in.

I guess it is the usb wifi driver either was not correctly upgraded or the usb wifi has spoils/damage. But, if it has, why do I still have connection to internet thru it?

I'm a linux/Ubuntu NEWB who is not very familiar with linux, so if anybody would like to help me out, please explain to me in plain english would be very much appreciated. TQ in advanced.

---

### Post by iponeverything on 2010-06-23
For me zd1211rw segfaults on shutdown or removal. I didn't have issue on previous zd1211 module. 

If your caps-lock is blinking when it does not shutdown, it is the segfault issue.

---

