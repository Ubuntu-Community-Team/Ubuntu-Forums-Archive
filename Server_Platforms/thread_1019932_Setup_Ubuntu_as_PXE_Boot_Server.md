---
title: "Setup Ubuntu as PXE Boot Server"
date: 2008-12-23
forum: Server Platforms
---

### Post by Pyro.699 on 2008-12-23
Hello,

Ive been looking online for guides for how to install Ubuntu as a PXE Boot Server, meaning a user could boot on-to a Linux environment through PXE (Not install from it, boot onto it). All the guides I've managed to find are on how to install from a PXE boot server. Looking at this guide [Here](http://linux-sxs.org/internet_serving/pxeboot.html) (I know its not dealing with ubuntu), it said i needed to have some packages in stalled, but when i ran "sudo apt-get <those packages>" it said they didn't exist so i dont really know what to do. Im running Ubuntu Server 8.04

Thankyou
~Cody Woolaver

---

### Post by eL_vErDe on 2008-12-23
/etc/fstab:
```
/tftpboot/ubuntu/iso/ubuntu-8.04-desktop-i386.iso       /tftpboot/ubuntu/live-mntpoint  auto    loop    0       0

```

/etc/exports:
```
/tftpboot/ubuntu/live-mntpoint  *(async,ro,no_root_squash,subtree_check)

```

PXE Bootloader (this a internal bootloader of my corpo, you will have to fix it for pxelinux):
```
title Ubuntu 8.04 Live
desc Ubuntu 8.04 Live
kernel (nd)/tftpboot/ubuntu/live-mntpoint/casper/vmlinuz boot=casper netboot=nfs nfsroot=192.168.0.7:/tftpboot/ubuntu/live-mntpoint console-setup/layoutcode=fr
initrd (nd)/tftpboot/ubuntu/live-mntpoint/casper/initrd.gz

```

---

### Post by Pyro.699 on 2008-12-23
My first look at that makes me feel like it is exactly like having a live image. I want the user to be able to read/write to the hard drive. Something in this order...

-Computer gets turned on
-Boots onto PXE server
-Loads Ubuntu Desktop (Also installed on the same partition (hdd0,2 (I have all the boot infor needed for that)))
-Asks the user for a login
-Runs as a normal install, allowing the user read/write access to the disk

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-12-24
Sorry for the double post, but after a night of searching i was still unable to get some results.

---

### Post by koenn on 2008-12-24
your server will have to do dhcp so that the clients get an ip address from it. The dhcp will also have to provide a reference to the clients about where to find a boot image, so that's a dhcp option you have to set.
The server then also needs to serve the boot image, usually by tftp. This means you'll need a boot image, and configure your server to serve it when clients request it. As you probably don't want the clients to download a complete OS at every boot, the boot image will most likely be some sort of thin client configuration that allows access to terminal sessions/desktop session/filesystem on the server.

So, those are the steps.
You can probably find additional info at edubuntu, they (used to ?) use a thin client network boot approach 
Linux Terminal Service also has good ifo - here's a start: [http://www.ltsp.org/twiki/bin/view/Ltsp/PXE](http://www.ltsp.org/twiki/bin/view/Ltsp/PXE)

Unless you find a boot image that suits your purpose, you may have to build one. Syslinux is often used for that
[http://syslinux.zytor.com/wiki/index.php/PXELINUX](http://syslinux.zytor.com/wiki/index.php/PXELINUX)


As for the actual packages : I assume Debian supports pxe so there's a good chance you'll find the required software in Universe. search for terminal service, thin client, pxe, ltsp, ...
Some of these may also be in the main repo as part of edubuntu.

---

### Post by Pyro.699 on 2008-12-25
Thank you,

After reading those pages i have a better understanding of whats going on. Before you had a chance to post that i came across [**This**]("https://help.ubuntu.com/community/DisklessUbuntuHowto"), which i think is exactly what i wanted. I went threw the steps used but i kept getting stuck due to a lack of knowledge. Ill explain the basic information i know.

-I want the hosts IP to be **192.168.1.0** Host name: **Flareon**
-The client IPs will range from **192.168.1.1** to [B]192.168.1.254

[/B] Here are the areas i have questions about:

[Question 1]("https://help.ubuntu.com/community/DisklessUbuntuHowto#Set%20up%20your%20server")
> 

allow booting;
allow bootp;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.xxx 192.168.2.xxx;
  option broadcast-address 192.168.2.255;
  option routers 192.168.2.xxx;
  option domain-name-servers 192.168.2.xxx;

  filename "/pxelinux.0";
}

