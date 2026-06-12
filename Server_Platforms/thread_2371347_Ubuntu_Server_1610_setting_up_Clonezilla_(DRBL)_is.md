---
title: "Ubuntu Server 16:10 setting up Clonezilla (DRBL) isolated setup"
date: 2017-09-13
forum: Server Platforms
---

### Post by ally2 on 2017-09-13
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]Gods of Linux / Guild of Linux :)[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]
[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]I have dugout a old box and am in the process of setting up clonezilla ( DRBL server)[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]Now the problem is I already have a DHCP server running which I do not want to clash with. I currently have a basic network not fancy wizardry such as subnets, vlans,[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]
[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]I could really do with some pointers.  [/FONT][/FONT][/FONT][/COLOR][COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]I have setup a box and have connected the ethernet card directly to a switch. Completely isolating it from the main network.[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]Go easy on me I have some basic questions appreciate the help:[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]1) The server isn't getting an i.p when I plug into the switch so I figured configure the card with a static i.p. In my network config file I have basically a i.p address and s/m. more information required? bearing in mind there is no DNS, Gateway.[/FONT][/FONT]
[/FONT][/COLOR]

[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]2) DRBL requires a working DHCP server, Can I run DHCP without having DNS, or a gateway. I basically want anything I plug in this isolated switch to touch base with the server via pxe.[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]3) What the hell do I put in the DHCP config? it's going to look pretty bare? what would the FQDN be or wouldn't I need one.

4) Can I use any network scope for the DHCP config or am I right in thinking go with a class C[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]Is any of this even possible with 1 nic on a isolated switch. [/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]
[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica][FONT=inherit][FONT=inherit]Many Thanks guys.[/FONT][/FONT]
[/FONT][/COLOR]

---

### Post by ally2 on 2017-09-14
Ok So I have been fiddling and am having some difficulty getting this isolated server to hand out DHCP is it even possible? I have posted up my entire config, feel free to shout at me call me an ******. I respect the knowledge you guys possess and could really do with some pointers here. With out further ado my config.

UBUNTU SERVER 16:10


[ /etc/network/interfaces]


# the loopback network interface 
auto lo
iface lo inet loopback


#the primary network interface
allow-hotplug enp3s0
iface enp3s0 static
address 192.168.2.1
netmask 255.255.0
gateway 0.0.0.0
broadcast 192.168.2.255




( This is a single ethernet card being connected directly to a switch, no router involved)


------------------------------------------------------------------------------------------------------


[DHCP Settings]


[/etc/default/isc-dhcp-server]


I added my interface 


#INTERFACES="enp0s3"


-----------------------------------------------------------------------------------------------------


[dhcpd.conf]


default-lease time 6000;
max-lease-time 7200;


subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.2 192.168.2.15;
option subnet-mask 255.255.255.0
option broadcast address 192.168.2.255
}




--------------------------------------------------------------------------------------------------------

---

