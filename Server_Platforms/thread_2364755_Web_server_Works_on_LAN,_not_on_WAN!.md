---
title: "Web server Works on LAN, not on WAN?!?"
date: 2017-06-27
forum: Server Platforms
---

### Post by Daniel_Clarke on 2017-06-27
I am new so patience and help is VERY appreciated.....

I recently migrate my web server from Ubuntu 14.04 LTS to 16.04 LTS, this was a complete migration from 1 VM to another VM. I copied the files and the databases, I can set my host file on my local desktop and it works fine to view the sites, however when I try to get them from **WAN/Internet** I get HTTP error 500....Did I forget to enable something?

I also have had some issues setting up the static IP on this machine and it seems the network configuration works then doesn't work. Is there a few tests/commands that would allow me to test connectivity other than a ping test?

I can provide any additional information that is required to solve, I just need to know what is needed to help.

Thanks in advance for any and all help.

-daniel

---

### Post by darkod on 2017-06-27
Well...

1. First you need to explain in more detail what kind of issues you had when setting up the IP. Basically setting up an IP in /etc/network/interfaces on ubuntu server is very simple. What happened? If you have networking issues that might be a reason why it is not working from outside although in such case LAN traffic would be affected too.

2. Does the new server have the same private IP as the old one? If not, have you allowed and forwarded the necessary port on your router so that external traffic is handled correctly?

---

### Post by Daniel_Clarke on 2017-06-27
Darko,

Thanks for responding, I should have included more information in my initial post, my apologies. Here is what my current network configuration looks like:

#This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
#Added for Static IP Address
iface eth0 inet static
            address 192.168.200.203
            netmask 255.255.255.0
            gateway 192.168.200.2
            dns-nameservers 192.168.200.251 8.8.8.8

