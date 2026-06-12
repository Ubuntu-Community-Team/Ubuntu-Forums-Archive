---
title: "Problems configuring eth0"
date: 2012-06-03
forum: Server Platforms
---

### Post by leschandrew on 2012-06-03
Okay so I just installed ubuntu server 12.04.  During install, I skipped the network setup and now cannot connect to the internet. Here's what I have tried so far: 

Editing the /etc/network/interfaces file to look like this: 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.2.1

then edited the /etc/resolv.conf file to look like this:

nameserver 208.67.222.222
nameserver 208.67.220.220

Afterwards, I ran sudo /etc/init.d/networking restart

Nothing I have tried has fixed the problem. When I ping anything, it reads "unknown host". Here is my $ route and $ ifconfig output: [http://paste.ubuntu.com/1020821/](http://paste.ubuntu.com/1020821/)

Can someone please help? thanks

---

### Post by sanderj on 2012-06-03
> **leschandrew said:**
> O
address 192.168.0.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.2.1


That's wrong. With a mask like 255.255.255.0, all addresses should start with the three same bytes, so 192.168.0.x for example.

---

### Post by Gyokuro on 2012-06-03
Hi

Your network and broadcast addresses are wrong and they should be:

network: 192.168.0.1
broadcast: 192.168.0.255

---

### Post by SeijiSensei on 2012-06-03
> auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.2.1


The machine itself needs an address in the same IP subnet specified in the network and broadcast parameters.  In your case that defines machines in the range 192.168.1.1-254.  So either this machine should have the address 192.168.1.100 or something similar, or the network parameter needs to be 192.168.0.0.

You're still not out of trouble yet, though.  The gateway parameter tells the machine where to send packets that it has no other route for.  If the machine joins an IP network, it can communicate with all the other machines on that network by broadcasting packets with the target machine's address.  For all other traffic, there needs to be a router *on the same network* to forward the traffic along. Your machine can't "see" machines in 192.168.2.0/24, so the gateway cannot be 192.168.2.1. It needs to be in the same network subnet as this machine.  If the machine is supposed to have 192.168.1.100 as its address, then the configuration would look like:

```

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

where 192.168.1.1 is a router.  If the machine is supposed to be 192.168.0.100, then change the values above accordingly.  The gateway must be in the subnet defined by "network".

---

### Post by leschandrew on 2012-06-03
Thanks everyone for the replies. However, the problem persists. Here's what I now have the /etc/network/interfaces file set to:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.124
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

I tried pinging my router @ 192.168.0.1, but I can't even get a reply from that. Is it maybe a wrong setting with my router? Thanks

---

### Post by sanderj on 2012-06-03
> **leschandrew said:**
> Thanks everyone for the replies. However, the problem persists. Here's what I now have the /etc/network/interfaces file set to:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.124
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

I tried pinging my router @ 192.168.0.1, but I can't even get a reply from that. Is it maybe a wrong setting with my router? Thanks

Are you sure the router is on 192.168.0.1? And are you sure 192.168.0.124 is available? Are you sure the format of the information above is correct (it's not the same as on my ubuntu server 11.10).

So ... a lot of questions. Therefor:

This is what I would do: re-install Ubuntu Server, and in network setup select that your server uses DHCP (so: as a client). Then everything should work. This will take 10 minutes in total or so.

Then, *if* you want your server to have a fixec IP address, go into your modem/router, and somewhere in your modem/router select that the IP address given to your device running ubuntu server, should be fixed / reserved for that device.

HTH

---

### Post by leschandrew on 2012-06-03
yeah i'm sure that is the router's address and 192.168.0.24 is available. I checked to make sure using ipconfig on my Windows desktop. I remember during the install it kept getting errors configuring dhcp, and couldn't set it up for some reason. So i just skipped it. I guess I will attempt a re-install.

---

### Post by leschandrew on 2012-06-03
okay, I am re-installing ubuntu 12.04, and I ran into a network hardware issue. The info I'm getting is that I am missing non-free firmware that my hardware needs to operate. The specific firmware file is: tigon/tg3_tso.bin. It then gives me an option to load the file from removable media. Can anyone tell me where to find it and any steps I need to take to install it? Thanks..

---

### Post by Cheesehead on 2012-06-03
It depends on how you are installing.

Here is the list of packages that include the driver: [http://packages.ubuntu.com/search?searchon=contents&keywords=tg3_tso.bin&mode=exactfilename&suite=precise&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tg3_tso.bin&mode=exactfilename&suite=precise&arch=any)


```
File 	                                                Packages
/lib/firmware/3.2.0-23-generic-pae/tigon/tg3_tso.bin 	linux-image-3.2.0-23-generic-pae [not amd64]
/lib/firmware/3.2.0-23-generic/tigon/tg3_tso.bin 	linux-image-3.2.0-23-generic
/lib/firmware/3.2.0-23-lowlatency-pae/tigon/tg3_tso.bin linux-image-3.2.0-23-lowlatency-pae [not amd64]
/lib/firmware/3.2.0-23-lowlatency/tigon/tg3_tso.bin 	linux-image-3.2.0-23-lowlatency
/lib/firmware/3.2.0-23-virtual/tigon/tg3_tso.bin 	linux-image-3.2.0-23-virtual
/lib/firmware/tigon/tg3_tso.bin 	                linux-firmware
```


You can see that it's in linux-firmware, but also included in all the kernel images.

So you can install linux-firmware, but first it may be easier to try a symlink to the existing file in a different location.

---

### Post by leschandrew on 2012-06-03
okay I got the firmware file installed, however I'm now having a problem configuring the DHCP network. It fails to autoconfigure each time. Not sure what is causing this problem. I am connecting to a router which in turn is connected to a Westell 6100 modem. I just figured out that the modem is doubling as a router as well, which may be messing everything up. does anyone have any ideas? I can include screenshots of both the router and modem configuration menus if needed. Thanks...

---

### Post by sanderj on 2012-06-04
> **leschandrew said:**
> okay I got the firmware file installed, however I'm now having a problem configuring the DHCP network. It fails to autoconfigure each time. Not sure what is causing this problem. I am connecting to a router which in turn is connected to a Westell 6100 modem. I just figured out that the modem is doubling as a router as well, which may be messing everything up. does anyone have any ideas? I can include screenshots of both the router and modem configuration menus if needed. Thanks...

What is the error message you get with DHCP?
What is the output of "ifconfig" after installation?
Does you network & DHCP work for other devices on your LAN?

---

### Post by leschandrew on 2012-06-04
sanderj, the error message is as follows:

"Your network is probably not using the dhcp protocol. Alternatively, the dhcp server may be slow or some network hardware is not working properly".

All other devices in my house work properly on the network. I have windows server 2008 R2 on my server as well (dual boot), and it connects to the internet just fine. As for the ifconfig, I will have to get back to you tomorrow on that since I didn't actually go through with the install once I got hung up on that error.

---

### Post by damunos on 2012-08-26
i know this will sound stupid but do you have the ethernet cord plugged in to slot 2 instead of 1 there is a slot 1 and 2 on ibm xseries and i made this mistake sounds like you have a connectivity issue just like me

---

### Post by kennethconn on 2012-08-26
Realise this is an old thread but seeing as someone else made it current ...
 
Some points to consider:
 
1) Are you sure the interface is eth0?
2) As usual, SeijiSensei provided an informative post on problems with your configuration. It is a good reference.
3) There should (typically) only be one DHCP server on your SOHO LAN - know which device it is and what IPs it is serving up to clients.
4) Devices like servers and printers really should have a static IP address, keep them out of the dynamic IP address pool.
5) An issue like this does not require a re-install and it is just bad advice. If you had a problem opening a spreadsheet file on your computer, would you re-install your OS? Doubt it.
 
You will learn very little if anything by reinstalling the OS and it is not practical in the work environment. Get to the root cause of this now and your troubleshooting skills will be greatly improved. Good luck (unless of course the issue is already resolved)!

---

### Post by leschandrew on 2012-08-26
Hey everyone, i fixed it a couple months ago. There are 4 ethernet ports on the server, and they were miss-labeled. I bought the server used, so I had no idea. Eth0 was actually labeled eth2, so i just plugged in the chord to the right port and I was good to go.  Thanks for the replies.

---

