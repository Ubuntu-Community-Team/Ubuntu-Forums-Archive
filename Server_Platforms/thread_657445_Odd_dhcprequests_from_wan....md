---
title: "Odd dhcprequests from wan..."
date: 2008-01-03
forum: Server Platforms
---

### Post by Rizado on 2008-01-03
daemon.log is filled with this:
```
Jan  3 22:55:27 foobar dhclient: DHCPREQUEST on eth0 to 172.20.240.130 port 67
Jan  3 22:55:27 foobar dhclient: send_packet: Operation not permitted
Jan  3 22:55:36 foobar dhclient: DHCPREQUEST on eth0 to 172.20.240.130 port 67
Jan  3 22:55:36 foobar dhclient: send_packet: Operation not permitted
Jan  3 22:55:51 foobar dhclient: DHCPREQUEST on eth0 to 172.20.240.130 port 67
Jan  3 22:55:51 foobar dhclient: send_packet: Operation not permitted
Jan  3 22:56:04 foobar dhclient: DHCPREQUEST on eth0 to 172.20.240.130 port 67
Jan  3 22:56:04 foobar dhclient: send_packet: Operation not permitted
Jan  3 22:56:19 foobar dhclient: DHCPREQUEST on eth0 to 172.20.240.130 port 67
Jan  3 22:56:19 foobar dhclient: send_packet: Operation not permitted

```

eth0 is the internet, so of course it shouldn't be permited. The thing is, the firewall shouldn't even let the requests through should it?

172.xxx is a private use address right? So how can it exist outside my internal lan? (Which uses 192.168.1.0 btw)

These requests have been made from the day the computer was plugged in at the present location. I'm thinking, could it be the modem?
It's some kind of adsl modem, I guess it's set to just pass through everything as I get a ip directly from the isp using dhcp. But the modem shouldn't send any request to the lan side right?

I don't have physical access to anything. Or atleast not very often, I am going to check things out in a while though. But I need to know what I should look for?

EDIT: I added eth1 to INTERFACES in /dev/defaults/dhcp3-server and I don't get the strange requests anymore. But the question remains, what is a private ip doing in what seems to be the internet?

EDIT2: Nope, they're still there. It just took awhile after I restarted the dhcp daemon.

---

### Post by Scipio_Publius on 2008-01-04
hummm...whats interesting about that is I have seen something similar after trying out thchydra (password cracking tool) against a server and then looking at the server logs.  The "foobar" is what catches my attention there.  I am not sure if that is common but thats where I have seen it.  Are you plugged directly into the internet?  
THCHydra does have the capability to spoof its source IP.

---

### Post by HermanAB on 2008-01-05
Anyhoo, your firewall should block DHCP requests coming from the internet.

---

### Post by Rizado on 2008-01-05
> **Scipio_Publius said:**
> hummm...whats interesting about that is I have seen something similar after trying out thchydra (password cracking tool) against a server and then looking at the server logs.  The "foobar" is what catches my attention there.  I am not sure if that is common but thats where I have seen it.  Are you plugged directly into the internet?  
THCHydra does have the capability to spoof its source IP.Well actually I replaced the actual computer name with foobar and also changed the ip somewhat incase someone somehow figure something out from it. 

I normally wouldn't pay any attention to things like these but this network is a bit sensitive.

EDIT: What the heck! I just realized something. It's dhclient making the request, not dhcpd. That must mean that it's the computer thats trying to make a request, not something outside requesting my dhcp server right?

Still... Why a private ip? Also the firewall is set up to not allow incomning traffic from private ips on eth0. I'm starting to wonder if there's something inside the network with that ip? But how will I figure that out?

EDIT2: Have found some things. The computer gets it's ip from the isp by dhcp. After it has made a request on 255.255.255.255 and gotten dhcpack back the other requests stops for a while. I checked dhclient.eth0.leases and found this option:
"option dhcp-server-identifier 172.20.240.130;"
Which is the ip it makes requests to. So is it in fact the isp who hasn't setuped their servers correctly?

---

### Post by MJN on 2008-01-05
Your ISP could well be using a private address range for its infrastructure - it's quite common, particularly for devices that don't require off-net access (DHCP servers being a good example).

Mathew

---

### Post by Rizado on 2008-01-05
> **MJN said:**
> Your ISP could well be using a private address range for its infrastructure - it's quite common, particularly for devices that don't require off-net access (DHCP servers being a good example).

MathewOkay, so is there anyway to override "option dhcp-server-identifier" and set it to 255.255.255.255 (which is broadcast right?) so that my logs aren't cluttered with all that?

---

### Post by MJN on 2008-01-05
Presumably your PC is connected directly to your ADSL modem? Or do you have a NAT router?

If the latter, then your router ought to be issuing IP addresses to your LAN clients.

If the former then your PC obtains its IP address from your ISP's DHCP server. The modem merely passes on the request from your PC.

The 'option dhcp-server-idenitifer' is being set in response to the DHCP assignment, along with your IP address, the IP addresses of your ISP's DNS server, etc. Until you obtain a lease your PC will have broadcast to 255.255.255.255 given it didn't then know who/where the DHCP was. Now it does, hence why it is trying to reestablish a connection (most likely to update the lease).

