---
title: "higher graphics resolution with KVM ?"
date: 2009-06-23
forum: Virtualisation
---

### Post by Tomy on 2009-06-23
If I start KVM from the command line I can get a screen resolution of 1680 x 1050 or higher by using "-vga std".

```
$ kvm  -usb -usbdevice tablet -vga std -hda ~/winXP3.img -boot c -m 512

```When I use the Virtual Machine Manager to start the same winXP3.img  the Display choices are 'VNC server' or 'Local SDL window'. 

I can't get 'Local SDL window' to work - hangs the Virtual Machine Manager.

VNC server works fine but defaults to "-vga cirrus" and a max resolution of 1280 x 1024.  How do I get the VNC server to use "-vga std"?

I'd like to use the Virtual Machine Manager because I have the network bridge working.

---

### Post by bodhi.zazen on 2009-06-23
Well, this is the draw back of virt-manager, not all the features of kvm are available.

I have similar issues and posted to the virt-manager mailing list.

You can still use your bridge when starting kvm from the command line, you will need a wrapper script.

I am writing a blog about it, it is a draft as I need to add info about wireless, I will "publish" the blog for you understanding it its a draft ;)

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

---

### Post by Tomy on 2009-06-25
Thanks bodhi,
I followed your howto and set up the wrapper script but when I try to run it I get this error.

```
$ kvm-bridge -hda ~winXP3.img -boot c -m 512
&#8220;Bringing up interface tap0 with mac address DE:AD:BE:EF&#8220;&#8220;&#8221;
invalid syntax for ethernet address
```What did I do wrong?

---

### Post by Tomy on 2009-06-26
After some trial and error I got it to work by replacing the "ranmac" line in the kvm-bridge script with this hardcoded mac address:

ranmac=00:11:22:33:44:55

I also had to copy /etc/qemu-ifup and /etc/qemu-ifdown to /etc/kvm-ifup and /etc/kvm-ifdown. 

And finally I have to run this as root using sudo.

But now it works -- which is great.

bodhi, thanks for posting the draft of your howto.

---

### Post by juancarlospaco on 2009-06-26
Use Convirt 1.1 you can do it, its better than Virt-Manager :)

---

### Post by bodhi.zazen on 2009-06-26
> **Tomy said:**
> After some trial and error I got it to work by replacing the "ranmac" line in the kvm-bridge script with this hardcoded mac address:

ranmac=00:11:22:33:44:55

I also had to copy /etc/qemu-ifup and /etc/qemu-ifdown to /etc/kvm-ifup and /etc/kvm-ifdown. 

And finally I have to run this as root using sudo.

But now it works -- which is great.

bodhi, thanks for posting the draft of your howto.

Glad you got it working. I am runing KVM on Fedora right now, so that may be the reason you needed to use /etc/kvm-ifup and /etc/kvm-ifdown 

I added that information to my blog, thank you.

I also reviewed my script and there may have been a typo , especially if you cut and paste from workpress.

Run this command in a bash shell :

```
(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)
```

Assuming works, check the syntax in kvm-bridge

```
ranmac=$(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)
```

---

### Post by Tomy on 2009-06-26
> **bodhi.zazen said:**
> Glad you got it working. I am runing KVM on Fedora right now, so that may be the reason you needed to use /etc/kvm-ifup and /etc/kvm-ifdown 

I added that information to my blog, thank you.

I also reviewed my script and there may have been a typo , especially if you cut and paste from workpress.

Run this command in a bash shell :

```
(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)
```Assuming works, check the syntax in kvm-bridge

```
ranmac=$(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)
```

Thanks, that worked and fixed the ranmac issue.

I start kvm with this command line:
```
sudo kvm-bridge -vga std -hda winXP3.img -boot c -m 512
```Am I suppose to be able to run kvm as a user or is sudo required?

Here is the output from starting and stopping my winXP guest using kvm-bridge.
 
