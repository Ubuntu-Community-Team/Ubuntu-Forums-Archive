---
title: "HOWTO: PXE booting Ubuntu Installer"
date: 2010-02-22
forum: Tutorials
---

### Post by yogesh.girikumar on 2010-02-22
Hi,

I looked around for a tutorial on this but couldn't find one. So I wrote this myself. This setup worked for me. Hope it works for you too. Let me know if you face any issues.  [B]

UBUNTU PXE BOOT INSTALLATION[/B]

       Ubuntu is usually installed on a system using a Live CD. Another method of installing it is over the network! PXE stands for Preboot eXecution Environment which is an environment for booting the Ubuntu installer off the network. This is helpful in installing Ubuntu on systems which do not have a CD-ROM drive. This can also be used to automate the installation process using preseeding on a large number of systems. 

   **STEPS INVOLVED**

[LIST=1]
[*]Set up a PXE Server
[LIST=1]
[*]Configure network interfaces
[*]Installing Xinet Daemon, DHCP Server and TFTP Server
[*]Configure Inet daemon [xinetd]
[*]Configure TFTP server [tftpd-hpa]
[*]Configure DHCP Server [dhcp3-server]
[/LIST]
 
[*]Fetch the boot files
[*]Preparing the client system
[*]Boot the client system
[/LIST]

    **Setting up a PXE Server**

       A PXE Server is a system that serves the client ( on which the system has to be installed ) with an IP address and the bootloader file to boot off from. The client system does not need a CD-ROM drive for this type of installation. A NIC card is all that is necessary and it must be able to boot off the network.

     **How it works:**
       

[LIST]
[*]The client machine starts and tries to boot off the network.
[*]It sends a DHCP REQUEST over broadcast.
[*]A DHCP server in the network gives a DHCP OFFER and provides the client with a valid IP address.
[*]The DHCP also provides the client with 1. **A file name** to look for and 2. **The TFTP server address** (next-server directive) to look into for the file.
[*]The file is a "pxelinux Loader" ( named **pxelinux.0** ). The file is uploaded to the client machine via TFTP.
[*]The bootloader is then started off the pxelinux Loader file.
[*]Packages necessary for the installation are fetched off the network ( Internet or a local mirror server )
[*]Installation is done.
[/LIST]
    **Installing Xinet Daemon, DHCP Server and TFTP Server**

 Xinetd, DHCP and TFTP are essential in performing a PXE boot. So they have to be installed in the system. To do so, type the following command in the terminal:
```
 $ sudo apt-get install xinetd tftpd-hpa dhcp3-server
``` **Configure inet daemon**

 Inet daemon is a super-server daemon. A super-server daemon can start a collection of other related servers. Xinetd is one such super server which stands for eXtended InterNET Daemon. It is capable of starting other networking servers such as FTPD, SSHD, etc..

We installed "xinetd" package. We need to enable inetd at boot time. To do so, execute the following command in the terminal.
```
$ sudo update-inetd --enable BOOT
``` Then restart the inetd server:
```
$ sudo /etc/init.d/xinetd restart
```**Configure TFTP Server**

       TFTP server is needed to serve the bootloader files necessary to start the installation. TFTP server is available in the package "tftpd-hpa". We have installed tftpd-hpa. Now we have to configure it.

[LIST]
[*]  Create a directory /tftpboot in which we will store all the necessary boot files. Then change the permissions so that it is accessible to the world [ all ].
[/LIST]
 ```
$ sudo mkdir /tftpboot
$ sudo chmod -R 774 /tftpboot
``` Then we need to change the ownership of the directory:

[LIST]
[*] ```
$ sudo chown nobody /tftpboot
``` We also need to set the permission to 777 in case the above permission doesn't work.
[/LIST]
     Edit the /etc/default/tftpd-hpa file
 ```
$ sudo nano /etc/default/tftpd-hpa
```
[LIST]
[*] Modify the file so that it looks something like this:
[/LIST]
 ```
RUN_DAEMON="yes" 
OPTIONS="-l -s /tftpboot" 
```The important changes here are setting RUN_DAEMON to "yes" and changing the directory path to "/tftpboot"   We now need to create a tftpd file inside Xinetd. To do so, create a file **named tftp** in the /etc/xinetd.d/ directory
```
$ sudo touch /etc/xinetd.d/tftp
$ sudo nano /etc/xinetd.d/tftp
```Then add the following lines to the file
```
# TFTP configuration
service tftp
{
socket_type = dgram
protocol = udp
port = 69
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /tftpboot
disable = no
}
```
[LIST]
[*]Now restart xinetd and tftpd-hpa
[/LIST]
 ```
$ sudo /etc/init.d/tftpd-hpa restart
$ sudo /etc/init.d/xinetd restart
```**Configure DHCP Server**

       DHCP server provides the client machine with a valid IP address so that it can identify itself to the network and fetch files that are necessary for the installation.

 The DHCP server should serve over a separate network interface that holds a static address. This can be done by editing the /etc/default/dhcp3-server file

