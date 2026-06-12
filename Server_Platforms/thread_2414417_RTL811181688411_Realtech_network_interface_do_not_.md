---
title: "RTL8111/8168/8411 Realtech network interface do not show logical name"
date: 2019-03-10
forum: Server Platforms
---

### Post by abhiways on 2019-03-10
Hello,

My networking suddenly stopped when I run sudo-apt-get update and restarted server Ubuntu 16.04

when I run
```
sudo lshw -short | grep network
```

I see output without Logical Name of Device Previously the name of device was enp3s0

I am attaching photo of my terminal.

[https://i.ibb.co/CWK16P6/photo6064273748283992122.jpg]("https://ibb.co/SJwscfc")
[upload pic]("https://imgbb.com/")

Please help.

---

### Post by TheFu on 2019-03-10
Need much more info.  The question and image doesn't make sense.  The image shows the same device you claim doesn't exist.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some steps to track down the issue.

---

### Post by abhiways on 2019-03-10
Hello TheFu,

 Apology for that Let me explain my question in details.

I run

```
sudo apt-get update
```
yesterday 

When I restarted ubuntu server 16.04 today my ethernet adapter was not showing up and internet is not working on my server.

Screenshot 1
[https://i.ibb.co/m0NFLCf/screenshot1.jpg]("https://ibb.co/2SZYD7G")

My ifconfig is

Screenshot 2
[https://i.ibb.co/LhPc63g/screenshot2.jpg]("https://ibb.co/Nn3JpMN")


My network shows UNCLAIMED

screenshot 3
[https://i.ibb.co/BVhFdby/screenshot3.jpg]("https://ibb.co/QFWtzLP")

My /etc/newtork/interfaces reads this

Screenshot 4
[https://i.ibb.co/gP2LsmQ/screenshot4.jpg]("https://ibb.co/Nmvdwtf")

when i run 

sudo ifup -v enp3s0
[https://i.ibb.co/8c0S2Hm/screenshot5.jpg]("https://ibb.co/6Bmfbky")

I get error failed to bring up enp3s0

I hope things are more clear now.

My Current kernel version is 4.13.0-26

---

### Post by TheFu on 2019-03-10
Please don't post images.  You can redirect the output to a file, copy the file to a USB drive, and use that to post here.  Some people pay for every byte here.

Looks like the driver isn't being loaded.   Assuming it is on the system already, and it should be, you can use the **insmod** command.  

From the "teaching you to fish" manual .... do you know the name of the module that the NIC uses?  If you search these forums for "RTL8111/8168/8411 driver", then the correct driver name should be there.  The output from **lshw** shows the driver.  I happen to have a machine with that same NIC **AND** the same version running 16.04.
```
$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
**       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller**
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       **version: 0c**
       serial: fc:aa:14:a7:06:51
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
```

So, **sudo modprobe r8169** is the command on 16.04 with a 4.4.x kernel.  insmod is another command, either should work.  Check it by using the lsmod command.  Here's what I see on my box:
```
$ lsmod |grep r81
r8169                  86016  0
mii                    16384  1 r8169
```

Then you can use **sudo ifup {device name}**  I override the default name and forced it to be eth0.  It may change after the kernel module is loaded.  IDK.

Anyway, that should be enough to get you on the right track, perhaps even a fix.  If you reboot and it is broken still, do the same manual stuff and blacklist the r816**8** module in /etc/modprobe.d/  Look to see if the r8169 module is blacklisted and remove that.

---

### Post by abhiways on 2019-03-11
I downgraded default kernel version to 4.4.0-87-generic and my problem is fixed.

---

### Post by TheFu on 2019-03-11
> **abhiways said:**
> I downgraded default kernel version to 4.4.0-87-generic and my problem is fixed.

You shouldn't need to do that. If normal Ubuntu patching/upgrade methods have been used, then a compatible version of the driver should have been installed for the new kernel.

But if this solution is working and you are happy with it, please use the thread tools button near the top and mark it as "solved" to help the community here.

---

### Post by abhiways on 2019-03-11
So far I am happy with the solution since this is a old web server and I am happy that it came up again.
As a revision I would like to give more information why I feel downgrading kernel was best solution for me 
as you said I run "lsmod | grep r81"

I did not get any result. I investigated it more and found that r6168 is not working on kernel versions 4.4 above.

I downloaded latest driver from their website and tried to installed it "r8168-8.025.00.tar.bz2" Mirror : [https://github.com/mtorromeo/r8168](https://github.com/mtorromeo/r8168)

but it required gcc version 4.9+ and on my machine there was gcc version 4.8

I tried to update it manually with deb files "since my internet was not working" and found that there are lot of dependencies hence chosen to downgrade the kernel. This information may be helpful for someone who is facing similar problem.

Note: before installing new driver you have to make sure you are running gcc 4.9+ and blacklist old driver

echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf

After downloading new driver use "make clean modules" followed my "make install"

One of our last steps is, to let the system know about the r8168 driver. With the command
depmod -a
you rebuild the kernel module dependencies and with an
insmod ./src/r8168.ko
To always use the new module, you have to make a new initrd boot file.
mkinitramfs -o /boot/initrd.img-'uname -r' 'uname -r'
At least, you have to add in the "/etc/modules" file a new entry, which is called "r8168", to get the driver automatically loaded after boot.
echo "r8168" >> /etc/modules

---

