---
title: "powerpc, g4 and ubuntu server ie. biting off more than i can chew"
date: 2009-04-28
forum: Server Platforms
---

### Post by hikaniknak on 2009-04-28
Hi all,
    Great forum you guys have here, it's nice to know the community spirit is alive and in good shape still. Ok, i have a question somebody might be able to answer for me. Basically i'm about to begin a project that involves installing Ubuntu 8.04 powerpc server on a higher-end mac g4. However i'm thinking of removing the harddrive that contains the OS and replacing it with a spare drive that i can use as the dedicated drive. Just wondering if anybody else has tried this. I guess basically my question is does one need to have the Mac OS on the drive before you begin to wreak havoc...i mean install... because my understanding is that the server system can aquire the necessary drivers etc during and after the install. Am i totally wrong here?? If any of you guys have tried this already i'd be happy to hear from you, it would save me some of the usual headbanging i inflict on myself everytime i get these ideas into my thick irish head.

regards

Mike

---

### Post by netztier on 2009-04-29
> **hikaniknak said:**
> However i'm thinking of removing the harddrive that contains the OS and replacing it with a spare drive that i can use as the dedicated drive. 

That should work perfectly ok. I don't speak from experience with powerpc, but from SPARC workstations, to bring an example of non-x86 hardware. 

I did the exact same thing with my SPARC boxes and their Solaris disks: out with the Solaris disks, in goes a blank one, box boots from Ubuntu-for-SPARC CD, and the kernel used for that should already have the minimal set of drivers to allow for the installation (IDE adapters, SCSI adapters, basic graphics drivers, keyboard, serial, network etc). No need to keep a Solaris drive in the box - so I wouldn't expect that you need a MacOS X drive in there.

Once Linux is installed on the drive, you'll get a kernel with more and more sophisticated modules (drivers) for all your hardware.

I've already been able to boot a G4 PowerBook off an Ubuntu-for-Powerpc CD - no real problems occured. 

regards

Marc

---

### Post by hikaniknak on 2009-04-30
Hi Marc,
    You were spot on. I went ahead and ran the install last night and it ran without a hitch and installed perfectly apart from one or two fonts dependency error. It's amazing how well ubuntu is though out and how smoothly it sets itself up
    I set it up with lamp and open ssh and have putty running on my windows machine so i've got the easy parts done. I also installed gnome as a safety net, i have a tendency to climb too far into holes and need  rescuing. However i'm currently on a dynamic ip address and am dreading having to change to the static address which i'm gonna have to do. Any link you or any of the other guys here can provide to a good tut on static address setup would be most welcome. take care


regards

Mike

---

### Post by netztier on 2009-04-30
> **hikaniknak said:**
> However i'm currently on a dynamic ip address and am dreading having to change to the static address which i'm gonna have to do. 


Well, not actually. You can configure your DHCP server (which might be living inside your broadband router) to have a "static DHCP lease" or a "DHCP reservation" for the MAC address of your server's network card. You can find the MAC address like this:

```
user@server:~$ **ifconfig**
eth0      Link encap:Ethernet  [COLOR="Red"]HWaddr 00:1b:21:33:fd:46[/COLOR]  
          inet addr:172.20.xxx.xxx  Bcast:172.20.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe33:fd46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:84367494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160919430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8259190186 (8.2 GB)  TX bytes:244784229151 (244.7 GB)
          Memory:fd8e0000-fd900000
``` 

So whenever your server reboots or needs to renew it's DHCP lease, it will always be assigned the same address - while still considering itself as a "dynamic IP" system: static IP address made easy.

If you can't modify the DHCP server's configuration, we need to check a few things:

Did you install the package "ubuntu-desktop" that brought network-manager along? Or is networking still configured via the /ect/network/interfaces file? Best practice is to do only either of the two - saves a lot of trouble.

The two can sometimes get into conflict - removing network-manager ("apt-get remove network-manager" and "apt-get remove resolvconf") shouldn't harm and will leave you with /etc/network/interfaces, where configuring a static IP address is as simple as (using the correct values for ethX and IP address/netmask/gateway for your subnet, of course).

```
auto ethX
 iface ethX inet static
 address 192.168.100.10
 netmask 255.255.255.0
 gateway 192.168.100.1

```

Don't forget to add the IP address(es) of your DNS servers to **/etc/resolv.conf*** afterwards, so it looks approximately like this:

```
nameserver 195.186.1.62
nameserver 195.186.1.162
```


regards

Marc


[SIZE="1"]* Nota: resolvconf (*without* the ".") is a software package that handles automatic changes of the configuration file /etc/resolv.conf (*with* the "."). Don't confuse the two; you always need /etc/resolv.conf to list the DNS your system should use - but you don't necessarily need resolvconf to maintain that file.[/SIZE]

---

### Post by hikaniknak on 2009-05-03
Hi Marc,
    Thanks a million, that info was very helpful. Having never set up a server before the thoughts of messing with IPs and the like was a little daunting but your instructions came in very handy and no doubt kept me from wandering off the track. 

Regards

Mike

---

### Post by hictio on 2009-05-03
If you are still with this project this link might come handy:

[Reviving a Power Mac G4 with Ubuntu Server](http://linuxtidbits.wordpress.com/2009/01/29/reviving-a-power-mac-g4-with-ubuntu-server/)

---

### Post by hikaniknak on 2009-05-17
Thanks for your help guys, it was valuable and it's nice to know there's people out there willing to help a guy when he doesn't know what he's doing. Hictio, that link you sent was fantastic too, the perfect starting point for somebody aboout to attempt what i did with a G4.

---

