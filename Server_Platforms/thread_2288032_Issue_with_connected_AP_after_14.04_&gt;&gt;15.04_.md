---
title: "Issue with connected AP after 14.04 &gt;&gt;15.04 server upgrade"
date: 2015-07-24
forum: Server Platforms
---

### Post by David_Etcell on 2015-07-24
Hi Everyone,

I recently upgraded my server from 14.04 >> 15.04 to solve some boot issues I was having (mdadm devices not reportinc correctly caused headless to grub prompt)

This is solved, however I am no longer able to connect to the network via a connected access point.

Firstly, it might be easier to show a rough picture of what the network looks like:

[ATTACH=CONFIG]263342[/ATTACH]

The Ubuntu server acts as the DHCP server for all devices.

After the upgrade, dhcpd had updated and had a blank .conf, but I found the backed up old one, and used that to restore the settings.

- All devices now with a fixed connection to the server via the switch are getting an IP and the gateway OK, and can see the internet
- All fixed devices capable of doing so can see the windows shares on the Ubuntu server
- All devices capable of doing so can see the DNLA media server running on the Ubuntu server

The problem now, is that the wireless devices are now reporting 'Unable to obtain IP address', and I am guessing thats because it is making that extra hop into the server.

I am not sure even where to start on this (though admittedly I have only had about a half hour to look at it so far), so I am hoping anyone can suggest anything I might try.

A few things to consider:
- The Ubuntu Server (lets call it 192.168.1.6) accesses the internet via an openvpn connection, meaning local traffic (destined for wireless devices) to/from the adsl modem/ap (lets call it 192.168.1.1) shouldn't behave this way (ie, go through eth0), and traffic through the WAN connection of .1.1 should (ie, go through tun0). Maybe for some reason it thinks everything from .1.1 is tun0 traffic?

- web traffic from devices which are not the Ubuntu server  goes directly to .1.1, and that device establishes its own VPN tunnel if it needs to.

- ufw is disabled

- I have noticed a new problem with Webmin. After maybe 5 mins, when I click anything on the side panel, the body panel just shows null. Refreshing and logging back in fixes this.., for another 5 mins.

- I have copied the configuration from the dhcpd.cond.dpkg-old into dhcpd.conf so if anything has changed, it may be causing problems. the service IS starting though, so I don't think this is the case.

- The server can still be referred to as its hostname (eg, can connect to webmin at [https://MyServerName:20000/](https://MyServerName:20000/))

- I can terminal into the Ubuntu server with openssh (seems better anyway with the annoying webmin problem)

- I haven't checked the resolv.conf.., yet, but I only just thought of it so will be checking that a little later.


Anyway.., anyone have thoughts?

Thanks in advance,

Dave

---

### Post by Bucky Ball on 2015-07-24
I can only help by bumping your thread, but add, and off-topic, that I'm a bit baffled why you would upgrade a server from a long-term support release which is supported for five years, and intended for servers, to an interim release that is supported until January 2016 at which time you will need to upgrade again. Was there a specific reason for the upgrade? :-k

---

### Post by David_Etcell on 2015-07-24
It was a tough decision to be honest, I was having an issue with the server hanging on boot. Sometimes at the grub select screen, sometimes at the ubuntu screen with the 4 red/white cycling dots, but it always seemed to be something with mdadm which I was never able to fix. I hoped updating the version would fix it. It seems to have.., which is great, because there is also a problem in that after the POST sequence, the screen I have near the server reports no signal and turns off. I'm not too worries about THAT one though, because I can still shell in, and I probably just need to go find the grub config file and mess with the resolution setting.

-update-

Managed to stumble about for an hour or so and either solve the problem.., or cause a problem which prevents whatever was causing the problem from manifesting.

Firstly, there were some extra lines in the dhcpd.conf I didn't initiallly notice.

Old 14.04 dhcpd.conf prior to upgrade:
```
ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.201;
        default-lease-time 2400;
        max-lease-time 21600;
        option routers 192.168.1.1;
        option domain-name-servers 192.168.1.1;
}

```

New 15.04 dhcpd.conf after upgrade:
```
ddns-update-style none;
log-facility local7;
default-lease-time 86400;
max-lease-time 172800;
subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.101 192.168.1.251;
        option subnet-mask 255.255.255.01;
        option routers 192.168.1.1;
        option broadcast-address 192.168.1.255;
        option domain-name-servers 192.168.1.1;
        }
ignore client-updates;
authoritative;

```

Keep in mind I have cut out all of the comment lines which make up the bulk of both files. I am concerned about the subnet mask being defined weirdly, I don't know what did that...

I'm not sure it made a difference but I:
```
mv dhcpd.conf dhcpd.conf.bak
cp dhcpd.conf.dpkg-old dhcpd.conf
```

I had a look in my /etc/default/grub and found:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw"
```

After giggling about the fact grub is configured to NOM NOM NOM, I cleared out all the repeating switches and did an update-grub though I wouldn't imagine it matters at all (at least to network problems)


Anyway, after a reboot, all seems fine and dandy! I'm glad because my next idea was to try and set the AP as a DHCP relay, which I've never tried before.

---