Describe your configuration/setup in terms of what equipment you've got, network adapters etc, and we can then go about establishing the correct configuration.

You mentioned you're running a firewall. In which case, if your PC is configured to obtain its IP address from your ISP's DHCP server then you should configure it to allow these requests, and the associated response, through.

Mathew

---

### Post by Rizado on 2008-01-05
Okay this is how it looks. This computer is set up as a router for a small network with windows computers. I think there's about 10 clients (Computers, printers and a switch) There are two interfaces on the router computer:
eth0 is connected to a ADSL modem. **WAN**
eth1 is connected to a switch and then on to the rest of the network. **LAN**

I only get one IP from the ISP and get that by dhcp. The ips and everything is clearly from the ISP so the modem must be set to just pass through everything.

There's no dedicated firewall in between the modem and the computer. But I have setup a firewall using firehol on the computer. So it's being used as a NAT router with a dhcp server giving out ips on eth1 and samba as WINS server and some other things.

eth0 make a request on 255.255.255.255 and recieves a IP. Renewal in 1525 seconds...
After that time has gone it starts to send out requests to 172.20.240.130 which is meant to be the ip to the isps dhcp server so that it doesn't have to make a broadcast request right? Only 172.20.240.130 is not a ip that is reachable from me at all.
So I guess what I want, except asking my isp to change their ways (I'm sure they won't) is to override "dhcp-server-identifier" and set it to the real ip of their dhcp server. Or just disable logging. (Very bad idea)

Everything works as it should, just that I can't really find anything out by looking at the logs as there's nothing except dhcprequests.

---

### Post by MJN on 2008-01-05
> **Rizado said:**
> Okay this is how it looks.

Excellent description - thanks.

> eth0 make a request on 255.255.255.255 and recieves a IP. Renewal in 1525 seconds...
After that time has gone it starts to send out requests to 172.20.240.130 which is meant to be the ip to the isps dhcp server so that it doesn't have to make a broadcast request right?Yup - there's no point in broadcasting as it already knows who/where the DHCP server is and if it wants to renew a particular lease it has to return to that same server (usually).

> Only 172.20.240.130 is not a ip that is reachable from me at all.On the contrary. That IP address is on your ISP's network, which you're connected to via your eth0 and your modem. Indeed, you know you can reach it given your DHCP lease came from it (according to the DHCP response details).

> So I guess what I want, except asking my isp to change their ways (I'm sure they won't) is to override "dhcp-server-identifier" and set it to the real ip of their dhcp server. Or just disable logging.Not at all - your ISP is configured correctly. You need to work out why your DHCP requests are failing, and having to be repeated every 10 seconds. 172.20.240.130 *is* the real IP address of your ISP's DHCP server (again, according to the DHCP response).

You mentioned you'd configured your firewall to disallow packets from private IP address ranges. Well, now you know that your ISP uses a private addres, legitimately, for its DHCP server you need to reconfigure that bit of the firewall.

Mathew

---

### Post by Rizado on 2008-01-05
But I get a DHCPACK from 85.X.X.X when the request is made to 255.255.255.255.
My ip also starts with 85 and the gateway is set to a 85 adress too, so is dns :)

I have allowed private ips on eth0 and now pinging the 172 address is allowed but I don't get any response. Will have to wait a few minutes until the lease time has gone out as I don't dare to do anything manually. I'm doing all these things remotely and I don't have physical access for awhile.

I'll be back 19:45 :)

EDIT: Heh, well it worked! "DHCPACK from 172.20.240.130" :P

Thank you for all the help!

---

### Post by MJN on 2008-01-05
> **Rizado said:**
> But I get a DHCPACK from 85.X.X.X when the request is made to 255.255.255.255.
My ip also starts with 85 and the gateway is set to a 85 adress too, so is dns :)

I have allowed private ips on eth0 and now pinging the 172 address is allowed but I don't get any response. Will have to wait a few minutes until the lease time has gone out as I don't dare to do anything manually. I'm doing all these things remotely and I don't have physical access for awhile.

I'll be back 19:45 :)

The DHCP server may well be reachable by two addresses, but if the DHCP response says you should be contacting the private address then that's really what you should look at allowing. Remember, the lack of a ping response unfortunately means little these days.

As for your remote configuration, yep - been there done that and I don't want to sit through getting my girlfriend to reconfigure iptables over the phone again after I locked myself out so I have every sympathy for your wish not to do anything too drastic! ;)

Mathew

---

### Post by Rizado on 2008-01-05
> **MJN said:**
> As for your remote configuration, yep - been there done that and I don't want to sit through getting my girlfriend to reconfigure iptables over the phone again after I locked myself out so I have every sympathy for your wish not to do anything too drastic! ;)

MathewHehe, no way :) Especially not as a key is needed as well as two different passwords :???: I don't even know where I would begin...

> **MJN said:**
> The DHCP server may well be reachable by two addresses, but if the DHCP response says you should be contacting the private address then that's really what you should look at allowing. Remember, the lack of a ping response unfortunately means little these days.Everything works as it should now, thanks again :)

---

### Post by MJN on 2008-01-05
Excellent - that's good to hear.

Cheers,

Mathew

---

