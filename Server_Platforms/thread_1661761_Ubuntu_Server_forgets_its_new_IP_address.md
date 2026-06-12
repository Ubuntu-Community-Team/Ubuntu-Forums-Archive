---
title: "Ubuntu Server forgets its new IP address"
date: 2011-01-07
forum: Server Platforms
---

### Post by Titanio Verde on 2011-01-07
Greetings. If this topic already exists, I haven't found it.

When installing this fresh new Ubuntu Server 10.10, I assigned it some IP address. Let's say 1.1.1.1.
Some days later I preferred to give it another address. Let's say 2.2.2.2.
I changed it editing */etc/network/interfaces*. I knew ifconfig method, but I read that it was only temporal.
*ifdown eth1*, *ifup eth1*, *ifconfig* (alone), new address assigned right. Everyone is happy.

I restart the server. ifconfig. IP address: 1.1.1.1. What?!
ifdown, ifup, ifconfig. IP address: 2.2.2.2. ...

Does this mean that the previous network configuration is saved in another file? Where else should I change it? I don't want to depend on init scripts to get the right address every time I power-on the server.


Thank you for reading and replying. For great justice.


**[COLOR="DarkGreen"]Solution:[/COLOR]** Look for the previous IP address in any config file, by *grep -r 'yourIPaddress' /etc/** . In this case, there was an *ifconfig* line in */etc/rc.local* file. Just delete or comment that line with a text editor.

---

### Post by HugoSerrano on 2011-01-07
hi!

Can you post the output of "cat /etc/network/interfaces"

Regards!

---

### Post by Titanio Verde on 2011-01-07
With the numbers I gave before, my interfaces file would be like this (skipping the starting comments, "This file describes blah blah blah"):

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 2.2.2.2
        netmask 255.255.0.0
        network 2.2.0.0
        broadcast 2.2.255.255
        gateway 2.2.1.1
        dns-search myownserver.com