```

It seems some days I am able to use the ping command and other days it doesn't work.....like today. I am not new to computers/servers so this just doesn't make sense it works one day but not the next. Do I have the DNS setup correctly in the config?

The new server does NOT have the same private IP but I have created the proper security policies to allow this traffic in our firewall.

Again thanks for any/all help. I am new to LINUX and appreciate those that take the time to assist.

-daniel

---

### Post by darkod on 2017-06-27
Yes, your config looks correct. Make sure no other device can use .203 on the lan otherwise you can get ip conflict which can produce unexpected behavior. Is .203 out of the dhcp range?

---

### Post by Daniel_Clarke on 2017-06-27
Darko,

Thanks for coming back, I have set the IP  192.168.200.203 on an exclusion list so DHCP would not hand it out to another device. My DHCP range is from 200.1-200.254 so yes it is in the DHCP range. Any other suggestions? I can ping my internal domain controller without any packet loss, however any ping outside of the LAN is 50/50 if it will work or not and usually has at least 70%-90% packet loss...

Thanks

-daniel

---

### Post by darkod on 2017-06-27
Hmmm can it be some issue with the router .2? Is the whole LAN using the same router/gateway?

Instead of running a .1 to .254 dhcp range I prefer leaving small part out of it and use those as static addresses. Exclusions should work, but I trust it more when the IPs are not inside dhcp range. :) That goes for the router/gateway too. It is very important device and I see that according to you its IP is also inside the dhcp range.

---

### Post by Daniel_Clarke on 2017-06-28
Darko,

Ok, I did some testing. If I switch back to DHCP from STATIC in my interfaces config my pings work flawlessly with no packet loss, every time!?! There has to be something going on with my STATIC CONFIG I iwll post it below and then what I am currently using. Could you pleasee look at them and let me know what might be causing the unstability with a static vs dhcp?

[B]My STATIC config that I originally had.
[/B]
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
#Added for Static IP Address
iface eth0 inet static
            address 192.168.200.203
            netmask 255.255.255.0
            gateway 192.168.200.2
            dns-nameservers 192.168.200.251 8.8.8.8

**My Current DHCP config that allowing for connectivity.**

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#Added for Static IP Address
#iface eth0 inet static
#address 192.168.200.203
#netmask 255.255.255.0
#gateway 192.168.200.2
#dns-nameservers 192.168.200.251 8.8.8.8

Thanks

---

### Post by cariboo on 2017-06-28
@Daniel_Clarke, do you have a separate DNS server? As your gateway and dns server have different ip addresses although they seem to be on the same sub net.

---

### Post by darkod on 2017-06-28
Set it to dhcp, reboot it, and then post us the output of:
```
ifconfig
route -n
cat /etc/resolv.conf
```

That will allow us to see the IP it got assigned, the gateway it is using, and the nameservers.

---

### Post by Michael_McKenney on 2017-06-28
When you say it works on LAN but not WAN.  Do you mean you can see the web server from inside your network but no one can get to your domain name from the internet?  When I setup my 4 web sites on a virtual server Apache2.   I had to go to GoDaddy to get the domain names and setup DNS with the IP address to my firewall at my house.   Then, the firewall port forwards port 80 to the web server.

---

### Post by Daniel_Clarke on 2017-06-28
Thank you all for the replies, DARKO, below is an image of the output from the commands you asked me to run. Again everyone, thanks for all your help in getting this sorted out.[URL="http://imgur.com/TIC1dDr"]

http://imgur.com/TIC1dDr[/URL]

@cariboo, Our gateway is our Firewall which is plugged into our switch that all our servers are connected to. One of those servers is our domain controller which is handling DNS.

@Michael_McKenney, I can confirm my Godaddy settings have been updated correctly. Thank you for the suggestion.

-daniel

---

### Post by darkod on 2017-06-28
Yes, according to this your static settings from earlier look ok. The GW is .2 and the nameserver is .251.

While you have the server configured like this with dhcp try pinging the .203 to make sure there is not another device using it:
```
ping -c 4 192.168.200.203
```

Also make sure you have no firewall running (that could block traffic):
```
sudo iptables -L -n -v
```

The policies should be ACCEPT for all three chains.

And I would again repeat my recommendation to use static IPs that are outside the dhcp range instead of depending whether the exclusions are working correctly...

PS. If you want to try ping using only the machine names (not the fqdn) you better add dns-search to your static setup. I am mentioning this for later when you switch again to static setup. I see the dhcp has the search as NASB.local, so in static setup you would also add the line:
```
dns-search NASB.local
```

That goes under the dns-nameservers line.

---

### Post by SeijiSensei on 2017-06-29
> **Daniel_Clarke said:**
> Ok, I did some testing. If I switch back to DHCP from STATIC in my interfaces config my pings work flawlessly with no packet loss, every time!?!

This definitely sounds like an address conflict.  Do you get the .203 address if you use DHCP?  On the server run the command
```
sudo arp eth0
```
and you'll get a list of all the other machines on the network that the server sees.

Another very valuable tool for network diagnosis is [nmap](http://nmap.org/) which is in the repositories.  You can scan the entire network with ping using
```
nmap -sP 192.168.200.0/24
```
(A ping scan does not require root privileges but other nmap scans do.)

---

### Post by Michael_McKenney on 2017-06-29
I was wondering if the port forward IP address was setup wrong.   You need Godaddy to point to your WAN port address on your modem.  Your firewall then sends any traffic on port 80 was going to the wrong box.

---

### Post by Daniel_Clarke on 2017-06-29
All,

Thank you for the kind support, it was definitely a conflict issue. I have no clue how .203 was handed out to another machine. Darko, I really appreciate you taking the time to offer support in the beginning.....Firm handshakes to you mate! Again thank you ALL for your suggestions and helping in getting this resolved.

-daniel

---

### Post by darkod on 2017-06-29
I will say again: static addresses pool outside of dhcp pool + good inventory of assigned static IPs = no headache. :)

Glad you got it solved. You can mark the thread as Solved in Thread Tools above the first post.

---

### Post by Daniel_Clarke on 2017-07-24
Ok this has happen again. Can someone please help me resolve this once and for all? We keep losing connectivity on our web server even with a STATIC configuration. The other issue appears to be even when we set it to DHCP it gets a new address but then if I setup that same IP address as a STATIC IP the server has a very unstable connection (tested using the ping command), if I set it back to DHCP using the same IP the connection is stable and PING works fine?!? Lastly, does Apache or Ubuntu cache IP addresses? It appears the webserver is also able to resolve the web site on all the IP addresses we have had on this machine at one point or another...is there a way to purge or clear cache?

Thanks in advance

-daniel

---

### Post by darkod on 2017-07-24
First, static IPs SHOULD NOT be part of the dhcp range. You saying you are trying the same IP as dhcp lease and as static, points that they are. The dhcp will not avoid assigning an IP just because you are using it as static too. It does not know that.

Design your subnet so that you have enough dhcp range and enough static IPs, and do not mix them.

I am not aware that apache or ubuntu can cache an IP you have used before. Your dns server on the other hand can cache it (have a record for it). Apache could be confused sometimes if you put IPs manually in its configuration, which usually is not done.

The bottom line is, you seem to have very confusing network. Sort that out first before setting up any servers on it, if you want to avoid unexpected results...

---

### Post by Daniel_Clarke on 2017-07-25
Thanks for the reply Darko, I understand what you are saying, however I was just thrown into this and its a production environment so I cant just let it sit while I try to sort out the issues with the network. My other concern is that the only machines that are ever affected by this are my 2 Ubuntu servers, no Windows desktops or servers ever have this issue when we are seeing these problems. Any suggestions?

---

### Post by SeijiSensei on 2017-07-25
I believe we have already made the suggestion you want.  Specify a fixed IP address for the server, and remove that IP from the range on the DHCP server.  The server's address should reside in a part of the address space that you have set aside for static assignments.  No server should ever rely on DHCP for its address.  DHCP was designed to manage the address space for machines that do not need static assignments, i.e., client workstations.

---

### Post by Daniel_Clarke on 2017-07-25
Hey guys, maybe I mis-communicated. I set the machine static, it had some issues so I set it back to DHCP. The DHCP address it was leased I was able to ping and everything was working fine, if I take that same DHCP address and move it outside of DHCP and set it as a static I get inconsistent results from ping and web site availability. I understand the difference between DHCP/STATIC and how to use then accordingly. My issues is the only servers that are having these inconsistencies are my 2 Ubuntu servers, if this was truly a IP conflict issue wouldn't it affect other machines instead of just my 2 Ubuntu servers? 

I am not new to Windows and Windows is good at showing duplicate IP conflicts in logs which I am not finding so this is why my confusion continues.

Thanks

-daniel

---

### Post by darkod on 2017-07-25
The problem is that giving the server a static IP does not mean that IP is unique. If it is part of dhcp range it can already be assigned to a client. Or it may get assigned the next day, or the next.

You need to have static range outside of the dhcp range. If who ever designed the network didn't set it up like that, simply adjust the current dhcp range leaving 10-20 IPs out of it, and after the leases expire those IPs will be your static range. If some clients have them, after adjusting the dhcp range, make those clients renew their IP and they will get another one from the dhcp range leaving your static range free for use.

As for inconsistent results, you can check for IP conflict by powering off the ubuntu server (for a short time) and pinging the IP. If it replies, something else is using it too.

It is very rare to get such inconsistent results and my first suspect is IP conflict, seeing how chaotic your IP assignments seem to be in your network.

Also make sure you are not running any firewall on the servers, that would block traffic. Some people activate it even on private LANs, something that I could never understand. Post the output of:
```
sudo iptables -L -n -v
```

---

### Post by lissa77 on 2017-12-07
Oh really, I don't know about these things !!!
Discussion tells lots of info





Thanks
-------------------------------------------
[SEO Bay Area]("http://www.friscowebsoft.com") | [Web Design Bay Area]("http://www.friscowebsoft.com/web-design-company/")

---

