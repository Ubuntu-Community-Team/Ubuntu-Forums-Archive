---
title: "Server fresh install issue with netmask"
date: 2013-01-09
forum: Server Platforms
---

### Post by bunglehaze on 2013-01-09
Hi guys, I have been left bamboozled at the datacentre today after moving my server from my office network.

I followed the typical instructions to switch from dhcp to static IP by editing the /etc/network/interfaces, changing the dhcp to static and making sure that the information was correct ie:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 18x.9x.7x.1xx
******* netmask 255.255.0.0
        network 18x.9x.7x.x
        broadcast 18x.9x.7x.2xx
        dns-nameservers 18x.9x.7x.2xx 18x.9x.7x.2xx
```

I restarted networking and tried to ping Google - nothing. looking at the output of ifconfig I am getting netmask of 255.255.255.255. Both myself and one of the guys at the DC have tried a number of ways to correct this but cannot see how or where this is being set.

In the interim (after about an hour of to-ing and fro-ing) we managed to command ifconfig to use the correct subnet mask required but it will not stick after a reboot.

```
sudo ifconfig eth0 18x.9x.7x.1xx netmask 255.255.255.0
```
and
```
sudo route add default gw 18x.9x.7x.2xx
```

allows us to temporarily get the server using the network correctly

Looking at a few pages in Google and people suggest that a dhcp client may still be operational and taking over the interfaces control so I checked by doing a:

ps -eF|grep dhclient

and it is indeed still bringing up a process:

1000      3104  2998  0  2345   924   0 14:54 pts/0    00:00:00 grep --color=auto dhclient

Now I cannot remove the dhcp-client as I get a warning about it being a virtual package and I have followed other tutorials about using the kill command on the process - it comes up with no process found.

Now I am tearing my hair out though, for now I am able to shell in remotely to try and fix this from my office but I need to start installing my clients sites ASAP and I cannot do this until I can make sure that on a reboot I am getting the correct networking setup - please help.

Obviously I am limited to what I am able to do remotely but the guys at the DC are being pretty good and will help out if they are around.

We have tried changing the interfaces settings a number of times to barebones settings and to what we currently use with either a networking restart or a full reboot afterwards but nothing seems to change, somewhere within ubuntu the netmask 255.255.255.255 is being set - incidentally though it looks like all the other network settings are correct - just not the netmask.

regards

leigh

---

### Post by koenn on 2013-01-09
couple of things you could look in to:

1- if you have indeed a dhclient installed, you can disable it by  removing its upstart or init script, or by the runlevel links to it

You *should* be able to uninstall it - the warning about it being a virtual package is irrelevant except in that it is also a hint that the package name, which you'll need to do the actual uninstall, is probably a versioned name, maybe something like 'dhcp3-client' 

2- leave out the broadcast and network directives in network/interfaces. You don't need them (they follow from address+netmask) - I've never heard of them triggering a wrong address, and I can't judge if they make sense given your address+mask as you chose to obfuscate them, but i any case, they're not needed, so you can simplify things by removing them

3- I note that the netmask in your /network/interfaces is different from the one you use in the ifconfig statement. Are you sure you're using a correct mask ? 

4- the only place I've ever seen 255.255.255.255 masks, and one of the very few scenarios where they make sense,  is in point-to-point configs, so if "something in Ubuntu" (other than all of the above) is doing this, that most be something related to P-t-P. If this really is a fresh install and you haven't been mucking with tunnels and PtP dial up stuff or anything like that, it's rather unlikely you have any of that sort. Therefore my 1,2 and 3 are probably what you should check first. 


And be careful :-) reconfiguring network settings over a network connection is somewhat risky

---

### Post by steeldriver on 2013-01-09
I don't know how to solve your netmask issue but your grep output is just showing the grep process itself

Just wanted to stop you going down the rabbit hole of looking for some rogue dhclient process

Cheers

> **bunglehaze said:**
> 
Looking at a few pages in Google and people suggest that a dhcp client may still be operational and taking over the interfaces control so I checked by doing a:

ps -eF|grep dhclient

and it is indeed **still bringing up a process**:

1000      3104  2998  0  2345   924   0 14:54 pts/0    00:00:00 [COLOR=Red]**grep**[/COLOR] --color=auto **dhclient**

Now I cannot remove the dhcp-client as I get a warning about it being a virtual package and I have followed other tutorials about using the kill command on the process - it comes up with no process found.


---

### Post by bunglehaze on 2013-01-09
Hi Koenn, thanks for the reply. To clarify a few things.

> 1- if you have indeed a dhclient installed, you can disable it by removing its upstart or init script, or by the runlevel links to it

You should be able to uninstall it - the warning about it being a virtual package is irrelevant except in that it is also a hint that the package name, which you'll need to do the actual uninstall, is probably a versioned name, maybe something like 'dhcp3-client' 

There is no dhclient installed, I checked to see if dhcp3-client was present and it wasn't, the only thing that was showing was isc-dhcp-client and isc-dhcp-common which I also removed but to no avail.

> 2- leave out the broadcast and network directives in network/interfaces. You don't need them (they follow from address+netmask) - I've never heard of them triggering a wrong address, and I can't judge if they make sense given your address+mask as you chose to obfuscate them, but i any case, they're not needed, so you can simplify things by removing them

We tried that too, just IP and netmask and had the same result in every configuration.

> 3- I note that the netmask in your /network/interfaces is different from the one you use in the ifconfig statement. Are you sure you're using a correct mask ? 


The DC Tech was stood beside me and tried setting the netmask to the correct setting (255.255.255.0) the pasted code had the wrong netmask but was also hashed out until we found a way to make the setting stick as it made no difference anyway.

> 4- the only place I've ever seen 255.255.255.255 masks, and one of the very few scenarios where they make sense, is in point-to-point configs, so if "something in Ubuntu" (other than all of the above) is doing this, that most be something related to P-t-P. If this really is a fresh install and you haven't been mucking with tunnels and PtP dial up stuff or anything like that, it's rather unlikely you have any of that sort. Therefore my 1,2 and 3 are probably what you should check first. 

It was a fresh install in the office, I SSH'd in via my phone network to make sure I could access it on the office network and then set the network/interfaces file to the required settings before moving it. Nothing else was done between the install and transporting it - this is what had us all baffled, none of us could see a reason why the 255.255.255.255 mask was being enforced over the correct settings.

As it happens, I lost my shell connection today so it looks like I might just take a trip to the DC tomorrow armed with my Ubuntu install drive and do a fresh install again in-situ unless I can figure this out beforehand. I would obviously prefer to know what happened in the first place though to avoid it happening again.

regards

---

### Post by koenn on 2013-01-09
Yeah, it's weird. Never heard or seen anything like that.

As you're going to do an install in the DC, you can do manual network config with the correct settings during the install, so I think it's unlikely this issue will show up again (unless you happened upon an install CD with buggy network software ?) 


I'm wondering if the phone connection played a role in this, but I can't really think of any scenario's that would cause something like what you describe. 



When I set up  a server in location different from the network where it will be deployed, I usually set it up with manual networking during the install, then make two copies of the interfaces files (interfaces.HERE, interfaces.THERE) so I can easily switch between the two configs by copying one of them to network/interfaces.
You can even test the "THERE" config while still HERE, by -say- giving a laptop a "THERE" address and see of it can connect to the server. Deploying it is then just a matter of putting the THERE config in place and rebooting the machine. 

Speaking of which, i prefer a reboot over simply restarting networking, just to make sure everything survives a reboot correctly.
Did you at any time try a reboot with a correct config ? If so, did your system still fall back to that 32 bit mask ?

---

### Post by bunglehaze on 2013-01-09
:D I'm glad its not just baffled me and the DC techs :D

The phone connection I doubt would have had any part in the issue as I was just connecting via shell using my 3G phone connection rather than using a network - just to be 100% sure I could access SSH remotely. The connection was setup using DHCP automatically during the server install - I am not actually sure how I would stop this happening to perform it manually as I cannot remember seeing a manual option.

Re: The reboot. Yes on each occasion a change was made we tried first doing a networking restart and if the setting remained we then did a full reboot.

regards

---

### Post by hawkmage on 2013-01-09
If you have an address of 18x.9x.7x.1xx and you define the network as 18x.9x.7x.x and a broadcast of 18x.9x.7x.2xx indicates a netmask of 255.255.255.0 but you have it set to 255.255.0.0.  This may have odd coincidences.  

Usually I just define the address, netmask and gateway

Try this:
```
auto eth0
iface eth0 inet static
        address 18x.9x.7x.1xx
        netmask 255.255.255.0
        gateway 18x.9x.7x.2xx
        dns-nameservers 18x.9x.7x.2xx 18x.9x.7x.2xx
