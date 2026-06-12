---
title: "OpenVPN Bridge"
date: 2006-04-21
forum: Server Platforms
---

### Post by brentoboy on 2006-04-21
I am trying to setup a network bridge using OpenVPN, Ive got almost everything working, but the bridge.

The certificates are in place, I can connect from an XP laptop using the OpenVPN GUI.  It even hands me an IP address.  But once I connect, everything dies.  I have no network at all.  The server is setup to push the new network connection as the primary connection, so if it doesnt work, then everything is dead for the client PC (the whole idea here is to tunnel my way out of a firewall through port 80).

So, I have the server at home, and it provides an unfirewalled gate to the internet for my laptop so when I am at school, I can use firewalled stuff like FTP, and other potentially "dangerous" protocols.

anyway, back to my point.  I need to bridge the connections in order for the client to see out through the server.  But, when I bridge them, the server cant see the network anymore.

When I got to this point on a windows openvpn server, I just selected the Tap interface and the ethernet interface and said "bridge these" and life was good.  On windows, the two sub-interfaces no longer show up when I "ipconfig" so I have no idea what it did to their IP addresses that made it work.  I just assigned the bridge interface the static IP I wanted to use and the clients worked great after that.

But I cant seem to bridge the network interfaces in Ubuntu (im using dapper--if it matters).