# force the client to this ip for pxe.
# This is only necessary assuming you want to send different images to different computers.
host pxe_client {
  hardware ethernet xx:xx:xx:xx:xx:xx;
  fixed-address 192.168.2.xxx;
}

This file should be located at: **/etc/dchp3/dchpd.conf**

Would i preform the following steps to change this content.

[B]subnet 192.168.1.0
range 192.168.1.1 192.168.1.254
option brodcast-address 192.168.1.254
option routers 192.168.1.???[/B] (I don't know what to put here)
**option domain-name-servers 192.168.1.???** (Don't know what to put here either)

**hardware ethernet MY:AD:RE:SS:HE:RE **(Would this be the MAC Address of the first client i wanted to add?)
[B]fixed-address 192.168.1.1

[/B]Next Question:

I created the file: **/tftpboot/pxelinux.cfg/default **then put the contents in it
[quote=/tftpboot/pxelinux.cfg/default]
LABEL linux
KERNEL /boot/vmlinuz-2.6.27-7-generic
APPEND root=/dev/nfs initrd=/boot/initrd.img-2.6.27-7-generic nfsroot=192.168.1.1:/nfsroot ip=dhcp rw
[/quote]

I got those values from /boot/grub/menu.lst
[quote=/boot/grub/menu.lst]
title Ubuntu 8.10
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4cbb2961-243a-4a24-b244-92ddab1c749f ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
[/quote]
Just wanting to make sure i had that part right it seems like a critical aspect.

Next Question:

[quote=/etc/exports]
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/nfsroot             192.168.1.1(rw,no_root_squash,async)
[/quote]
 
Just needed to see if i had the IP address correct.

[Question x]("https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating%20your%20NFS%20installation")
I created the directory **/ntfsroot** but was unsure what it wanted, i have to copy my entire install to that location. Is there anyways that i could just use the current install without waisting all that disk space?

I think thats it for now.

Thankyou very much!
~Cody Woolaver

---

### Post by koenn on 2008-12-25
By the looks of it, you miss even elementary network knwoledge. What are you  setting up network boot for ? 

I assume  by 'the host' you mean a server ?
you can't use 192.162.1.0 as a host address. It's a network address. You probably want 192.168.1.1 in stead. You should probably mannually configure the server with a static ip address.

Consequently, your dhcp range shouldn't include 192.168.1.1. Try starting from 192.168.1.2

option routers : sets the default gateway for dhcp clients, so it probably should be the address of a router

option domain name servers : tells the dhcp clients what dns servers to use. what to pot here depends on how you deal with dns on your LAN.

The section with hardware ethernet and fixed-address is if you want to assign a specific ip address to a computer with a given MAC address. If you're just doing plain dhcp, you don't need it.


you'll have to have your network config, especially the dhcp, correct before you can even think about network boot.

As for your questions about pxe specifically, I've never done this, so I wouldn't know - the Ubuntu howto you referred too looks pretty complete.

I think, however, that it's not a good idea to serve up your server's filesystem / operating system to the clients. They'll be using it as ther filesystem / OS, and you probably don't want multiple identical servers on your network. It can cause al sorts of trouble. You also don't want clients modifying the server's files.

---

### Post by Pyro.699 on 2008-12-25
The "clients" that are going to be accessing this is just me. Im doing this for 2 reasons.

First im doing this so that i can gain some learning experience from it. As you stated early i lack a lot of networking knowledge and doing small projects like this allows me to learn by experience.

Second I'm doing this so that i can have more computers setup for some calculations (**not** WPA cracking), another thing i do im my spare time is create programs to do complex complications, my only limiter is that i dont have enough hard drives to have more computers running.

The host will be running Ubuntu Desktop 8.10. I already have a static ip asigned (now changed to **192.168.1.1**)

Thanks
~Cody Woolaver

---

### Post by koenn on 2008-12-25
you still need to separate between the client system and the server system, I think.

If it were men I'd take this in 3 steps :
1- see if you can get a working dhcp server
2- see if you can get network boot working, without much concern of what exactly it is that's booting (just follow a guide or a howto)
3- if you have a working pxe boot, look into how you can modify the OS that the clients will boot.

---

### Post by druhboruch on 2008-12-26
This is all you need:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients](https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients)
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp+howto+nic](http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp+howto+nic)

