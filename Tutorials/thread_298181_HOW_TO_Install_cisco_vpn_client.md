---
title: "HOW TO: Install cisco vpn client"
date: 2006-11-12
forum: Tutorials
---

### Post by Laalitha on 2006-11-12
I am a total newbie to linux and ubuntu. After installing ubuntu edgy eft I strugled a few weeks to get the cisco vpnclient 4.8 to work. I couldn't do without it since my campus network required to use it.

I read a few howtos and got it working finally

So here goes

Before doing anything logon as super user. It makes things easy.

FIRST install network-manager-gnome and the pptp plugin
========================================================

You can do this in various ways through synaptic, automatix, or apt-get.

here's the apt-get commands

```

apt-get install network-manager-gnome 
apt-get install network-manager-pptp 

```

When you do this the network manager applet will start to run in your system tray. It has a similar icon to your network monitor icon. And it will appear beside it

SECOND Go and edit the "interfaces" file @ /etc/network
=========================================================

replace

```

iface eth1 inet dhcp
wireless-essid MY_NETWORK 

```

with

```

auto eth1
iface eth1 inet dhcp

```

I assume your wireless network interface is eth1. If not replace as appropriate.

THIRDLY you have to shutdown the network manager and restart. 
=============================================================

here are the commands

```

ps -ef | grep NetworkManager

When you run this command you'll get a result like

root      4295     1  0 00:56 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4329     1  0 00:56 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      7535  7511  0 02:07 pts/2    00:00:00 grep NetworkManager

you have to kill both the 'NetworkManager' and the 'NetworkManagerDispatcher' by running the following commands. (use the relevent pids)

kill -9 4295
kill -9 4329

Then restart application by running the following commands

/etc/init.d/networking restart
/usr/sbin/NetworkManager

```

Now go and left click on the NetworkManager applet icon on the system tray .You should see the available wireless networks with their signal strengths. If you have already connected to a wired lan that will also be indicated by the wired option being toggled on.

(Now if you go thru Network Monitor and check the properties of your eth1 connection you will see that it is not enabled. LEAVE IT THAT WAY.)

FOURTHLY you install the cisco vpnclient 4.8
=============================================

Before doing this you should have linux headers installed. Get this from synaptic. Before doing this get your kernel version by typing uname -r and install the relevent headers

cd to the directory which you unpacked it and run ./vpn_install or whatever the install file you have.

Just follow the installation mostly you can answer yes or enter since the answers to the questions asked are taken by default. This worked for me but it may not work for everybody.

After you've install copy the .pcf file (eg: abc.pcf) relevent to your network into the /etc/CiscoSystemsVPNClient/Profiles directory.

then run the following command to start the vpnclient (you need super user access)

```

/etc/init.d/vpnclient_init start

```

and to connect run

```

vpnclient connect abc

```

That's it if it got connected you should have the following resulting screen

```

root@LSIL-PrecisionM60:/home/laalitha# vpnclient connect abc
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at xxx.xx.x.xxx
User Authentication for msu...

Enter Username and Password.

Username []:
Password []:

```
After you enter your username and password it should continue to give you
```
 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: xxx.xx.xxx.xxx
Server address: xxx.xx.x.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled


```

Now you are connected thru vpn to the network

To disconnect open another terminal and type

```

vpnclient disconnect

```

Most people I asked said to use vpnc or pptp or some other daemon but none were successful for my campus network. But the above procedure enabled me to connect to my campus network

The installation of the NetworkManager was taken from the guide at this link 
[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)
I thank B.Daily for that info. 

Hope this helps some people who have a difficult time with vpn.
Bye

Laalitha

---

### Post by arunsub on 2006-11-15
I tried the steps you have given. I didn't modify the network/interface file since uncommenting the eth1 part might disable the network manager. I have commented out everything in the interface file except "lo" to make the network manager to work. I started the VPN and got the following:
Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xx.xxx
Contacting the gateway at xxx.xxx.xx.xxx (balancing)
User Authentication for XXXXX...