```
[sudo] password for tomy: 
“Bringing up interface tap0 with mac address DE:AD:BE:EF:21:67”
+ [ -n tap0 ]
+ /usr/bin/sudo /usr/sbin/tunctl -u user -g kvm -t tap0
'user' is neither a username nor a numeric uid.
Create: /usr/sbin/tunctl [-b] [-u owner] [-g group] [-t device-name] [-f tun-clone-device]
Delete: /usr/sbin/tunctl -d device-name [-f tun-clone-device]

The default tun clone device is /dev/net/tun - some systems use
/dev/misc/net/tun instead

-b will result in brief output (just the device name)
+ /usr/bin/sudo /sbin/ip link set tap0 up
+ sleep 0.5s
+ /usr/bin/sudo /usr/sbin/brctl addif br0 tap0
+ exit 0
TUNSETIFF: Device or resource busy
/etc/kvm-ifdown: could not launch network script
$

```When I shut down winXP I get the final error message that /etc/kvm-ifdown "could not launch" but it seems to run anyway and shutdown tapX. If I remove /etc/kvm-ifdown tapX is not removed (it will continue to hang around as shown by ifconfig). 

Everytime I startup and shutdown my winXP guest tapX is incremented by 1 (tapX is then removed if /etc/kvm-ifdown exists). Only after a reboot will I get a tap0. Is this the expected behavior?

Thanks for the help, bodhi. I now have both high resolution graphics and bridged networking. I set up a little script to run kvm-bridge and run it from a launcher in my Applications menu. I'm happy! :D

---

### Post by bodhi.zazen on 2009-06-26
run kvm-bridge as a user.

On this line :

> /usr/bin/sudo /usr/sbin/tunctl -u user -g kvm -t tap0

you need to change "user" to your log in user name. The user also needs to be in the kvm group.

---

### Post by Tomy on 2009-06-26
> **bodhi.zazen said:**
> run kvm-bridge as a user.

On this line :

Quote:
                                                 /usr/bin/sudo /usr/sbin/tunctl -u user -g kvm -t tap0                      

you need to change "user" to your log in user name. The user also needs to be in the kvm group.

No luck with that. I already was in the kvm group. I edited /etc/kvm-ifup and changed "user" to "tomy". I rebooted. Here's what happened as a user:

```
$ ./boot-winXP3.sh
“Bringing up interface tap0 with mac address DE:AD:BE:EF:26:11”
warning: could not open /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'
```and then with sudo:

```
$ sudo ./boot-winXP3.sh
“Bringing up interface tap1 with mac address DE:AD:BE:EF:26:11”
+ [ -n tap1 ]
+ /usr/bin/sudo /usr/sbin/tunctl -u tomy -g kvm -t tap1
TUNSETIFF: Device or resource busy
+ /usr/bin/sudo /sbin/ip link set tap1 up
+ sleep 0.5s
+ /usr/bin/sudo /usr/sbin/brctl addif br0 tap1
+ exit 0
TUNSETIFF: Device or resource busy
/etc/kvm-ifdown: could not launch network script
$ 
 
```
I checked /etc/sudoers and it has these lines:
```
## KVM
Cmnd_Alias KVM = /usr/sbin/tunctl, /sbin/ifconfig, /usr/sbin/brctl, /sbin/ip

%kvm ALL=(ALL) NOPASSWD: KVM

```

I must have done something wrong.

---

### Post by bodhi.zazen on 2009-06-26
Do you already have a tap1 ?

What are the permissions of /dev/net/tun ?

---

### Post by Tomy on 2009-06-26
> **bodhi.zazen said:**
> Do you already have a tap1 ?

What are the permissions of /dev/net/tun ?

Yes, tap1 was automagically set up when I started boot-winXP3.sh (really just a command line using kvm-bridge) and was also deleted when I shutdown winXP. As I mentioned above tapX is incremented everytime I start/stop my winXP guest. Actually it is incremented everytime I TRY to start my winXP guest -- in my post above you will see that the first failed attempt as a user shows tap0 and the next successful attempt using sudo creates tap1. I am now up to tap4 because I started/stopped winXP guest several times.
[FONT=monospace]
the permissions
[/FONT] ```
# ll /dev/net/
total 0
crw-rw-rw- 1 root root 10, 200 2009-05-04 14:59 tun

```

---

### Post by bodhi.zazen on 2009-06-26
You can remove old tap with 

```
sudo tunctl -d tap{0,1,2,3,4,5,6}
```It also appears your kvm-ifdown script is not running, is it executable ?

did you make a group kvm ?

Can you post boot-winXP3.sh ?

---

### Post by Tomy on 2009-06-26
> It also appears your kvm-ifdown script is not running, is it executable ?
```
# ll /etc/kvm*
-rwxr-xr-x 1 root root  158 2009-06-26 07:19 /etc/kvm-ifdown
-rwxr-xr-x 1 root root  272 2009-06-26 12:46 /etc/kvm-ifup

/etc/kvm:
total 8
-rwxr-xr-x 1 root root  174 2009-04-17 11:10 kvm-ifup
drwxr-xr-x 2 root root 4096 2009-04-21 19:26 utils

```Although I get the error message about kvm-ifdown it apparently is running because if I delete it tapX will not get removed.