---

### Post by Pyro.699 on 2008-12-27
Thank you very much for your replies.

After a few days of trying this on my own i once again must ask for help. I read several sites on how to setup a DHCP server and after many reformats (this is a junk machine that im testing this server on).

This computer is isolated from other computers for now but is connected to a switch (its the only one plugged in). I reinstalled Ubuntu Server 8.04 several times (each time i fully upgraded it). The only packages i installed were **dhcp3-server **and when i ran **/etc/init.d/dhcp3-server start** it returned as **[fail]**'ed. I then used several examples of a proper **dhcpd.conf** file. I got the examples from:

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

And both seem to return **[fail]**

my config file has this in it right now.

> 
subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.100 192.168.0.200;
option routers 192.168.0.1;
option broadcast-address 192.168.0.255;
default-lease-time 600;
max-lease-time 7200;
}


Thanks
~Cody Woolaver

---

### Post by koenn on 2008-12-27
there's probably an explanation in the log file.
Don't remember exactly where these things are logged, but yuo can try dmesg

your dhcp config looks ok, but you're defining a 192.168.0.0 subnet while in previous posts you said your server has 192.168.1.1. If that's still the case, the dhcp server will not work because it doesn't have an interface in 192.168.0.0. That might be the reason it fails to start.

Also, it's probably better to do 'restart' in stead of 'start' if dhcpd is running and you want to load a new configuration - it might fail to start because it's already running

---

### Post by Pyro.699 on 2008-12-27
Thankyou,

Heres what i did...

First i restarted the tower then ran this command 3 times: **sudo /etc/init.d/dhcp3-server restart; sudo dmesg > file1**
The first time it was plugged into a switch:
[quote=In Switch]
[   41.526718] NET: Registered protocol family 17
[   43.873250] loop: module loaded
[   43.884671] lp0: using parport0 (interrupt-driven).
[   44.074218] Adding 9775512k swap on /dev/sda5.  Priority:-1 extents:1 across:9775512k
[   44.435441] EXT3 FS on sda4, internal journal
[   45.056809] kjournald starting.  Commit interval 5 seconds
[   45.058910] EXT3 FS on sda3, internal journal
[   45.058915] EXT3-fs: mounted filesystem with ordered data mode.
[   46.212603] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.688686] NET: Registered protocol family 10
[   48.688882] lo: Disabled Privacy Extensions
[   58.878463] eth0: no IPv6 routers present
[/quote]

Second was in a router
[quote=In Router]
[   41.526718] NET: Registered protocol family 17
[   43.873250] loop: module loaded
[   43.884671] lp0: using parport0 (interrupt-driven).
[   44.074218] Adding 9775512k swap on /dev/sda5.  Priority:-1 extents:1 across:9775512k
[   44.435441] EXT3 FS on sda4, internal journal
[   45.056809] kjournald starting.  Commit interval 5 seconds
[   45.058910] EXT3 FS on sda3, internal journal
[   45.058915] EXT3-fs: mounted filesystem with ordered data mode.
[   46.212603] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.688686] NET: Registered protocol family 10
[   48.688882] lo: Disabled Privacy Extensions
[   58.878463] eth0: no IPv6 routers present
[  195.957818] eth0: link down.
[  202.996735] eth0: link up.
[/quote]

Then i had it unplugged completly
[quote=None]
[   41.526718] NET: Registered protocol family 17
[   43.873250] loop: module loaded
[   43.884671] lp0: using parport0 (interrupt-driven).
[   44.074218] Adding 9775512k swap on /dev/sda5.  Priority:-1 extents:1 across:9775512k
[   44.435441] EXT3 FS on sda4, internal journal
[   45.056809] kjournald starting.  Commit interval 5 seconds
[   45.058910] EXT3 FS on sda3, internal journal
[   45.058915] EXT3-fs: mounted filesystem with ordered data mode.
[   46.212603] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.688686] NET: Registered protocol family 10
[   48.688882] lo: Disabled Privacy Extensions
[   58.878463] eth0: no IPv6 routers present
[  195.957818] eth0: link down.
[  202.996735] eth0: link up.
[  226.374901] eth0: link down.
[/quote]

