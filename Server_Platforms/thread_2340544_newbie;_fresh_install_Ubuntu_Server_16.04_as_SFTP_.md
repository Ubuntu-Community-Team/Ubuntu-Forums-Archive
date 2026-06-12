---
title: "newbie; fresh install Ubuntu Server 16.04 as SFTP server, I can't ping the LAN"
date: 2016-10-19
forum: Server Platforms
---

### Post by bfordz on 2016-10-19
I'm setting up Ubuntu Server 16.04.1 with the OpenSSH package.
I'm very new to Linux so this install and learning commands is going relatively slow.

My goal is, I need to have an SFTP server to dump backup files from our phone system server to. My only option when I run backup is local(which I don't want) or an SFTP server, which I currently don't have "yet".
 
I installed Ubuntu Server 16.04 LTS with the OpenSSH package; which I figured I needed for the SFTP. 

I cannot ping any of the LAN IP's. I can ping my localhost (127.0.0.1) ok, I cannot ping my default gateway, my switch or any other devices on the same LAN.

I won't be able to provide screen shots as my server can't access anything. But I'll do my best to pass along my settings.

Does adding the OpenSSH package have anything to do with my problem?

I'm attaching some pics of my screen for reference to what I have setup.

Any suggestions would be greatly appreciated. I'm a bit lost in Linux. Google and I are gettng to be great friends. I've also downloaded the Ubuntu Server Guide, I've been reading. Not much for troubleshooting though.

---

### Post by steeldriver on 2016-10-19
I don't see how installing the OpenSSH package would affect your ability to ping the gateway

Are you sure there isn't another LAN device that is already using the specified host address? are you sure that it is outside the router's DHCP pool?

Are you sure the gateway address is correct? Can you check it from another machine on the LAN?

---

### Post by kpatz on 2016-10-19
It looks like you have two Ethernet ports, and the active one (enp2s0) isn't physically connected to the switch (it says NO-CARRIER).  Have you tried switching the cable to the other Ethernet jack?

---

### Post by darkod on 2016-10-19
Yes, as mentioned, make sure you connect the network cable to the correct ethernet port.

Then, you seem to be configuring a public IP on the server. Will you have it connected in a way that it can use public IP, or it will be on local LAN behind a router/firewall? Most machines on local LANs have private IPs, not public.

---

### Post by bfordz on 2016-10-19
Thank you for the replies,

> steeldriver                   [INDENT]                              Re: newbie; fresh install Ubuntu Server 16.04 as SFTP server, I can't ping the LAN
                          I don't see how installing the OpenSSH package would affect your ability to ping the gateway

Are you sure there isn't another LAN device that is already using the  specified host address? are you sure that it is outside the router's  DHCP pool?

Are you sure the gateway address is correct? Can you check it from another machine on the LAN?         [/INDENT]
    


No other device should be using this IP address; this box 'was' using this IP for a previous use. All our devices are setup with static IP's so no DHCP, and yes the gateway address is correct.


> kpatz                   [INDENT]                              Re: newbie; fresh install Ubuntu Server 16.04 as SFTP server, I can't ping the LAN
                          It looks like you have two Ethernet ports, and the active one  (enp2s0) isn't physically connected to the switch (it says NO-CARRIER).   Have you tried switching the cable to the other Ethernet jack?         [/INDENT]
    


Yes, I did notice I wasn't getting any link lights (I thought I had them), so I moved the cable over to the other Eth port enp3s0 and changed the network settings to reflect the change.  I'm still getting the NO-CARRIER message.

I also changed it over to DHCP and connected directly to our router, I'm still getting the NO-CARRIER message and I'm not getting an IP address either.


> darkod                   [INDENT]                              Re: newbie; fresh install Ubuntu Server 16.04 as SFTP server, I can't ping the LAN
                          Yes, as mentioned, make sure you connect the network cable to the correct ethernet port.

Then, you seem to be configuring a public IP on the server. Will you  have it connected in a way that it can use public IP, or it will be on  local LAN behind a router/firewall? Most machines on local LANs have  private IPs, not public.         [/INDENT]
    
 

Yes, we use public IP's but they're NAT'd out through our firewall (long story, just have taken the time to switch to private). This server won't have any public presence it's just for backing up our phone system in house.


Is it possible the NIC drivers aren't compatible with Ubuntu 16.04? 
Being a newbie how would / could I go about finding / getting different drivers.

---

### Post by darkod on 2016-10-20
I wouldn't say you have problems with NIC drivers because in my understanding if the OS doesn't have correct drivers to communicate with the NICs it doesn't even show them as present. You should see the correct model/chipset with:
```
lspci
```

Then you can investigate which driver should be used and even check if that module is loaded with:
```
lsmod
```

And as for using public IPs, you say they are also NATed. If that means you don't own this public IP subnet, it is not only bad practice to use them on internal LAN but is also not allowed. Yes, the setup should work but it shouldn't be set up like that in this case.

I would double check connections to the router, try new different patch cables, etc. And make sure you use the correct NIC on the machine. I know you said you tried both, but in reality you should know which one you are using and configure the IP on that one.

Also, is the netmask 255.255.255.0 the correct one to use?

Double check the NICs names with:
```
sudo lshw -short | grep network
```

Make sure you have them right. That's all I can think of right now.

---

### Post by volkswagner on 2016-10-20
I would start by connecting a known good machine to the same router port wit same settings. Perhaps router/firewall isn't configured to allow such a connection.

---

### Post by bfordz on 2016-10-20
darkod,
Thanks for the reply.
Since I'm a newbie, it's nice to get some new commands to learn to see what's going on and what to look at.

I will try those out later.

What I did last night before leaving; I rebooted with Ubuntu Live 10.04 LTS via usb.
I was still connected straight to our router, it took a couple of minutes but it's working and I can get online with it using the same port, different flavor / edition of Ubuntu. 
I also used a different cable that was already plugged into the router, so I'm going to see if that cable is long enough to plug into my switch and reboot to Ubuntu Svr 16.04 and see what happens. 

I also run those commands you gave me.

"I'll be back" hopefully with good news.

---

### Post by bfordz on 2016-10-20
volkswagner,
Thanks for your input reply.

Those same ports, switch and router, have been running Windows without any problems. Shouldn't make any difference just because this is Linux should it?

---

### Post by bfordz on 2016-10-20
I'm online using the Ubuntu Live 10.04. Same box I was trying to get Ubuntu Svr 16.04 to work on.

ubuntu@ubuntu:~$ sudo lshw -short | grep network
/0/100/1c.1/0          eth0       network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2/0          eth1       network     RTL8111/8168B PCI Express Gigabit Ethernet controller
ubuntu@ubuntu:~$ 

I moved the cable from my router over to my switch, changed the network / IP from DHCP to a static IP; the same I was trying to use before with Ubuntu Svr 16.04.
Obviously I can ping my network, I can get online. I'm using that machine currently. 

What I did notice between the two is:
Ubuntu Svr 16.04 recognizes my NICs as enpXs0 (enp2x0 and enp3s0)
Ubuntu Live 10.04 recognizes them as EthX (Eth0 and Eth1) 

Which I understand from reading ver. 16.04 changed how it labels things. The part I find interesting is the two versions label them just the opposite. 

My cable has been in the same port; ver 16.04 says it port 2(?) enp3s0, ver 10.04 says it port 1(?) Eth0. 
 IF port 1 = enp2s0 or Eth0, port 2 = enp3s0 or Eth1.

Am I correct in the way it numbered them?

---

### Post by kpatz on 2016-10-20
While you're on 10.04, run the ip addr command and note the output, especially which interface is which (use the link/ether address, aka MAC address, to determine this).

Then on 16.04, see which interface is which based on the MAC address.  Set up the interface that you have the cable connected to.

16.04's labels should be consistent--enp2s0 will always be enp2s0.  On older versions that used eth0, eth1 etc. it wasn't always consistent from boot to boot which interface would be eth0 and which would be eth1, unless you set up udev rules to force them to be a particular way.

---

### Post by darkod on 2016-10-20
Yes, compare the MAC addresses and that's how you will know.

But I also expect enp2s0 to be eth0, and esp3s0 to be eth1.

---

### Post by bfordz on 2016-10-20
Well, well!
I don't know what changed or what happened but;

I reconnected the Pc to my network switch from my router, rebooted back into Ubuntu Svr 16.04.
I changed my network settings from DHCP back to static with the same IP/subnet/gateway I've been using.

I now have network connections, I can ping my network, gateway, DNS server and [www.yahoo.com](www.yahoo.com) and all respond.

I have even changed back to the original patch cable I was using yesterday. All still works.

I have noticed what is different from yesterday is, IF i move the cable from one port to the other; today I'm getting link / status lights on both ports, configured with an IP or not. Yesterday it was questionable if I'd get lights, especially on the port that was 'not' configured with an IP.

When I lookup the names of the NIC's, I'm getting the same response from both versions of Ubuntu that I've been working with.
 "sudo lshw -short | grep network"

"lspci" , response looks a little different with Svr 16.04 vs Desktop Live 10.04 but both show the same NIC information, Realtek Semiconductor.

"lsmod" , I don't know what I'm looking for there, the reference to "Realtek", my NIC, looked more like sound references (codecs). Then again I don't know how to read that list.

Gentlemen, 
thank you for all your help and suggestions. 
It's a good day, I've learned a few things. 

I may be back, I still have to get the SFTP part working for my backups.

---

### Post by bfordz on 2016-10-20
Ah! Thanks for that reminder to compare MAC addresses. 
I was so wrapped up in trying to figure out why my connections weren't working, in an OS I don't know anything about, to stop and use the basics. Doh! 

Thanks again.

---