```

This is kind of normal, isn't it?

---

### Post by HugoSerrano on 2011-01-07
it looks ok.

---

### Post by kevinthecomputerguy on 2011-01-07
try this
 
sudo apt-get remove dhcp3-client

---

### Post by kevinthecomputerguy on 2011-01-07
Try this
 
sudo apt-get remove dhcp3-client

---

### Post by kevinthecomputerguy on 2011-01-07
Try this
  
 sudo apt-get remove dhcp3-client

---

### Post by kevinthecomputerguy on 2011-01-07
Try this
  
 sudo apt-get remove dhcp3-client

---

### Post by stlsaint on 2011-01-07
Please post the actual contents of your interfaces file.
Would be best to simply copy/paste contents.

---

### Post by Titanio Verde on 2011-01-10
Is it really important? I copy-pasted the parameters, but I rather to keep some privacy, so I changed the numbers and servername.
So let's just say that I want to change permanently the IP address from 2.2.2.1 to 2.2.2.2.

Anyway, I uninstalled dhcp3-client, as kevinthecomputerguy suggested. It did fix up nothing.

---

### Post by HugoSerrano on 2011-01-10
Do you got graphic environment?

---

### Post by Titanio Verde on 2011-01-10
No. Text only.
Do you think it will be easier to install a desktop and change the address through its control panel?

Yes, it is a way, but there is no other alternative through command line?

---

### Post by kevinthecomputerguy on 2011-01-10
Removing dhcp3-client worked for me.
 
I noticed your conf file is calling too "eth1"
Is it maybe "eth0" that your after?
 
You can see all the interfaces by running 
[COLOR=red]sudo ifconfig -a[/COLOR]

---

### Post by Titanio Verde on 2011-01-11
I'm used to see eth0 in other computers, too. But this computer has got two interfaces: eth1 and eth2. Only eth1 is plugged, and eth2 settings are empty.

---

### Post by HugoSerrano on 2011-01-11
> **Titanio Verde said:**
> No. Text only.
Do you think it will be easier to install a desktop and change the address through its control panel?

Yes, it is a way, but there is no other alternative through command line?

No, keep it without GUI :P

The dhcp3-client is called when you got, in your configuration file:

iface eth1 inet dhcp

As this is not the case, removing the package shouldn't do any difference.

When you boot the server what's ETH1 IP?

---

### Post by Titanio Verde on 2011-01-11
> **HugoSerrano said:**
> When you boot the server what's ETH1 IP?

2.2.2.1, the previous one.
I want 2.2.2.2. So I wrote 2.2.2.2 in */etc/network/interfaces*, as I did show.

Maybe I should search for a file which contains 2.2.2.1 (if there it is any in-file searcher, like in Wind*ws).

---

### Post by HugoSerrano on 2011-01-11
and when you do:

/etc/init.d/networking restart

What's ETH1 IP?

---

### Post by Titanio Verde on 2011-01-11
*/etc/init.d/networking* restart seems to do exactly the same than *ifdown eth1; ifup eth1*
The IP comes to be 2.2.2.2, the desired one.

But, of course, I don't want to get 2.2.2.1 every time I start/reboot the machine.

---

### Post by HugoSerrano on 2011-01-11
have you ever done a script or something similar to change the IP to 2.2.2.1? you may be calling that on boot...

---

### Post by Titanio Verde on 2011-01-11
I know that kind of scripts, but I ask again: is there any CLI way to change permanently the IP?

Scripts in the boot to change the IP every time don't look professional to me. :(

---

### Post by HugoSerrano on 2011-01-11
I'm asking if you don't already have one, doing that!
The professional way is editing the /etc/network/interfaces file...

---

### Post by Titanio Verde on 2011-01-11
Ah... No, I haven't. I just installed Ubuntu Server, a pair of services, tested SSH around, and that is all before trying to change the IP.

Maybe it will be faster to just reinstall Ubuntu. Or another server-friendly distro.

---

### Post by HugoSerrano on 2011-01-11
Keep with Ubuntu Server :-)

You can do a fresh installation, but you will never know what happened! :-P

---

### Post by ripat on 2011-01-11
Post the result of:
```
$ grep '2.2.2.1' /var/log/syslog
```

---

### Post by Titanio Verde on 2011-01-11
> **HugoSerrano said:**
> but you will never know what happened! :-P

Yes, that is the problem. :confused:

---

### Post by Titanio Verde on 2011-01-12
> **ripat said:**
> Post the result of:
```
$ grep '2.2.2.1' /var/log/syslog
```

The only message not related with dhcp3-server is:
```
Dec 22 11:26:47 MyServer dhcpd: No subnet declaration for eth1 (2.2.2.1).
```

That was before giving a full /etc/network/interfaces, as I pasted before.

And every message with the current IP is related with dhcp3-server. No more clues. Maybe I should read carefully **every** log line about boot (every component and service starting, and all of that)?

---

### Post by ripat on 2011-01-12
Your server is hosting a dhcp server (dhcpd). Do you need it? If the other hosts from your network get their ip's from a router, disable or uninstall the dhcpd server and everything should be fine.

If your server is used as dhcp server for the other hosts of your lan, check the dhcpd.conf if there is a rule assigning the 2.2.2.1 to your own machine.

---

### Post by Titanio Verde on 2011-01-12
Yes, being a DHCP server is the first purpose for this machine. But I keep the service stopped while the machine doesn't get the right address. Here it is no other DHCP server giving that kind of addresses.

In */etc/dhcp3/dhcpd.conf* there is no mention about previous nor new IP address. The only uncommented lines are the properties I wrote, lease times, *ddns-update-style none* (by default, I think), and *log-facility local7* (by default, too?).
There shouldn't be any other dhcpd.conf, right?

---

### Post by ripat on 2011-01-12
What you could do for troubleshooting is:

1- check if you have a lease assigned to the server's own mac address. Look for the file dhcpd.leases (/var/lib/dhcp/dhcpd.leases ?)

2- if so it means the the dhcpd is assigning the wrong ip in some way.

3- you could also grep 2.2.2.1 traversing all config files (it can take some time): grep -r '2\.2\.2\.1' /etc/*

4- Analyse (grep) all entries with 2.2.2.1 in syslog and dmesg. It could give you some indication of who's assigning that ip to your server.

---

### Post by HugoSerrano on 2011-01-12
He removed dhclient package, and got "static" at /etc/network/interfaces file. The server should never ask for an IP.

---

### Post by ripat on 2011-01-12
> **HugoSerrano said:**
> He removed dhclient package, and got "static" at /etc/network/interfaces file. The server should never ask for an IP.

I know but somehow a wrong ip gets assigned by some process. The troubleshooting guide lines above can help determining which one.

---

### Post by HugoSerrano on 2011-01-12
Sure. I'm just saying what should not happen! 
I'm also curious about this one! hehe

---

### Post by ripat on 2011-01-12
Could also be a script that ended up in */etc/network/if-up.d/* directory for some reason and that is assigning an IP using the *ifconfig* or *ip* commands.

The recurrent grep that I suggested above should find it. Otherwise have a look into the *if-up.d* and *if-pre-up.d* directories if you can find something "exotic".

---

### Post by chrislynch8 on 2011-01-12
My Two cents

You have two Interfaces, so you should have eth0 and eth1 unless you have manually edited the /etc/udev/rules.d/70-persistent-net.rules

When you issue ifconfig is the MAC address of your configured Interface matching the address stored in the interfaces file is you have it there or in the udev rules file above.

Rgds
Chris

---

### Post by chrislynch8 on 2011-01-12
My Two cents

You have two Interfaces, so you should have eth0 and eth1 unless you have manually edited the /etc/udev/rules.d/70-persistent-net.rules

When you issue ifconfig is the MAC address of your configured Interface matching the address stored in the interfaces file is you have it there or in the udev rules file above.

Rgds
Chris

---

### Post by Titanio Verde on 2011-01-13
And the winner is:
> **ripat said:**
> 
3- you could also grep 2.2.2.1 traversing all config files (it can take some time): grep -r '2\.2\.2\.1' /etc/*

**There was a line to change the address through ifconfig in /etc/rc.local.** Maybe the Ubuntu installer wrote it from the beginning (I didn't do it, I swear).

So I commented that line through Nano, and rebooted inmediately. Now it boots with 2.2.2.2, the right IP address.

Thank you, Ripat and people. I love you so much.
I'm going to put the solution in the first post.

---

### Post by ripat on 2011-01-13
Just out of curiosity can you post that line?

---

### Post by Titanio Verde on 2011-01-13
The usual to change temporarily the address:
```
ifconfig eth1 2.2.2.1 netmask 255.255.0.0
```

---

