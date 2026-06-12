---
title: "retain ip address after reboot while using DHCP"
date: 2005-03-07
forum: Server Platforms
---

### Post by lartan on 2005-03-07
Hi,

I'm setting up a new server using Ubuntu.
Each time I reboot the Server the ip address changes. I use DHCP. I would like to obtain the same IP address after reboot. This is what I am used to on other systems like Windows XP, Mac OS X or Fedora Linux all using dhcp.

So my question is how to obtain the same IP address after a reboot while using DHCP (given that the IP is not given to an other machine during the reboot)

Thanx!!

---

### Post by lartan on 2005-03-07
Sorry for posting this question on the wrong location, can somebody tell me how I can move this post to the server thread?

---

### Post by dewey on 2005-03-07
I believe only moderators can move posts.

May I ask, why do you want to use DHCP to obtain the same ip address?  While this can certainly be achieved, by the use of ip leases and such, it's simpler to set a static ip address.  I believe it's under system tools, there's an entry on your taskbar menu somewhere called "network" Go into the ethernet section, and look for an ip field, simply fill it in with your desired internal ip, and you're good to go.

Sorry I couldn't give you the exact location, I'm on my windows partition at the moment.  Shame on me.

---

### Post by lartan on 2005-03-08
Thanks for the reply,
To answer your question why I like to use DHCP: Because it works fine on other systems like Fedora, so I think it should be possible. (only do not know how..)

I think a static ip would olso be an option. I have a Ubuntu 'custom' installation so without a GUI. So haw can I  configure my system to use a static IP instead of DHCP via commandline?

Arne

---

### Post by alastair on 2005-03-08
The network config is given in the file :

/etc/network/interfaces

see : man interfaces

It is perfectly acceptable to rquest the same IP address from a DHCP server - or have it assign the same IP address to you (via MAC address say). This is something best configured via the DHCP server I think.

For static addressing, by all means stop "dhclient" (or whatever) from running and manually assign an ip address e.g.

ifconfig eth0 down
ifconfig eth0 <ip address> netmask <mask>

e.g.

ifconfig eth0 192.168.0.10 netmask 255.255.255.0

Check with "ifconfig eth0".

Or, in the "interfaces" file :

iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

Adjust to your needs.

---

### Post by Viper12 on 2005-03-09
Another way (my own home network way).......is to just reserve the address you want in the router.
My netgear router is my dhcp server......and its configuration app allows me to reserve addresses for specific hostnames/mac addresses and such.  All my ubuntu boxes here are set up to NFS and cups print share with each other, and the addresses, while dhcp are set in stone on the router itself.  save a lotta dinkin' around. :)

---

### Post by istoyanov on 2005-03-09
I had the same problem -- please look at [http://ubuntuforums.org/showthread.php?t=15057](http://ubuntuforums.org/showthread.php?t=15057)

---

### Post by lartan on 2005-03-09
I have chainged the /etc/network/interfaces file according to the information above. So now I have a static IP adress. The other machines on my network recieve their ip's from my router which includes a DHCP server.
I was not able to configure this router to use the mac address of my ubuntu server to assign the same ip each time (as Viper12 suggests). I think this is because i have a rather old Speedtouche pro DSLModem/router.

Thanx for the information above. 

One question remaining is why a Fedora installation configured to use DHCP recieves the same IP each time while my Ubuntu server does not. The DHCP server is the same (my router) so I suspect it has something to do with the configuration on Ubuntu.
Again, this is only because I like to know why, the static IP resolves my practical problem!!

---