```
$ sudo nano /etc/default/dhcp3-server
```edit the file so it looks like
```
INTERFACES="eth1" 
```if eth1 is the interface where you want DHCP to serve and provide IP addresses.  Now we need to configure DHCP Server.

[LIST]
[*]Create a backup copy of the DHCP config file [ just in case ;-) ]
[/LIST]
 ```
$ sudo cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.orig.conf
```
[LIST]
[*]edit the /etc/dhcp3/dhcpd.conf file
[/LIST]
```
 $ sudo nano /etc/dhcp3/dhcpd.conf
```Add the following lines to the configuration file or uncomment them if they are already present
```
#option definitions
option domain-name "companydomain.com";
option domain-name-servers 10.10.6.3;

default-lease-time 600;
max-lease-time 7200;

authoritative;

#subnet declaration
subnet 192.168.2.0 netmask 255.255.255.0 {
   range 192.168.2.2 192.168.2.255;
   option subnet-mask 255.255.255.0;
   option broadcast-address 192.168.2.255;
   filename "pxelinux.0";
   next-server 192.168.2.100
}
```     the filename "pxelinux.0"; and "next-server 192.168.2.100"; directives should be added to the file.

***Edit:** companydomain.com is the domain name of my organization and 10.10.6.3 is the IP address of the local DNS server*

   Now restart the dhcp server
```
$ sudo /etc/init.d/dhcp3-server restart
```**Fetching the boot files**

 The boot files and network booting installation scripts and configurations should be downloaded to the TFTP server directory (/tftpboot). The files can be downloaded to the directory using the lftp command. You may have to install lftp program to use it.
```
$ cd /tftpboot
$ lftp -c "open [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/;](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/;) mirror" 
``` Now we need to edit the /tftpboot/pxelinux.cfg/default file. The contents of the file should be something similar to this:
```
include ubuntu-installer/i386/boot-screens/menu.cfg
Menu Background sample.png
prompt 0
timeout 0
```     If you decide to have your own Custom Boot Menu, you can edit the file so that it looks like this. Please comment out or remove the include option.. I have commented it out here in my configuration file ( first line ).
   ```
# include ubuntu-installer/i386/boot-screens/menu.cfg
default vesamenu.c32
Menu Background sample.png
Menu Title Boot Menu

label install
   menu label ^Install
   menu default
   kernel ubuntu-installer/i386/linux
   append vga=normal initrd=ubuntu-installer/i386/initrd.gz --quiet

label expert
   menu label ^Expert Install
   kernel ubuntu-installer/i386/linux
   append priority=low vga=normal initrd=ubuntu-installer/i386/initrd.gz --

label cli-expert
   menu label Command-^line expert Install
   kernel ubuntu-installer/i386/linux
   append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=normal initrd=ubuntu-installer/i386/initrd.gz --

label rescue
   menu label ^Rescue Mode
   kernel ubuntu-installer/i386/linux
   append vga=normal initrd=ubuntu-installer/i386/initrd.gz rescue/enable=true --quiet

label Local_drive
   localboot 0
   menu label ^Local Drive

prompt 0
timeout 0
```**Preparing the Client System**

       The client system needs to be able to boot from the network for this setup to work. The client systems should boot via network first. In order to do this, you may have to change the boot order in the Client machine's BIOS settings. A typical setup would be to boot from Network first and then from Hard Disk.
       **Booting the client**

       Switch on the client machine. Check if the BIOS settings are OK and verify if the system is set to boot off the Network first. If All settings are working fine, then the client machine should give out a DHCPREQ DHCP request and get a valid working IP address for itself. Then the BootLoader menu should be shown from where you can proceed with installing the OS.

Should you need help with any command, you can type the following in the terminal 
```
$ man <command>
```
       
**UN-COMMENTING IN CONFIG FILES**

       Uncommenting lines in the config files can be done by removing a '#' sign from the start of the line. This is usually true for most files. Some file might have a semicolon ';' as a commenting symbol instead of '#'. To comment out a line, simply add a '#' or a ';' (whichever is appropriate) to the start of the line.

---

### Post by Zalanthas on 2010-02-24
SUPERB GUIDE!

[B]One question:
[/B] 
```
#option definitions
option domain-name "slashsupport.com";
option domain-name-servers 10.10.6.3;
```Do we need the domain name and name servers?
Could you write a couple of lines to your guide how the domain name and name servers work in this solution and how should we edit them if needed?



**One comment:**

When I try to boot with custom boot menu, it passes pxelinux.0, but fails at pxelinux.cfg file, resulting in "cannot load kernel".