Thats what i got from dmseg. I dont really understand what it is saying, but im sure that resolving it will fix the problem.

Thanks
~Cody Woolaver

---

### Post by koenn on 2008-12-27
no, that's not it
try syslog 
```
/etc/init.d/dhcp3-server restart 
tail /var/log/syslog
```
add sudo where appropriate

(I use debian on my servers, and have dnsmasq doing dhcp, so I can't check  this)

---

### Post by Pyro.699 on 2008-12-27
(I restarted again)

I got this:

> 
Dec 27 17:25:32 Flareon dhcpd: Wrote 0 leases to leases file.
Dec 27 17:25:32 Flareon dhcpd: 
Dec 27 17:25:32 Flareon dhcpd: No subnet declaration for eth0 (192.168.1.102).
Dec 27 17:25:32 Flareon dhcpd: ** Ignoring requests on eth0.  If this is not what
Dec 27 17:25:32 Flareon dhcpd:    you want, please write a subnet declaration
Dec 27 17:25:32 Flareon dhcpd:    in your dhcpd.conf file for the network segment
Dec 27 17:25:32 Flareon dhcpd:    to which interface eth0 is attached. **
Dec 27 17:25:32 Flareon dhcpd: 
Dec 27 17:25:32 Flareon dhcpd: 
Dec 27 17:25:32 Flareon dhcpd: Not configured to listen on any interfaces!
i do have INTERFACES="eth0" in my /etc/default/dhcp3-server file

(Also, it is in the router right now)
 
Thanks
~Cody Woolaver

---

### Post by koenn on 2008-12-27
```
Dec 27 17:25:32 Flareon dhcpd: No subnet declaration for eth0 (192.168.1.102).
Dec 27 17:25:32 Flareon dhcpd: ** Ignoring requests on eth0. If this is not what
Dec 27 17:25:32 Flareon dhcpd: you want, please write a subnet declaration
Dec 27 17:25:32 Flareon dhcpd: in your dhcpd.conf file for the network segment
Dec 27 17:25:32 Flareon dhcpd: to which interface eth0 is attached. **
```
It's what I said before : your dhcp server has no address in the subnet it is supposed to serve 
If you're going to use 192.168**_.1._**x addresses, say so in your subnet declaration.

Also, apparently your server address now is 192.168.1.102, not 192.168.1.1
if your router is doing dhcp as well, this is going to interfere (later)
it's better you  set up your server with a static address, configured manually

---

### Post by Pyro.699 on 2008-12-27
Thanks (i kinda feel stupid),

In the end im going to have the server "dish" out the ips so i do need to have the server declare its own ip. Thats found in:

[B]subnet 192.168.1.0 netmask 255.255.255.0 {
[/B]range 192.168.1.100 192.168.1.200;
option routers 192.168.1.1;
option broadcast-address 192.168.1.255;
default-lease-time 600;
max-lease-time 7200;
} 			 		

the bolded line, correct? Ive now unplugged the server from the router and now into the switch (its more permanent home)

Sorry for the massive amount of confusion/questions
~Cody

---

### Post by koenn on 2008-12-27
no.
what you have there is a subnet declaration, specifying the configurations for hosts on the network that will be getting their network configuration via dhcp. The bold line describes the (sub)network these settings apply to.

your server ip config is in /etc/network/interfaces.
there's an example here : [http://ubuntuforums.org/showthread.php?t=419025](http://ubuntuforums.org/showthread.php?t=419025)

I see you're giving 'option routers 192.168.1.1;' That's the IP address of your router ? In that case, be sure not to use that address for your server.

---

### Post by Pyro.699 on 2008-12-27
Heres what i have

The IP range is: 192.168.1.100 -> 192.168.1.150
The routers IP is: 192.168.1.1 (its special i guess?)
The IP address that is assigned to the server (by the router) is 192.168.1.102

My interface file looks like this:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

My config file now looks like:
> 
default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option router 192.168.1.1
option broadcast-address 192.168.1.255;

subnet 192.168.1.102 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.150;
}


