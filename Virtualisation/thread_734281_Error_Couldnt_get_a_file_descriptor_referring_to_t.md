---
title: "Error: Couldnt get a file descriptor referring to the console"
date: 2008-03-24
forum: Virtualisation
---

### Post by medha on 2008-03-24
I get the above message when I try to create a domain in Xen using: 
sudo xm create -c /etc/xen/d1-config extra='xencons=tty'

My config file is:
kernel = "/boot/vmlinuz-2.6.22-14-xen-D1"
ramdisk = "/boot/initrd.img-2.6.22-14-xen-D1"
memory = 64
maxmem = 128
name = "First-Domain"
disk = ['phy:/dev/sda5,sda5,w']
dhcp="dhcp"
root = "/dev/sda5 ro"
extra = "4"

This is how the log looks like:
.....
.....
[ 6411.691723] XENBUS: Device with no driver: device/console/0
[ 6411.692348] Freeing unused kernel memory: 200k freed
Loading, please wait...
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Begin: Loading essential drivers... ...
[ 6412.145871] AppArmor: AppArmor initialized<5>audit(1206391329.140:2):  type=1505 info="AppArmor initialized" pid=928
[ 6412.162469] fuse init (API version 7.8)
[ 6412.176393] Failure registering capabilities with primary security module.
[ 6412.229138] thermal: Unknown symbol acpi_processor_set_thermal_limit
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
Done.
Begin: Running /scripts/local-premount ...
Done.
[ 6412.908504] kjournald starting.  Commit interval 5 seconds
[ 6412.909050] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
 * Setting preliminary keymap...                                                [ 6414.429123] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
                                                                         [ OK ]
 * Preparing restricted drivers...                                       [ OK ]
 * Setting the system clock

It doesnt go any further.

Any ideas?

---

### Post by matey3 on 2008-12-03
Hey mates;
Has anyone seen this error before and somehow got it fixed?


I do not believe it is my OS/Image files because the other xen machines are working fine.
 
Let me know if you  seen this b4,please ...On my test server it gives the same error I dont know how many times.. like an endless loop but when I ctrl c out of it , gives a few errors (like interfaces file is bad etc.) and it goes ahead and boots up! (domU I mean) BUT when I tried it on the production server (off site) the dumb thing crashed and had to be rebooted (I mean our whole web server etc went down)!!!

I got to figure out why this error occurs?
On the production server which I am ssh-ing to I cannot control-c out of it. But on my test server which is here but I also ssh to, it comes out of this loop:


Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console 

this fills the screen until I Ctrl C out of it.

Thanks very much!

---

### Post by gna on 2009-03-18
This is a reply to medha:

The problems lies in the clock thing:
Do in the guest the following if you can start it otherwise:
update-rc.d -f hwclock.sh remove
update-rc.d -f hwclockfirst.sh remove

Or simply mount the guest image and remove all references in /etc/rc*.d/
> 
/etc/rc0.d/K25hwclock.sh
/etc/rc6.d/K25hwclock.sh
/etc/rcS.d/S11hwclock.sh
/etc/rcS.d/S08hwclockfirst.sh


Then youll be fine

---

