---
title: "HOW TO: Configure Shorewall on Host Machine for a Bridged VirtualBox"
date: 2008-11-02
forum: Virtualisation
---

### Post by r4e on 2008-11-02
As a general disclaimer, I don't really consider myself to be a shorewall expert, so if anyone sees any problems with my configuration please let me know.

I had a lot of trouble figuring this out and there's not much support material available via Googling, so I thought I'd post my configuration for Shorewall, which allows both inbound and outbound traffic from the bridged VirtualBox guest.

**SETUP BRIDGE**

First, setup the bridged networking with the instructions found here:

[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

Disabling shorewall for this part will make your life much easier, because otherwise it will seem like your bridged connection isn't working when it actually is. I commented out all lines in my /etc/shorewall/policy except the following line I added:

**[COLOR="DarkGreen"]HOST:[/COLOR]** /etc/shorewall/policy
```

#SOURCE    DEST    POLICY     LOG        LIMIT:BURST
all        all     ACCEPT     info

```

**Don't forget to remove that line later, because it effectively disables your firewall.**

Then restart shorewall:

```
sudo shorewall restart
```

**CONFIGURE SHOREWALL**

Once I got my bridge connection configured with both inbound and outbound traffic working, I made the following modifications to my shorewall config files.

**[COLOR="DarkGreen"]HOST:[/COLOR]** /etc/shorewall/interfaces
```

#ZONE   INTERFACE       BROADCAST       OPTIONS
lan     eth0            192.168.1.255   dhcp
bri     br0             192.168.1.255   [COLOR="DarkRed"]routeback[/COLOR]
vbx     vbox0           192.168.1.255   dhcp

```
NOTE: The [COLOR="DarkRed"]routeback[/COLOR] option must be set on the bridge interface or guest outbound traffic won't work.

**[COLOR="DarkGreen"]HOST:[/COLOR]** /etc/shorewall/zones
```

#ZONE   TYPE          OPTIONS     IN OPTIONS     OUT OPTIONS
fw      firewall
lan     ipv4
bri     ipv4
vbx     ipv4

```

**[COLOR="DarkGreen"]HOST:[/COLOR]** /etc/shorewall/policy
```

#SOURCE         DEST            POLICY          LOG            LIMIT:BURST
$FW             lan             ACCEPT
$FW             bri             ACCEPT
lan             $FW             DROP            info
bri             $FW             DROP            info
vbx             $FW             DROP            info
lan             all             DROP            info
bri             all             DROP            info
vbx             all             DROP            info
all             all             DROP            info

```

Remember: Remove the "all all ACCEPT info" line from the policy file, otherwise you may as well not have shorewall installed since all connections are allowed. Also uncomment any of the custom lines that you commented before.

Restart shorewall:

```
sudo shorewall restart
```

**TESTING**

From a web browser on the host machine, you should be able to access apache on the guest machine (assuming you installed LAMP).

[http://192.168.1.200](http://192.168.1.200)

NOTE: The guest IP address depends upon what you configured on the guest OS. Mine is configured as static, since I'm using it as a server:

**[COLOR="DarkGreen"]GUEST:[/COLOR]** /etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

```

And from the Guest OS, try accessing Google:

```

$ telnet google.com 80
Trying 209.85.171.99...
Connected to google.com.
Escape character is '^]'.
GET /index.html

```

If both inbound/outbound connections succeed, then your shorewall configuration should be good to go.

You'll probably want to setup shorewall on the guest machine as well, because this configuration just passes all traffic to and from the guest machine, while still (hopefully) protecting the host machine with the shorewall firewall. You should be able to configure shorewall on the guest machine the same way you would if it were a real machine. I did do some basic security testing with nmap and the firewall does seem to operate as I would expect it to.

Anyway, I hope this saves someone else several hours of troubleshooting.

---

### Post by r4e on 2008-11-08
One more thing that I didn't really mention is that you'll have to modify your /etc/shorewall/rules file. The host IP address is no longer assigned to the eth0 interface. It's assigned to the bridge br0 interface. So your rules have to be modified to accept host traffic to the bridge.

For example, this will accept incoming connections to an http server running on the host machine:

[COLOR="DarkGreen"]**HOST:**[/COLOR] /etc/shorewall/rules
```

#ACTION    SOURCE   DEST     PROTO      DEST PORT(S)
ACCEPT     bri      $FW      tcp        80

```

And of course, restart shorewall after you make the modifications.

---