When i go to start the server i get an error saying there is an ip conflict with this line in the config file 
[B]subnet 192.168.1.102 netmask 255.255.255.0 {

[/B]Thankyou once again, youve been alot of help
~Cody Woolaver

---

### Post by koenn on 2008-12-28
you still don't get it.

try this  - I made your server IP address 192.168.1.10 and assume 192.168.1.1 is indeed the router's address :

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet [COLOR="Red"]static[/COLOR]
    address [COLOR="Red"]192.168.1.10[/COLOR]
    netmask 255.255.255.0
    [COLOR="DarkOrchid"]network 192.168.1.0[/COLOR]
    broadcast 192.168.1.255
    gateway 192.168.1.1 

```
/etc/dchp3/dchpd.conf
```

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option router 192.168.1.1
option broadcast-address 192.168.1.255;

subnet[COLOR="DarkOrchid"]** 192.168.1.0**[/COLOR] netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.150;
} 

```

restart services to activate the changes
```

/etc/init.d/networking restart
/etc/init.d/dhcp3-server restart

```

if dhcp server fails to start, check syslog, as before

check server ip address :
```
ifconfig eth0 
```

---

### Post by Pyro.699 on 2008-12-28
Thank you for your patience,

I now have the DHCP working properly (i added the line **filename "/pxelinux.0";** above **range 192.168.1.100 192.168.1.150;**). When i boot up a computer connected to the network, it gets the address fine (From the pxe loader) but then says something like the file could not be found (im asuming that its refering to **pxelinux.0** but when i go to **/tftboot** the file is there. In my **/etc/default/tftpd-hpa** i have the lines **RUN_DAEMON="yes" **and **OPTIONS="-l -s /tftboot"** which im asuming makes it the default directory.

Thanks
~Cody Woolaver

---

### Post by koenn on 2008-12-29
(bump)
anyone else ?

I'd guess it's a problem of file locations / names / paths ... 
but I have no experience with this.

---

### Post by Pyro.699 on 2008-12-29
Alright,

I got everything to boot properly (as in PXE finds (now moved) **/var/lib/tftboot/pxelinux.0** and loads **/var/lib/tftboot/pxelinux.cfg/default**)). I found a tutorial online that i used to boot from a live cd (and it worked :D) now what i need to do is boot into a linux opperating system located in **/desktop**. I have a hard drive and on it are 4 partitions. Windows XP, Ubuntu Desktop 8.10, Ubuntu Server 8.04 and 1 Swap space). I dont know how to set **/var/lib/tftboot/pxelinux.cfg/default**  to boot from the kernel thats installed on that partition.

Thanks
~Cody Woolaver

---

### Post by Cracauer on 2008-12-30
Unless I overlooked something you also miss the tftp part.

PXEBOOT as in the BIOS will only load a OS loader, not a kernel.

You will have to have a loader and a kernel in tftp space. For diskless Linux boots I usually use pxelinux from LILO (the grub stuff didn't compile for me and wasn't compiled into distribution's binaries). If you use pxelinux, then you also need a special kind of tftp server that support the file length attribute, the small one that you normally run from inetd won't do. tftpd-hpa works, but seems insecure, so I run it in a chroot.

Anyway, you first need to make dhcp work, and test it with a non-diskless client, then go from there.

---

### Post by Pyro.699 on 2008-12-30
I have a working dhcp server, and it will boot properly from that (loads **pxelinux.cfg/default** just fine) what i need to do is be able to boot onto the ubuntu opperating system that is located in **/desktop **(its in the root directory, not **/var/lib/tftboot**)

Thanks
~Cody Woolaver

---

### Post by Cracauer on 2008-12-30
> **Pyro.699 said:**
> I have a working dhcp server, and it will boot properly from that (loads **pxelinux.cfg/default** just fine) what i need to do is be able to boot onto the ubuntu opperating system that is located in **/desktop **(its in the root directory, not **/var/lib/tftboot**)

Thanks
~Cody Woolaver

OK, now I see it, so you have a working tftpd.

You understand that pxelinux and kernel are loaded via tftp and the root filesystem via NFS, yes? Normally people copy the kernel into the tftpboot directory instead of making the ftpd directory the same as the root filesystem.

Does your kernel come up yet?

---

### Post by Pyro.699 on 2008-12-30
so i should copy:

[B]/desktop/boot/vmlinux*
[/B]and
[B]/desktop/boot/img*

[/B](I'm not home right now and forget the exact names >< but those 2, i know mine are 2.6.27-9-generic)

to **/var/lib/tftboot/**?

I did that once and it brought up a few errors in the boot process....the first was right after the configuration file was loaded (i cant get the exact error cause it goes by too fast) but it basically says "Missing Configuration Parameter" or something... Then will load everything (in what looks like the recovery console) and stop after it loads the cd driver and says its missing the root something (i can look later and post it)

Thanks
~Cody

---

### Post by Cracauer on 2008-12-30
No, only the kernel.

So does the kernel come up?

I'm not sure what you mean with recovery console. What exactly comes up?

---

### Post by Pyro.699 on 2008-12-30
Heres what happens...

I turn on the client computer and it starts to boot. It successfully gets its ip from the dhcp and begins to boot. Instead of the grahical boot screen (the one that shows ubuntu and the loading bar) something comes up and tells you what it is loading, the drivers for all the cards and such. It will then halt and come to a command line interface that looks like this:

(initrd):

and you put your command there, when i type ls, there are a few directories there but most are empty and the /home one is not there.

Thanks
~Cody Woolaver

---

### Post by Cracauer on 2008-12-30
> **Pyro.699 said:**
> Heres what happens...

I turn on the client computer and it starts to boot. It successfully gets its ip from the dhcp and begins to boot. Instead of the grahical boot screen (the one that shows ubuntu and the loading bar) something comes up and tells you what it is loading, the drivers for all the cards and such. It will then halt and come to a command line interface that looks like this:

(initrd):

and you put your command there, when i type ls, there are a few directories there but most are empty and the /home one is not there.

Thanks
~Cody Woolaver

That's the kernel coming up all right. Very good.

What do you have in the pxelinuc cfg directory's file? What are the parameters you pass to this kernel?

Are you sure that config file is loaded?

---

### Post by Pyro.699 on 2008-12-30
This is whats in my **pxelinux.cfg/default** file:

> 
LABEL linux
KERNEL vmlinuz-2.6.27-9-generic 
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-9-generic nfsroot=192.168.1.102:/desktop ip=dhcp rw

what file are you refering to when you say "config file"?

Thanks
~Cody

---

### Post by Cracauer on 2008-12-30
Here is a working one from my server:

```

