---
title: "kvm qemu performance problem"
date: 2009-09-06
forum: Virtualisation
---

### Post by guentherk1 on 2009-09-06
On Ubuntu 9.04 Jaunty I get very slow startup after reboot of an Windows XP virtual machine using KVM and QEMU.  I start the XP VM with a KVM command.  It takes about 35 seconds to start ( To get the black terminal execution window.)

On the same machine using a Fedora Core 11 partition after reboot the same virtual machine file started in a vm using KVM and QEMU starts immediately.

On Ubuntu once the XP VM is shutdown and then restarted after the same original boot of Ubuntu the VM starts up at the same speed:) as the XP VM on Fedora Core 11.

The other thing is on Ubuntu I can't start the VM from a desktop launcher.  I have to open a terminal window and run it using the command

 kvm -boot c -hda /home/karl/xp.img&  

Anyone know if there is a fix for the slow startup on Ubuntu 9.04 and why kvm won't start from a desktop launcher using the same command as I use in a terminal window.

I am using KVM-84 directly from an apt-get install and Ubuntu 9.04, kernel 2.6.28-15-generic.  All results are using 64 bit OS and 8GB of memory.

Thank You,

Karl:)

---

### Post by mitchd123 on 2009-09-13
Just a guess, but it may be the way your networking is configured.  I have my network "bridged" to simply pull a DHCP address from my wireless router.  

I also have 9.04 running KVM 1:84+dfsg-0ubuntu12.3 with 8gb of memory running on AMD 4850e 64 bit  I am NOT using libvirt.

There are probably better ways to configure it, but here's how I have mine setup:

Two lines which start up the VM on computer boot up in  /etc/rc.local

-----------------------------------------------------
/home/kvm/kvm_start  & > /dev/null
/home/kvm/iorenice kvm -c2 -n0 & > /dev/null
------------------------------------------------------

Here's the kvm_start file I created
--------------------------------------------------------
#!/bin/bash
/usr/sbin/tunctl -b -u root -t qtap0 
/usr/sbin/brctl addif br0 qtap0
/sbin/ifconfig qtap0 up 0.0.0.0 promisc
nice -n -7 \
/usr/bin/kvm \
-m 3G \
-smp 2 \
-localtime \
-nographic \
-net nic,model=virtio,macaddr=00:0C:29:82:D9:00 \
-net tap,ifname=qtap0,script=no,downscript=no \
/mnt/raid/kvm/XP.img &
---------------------------------------------------------
I use -nographic because I connect via RDP / Terminal Services
Here's my iorenice (thanks to someone on the Gentoo forums) The command iorenice is designed to increase the io priority of the file access.  This makes the VM perform much more "snappy" rather than sluggish. 

----------------------------------------------------------
#!/bin/bash

cmd="$@"
if [ -z "$cmd" ]
 then
     echo "feed me something...usage: iorenice [partial prog name] [ionice options]"
     exit 0
fi

# get all options
params=`echo $@ | sed -e "s/ /\n/g" | sed -n "/^-/p"`
# get rid of extra \n
params=`echo $params`

# set a def val if needed
if [ -z "$params" ]
then
    params="-c3"
fi

# for each given prog name
for item in `echo $@ | sed "s/-.*//g" | sed "s/\ /\n/g"`
do
       # for each process hitting this
      for pid in `ps -A | grep $item | sed "s/[^ 0-9].*//g"`
      do
      echo "ionicing $item ($pid) with $params"
      ionice $params -p$pid
    done
done
------------------------------------------------------------------


Manually starting the VM with graphics it takes around 7 to 8 seconds from when I press enter on the command until I see the XP black screen with the white startup/loading bar.  Here's the command I run to start manually:

kvm -m 3G -smp 2 -localtime -net nic,model=vtio,macaddr=00:0C:29:82:D9:00 -net tap,ifname=qtap0,script=no,downscript=no /mnt/raid/kvm/XP.img

Yours probably won't start from a desktop launcher due to permissions of the logged on user. 

On a straight xp reboot from within the windows OS, from when the system shuts down completely until I see the black and white loading bar is about 5 seconds.  

Hope this helps.

---

### Post by shamael on 2009-09-22
OT: I like the idea of having static tap interfaces, but how do you avoid running virtual machines as root?


--EDIT--
Ok, got it... tap interfaces are not static, so I have to recreate them at boot.
I've also found out that I only need to have them owned by a kvm user to be able to start the VMs without root privileges.

---

