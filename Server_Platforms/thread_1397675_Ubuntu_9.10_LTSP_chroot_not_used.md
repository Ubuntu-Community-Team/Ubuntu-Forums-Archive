---
title: "Ubuntu 9.10 LTSP chroot not used"
date: 2010-02-03
forum: Server Platforms
---

### Post by gunnerjoe53 on 2010-02-03
[SIZE=4][SIZE=3]Hi All,

I setup Ubuntu 9.10 Desktop / ltsp 5.1.90-0ubuntu3, and using a Thin Client from disklessworkstations.com ([LTSP Term 1520 - PXE Boot - Thin Client]("http://www.disklessworkstations.com/cgi-bin/prod/200118.html?id=mvnYQowr"))

After LTSP install following the docs on [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)  the thin client booted with no tweaking to any of the configs.  While I can boot and login just fine it does not work as I expected. 

1. When logged in as a regular user through the thin client I am not put into the chroot enviroment  /opt/ltsp/i386 , the regular user can browse the real / directory.  The only place I see that makes reference to chrooted environment is the /etc/ltsp/dhcpd.conf  and /opt/ltsp/i386/etc/ltsp_chroot, [/SIZE][/SIZE][SIZE=4][SIZE=3]which is as follows:

#ltsp_chroot:

[/SIZE][/SIZE][SIZE=4][SIZE=3]LTSP_CHROOT=/opt/ltsp/i386
 
=============================

# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

It looks to be set correctly... Ideas?

2. Also,  the main config lts.conf has no entries what so ever, is that because the LTSP Thin Client work out of the box?  

3. Also the lts.conf has a note that the lts.conf file should be located in /var/lib/tftpboot/ltsp/i386, the file did not exist there, so I'm guessing if you needed to use lts.conf you would create it there?


Any Help Greatly Appreciated.

Joe

[/SIZE][/SIZE]

---

### Post by kaltoza on 2010-02-10
Hi Joe

Have you tried changing your routers IP address in your
LTSP config file to 192.168.0.254

eg: option routers 192.168.0.254;

then

sudo ltsp-update-sshkeys
sudo ltsp-update-image

and reset your network and ltsp server

sudo /etc/init.d/networking restart
sudo /etc/init.d/dhcp3-server restart

just to make sure everything is up to date ;)

---