> did you make a group kvm ?```

# cat group | grep kvm
kvm:x:124:tomy,root

```> Can you post boot-winXP3.sh ? ```
# cat boot-winXP3.sh
#!/bin/sh
kvm-bridge  -soundhw all -vga std \
-hda /winXP/winXP3.img \
-boot c \
-m 512

```

---

### Post by bodhi.zazen on 2009-06-26
post kvm-bridge also please ;)

---

### Post by Tomy on 2009-06-26
> **bodhi.zazen said:**
> post kvm-bridge also please ;)
This was copied from your blog howto. I changed the NIC model. 
```
# cat /bin/kvm-bridge
#!/usr/bin/env bash
# tap interface automagic allocation
# for linux kernels >= 2.6.18

# modified by bodhi.zazen from :
# http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/FrequentlyAskedQuestions

# set up a tap interface for qemu/kvm
# USERID – uid qemu is being run under.
USERID=`whoami`

# generate a random mac address for use the virtual nic
# With thanks to pheldens @ qemu forum

ranmac=$(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)

# specify which NIC to use – see man qemu
model=rtl8139

# The iface variable is automatically set to the next available tap
# Numbering starts with tap0
iface=`sudo tunctl -b -u $USERID`

# start kvm with our parameters
# $@ allows us to add additional command like parameters
# such as -hda $HOME/ubuntu.qcow2
echo “Bringing up interface $iface with mac address $ranmac”
# For Fedora 11 change “kvm” to “qemu-kvm”
kvm -net nic,vlan=0,macaddr=$ranmac,model=$model -net tap,vlan=0,ifname=$iface -usb -usbdevice tablet $@
# 

```

---

### Post by bodhi.zazen on 2009-06-26
I am not seeing anything obvious.

You can try removing -g kvm from your kvm-ifup script and / or running again as root to see where the problem may be.

---

### Post by Tomy on 2009-06-26
> **bodhi.zazen said:**
> I am not seeing anything obvious.

You can try removing -g kvm from your kvm-ifup script and / or running again as root to see where the problem may be.

Okay, thanks very much for the follow-up. 

In spite of the error message things work pretty well. I am using gksu to run my script from a menu entry -- so I have to enter my admin password. Not a big deal. 

And did I say it works :) and thank you :D

Have a great day
Tomy

---

### Post by bodhi.zazen on 2009-06-26
you are welcome. If it runs when running as root the problem is most likely with the 

-g kvm

you can test this by changing your primary group (this will be temporary)

```
newgrp kvm
```

That command will start a new shell and your primary group will be kvm.

If that works, either remove the -g kvm or change your primary group to kvm.

```
sudo usermod -g kvm user
```

you need to log off and back on or start a new log in shell for those changes to take effect

```
su - user
```

---

### Post by Tomy on 2009-06-26
Didn't seem to help -- the output looks the same.

```
$ newgrp kvm
$ kvm-bridge -hda winXP3.img -boot c -m 512
“Bringing up interface tap2 with mac address DE:AD:BE:EF:34:21”
warning: could not open /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'
$ 
$ sudo kvm-bridge -hda winXP3.img -boot c -m 512
[sudo] password for tomy: 
“Bringing up interface tap3 with mac address DE:AD:BE:EF:19:46”
+ [ -n tap3 ]
+ /usr/bin/sudo /usr/sbin/tunctl -u tomy -g kvm -t tap3
TUNSETIFF: Device or resource busy
+ /usr/bin/sudo /sbin/ip link set tap3 up
+ sleep 0.5s
+ /usr/bin/sudo /usr/sbin/brctl addif br0 tap3
+ exit 0
TUNSETIFF: Device or resource busy
/etc/kvm-ifdown: could not launch network script
$ 

```sudo kvm-bridge [options] works fine in spite of the "resource busy" and "could not launch" messages.

________________________________________________
Update: By adding kvm-bridge to /etc/sudoers (using visudo) I no longer have to enter my password. My addition to  /etc/sudoers is now:

```
# Allow members of the kvm group to configure a bridged virtual network interface
%kvm ALL=(ALL) NOPASSWD: /sbin/ifconfig, /usr/sbin/brctl, /usr/sbin/tunctl, /bin/kvm-bridge
```

---

