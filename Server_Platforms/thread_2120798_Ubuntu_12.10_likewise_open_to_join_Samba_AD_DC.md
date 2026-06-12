---
title: "Ubuntu 12.10 likewise open to join Samba AD DC"
date: 2013-02-27
forum: Server Platforms
---

### Post by IJselflearner on 2013-02-27
Hi Ubuntu Community,
 
 
After a lot of testing, I am still unsuccessful in joining my Ubuntu 12.10 client to my Samba AD DC.
 
Currently, I have a working Samba AD DC, successfully joined a Windows 7 machine, and the Samba AD DC is running.
 
I tried using Likewise open installed from Ubuntu Software Center, try to connect via Likewise open GUI, input my Domain Name then Join, entered Domain administrator credentials, click OK. response: DNS_ERROR_BAD_PACKET; A bad packet was received from a DNS server. Potentially the requested address does not exist.
(Some tutorials worked out successfully; Any configuration I am missing here.)
 
I find it more easy to join Windows client to join the domain, connection is easily established. But with Ubuntu client, it seems to be a narrow road.
 
Anyone who was able to successfully join an Ubuntu machine. Hope you will share your configuration.
 
Thanks so much in advance.
 
 
-IJ-

---

### Post by lingpanda on 2013-02-27
> **IJselflearner said:**
> Hi Ubuntu Community,
 
 
After a lot of testing, I am still unsuccessful in joining my Ubuntu 12.10 client to my Samba AD DC.
 
Currently, I have a working Samba AD DC, successfully joined a Windows 7 machine, and the Samba AD DC is running.
 
I tried using Likewise open installed from Ubuntu Software Center, try to connect via Likewise open GUI, input my Domain Name then Join, entered Domain administrator credentials, click OK. response: DNS_ERROR_BAD_PACKET; A bad packet was received from a DNS server. Potentially the requested address does not exist.
(Some tutorials worked out successfully; Any configuration I am missing here.)
 
I find it more easy to join Windows client to join the domain, connection is easily established. But with Ubuntu client, it seems to be a narrow road.
 
Anyone who was able to successfully join an Ubuntu machine. Hope you will share your configuration.
 
Thanks so much in advance.
 
 
-IJ-

Here is my cheat sheet I made for 12.04.

