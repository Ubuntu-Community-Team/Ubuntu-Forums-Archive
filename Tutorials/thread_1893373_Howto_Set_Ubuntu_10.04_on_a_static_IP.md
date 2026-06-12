---
title: "Howto Set Ubuntu 10.04 on a static IP"
date: 2011-12-10
forum: Tutorials
---

### Post by L a r r y on 2011-12-10
Before I begin, a note about local network addresses:  The IP address range in most home networking applications will be of the range of 192.168.x.2 through 192.168.x.254, with a gateway of 192.168.x.1 and a netmask of 255.255.255.0.  Depending on your router manufacturer, your x may be the numeric value of 0, 1 or 2.  But whatever value it is, it is unchanging throughout the life of your network.

Typically, if your router is built-in to the modem, the number for x is often 0, and may be 1.  I have been acquainted with people running the combined modem-router on a DSL circuit, but have not been around a cable modem.  My personal experience has always been separate modem and router on a DSL circuit.

The procedure I followed to set up my computer running Ubuntu 10.04 to be on a static IP within my router's local network is as follows:

Determine the parameters of my local network by visiting my router's admin page with my browser.  In the case of my Belkin, that would be 192.168.2.1.  For security, you should have a password set for accessing this page.

The admin page address also serves on my network as the **gateway.**

(If you have a wireless network involved with your router, it definitely should be configured to require a passphrase or a key to permit others' access.  And there definitely should be a password on the admin page, to prevent someone from entering your unprotected wireless network on a driveby and changing settings.  But wireless networking is beyond the scope of this article.)

I need to determine from my router, the current range of addresses available to my DHCP server, which acts to assign an IP address to connecting devices on the fly.  At the outset, this pool contained the full range of available addresses from 192.168.2.2 through 192.168.2.254.  Not a good idea to assign static IP addresses within the DHCP server's pool range, risking the chance of dynamically assigning the same address to a second device.  No two devices may share the same IP address without there being a communications failure.

I assigned a smaller range of addresses to the DHCP server pool, from 192.168.2.5 through 192.168.2.15, leaving numbers 2, 3 and 4, and above 15 available for static assignment.  The DHCP server can assign its pool of addresses for a set amount of time ranging from zero time to forever.  This setting, together with the size of the assignment pool, determines how many addresses may be available at a given time.

So now I have the gateway, the netmask, and a range of addresses from which to choose a static IP address.

I need to gather the two DNS servers my ISP has provided me, from my modem's admin page.

I point my browser to 192.168.0.1 and obtain the DNS addresses provided there.  This page, too, should be secured by a password.

The Linux command ```
ifconfig
``` is not quite the same as the Windows ipconfig, but it provides a pile of information including your current IP address, netmask and gateway.

As I recall,though, there was no information for eth0, my ethernet connection; instead, I saw:
```
~$ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9640 (9.6 KB)  TX bytes:9640 (9.6 KB)

~$
```
The device **lo** is the localhost device.  Every computer has the IP address of 127.0.0.1, and it is the address of itaelf.  I cannot visit your 127.0.0.1 because if I go to that address I will be looking at my computer instead.

I need to run from the command line (ALT-F2): ```
gksudo gedit /etc/network/interfaces
```
Enter my password and then the Text Editor will launch with root privileges, loaded with the interfaces file, ready to edit.

There I add to the bottom of the file:```

auto eth0
iface eth0 inet static
address 192.168.2.204
netmask 255.255.255.0
gateway 192.168.2.1

```

Next, I wanted to add the primary and secondary Domain Name Servers, or DNS, that are provided by my ISP, but the tutorial I saw to do this only listed one nameserver as in:```

nameserver 234.56.789.10
```
```
 gksudo gedit /etc/network/resolv.conf
```
is where this nameserver should be listed.  Being unsure how to list the second one, I went instead into the GUI.

Go to **System > Administration > Network**, and in Network Settings go to the DNS tab.  At the bottom just right of Help is an icon button to be clicked before entering your password to make changes.  Too bad the words, "Click to make changes" are not clickable, nor is there a tool tip for the icon.

Click Add button and overwrite the highlighted text with your desired IP address.  Click outside of the newly added line to set it, then click Add again and add another.

There I already had 192.168.2.1 listed as a nameserver.  So I added my nameservers as numbers 2 and 3.  Next I had to click the image to lock my changes.

Now to update the system with the new settings, I was instructed to go in the Terminal and type ```
sudo ifup eth0
```
or to restart the computer.  The ifup instruction did not cut it for me.

Better instructions were provided by a commenter, to enter ```
sudo /etc/init.d/networking restart
```
then open a fresh browser window and see if you have access to the Internet.

**System > Administration > Network Tools** or command line ```
ifconfig
```
will display the new IP address settings on your computer.

Advantages to having a fixed IP on the network include:

A Web server at a fixed address in your internal network; 

Ability to set up port forwarding to send traffic to the proper computer on the network.

---