When I search the topic on these forums, I find this as the "key" to getting it to work:
[http://openvpn.net/wiki/Bridged_Mode...n_Debian_HOWTO](http://openvpn.net/wiki/Bridged_Mode...n_Debian_HOWTO)
but, alas, the openvpn wiki is down. so I cant read a word of it.

Here is what I have done so far to form the bridge:

sudo{
openvpn --mktun --dev tap0  //creates the virutal interface
brctl addbr br0  //creates a bridge interface
brctl addif br0 eth0 //adds my normal ethernet interface to the bridge
brctl addif br0 tap0 // adds my virtual interface to the bridge
ifconfig tap0 0.0.0.0 promisc up //I assume this tells it to assign itself an ip
ifconfig eth0 0.0.0.0 up //I have a static IP so I dont know if this does much
ifconfig br0 192.168.2.233 netmask 255.255.255.0 broadcast 192.168.2.255
// that last line assigns ip settings to the bridge
}

When I am done, the tap0 interface has an ip6 address, but not an inet address.

and I cant ping anything anymore, until I use brctl to kill br0, and then life is good again.

anyone have any ideas?

---

### Post by nagilum on 2006-04-22
The standard way in Debian/Ubuntu using /etc/network/interfaces has support for bridged interfaces, you can declare the br0 devive there and just use an 'ifup br0' later on. E.g.:
```
iface br0 inet static
  address  192.168.2.233
  network  192.168.2.0
  netmask  255.255.255.0
  broadcast  192.168.2.255
  bridge_ports  eth0 tap0
```

---

### Post by brentoboy on 2006-04-22
ok,
that sounds pretty good, but how do I make the tap0 interface persist beyond a reboot?
If I add the br0 stats to /etc/network/interfaces then it will need tap0 when it boots up, but it doenst get created until I run

openvpn --mktun --dev tap0
does that persist beyond a reboot? - it shouldnt unless I have it in /etc/network/interfaces - right?

---

### Post by nagilum on 2006-04-22
Ah, it surely won't live beyond a reboot, but you can add a line to the br0 definition in /etc/network/interfaces to create the device automatically:
```
iface br0 inet static
  address  192.168.2.233
  network  192.168.2.0
  netmask  255.255.255.0
  broadcast  192.168.2.255
  bridge_ports  eth0 tap0
  pre-up  openvpn --mktun --dev tap0

```

---

### Post by brentoboy on 2006-04-22
ok, only one problem left:
when I bring up the br0 interface on my server box it cant see my network anymore.

do I need to reinit eth0 and tap0, or should they be up and running first, and then left alone?

does tap0 need to be assigned an inet address?  it looks like it only gets an inet6 address.
--
and, when I reboot, br0 isnt automatically started.  So, ifconfig after a fresh reboot shows eth0 and lo.

how do I get br0 to come up on boot, and also, how do I get the bridge to access my network instead of bringing down the house?
(you have been very helpful so far, thank you)

---

### Post by fdoving on 2006-04-22
[QUOTE=brentoboy]ok, only one problem left:
when I bring up the br0 interface on my server box it cant see my network anymore.

do I need to reinit eth0 and tap0, or should they be up and running first, and then left alone?

does tap0 need to be assigned an inet address?  it looks like it only gets an inet6 address.
--
and, when I reboot, br0 isnt automatically started.  So, ifconfig after a fresh reboot shows eth0 and lo.

how do I get br0 to come up on boot, and also, how do I get the bridge to access my network instead of bringing down the house?
(you have been very helpful so far, thank you)[/QUOTE]

If you give br0 an IP on the local network it should run just fine. AFAIK. 

To automatically bring up br0:
Add this to /etc/network/interfaces:
```

auto br0

```


- Frode

---

### Post by brentoboy on 2006-04-22
So, I added "auto br0" to my interfaces file.
While I was at it, I added "post-up ifconfig tap0 192.168.2.232" too so that all my interfaces would have an ip address on my network.

I rebooted to see what happens after a fresh reboot, but after reboot, ifconfig only reports on eth0 and lo
strangly enough, eth0 has an ip6 address, but no inet address.  

When I try to ping anything at this point, it fails.
That is a good sign, becuase that means that the auto br0 did its job--I now have exactly the same scenario I used to get after I ran "ifup br0"  so we are heading the right direction.

So, I try bringing down my bridge, so I can get online, but it doesnt think it is running.  I opened up the Sytem->Admin>Networking gui and deactivated eth0 and reactivated it to see if that would restore my network, but nothing.

so I ran "brctl show", which reported this:
bridge name     bridge id               STP enabled     interfaces
br0_ifrename            8000.00508dd71e33       no              eth0

so I ran "sudo brctl delbr br0_ifrename" and now eth0 works again, and I can use the web.
---
I guess my only question at this point is:  how do I get the network to function when the bridge is up?

Do I need to reassign ip addresses to the bridged interfaces after I add them to the bridge? or is it best to leave them alone?

Im to the point now where if I could get the bridge to come up with brctl commands, the I could modify /etc/network/interfaces to make it work correctly too.

anyone have any ideas?  --thanks

---

### Post by fdoving on 2006-04-22
Doesn't that happen automagically from the /etc/network/interfaces setup? 

Did you look at [http://openvpn.net/bridge.html](http://openvpn.net/bridge.html) ? 
- Frode

---

### Post by brentoboy on 2006-04-22
I think this was the part I was missing:
sudo{
    iptables -A INPUT -i tap0 -j ACCEPT
    iptables -A INPUT -i br0 -j ACCEPT
    iptables -A FORWARD -i br0 -j ACCEPT
}

so I can see the world now while the bridge interface is up.  I'll play around with it again to see if  I can get it all working together again.

--thanks

---

### Post by brentoboy on 2006-04-22
ok, here is what I did to finally get things running the way I need it...

I completely removed br0 from /etc/network/interfaces

I added a line inside of /etc/init.d/openvpn that calls bridge-start before it does its business.
and I added another line in that same file that calls bridge-stop when the daemon is stopped.

bridge-start and bridge-stop are my modified version of what I got from the openvpn website.  most notably, instead of using ifconfig eth0 0.0.0.0, I used my static ip address for eth0, same for tap0 -- I have no idea if that was necessary.

now, when the pc boots, doesnt load br0 until it starts the openvpn daemon.


I think it would have worked right from the start, except I didnt issue the firewall forwarding commands. I didnt think I needed to, becuase I dont have firestarter running or any other firewall I was aware of.

Thanks for all the help.

---

### Post by nagilum on 2006-04-23
[QUOTE=brentoboy]bridge-start and bridge-stop are my modified version of what I got from the openvpn website.  most notably, instead of using ifconfig eth0 0.0.0.0, I used my static ip address for eth0, same for tap0 -- I have no idea if that was necessary.[/QUOTE]
If you configure bridge devices the interfaces you bind together must not have an IP address, that's why you usually bring them up with ifconfig dev 0.0.0.0 (the /etc/network/interfaces does all this automatically). The IP is assigned to the bridge device, which is the only one you will work with later on, i.e. don't add iptables rules for eth0 or tap0 after the bridge is configured (you can match them with the physdev module of iptables though). Since eth0 appeared after a fresh boot you probably had assigned it an IP address, guess that's what went wrong.
Anyway, good it works now. :)

---