prompt 1
default Linux-amd64
timeout 70

label Linux-amd64
        kernel vmlinuz-2.6.26.3-perfctr-em64t-cracauer
        append root=/dev/nfs ip=dhcp nfsroot=172.18.30.2:/home/diskless/debian-amd64-root1 init=/sbin/init verbose=8

```

For the record, LILO's pxelinux is one of the most backwards subsystems in Linux. This config mechanism just stinks. Wait until you try to maintain a whole farm of machines.

---

### Post by koenn on 2008-12-31
> **Pyro.699 said:**
> Heres what happens...

I turn on the client computer and it starts to boot. It successfully gets its ip from the dhcp and begins to boot. Instead of the grahical boot screen (the one that shows ubuntu and the loading bar) something comes up and tells you what it is loading, the drivers for all the cards and such. It will then halt and come to a command line interface that looks like this:

(initrd):

and you put your command there, when i type ls, there are a few directories there but most are empty and the /home one is not there.

Thanks
~Cody Woolaver

sounds like you enter initrd succesfully (so your pxe is working). initrd is a small filesystem used during boot. The next step should be that the root filesystem is mounted - apparently this doesn't happen. 

Did you create an nfs export for /desktop on the server ?

---

### Post by Pyro.699 on 2008-12-31
This is in my exports file **/desktop             192.168.1.102(rw,no_root_squash,async)**. Im going to be going home soon so i can get you more accurate data then. (but i do know thats what my exports file is)

Thanks
~Cody

---

### Post by Pyro.699 on 2009-01-01
Hello,

So instead of restarting my client several times i went and got my digital camera and video taped the startup process and then screen shotted the parts that would be of some help. Throughout this entire process there is no graphical user interface, everything is presented via command line.

Thanks
~Cody Woolaver

---

### Post by koenn on 2009-01-02
If you really want to learn from this, like you said in one of your previous posts, you could start with actually reading the error messages.

the screen shots you post show that your pc can't find a root filesystem to mount. This is the problem I explained 3 posts back.

diagnostics : what's the output of these commands (on your server: )
```

netstat -tua |grep rpc
netstat -tua |grep nfs

