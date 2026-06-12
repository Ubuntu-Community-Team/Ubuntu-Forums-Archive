---
title: "Wireless stopped working about 4 weeks ago"
date: 2007-10-14
forum: System76 Support
---

### Post by ajlewis2 on 2007-10-14
Actually I have been able to connect with an outside router, but not the one I'm supposed to be using.  It was connecting very nicely until about 4 weeks ago--maybe more.  The connection is fine on my desktop machine with an atheros card.  

On the Darter laptop I have Feisty installed since it came out and have Kubuntu-desktop also installed.  I have been using network manager.  I have tried wifi-radar as well, trying to get the connection.

It seems to find the router, but does not acquire an IP Address. The router is upstairs and as I said, I connect with my desktop.  

What steps should I take to track down the problem? I'm guessing this is because of some upgrade that took place a while back since nothing else has changed.

---

### Post by thomasaaron on 2007-10-15
We've not had any reports of upgrades hosing wireless on Darters (or anything else for that matter). It is probably either a configuration problem or a proximity issue.

How strong is the signal you're seeing?
Can you give a little more detail on your configuration with the router?

Also, can you post the output of:
cat /etc/network/interfaces

---

### Post by ajlewis2 on 2007-10-17
1. How strong is the signal you're seeing?

I guess iwlist scan will show that.  I'm not sure what I'm looking for; so here is that output for the two open available connections:
```
       Cell 01 - Address: 00:E0:98:DE:73:D1
                    ESSID:"04Z412556244"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

          Cell 02 - Address: 00:13:10:E5:5D:E3
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

2. Can you give a little more detail on your configuration with the router?

Probably not.  I don't have access to either of them. I do have permission to connect to the  "04Z412556244".  I don't even know where "linksys" is.  Here is the iwconfig from each.  First from my desktop where I am not using network-manager.  By the way, I did try a Gutsy disk last night and cannot connect from the desktop to "04Z..." but could connect with "linksys"  I am using a simple entry in /etc/network/interfaces on the desktop along with dhclient.  

Desktop iwconfig: 
```
wlan0     IEEE 802.11g  ESSID:"04Z412556244"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:DE:73:D1
          Bit Rate=54 Mb/s
          Power Management:off
          Link Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Desktop interfaces file which also works using essid "any":

```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

auto wlan0
iface wlan0 inet dhcp
   wireless-mode managed
#   wireless-essid any
  wireless-essid 04Z412556244
```

3. Also, can you post the output of:
cat /etc/network/interfaces 

The desktop is above.  Here is the laptop interfaces.  You will see I have everything just about commented out.  I tried connecting with using dhclient with the various essids and could connect with linksys, but not "04Z..."  When I try to connect to the latter with network manager, it fails to obtain the IP address (58% mark) and after a while connects to linksys.

interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
#address 127.0.0.1
#netmask 255.0.0.0

# The primary network interface
#Comment out the next 4 lines when not wanting to use home dsl
#iface eth2 inet dhcp
#wireless-mode managed
#wireless-essid 04Z412556244
# wireless-essid linksys
# wireless-essid any
#auto eth2

```
iwconfig while connected to linksys:

```
eth2      IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:E5:5D:E3   
          Bit Rate:5.5 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=-78 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2948   Missed beacon:0
```

I notice the protocols are different--one is g and one is b.  I would say there was something on the router that allows only my MAC address in, but that was not the case four weeks or so ago when I was connecting to it and I don't think he has made changes without telling me.  Then there is the fact that the desktop does not connect with network manager to that router using Gutsy LiveCD, but does connect to linksys.

---

### Post by thomasaaron on 2007-10-17
OK, here is what I'm getting from this:

**Computer  **                        **04Z412556244**                  **Linksys**

Desktop w/o Network Manager            YES                                          ??
Desktop with Network Manager            NO                                           YES
Laptop with Network Manager               NO                                           YES


Two possibilities are:

1. Proximity.
You only have a 21% signal strength on the 04z... router. That's not that good. The desktop's wireless card may be a little stronger. But this is difficult to tell. Signal strength often appears greater in iwlist when there is an actual connection.

2. Configuration.
If the desktop can connect to the 04z... router without Network manager, but not with it, that situation is most likely configuration based.

If network manager if failing to get an ip address, the router is probably rejecting it. I think you need to talk to the IT guy and get the exact specifications you need to configure your router. Since we know the laptop will make the linksys connection, we can be pretty sure it's not a hardware issue.

The IT guy should also check to make sure your mac address isn't getting blocked. Something has obviously changed since four weeks ago. And if you didn't change anything on your laptop, it is probably on his end.

That said, you may also want to carry your laptop to a location closer to the router just to eliminate proximity as a cause.

The common denominator here seems to be network manager and it's inability to obtain an ip address. It either

---

### Post by ajlewis2 on 2007-10-20
Thanks for the advice.  I knew the signal strength was stronger on 04Z.  The iwlist was inaccurate on the laptop.  Now that I have got connected to that router on the laptop, I see 74/100 for the quality.

The way I got connected was to install wicd.  That removed network-manager.  Wicd has a feature for checking hidden network.  I put the known essid in and it found it.  I really have no clue why it is working now, but as you suggested, it surely was a configuration problem.  I'll stick with wicd for now and later perhaps try network-manager again.  

If you want me to do anything to check into it further, just let me know.

---