Enter Username and Password.

Username []: xxx
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: xxx.xxx.xx.xx
Server address: xxx.xxx.xx.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled

When I tried to connect to my office URL, it doesn't work. The URL works fine with Windows Cisco VPN. I have firestarter installed. I'm not sure if I have to change anything in that. Any idea?

---

### Post by arunsub on 2006-11-16
I got vpnc to work. Please ignore my previous post.

---

### Post by chatuser on 2006-11-17
I also use vpnc, It's got less functions than Cisco VPN Client but it's easier to configure.

I use it to create an IPSec VPN to a Cisco PIX, and it works like a charm.

I use a parameter to avoid overwrite DNS's on /etc/resolv.conf

---

### Post by hackmeister on 2006-11-22
I got the ciscovpn running pretty easily. When I try to connect to work I get the following:
[I]Secure VPN Connection terminated by Peer.
Reason: Firewall Policy Mismatch[/I]

I'm the first person in my company attempting to connect with the Linux client. I know some of the unix guys are able to get in without issue. I'm thinking the server is configured to allow connections with machines running firewall software and only accepting TCP/IP traffic originating from the VPN. I found a thread on a mac bulletin board with the following:

> I couldn’t use Cisco because I kept getting ‘firewall policy mismatch’ errors preventing connection with Cisco VPN Client 4.0.2 to a corporate network.
It turned out that this error is a fairly common error, according to a Cisco engineer. This occures with the Mac client and the VPN concentrator when the concentrator group is set to "Require Firewall" on the connecting host.
This function (“require firewall”) is available on the Windows VPN client software, but not the Mac client! 

I also found this script at the end of the 4.8 release notes:
[I]# Firewall configuration written by Cisco Systems
# Designed for the Linux VPN Client 4.8.00.0490 Virtual Adapter
# Blocks ALL traffic on eth0 except for tunneled traffic
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

# Allow all traffic in both directions through the VA adapter
-A INPUT -i cipsec0 -j ACCEPT
-A OUTPUT -o cipsec0 -j ACCEPT

# Accept all encrypted VPN Client traffic in either direction on eth0
-A INPUT -i eth0 -p udp -s 0/0 --sport 500 -d 0/0 --dport 500 -j ACCEPT 
-A OUTPUT -o eth0 -p udp -s 0/0 --sport 500 -d 0/0 --dport 500 -j ACCEPT 

-A INPUT -i eth0 -p udp -s 0/0 --sport 4500 -d 0/0 --dport 4500 -j ACCEPT 
-A OUTPUT -o eth0 -p udp -s 0/0 --sport 4500 -d 0/0 --dport 4500 -j ACCEPT 

-A OUTPUT -o eth0 -p udp -s 0/0 --sport 1024: -d 0/0 --dport 29747 -j ACCEPT 

# Block all other traffic in either direction on eth0
-A INPUT -i eth0 -j REJECT 
-A OUTPUT -o eth0 -j REJECT
COMMIT[/I]

It's not clear where this should go. Anyone have some tips? 


I'll follow up with unix guys at work to see if they're running iptables or something comparable. Anyone else run into this?
Thanks in advance.

---

### Post by meng on 2006-11-22
Another vote for vpnc here. It's nowhere near as difficult to set up as the Cisco VPN client, and it won't break across kernel upgrades.

---

### Post by inetd on 2006-12-12
I was having trouble with 2.6.19 kernel.  I found a patch from the net and everything is working again.