```

---

### Post by Pyro.699 on 2009-01-02
Thanks,

I ran those commands and got this

> 
cody@Flareon:~$ netstat -tua | grep rpc
tcp        0      0 *:sunrpc                *:*                     LISTEN     
udp        0      0 *:sunrpc                *:*                                
cody@Flareon:~$ netstat -tua | grep nfs
tcp        0      0 *:nfs                   *:*                     LISTEN     
udp        0      0 *:nfs                   *:*       


This is in my exports file:

> 
/desktop             192.168.1.102(rw,no_root_squash,async)


**182.168.1.102** being the ip address of my server

Thanks once again
~Cody

---

### Post by koenn on 2009-01-02
your exports is wrong.
the exports says what you are exporting (/desktop), and who you are exporting for, so you need the client addresses / network / ... there, not the server's address.

try
```

/desktop      192.168.1.0/255.255.255.0(rw,no_root_squash,no_subtree_check)

```

---

### Post by Cracauer on 2009-01-02
Didn't somebody already point out that you need to test the exports from a regular booted machine first? It's a couple posts up I think.

You can't really debug from a half-dead diskless boot.

---

### Post by Pyro.699 on 2009-01-02
I changed the export file, and used **exportfs -rv** to export it. I then rebooted the client computer and got all the same messages.

Cracauer you mentioned (in post #24) that i needed to test the boot server. How do i go about doing that with a non-diskless system?[]("http://ubuntuforums.org/member.php?u=392315")

Something else i noticed was that in the second screenshot it says **ALERT! /dev/nfs does not exist. Dropping to a shell!** in my **/var/lib/tftboot/pxelinux.cfg/default** it has

> 
LABEL linux
KERNEL vmlinuz-2.6.27-9-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-9-generic nfsroot=192.168.1.102:/desktop ip=dhcp
rw


root is given the value of **/dev/nfs** which must be wrong. (I got that from [Here](https://help.ubuntu.com/community/DisklessUbuntuHowto#Set%20up%20your%20server))

Thanks again guys
~Cody

---

### Post by pla on 2009-01-21
Hey 

I got stuck at the same spot. After re-reading the How-To document you reference in post #40 it looks like there may be a typo in that document. 

Where it says "* Change the BOOT flag to NFS in /nfsroot/etc/initramfs-tools/initramfs.conf" I think is should say "* Change the BOOT flag to NFS in /etc/initramfs-tools/initramfs.conf on the client." 

I changed the initramfs.conf file on the client, reran mkinitramfs, copied the image to the server and booted the diskless client successfully. 

Thanks, PLA

---

### Post by djsephiroth on 2009-01-22
> **koenn said:**
> you still don't get it.

You can't blame the OP too much when no one here has explained the  basic networking concepts that are missing from his or her experience. Please don't yell at him or her for not "getting it" when you're not explaining anything that he or she should reasonably "get", e.g., the concept of subnets and the legal IP addresses therein. 

Let me get on my pedestal... ahem:

A subnet is a "range" of IP addresses: it's a set of addresses that are treated as a network, regardless of where and how they're physically connected. To declare a subnet, one needs the name of the subnet and a subnet mask. These are two numbers that will allow both you and your gear to figure out which addresses are part of a given subnet.

Example: 192.16.1.0 is a subnet. Let's say it has mask 255.255.255.0. What this mask means in English: the first three numbers separated by periods identify the subnet, and the last one identifies the hosts in the subnet. So, anything starting with 192.16.1 is a host in our subnet. Everything with an IP address from 192.16.1.1-192.16.1.254 is in our subnet.

As a general rule, one cannot use IP addresses ending in .0 or .255. While this is not technically true (for example, given network 10.0.0.0 and subnet mask 128.0.0.0, 10.0.1.0 is a valid host IP address), it is essentially true within the scope of small home and office networks (since they tend to follow classful addressing rules). A good rule of thumb is to give your server, router, printers, and other essential hosts IP addresses at the start or end of your subnet's address range. Example: given network 192.168.0.0 and subnet mask 255.255.0.0, your IP addresses go from 192.168.0.1 to 192.168.255.254; giving the server the address 192.168.0.1 makes it easy to remember and easy to recognize.

Hope that helped. I apologize if I merely restated something posted by another (and in all likelihood more informed) member.

---

### Post by koenn on 2009-01-22
> **djsephiroth said:**
> You can't blame the OP too much when no one here has explained the  basic networking concepts that are missing from his or her experience. Please don't yell at him or her for not "getting it" when you're not explaining anything that he or she should reasonably "get", e.g., the concept of subnets and the legal IP addresses therein. 

that "you still don't get it" was a factual observation, delivered in a calm and informative manner. The 'yelling at him' exists only in your perception. Please refrain from drawing conclusions and making accusations based on nothing but unsubstantiated assumptions

---

### Post by Cracauer on 2009-01-22
I don't think it's wrong to recommend that somebody first tests his NFS server setup from a regular client, not in a first-timer diskless boot.

---

### Post by djsephiroth on 2009-01-23
> **koenn said:**
> that "you still don't get it" was a factual observation, delivered in a calm and informative manner. The 'yelling at him' exists only in your perception. Please refrain from drawing conclusions and making accusations based on nothing but unsubstantiated assumptions
Roger that. My apologies if I took it out of context.

---

### Post by xris_xcess on 2009-04-16
Hi:

I set up a complete PXE, DHCP, NFS ubuntu server from scratch following some of the guides here posted, buy I especially recomend

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I followed it to the dots and the i's (except for my use of dnsmask) and got pxe-booting in no time.

First I must say that you really need to understand exactly how an TCP/IP network "works" befory trying this, or you could find youself going around in circles trying to figure out which part, typos or subnet masks are not working/wrong.

Second, I don't recall where I picked this up, but my server also acts as a network router/firewall. Since I wanted a dns-caching facility to speed up my network somewhat I looked into that. Of course dhcp-hpa usually is the de-facto suggested but I found a much simpler (config and resource wise) alternative. dnsmasq.

dnsmask ([https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)) is a very simple dns-caching-forwarder-dhcp-tftp server. So, in one program, you really cover 90% of the pxe-booting requirements. I uses just one config file, full of anotated explanations, so you can pick up a lot of info right there.

The other 10% is NFS ( [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) ). The "write to disk" that is metioned happens to the NFS share on the server. It also contains the so called "nfsroot", which is just the equivalent of your local HD system served over the network.

I can see that the exports file points to "/desktop"... well... there is no root system on the desktop (I could be wrong). You could try just plain "/", but your 'clients' would boot the same root as the server. So you would end up with a bunch of servers.

As in the first link I gave, you need at LEAST two fully set up PC's (you could do it with one, but that could get pretty awkward). One as the server (or a regular desktop working as a server) and a second machine to set up as a MODEL client. Once your client is set up as you would like it to boot, you tranfer its ROOT system to a folder on the server, hence "nfsroot". THIS is the folder that we export as an NFS share and this is the root of the client machines.

I admit that setting it all up is rather tedious. I regularly boot 6 machines off a server and it all works like a charm. Plus the fact that I only mantain 'one' client now, when before it was 6.

I suggest you invest some time researching TCP/IP network theory first and then just follow [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto).

---

### Post by poloxyt on 2010-03-16
Hi evreyone

I met similar problem to Pyro.699
I read this tutorial precisly:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

Everythigns works fine: dhcp - work, tftp - work.
Only with "Creating your NFS installation, punnkt 3 - Copy OS files to the server" of this tutorial i've got problem
Command i used:

```
mount -tnfs -onolock 192.168.1.2:/nfsroot /mnt
cp -ax /. /mnt/.
cp -ax /dev/. /mnt/dev/.
```

And when i was copying : cp -ax /. /mnt/. this shown in my console:

```
sroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/nfsroot/
nfsroot/nfsroot/nfsroot/nfsroot': File name too long
cp: cannot stat `/./home/serbart/.gvfs': Permission denied
root@serbart-desktop:/# 
```


There are plenty of /nfsroot/nfsroot/... lines.
I firured that my copy didn't work fine (example: i couldn't copy /sys) ;/

When i boot my client:
1. Client get ip fron dhcp - ok
2. Client get pxelinux.0 by tftp - ok
3. Client loads kernel and initrd.img - ok
4. Then client start to load multiple files. All works fine whent client couldn'f mount some folders like /sys (or root-sys or sys-root - i don't remember exactly :P). If i mount it (/sys) then another mount problem show up.

The major problem is:
How can I make my client filesystem in example folder/folders?
Wich files should i copy?
Whwere i shold i copy it?

I'm asking for help :P

edit. [SOLVED] I didn't change fstab :P, and this multi word /nfsroot/nfsroot/... doesn't change anything :p

---