[COLOR=#000000][FONT=Verdana-Bold][SIZE=4]**Configure nsswitch.conf**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]Before you attempt to join an Active Directory domain, make sure the[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]/etc/nsswitch.conf [/FONT][FONT=Garamond, serif][SIZE=3]file contains the following line:[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]hosts: files dns[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]The [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]hosts [/FONT][FONT=Garamond, serif][SIZE=3]line can contain additional information, but it must include the[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]dns [/FONT][FONT=Garamond, serif][SIZE=3]entry, and it is recommended that the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]dns [/FONT][FONT=Garamond, serif][SIZE=3]entry appear after the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]files[/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]entry.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]Computers running Solaris, in particular, may not contain this line in[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]nsswitch.conf [/FONT][FONT=Garamond, serif][SIZE=3]until you add it.[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]When you use PowerBroker Identity Services with Multicast DNS 4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3](mDNS4) and have a domain in your environment that ends in [/SIZE][/FONT][FONT=CourierNewPSMT, monospace].local[/FONT][FONT=Garamond, serif][SIZE=3], you[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]must place the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]dns [/FONT][FONT=Garamond, serif][SIZE=3]entry before the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]mdns4_minimal [/FONT][FONT=Garamond, serif][SIZE=3]entry and before the[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]mdns4 [/FONT][FONT=Garamond, serif][SIZE=3]entry:[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]hosts: files dns mdns4_minimal [NOTFOUND=return] mdns4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]The default setting for many Linux systems is to list the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]mdns4 [/FONT][FONT=Garamond, serif][SIZE=3]entries[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]before the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]dns [/FONT][FONT=Garamond, serif][SIZE=3]entry—a configuration that leaves PBIS unable to find the[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]domain.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond-Bold][SIZE=3]**Important: **[/SIZE][/FONT][FONT=Garamond, serif][SIZE=3]For PBIS to process changes to your [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]nsswitch.conf [/FONT][FONT=Garamond, serif][SIZE=3]file, you[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]must restart the PBIS input-output service ([/SIZE][/FONT][FONT=CourierNewPSMT, monospace]lwio[/FONT][FONT=Garamond, serif][SIZE=3]) and the authentication[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]service ([/SIZE][/FONT][FONT=CourierNewPSMT, monospace]lsass[/FONT][FONT=Garamond, serif][SIZE=3]). Running the following command as root restarts both[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]services:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]/opt/pbis/bin/lwsm restart lwio[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond, serif][SIZE=3]For PBIS to work correctly, the [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]nsswitch.conf [/FONT][FONT=Garamond, serif][SIZE=3]file must be readable by[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]user, group, and world.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]For more information on configuring nsswitch, see the man page for[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]nsswitch.conf[/FONT][FONT=Garamond, serif][SIZE=3].[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Verdana-Bold][SIZE=4]**Configure resolv.conf**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]Before you attempt to join an Active Directory domain, make sure that[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]/etc/resolv.conf [/FONT][FONT=Garamond, serif][SIZE=3]on your Linux, Unix, or Mac client includes a DNS[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]server that can resolve SRV records for your domain.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]Example: [FONT=CourierNewPSMT, monospace][SIZE=2][root@rhel5d Desktop]# vi /etc/resolvconf/resolv.conf.d/head[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]search [SIZE=2]mydomain[/SIZE].local[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]nameserver 192.168.68.132[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Verdana-Bold][SIZE=3]**Step 2: Install PBIS Open on Linux**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]You install PBIS Open by using a shell script that contains a self-extracting[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]executable—an SFX installer with a file name that ends in sh. Example:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=CourierNewPSMT, monospace]pbis-open-6.5.0.3499-linux-i386-rpm.sh[/FONT][FONT=Garamond, serif][SIZE=3].[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]1. As root, run the installer, substituting the file name of the installer that[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]you have selected for the one shown below:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]sh ./pbis-open-6.5.0.3499-linux-i386-rpm.sh[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]Alternatively, you can run the installer as a regular user:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=CourierNewPSMT, monospace][SIZE=2]sudo sh ./pbis-open-6.5.0.3499-linux-i386-rpm.sh[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]2. Follow the instructions in the installer.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana-Bold][SIZE=2][FONT=Garamond-Bold][SIZE=3]**Note: **[/SIZE][/FONT][FONT=Garamond, serif][SIZE=3]On SLES and other systems on which the pager is set to less, you[/SIZE][/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Garamond, serif][SIZE=3]must exit the end user license agreement, or EULA, by typing the[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2][FONT=Garamond, serif][SIZE=3]following command: [/SIZE][/FONT][FONT=CourierNewPSMT, monospace]q[/FONT][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=4]**Enable Other Login**[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]1) You have to be root to perform this how-to.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]If you are not root then be root by executing following command :-[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]ubuntu-12.04lts@tejas-barot-linux-ahmedabad:~$ sudo su – ( Single Hyphen )[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]2) First of all Please take backup of original file, execute following command :-[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]root@tejas-barot-linux-ahmedabad:~# cp -p /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.orig[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]3) Execute Following command :-[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]root@tejas-barot-linux-ahmedabad:~#/usr/lib/lightdm/lightdm-set-defaults -m true[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]root@tejas-barot-linux-ahmedabad:~#/etc/init.d/lightdm restart[/SIZE][/FONT][/COLOR]
 

 

 

 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=4]**Disable Guest Account**[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]Open /etc/lightdm/lightdm.conf file from your terminal using the following command[/SIZE][/FONT][/COLOR]
 [COLOR=#073763][FONT=arial, sans-serif][SIZE=2]**sudo gedit /etc/lightdm/lightdm.conf**[/SIZE][/FONT][/COLOR] Add the following line
 [COLOR=#073763][FONT=arial, sans-serif][SIZE=2]**allow-guest=false**[/SIZE][/FONT][/COLOR] Save and exit the file

After adding the above line you should see similar to the following in lightdm.conf file
[I][B][SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
allow-guest=false[/B][/I]

Finally you have to restart lightdm using the following command from your terminal
 [COLOR=#073763][FONT=arial, sans-serif][SIZE=2]**sudo restart lightdm**[/SIZE][/FONT][/COLOR] Enjoy

---