I had to change it to this =>

```
default ubuntu-installer/i386/boot-screens/vesamenu.c32
```instead of this 

```
default vesamenu.c32
```

---

### Post by yogesh.girikumar on 2010-03-01
Hi Zalanthas,

> **Zalanthas said:**
> SUPERB GUIDE!

Thanks !

> **Zalanthas said:**
> 
Do we need the domain name and name servers?
Could you write a couple of lines to your guide how the domain name and name servers work in this solution and how should we edit them if needed?

  Having a domain name is optional. If your organization has a common domain name, then you can just add it in the dhcpd.conf file. This parameter will be supplied to the client when a DHCPOFFER is given out.

The domain-name-server directive is used to pass the address of the organizational domain name server. 

see: [http://www.nisi.ab.ca/lrp/Packages/man/dhcpd.conf.5.man.htm](http://www.nisi.ab.ca/lrp/Packages/man/dhcpd.conf.5.man.htm)  ( EXAMPLES section )

> **Zalanthas said:**
> 

When I try to boot with custom boot menu, it passes pxelinux.0, but fails at pxelinux.cfg file, resulting in "cannot load kernel".

I had to change it to this =>

```
default ubuntu-installer/i386/boot-screens/vesamenu.c32
```instead of this 

```
default vesamenu.c32
```

Yes! I am sorry! I should have mentioned. Right after you fetch the files from the server, you can ( for the sake of simplicity ) create a symbolic link for the files in the top directory.

```
$ sudo ln -s ./ubuntu-installer/i386/boot-screens/vesamenu.c32 ./vesamenu.c32
```I had done this and referred to the symlink 

Thanks for the comments.

---

### Post by mchlor on 2010-07-16
Trying to fiddling with server lucid i386.
might be a bug in lucid server distro with dhcpd3 package.  I get...

```
 * Stopping DHCP server dhcpd3
   ...fail!
 * Starting DHCP server dhcpd3
 * check syslog for diagnostics.
   ...fail!

```

I'm not quite clear on this domain name and domain name server thing.  What should they be if my router already is running dhcp server?  Do I need to turn the router dhcp server off?

---

### Post by Z.K. on 2010-10-02
> **mchlor said:**
> Trying to fiddling with server lucid i386.
might be a bug in lucid server distro with dhcpd3 package.  I get...

```
 * Stopping DHCP server dhcpd3
   ...fail!
 * Starting DHCP server dhcpd3
 * check syslog for diagnostics.
   ...fail!

```

I'm not quite clear on this domain name and domain name server thing.  What should they be if my router already is running dhcp server?  Do I need to turn the router dhcp server off?

Did you ever find an answer to this error, I get the same error when dhcp tries to start up.

---

### Post by kufio on 2010-11-24
I followed  a mixture of these 2 links:
[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot) (just the first 3 steps) the best solution for ubuntu 10.10 netbooting  with tftp is dnsmasq and atftp
Then I followed this guide [http://www.linuxreaders.com/2010/06/24/pxe-boot-ubuntu-10-04/](http://www.linuxreaders.com/2010/06/24/pxe-boot-ubuntu-10-04/)
with a minor change:  **mount ubuntu-10.04-desktop-i386.iso /mnt/iso** should be  **mount loop -o ubuntu-10.04-desktop-i386.iso /mnt/iso**

and then before executing **Enter following in /etc/exports** install 
NFS kernel server

I now have ubuntu maverick up and running on a machine with no cdrom and/or usb

---

### Post by NumPy on 2010-11-30
I was JUST about to start one of these.
The problem I personally ran into, was setting up a DHCP server. Building one is fine, yet I wanted to use the one on my router yet did not have options for identifying tftp boot files, or the like. Since I am a hard head and love to tinker I took a day off and started a tftp proxy to the router using the dnsmasq proxy feature for this. Your tutorial is a complete array, and well written. Think you might want to add a snippet for the users that might not want to setup dhcpd, or cant use dhcpd's feature? I have it drafted, and can send it by email.

---

### Post by tfultz33 on 2010-12-17
Ive been trying to get tftpd-hpa to work for a year and still no luck. Times out even on the local machine. Says it is running with 
```
julius@Caesar:~$ ps -e | grep tftp
 4599 ?        00:00:00 in.tftpd
julius@Caesar:~$ 

```and 
```
julius@Caesar:~$ netstat -a | grep tftp
udp        0      0 *:tftp                  *:*                                
julius@Caesar:~$ 
 
``````
tftp> julius@Caesar:~$ tftp localhost
tftp> get version.info
Transfer timed out.

```
version.info exists in /tftpboot.
I have been trying to install ubuntu on my laptop this way for a year or more. The cd rom is broken and I am on dialup. I downloaded the 10.04 alternate image to upgrade from karmic on this machine. I run old debian that is way outdated. To update one package on that machine it has to update 100 more. Dialup sux. I miss my roadrunner. BEEP! BEEP!

---

### Post by tfultz33 on 2010-12-18
This is etc/xinetd.d/tftp:

# TFTP configuration
service tftp
{
socket_type = dgram
protocol = udp
port = 69
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /tftpboot
disable = no
}

This is /etc/default/tftpd-hpa:

# /etc/default/tftpd-hpa

RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot"

Every sign says it is running, but it wont respond in any way.
Any takers?

---

### Post by tfultz33 on 2010-12-18
Ahhhh! I got it!
No one ever mentions the fact that you need a tab whitespace before each statement in between the brackets.

Then i changed the ownership back to root.
Now the file looks like this:

# TFTP configuration
service tftp
{
         socket_type = dgram
         protocol = udp
         port = 69
         wait = yes
         user = root
         server = /usr/sbin/in.tftpd
         server_args = -s /tftpboot
         disable = no
}
Atleast I have it working locally now. Now to get that laptop in the other room to connect. :D

---

### Post by voidman on 2011-02-13
mchlor, Z.K.
have you found answer to this error?
I'm can't fix it and my dhpc3 service does not work propertly even after reboot (I thought after reboot dhpc3 will have to reload anyway)

Then i try to connect to other notebook it displays "Can't get to dhcp" or something like that message. 

I think I tried everything... Can anybody help me? 
I even can't tell thats wrong...

sudo /etc/init.d/dhcp3-server status
Status of DHCP server: dhcpd3 is not running.

sudo /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                                         * check syslog for diagnostics.
                                      dmesg | tail
[   90.470708] atkbd serio0: Use 'setkeycodes e077 <keycode>' to make it known.
[  100.065344] r8169 0000:08:00.0: eth0: link up
[  100.065855] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  110.742727] eth0: no IPv6 routers present
[  144.402194] r8169 0000:08:00.0: eth0: link down
[  148.760124] r8169 0000:08:00.0: eth0: link up
[  155.583054] r8169 0000:08:00.0: eth0: link down                                    
[  157.184697] r8169 0000:08:00.0: eth0: link up                                      
[  210.350645] r8169 0000:08:00.0: eth0: link down                                    
[  235.673983] r8169 0000:08:00.0: eth0: link up                                             [fail]

---

### Post by jmac25 on 2011-07-25
I have been trying to figure this out for days and am going crazy.  I finally got dhcp working and the client gets its ip but for some reason it doesn't connect to tftp it gets an error 
PXE-E32: TFTP open timeout
 
I can see it trying to connect in my syslog it shows 
 
Inbound IN=eth0 OUT= MAC=00:16:d3:fe:07:f4:00:11:3e:de:4b:76:08:00 SRC=10.42.43.10 DST=10.42.43.1 LEN=60 TOS=0x00 TTL=20 ID=10 Proto=UDP SPT=2078 DPT=69 LEN=40
 
I am stuck any help would be greatly appreciated.  I am running 2.6.32-33-generic Ubuntu 10.04 LTS

---

### Post by voidman on 2011-08-31
Any progress?

---

### Post by Vidyadhar D S on 2011-09-02
Free you need to create a PXE server, to do the same follow this tutorial
[PXE BOOT SERVER ON UBUNTU]("http://www.techienote.com/2010/11/pxe-boot-server-on-ubuntu.html")

After this you need to add ubuntu in boot menu
[ADDING UBUNTU IN PXE BOOT MENU]("http://www.techienote.com/2010/06/pxe-booting-lucid-lynx-ubuntu-10-04.html")

I am using the above tutorial from last 10 months and did not found any problem in the same.

Thanks,
Vidyadhar
[http://techienote.com](http://techienote.com)

---

### Post by tfultz33 on 2011-09-04
What fixed this problem for me was making sure there are tabs in the tftpd configuration file. I cant remember the file name it wa s a long time ago and have since removed tftp but the problem was incorrectly formatted config file. I was then able to install ubuntu on a laptop with no internet or cdrom drive via tftp and apache.

---

### Post by ptmuldoon on 2011-09-07
Hi,

I just followed this tutorial, and was able to pxe boot and install ubuntu on a client machine.   But...... it installed an older 9.x version, and not the latest 11.04 version.

Can we install the latest version following this tutorial?  I'm pretty new to pxe booting and installing, and have seen other tutorials that use nfs.

Should I follow this tutorial to install the latest 11.04 version with nfs?
[http://www.thelupine.com/content/ubuntu-pxe-booting](http://www.thelupine.com/content/ubuntu-pxe-booting)

And do you also need to mount the iso's, or can I extract the iso contents, and point to installer?

---