```

---

### Post by Groodles on 2013-01-10
The only people who can tell you exactly what your settings should be is the network admin for the ISP/Network you're plugging into.  Ask them!

a /24 (255.255.255.255) netmask is perfectly valid just means that the gateway you're connected to is doing the funky stuff on your behalf.

```

# The primary network interface
auto eth0
iface eth0 inet static
        address 1xx.3x.6x.2x
        netmask 255.255.255.255
        broadcast 1xx.3x.6x.2x

post-up route add 1xx.1xx.1xx.254 dev eth0
post-up route add default gw 1xx.1xx.1xx.254
post-down route del 1xx.1xx.1xx.254 dev eth0
post-down route del default gw 1xx.1xx.1xx.254

```

---

### Post by bunglehaze on 2013-01-10
Hawkeye, I mistyped the mask in the ifconfig output which is what I mentioned in the previous post.

Groodles. The settings were fine, I was stood installing the server with the datacentre tech next to me who checked and double checked my server and their side of things multiple times to no avail. 

I went in today armed with my Ubuntu flash drive, a quick couple of buttons pushes here and there and I did a fresh install on site and manually entered the network settings. We are all working now (for now at least, until I break something)

I still have no idea where the 255.255.255.255 came from though...

regards

---

### Post by koenn on 2013-01-10
> The connection was setup using DHCP automatically during the server install - I am not actually sure how I would stop this happening to perform it manually as I cannot remember seeing a manual option.

The option to configure networking manually is not shown by default. I'm guessing one is supposed to use DHCP reservations to assign fixed addresses to servers, rather than do manual configuration.
(But I'm a bit old school when it comes to that)

The option to configure networking manually does pop up if dhcp is unsuccessful (no dhcp server, slow reply, ...) , or if you've chosen to install in "expert mode".

---