[http://www.tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff](http://www.tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff)

---

### Post by SuperMike on 2006-12-13
vpnc is a snap and I prefer that. I slapped together an elegant Python GTK GUI for it, which I dubbed 'gvpnc'. If someone knows how to bundle it into a DEB and make it available in the Ubuntu universe for apt-get, and doesn't mind doing that work for me, please let me know. You can even put your stamp on it as co-author -- I don't care. I just don't have the time to do all that, provide a helpfile for it, etc.

---

### Post by bodhi.zazen on 2006-12-16
Nice How-to

This thread has been added to the UDSF wiki.

[Cisco_VPN_Client](http://doc.gwos.org/index.php/Cisco_VPN_Client)

---

### Post by Dragonbite on 2007-01-31
I've got vpnclient-linux and I'm not sure the right answer for a few of the question it asks.  It fails on the install and I'm thinking it is becuase I'm pointing to the wrong location.
[LIST]
[*]Directory where binaries will be installed 
[*]Directory containing linux kernel source code 
[/LIST]
I get the following error instead
```
Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".

```
Any ideas?

---

### Post by platinummonkey on 2007-02-05
@dragonbite - you can answer yes for default on all questions until when it asks for your kernel source.
 type **uname -r** in the terminal. now check synaptic package manager by searching: the version (ex. if you got "2.6.17-10-generic" from the last commande then type in "2.6.17-10 headers"). Make sure the correct headers are installed (on edgy they should be there if you installed fresh). If they are installed yay! now you gotta find them, click on the correct one, it usually has a path for the spot it would install if it wasnt installed. probably /usr/lib/.... or /lib/modules/...  mine happened to be /lib/modules/2.6.17-10-generic/build.
now the cisco installed default may or may not be the correct path, you just need to make sure that you can find: "/path to your kernel version/kernel version/build" that will most likely be the correct source headers to install.
hope that helps. i installed cisco on my laptop and it was a pain, and now that i upgraded it no longer works, so ive decided to try vpnc instead from what ive heard.

---

### Post by Flatline-kun on 2007-02-06
Okay...I've installed the Cisco client, and it seemed to install okay, but I cannot seem to connect to the VPN. This is the output I get:

```

Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xxx.xxx
User Authentication for XXXXXXXXX...

Enter Username and Password.

Username []: XXXXXXXX
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.
Secure VPN Connection terminated by Peer.
Reason: (Reason Not Specified by Peer)
There are no new notification messages at this time.


```

What could the problem be? I can connect to this VPN in Windows no problem, and copied the .pcf file directly from the Windows client. The settings are all the same as in the Windows client,  but that particular error message (Reason Not Specified by Peer) isn't helping!

Thanks,

Flatline

---

### Post by platinummonkey on 2007-02-06
hmm, well, i assume it has to do with the pcf configured for windows settings that when registering with the vpn services they do not match and would reject you, but before i say thats what happened, im going to experiment on my dual boot laptop on my schools wireless network, so give me a day or two and ill tell you what ive figured out. :)

---

### Post by platinummonkey on 2007-02-07
well, after quite a bit of testing and even using vpnc and kvpnc (which isnt really much different) with the same settings and even tweaking the settings... I've got nothing :( anyone else have any ideas, im still going to try as many things as i can, but help would be most appreciated :P)

---

### Post by Flatline-kun on 2007-02-07
I actually think I may have figured it out. I think they have their Cisco server set up so I cannot connect from a non-windows client. I found a post elsewhere that mentioned something about the server detecting the type of firewall you are running, and the non-windows clients (vpnc included) cannot emulate it. That kinda sucks too because the VPN is now the ONLY reason I have to not erase my Windows XP partition. :( 

Thanks for the help though!!!


Flatline

---

### Post by hackmeister on 2008-03-18
It was the VPN server configuration that was the problem. The VPN admin finally configured the VPN to allow non windows clients. I can now successfully connect to my job's VPN via Linux. It only took 2 years of badgering for them to do it. Within 24 hours I deleted the last Windows partition on my systems. My house is officially windows free!! Good riddance! Life is good.

---

### Post by dcstar on 2008-03-21
Anyone using the 64 bit kernel needs to patch the Cisco software so it can compile, here is a link on how to do this:

[http://ubuntuforums.org/showpost.php?p=4556713&postcount=2](http://ubuntuforums.org/showpost.php?p=4556713&postcount=2)

---

### Post by hackmeister on 2008-04-30
HH (and all distros with kernel => 2.6.24) net to patch the CiscoVPN source prior to compiling the modules. This worked for me:
[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/](http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/)

---

### Post by JamesR404 on 2010-11-04
Thank you for this thread! 

I see there are many votes for vpnc, and to be honest, if it's easier then I rather do that, as the instruction for the Cisco VPN seems rather daunting.

But, the big question, would we be able to connect with vpnc to a Cisco VPN using a PCF certificate?

Guess I'll just try and see =D

---

### Post by simarjeet_bhasin on 2011-09-16
Hi all,

I am totally new to the linux world and chose ubuntu 11.04 for the work, installed it on pendrive to try instead of complete install, so that i donot loose my work. now i need a VPN Client installation, and even after going thru all this, am still not able to get it to work.

Any help would be much appreciated. or if am totally messed up by trying it from pendrive,i can clean install it on an alternative HDD for trial.

:confused:. PLEASE HELP.

Thanks.

---

### Post by Ancanus on 2011-09-22
The following blog has all the necessary shell commands for installing Cisco VPN Client on Natty Narwhal (Kernel: 2.6.38-11-generic).

It's in german, but the installation commands are in universal shell code.

```
Installation vpnclient für Linux 2.6.38+

Cisco-Archiv herunterladen
# wget http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.02/vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz

Patch für Linux 2.5.38+ herunterladen
# wget http://www.fseitz.de/download/vpnclient.patch-2.6.38

Cisco-Archiv entpacken
# tar xvzf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz

Ins vpnclient-Verzeichnis wechseln
# cd vpnclient

Patch anwenden
# patch <../vpnclient.patch-2.6.38

Cisco Software kompilieren
# make

Cisco Software installieren
# ./vpn_install

SOURCE: http://fseitz.de/blog/index.php?/categories/27-Cisco-VPN-Client
```

(I think the installation breaks if you upgrade to Oneiric (Kernel: 3.0, so you may want to hold that until we get another workaround.)

---

### Post by dccarson on 2011-10-15
Yes, I can confirm that these instructions do not work for Ubuntu 11.10 (oneiric ocelot).

The kernel module builds successfully, but when I try to load it:

[SIZE="2"](0)root@eagle:~# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/3.0.0-12-generic/CiscoVPN/cisco_ipsec': -1 Invalid module format
Failed (insmod)[/SIZE]

I only started using the Cisco client -- back when I was still on 11.04 -- because the vpnc client disconnects every 30 minutes or so.  So, I found these instructions and got the Cisco client working great with 2.6.38 kernel.  Now I'm back to using vpnc.  It works but will, I suspect, continue to disconnect.

The problem with vpnc, I think, is that it does not handle rekeying requests, and so times out.  Hopefully, vpnc is fixed and supports rekeying now -- we shall see.  If not, then I'll have to wait until someone fixes this insmod problem with the Cisco client.

Thanks,
David

---

### Post by d4m1r on 2011-10-15
Just a note that after installing vpnc you have to restart network-manager to be able to connect to a specified VPN (ex: if you imported a .pcf) in 11.04. Not sure if it's a bug or not, but I couldn't connect to the VPN entry I created until I did that (clicking on the VPN did nothing).

Does anyone have a straightforward guide on how to compile the Cisco client for linux? I am using vpnc on 11.04 (32 bit) but am getting disconnected every hour or so...

---

### Post by dccarson on 2011-10-18
> **d4m1r said:**
> 
Does anyone have a straightforward guide on how to compile the Cisco client for linux? I am using vpnc on 11.04 (32 bit) but am getting disconnected every hour or so...

The instructions in the post before mine (#21) worked perfectly for me under Ubuntu 11.04.  Not sure why you are getting disconnected every hour.  That is precisely why I went away from vpnc and started using the Cisco client.  

However, as I said before, the instructions do not work with 11.10.  It compiles fine, but will not load the module.

---

### Post by devlindeboree on 2011-11-08
anyone find a solution for this on 11.10?

---

### Post by d4m1r on 2011-11-08
2 small updates:

1)to stop random disconnect, disable "dead peer detection" (google it, or if you are using 11.04, its a simple UI check box when configuring the VPN connection

2)to stop the refresh issue when connected to a remote system (desktop refreshes every time you minimize/delete something), do not use a wallpaper. It is annoying how such a trivial thing forced me to wait 2-3 seconds every time something on my desktop refreshed but...Note - I was connecting to a Windows XP system and with the plain blue background everything refreshes instantly.

---

### Post by airmid on 2011-11-17
Don't know if this was solved but this is how I got it to work on 1.10 64-bit. I've been running cisco vpn client for about 4 years now and every new release it have to re-install it. You do need a patch though at the following website:

[https://nowhere.dk/articles/installing-cisco-vpn-client-on-ubuntu-11-10-oneiric-ocelot](https://nowhere.dk/articles/installing-cisco-vpn-client-on-ubuntu-11-10-oneiric-ocelot)

Then I had to remove vpnclient directory completely and start from scratch:

# sudo rm -r vpnclient

The next steps is to assure I have a good copy of my builds for 3.0.0-12

# sudo apt-get install --reinstall linux-headers-`uname -r`
# sudo apt-get install build-essential

Then do the install from scratch

# sudo tar -xzf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz
# cd vpnclient
# wget [http://www.fseitz.de/download/vpnclient.patch-2.6.38](http://www.fseitz.de/download/vpnclient.patch-2.6.38) <-- download patch
# patch < vpnclient.patch-2.6.38
# patch < vpnclient_linux3.0.diff   <--patch from above website
# sudo ./vpn_install
# sudo /etc/init.d/vpnclient_init start

Started up and I'm rockin and rollin.

---

### Post by d4m1r on 2011-11-17
> **airmid said:**
> Don't know if this was solved but this is how I got it to work on 1.10 64-bit. I've been running cisco vpn client for about 4 years now and every new release it have to re-install it. You do need a patch though at the following website:

[https://nowhere.dk/articles/installing-cisco-vpn-client-on-ubuntu-11-10-oneiric-ocelot](https://nowhere.dk/articles/installing-cisco-vpn-client-on-ubuntu-11-10-oneiric-ocelot)

Then I had to remove vpnclient directory completely and start from scratch:

# sudo rm -r vpnclient

The next steps is to assure I have a good copy of my builds for 3.0.0-12

# sudo apt-get install --reinstall linux-headers-`uname -r`
# sudo apt-get install build-essential

Then do the install from scratch

# sudo tar -xzf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz
# cd vpnclient
# wget [http://www.fseitz.de/download/vpnclient.patch-2.6.38](http://www.fseitz.de/download/vpnclient.patch-2.6.38) <-- download patch
# patch < vpnclient.patch-2.6.38
# patch < vpnclient_linux3.0.diff   <--patch from above website
# sudo ./vpn_install
# sudo /etc/init.d/vpnclient_init start

Started up and I'm rockin and rollin.

Does that give you an interface or do you have to add address etc via command line?

---

### Post by airmid on 2011-11-18
Once you got the vpn up and running, put your profile or .pcf files in /etc/opt/cisco-vpnclient/Profiles/ directory and to connect issue the following command:

# vpnclient connect *profile_name*

To disconnect

# vpnclient disconnect

If you just type:

# vpnclient

It will give you a help menu.

---

### Post by d4m1r on 2011-11-18
> **airmid said:**
> Once you got the vpn up and running, put your profile or .pcf files in /etc/opt/cisco-vpnclient/Profiles/ directory and to connect issue the following command:

# vpnclient connect *profile_name*

To disconnect

# vpnclient disconnect

If you just type:

# vpnclient

It will give you a help menu.

vpnc is basically the same thing...however, regardless of what I use, my VPN seems to create the tunnel (shows it connects "successfully") but then I can't ping any internal IPs, access any internal sites, access my PC thro RDP, etc:(

---

