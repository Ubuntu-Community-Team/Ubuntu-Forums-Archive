---
title: "New to VPN.... looking for guidance"
date: 2010-06-15
forum: Server Platforms
---

### Post by rwslippey on 2010-06-15
Hello forum, once again I look to your expertise...

I am in the process of setting up a few servers.   First being the obvious LAMP... a second being another LAMP and Samba server. 

The 2nd server being my LAMP and Samba server I want to protect more than the open LAMP , the open lamp is going to be a public website.. the 2nd server , I'll call my mini intranet... I'm hosting a opensource web accessed accounting program on it and using it for file storage. 

I would like to be able to access the intranet box from outside my network, but want it secure, for obvious reasons... I'd like to go with VPN, which should also give me the ability to access files over the VPN, through samba. 

I've set up a vpn before however it is very vauge...

question is    PPTP or openvpn... or any others... I'd prefer to use the "soemthing you have and soemthing you know" theory..  ie; a certificate on the client with a password   vs  just username and password...  anyone have any insight?

Thanks again

Rob

---

### Post by spynappels on 2010-06-16
Have a look at OpenVPN, there are quite a few Howto's on the net and if you need help, just ask and I'll try to answer any questions.

Just for the record, I use OpenVPN to do exactly what you are proposing.

---

### Post by rwslippey on 2010-06-16
Talk about timing...

Was just coming to change my post here and say that I have decided to use openvpn however I am having some issues getting it setup. 

I used this tutorial [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) 
to configure openvpn and am able to make connections.. 

Now I have an issue. The first issue is, I can connect to the server running my openvpn server, however I can't connect to any other devices on the network.

I'm assuming its a config issue... Their is a point in the config file that I'm a bit confused about...

```

server-bridge 192.168.1.10 255.255.255.0 192.168.1.100 192.168.1.110
push "dhcp-option DNS your.dns.ip.here"

```

server bridge ... I currenttly have my network set for 10.66.77.X   and the subnet mask as 255.255.255.0 ... I'm not sure what I should enter here..

additionaly for the dns, I'm not sure the entry here as I have no local DNS , and only have 3 servers max so thus don't beleive I need one.

Appriciate your response and you help...

Rob

---

### Post by paulisdead on 2010-06-16
Those lines look like this on my home setup
push "dhcp-option DOMAIN mydomain.com"
push "dhcp-option DNS 192.168.0.2"

Where mydomain.com, is my actual domain name.  The domain line is unnecessary, but nice to have, so you can access machines with the same domain suffix without typing it out each time.

What DNS server do the clients on the LAN get from dhcp?  It could be your router works as a DNS server as well, and you could use that IP.  If you're running a company network, I'd probably throw bind9 on one of those 2 machines, and use it for internal DNS and push that in openvpn.  You might want to run your own dhcp server on that box too, so you can map your computers mac addresses to IPs.  Essentially giving them static IPs only while in the office, in one central configuration.  Then your users don't have to change settings when they take their laptop home or to the coffee shop, since it's still dhcp.  Also, make sure the IPs you allow the VPN to use aren't in the general lease pool for your DHCP setup.

Forgot about the server bridge.  The first IP is the internal IP of the VPN server, the second number is your subnet mask (subnet mask is probably right).  Those last 2 numbers, are the range of IPs that will be assigned to vpn clients when they connect.  You see they receive an IP on your internal network, and it's in the range specified there.

So mine looks like this.
server-bridge 192.168.0.2 255.255.255.0 192.168.0.200 192.168.0.210

So my server is on 192.168.0.2, and I have the same subnet mask as you.  A connecting client will get an IP address internally somewhere between 192.168.0.200-210.

BTW I don't think you need to specify a DNS server, but if you don't specify one that's aware of the machines on the network, you'll have to access the machines by IP address.  You could also just put them in your hosts file on the machine that connects remotely.

---

### Post by spynappels on 2010-06-17
Ok, have you set this up in bridged mode rather than routing mode? I find that for me, routing mode works better as I can just use the LAN ips of the servers I'm trying to access. This is because when my client connects to my VPN, the VPN server pushes a route to the client. 
Example:


My home LAN is on 192.168.10.x and my VPN is set up in routed mode. It hands out IPs in the 10.8.0.x range. When I connect to it, my VPN IP will be something like 10.8.0.6 and a route to my home LAN will be pushed to my client, so if I try to access 192.168.10.100 or something, the traffic is pushed through the VPN  to my home LAN. There are some settings which need to be set up to make this work flawlessly, but it works perfectly. You do need to make sure your home LAN is on a non-standard network so you do notget routing conflicts when you are in a remote location.

---

### Post by rwslippey on 2010-06-17
I believe I'm headed on the right path.   curious if I'm able to access samba in routed mode?  I currently have it configured to work in bridged mode.  I'd like to be able to access everything by hostname. Is this all possible with routed mode?

also... I'm up in the air on weather a dns is worth it or not... I currently use dhcp through my router, (10.66.77.X)(local) 

I like the idea of cacheing while browsing and not sure if this would assist hostnames. Had some problems configuring that earlier. Again thanks for everyone's help

Rob

---

### Post by paulisdead on 2010-06-17
I think you can access Samba in routed mode if you specify the IP and share name when connecting, but you won't be able to just browse to the shares.  You'd have to access them like \\serverIP\sharename in windows, and smb://serverIP/sharename in nautilus on Linux.  I'm not positive on this, though.

*edit You can get away without having DNS, and specifying IPs each time you connect if you put the address in the hosts file of the client computer.  In Linux it's /etc/hosts.  I forget where it's buried on Windows, but it does have one as well.  So if you don't have many clients, that might be preferable to setting up a DNS server.

---

### Post by spynappels on 2010-06-17
Don't forget that you can map a network drive in a Windows client using the IP address and share name, and as long as you are connected to the VPN you should be able to access the mapped drive. Not entirely sure if tuis works on a Linux client though........

---

### Post by rwslippey on 2010-06-21
Ok ... I appologies for disappearing for a few days.. got wrapped up in other things.. Got back to this this morning.. and did the math and decided a dns server just isn't work it.. so I scratched that idea.. (although I left it running for caching)   I now have my setup as follows and VPN is the last step

1 physical machine

 3VMS as follows
      intranet    (internal web access and file server)
      web1        ( just a simple lamp for a few websites I have)
      ns          (  not really a name server, but it's got bind on it so what the heck...  it's also goin to run openvpn)

I'll post here how I make out with openvpn... plugging that step in right now...

thanks again for all the help

Rob

---

### Post by rwslippey on 2010-06-21
Okay    got everything working... I modified my hosts file on my winxp machine (the client)... and can connect (in routing mode) to the vpn server, however I can't access samba shares or any of the servers via ip address or host name...

---

### Post by spynappels on 2010-06-21
You have to enable ipv4_forwarding in the openVPN server. I have not got the syntax in front of me, but search for it on the forums and it will be explained for you.

---

### Post by rwslippey on 2010-06-21
I'm thinking it may be a problem all around with some type of ip forwarding... I can't access any of the other servers on http or ssh via ip address either...

looking into the enable this now...

---

### Post by rwslippey on 2010-06-22
ok I've been playing with this for the better part of a day and seem to have messed something up along the way.....  

below is my server config file...
my LAN ip is 10.66.77.X for reference  ... hopfully someone has an awnser... 

```

local 10.66.77.210
port 1194
proto tcp
dev tun
EDIT---- KEY INFO REMOVED ------
server 10.10.10.0 255.255.255.0
push "route 10.66.77.0 255.255.255.0"
ifconfig-pool-persist client-addresses.txt
;push "redirect-gateway"
keepalive 10 120
cipher AES-128-CBC
comp-lzo
max-clients 100
user nobody
persist-key
persist-tun
status openvpn-status.log
log openvpn.log
verb 4
mute 20

```

I'm possative it's something I've overlooked, just have no clue what, and google has failed me in figuring that out... once again thanks for everyones time energy and much appriciated help as I hopfully will soon figure this out...

---

### Post by spynappels on 2010-06-22
This may help, you need to enable ip forwarding in the OS, then it should work. This has to be done on the OpenVPN Server.

[http://ubuntuwiki.net/index.php/Packet_Forwarding](http://ubuntuwiki.net/index.php/Packet_Forwarding)

Hope this helps.

---

### Post by xyepblra on 2010-06-24
Guys, in order to access the web sites banned in China, I bought a subscription for VPN access from a provider I don't mention the name of. So far the service works flawlessly in WinXP running on my VMWare, and the installation was a piece of pie. Service provider does not provide any support for non-Win and non-Mac users, but there were 7 files provided to me and I'm looking for an advise from somebody who has experience in setting up VPN connections using those files:
ca.crt
client.crt
client.key
vpninchina.com FR.ovpn
vpninchina.com FR TCP.ovpn
vpninchina.com US.ovpn
vpninchina.com US TCP.ovpn
Could somebody be so kind as to point me to a howto or a manual describing the set up procedure fo Lucid Lynx? My progress so far is limited to successful installation of OpenVPN module for Network Manager and import of settings from the above-mentioned 7 files. Every time I try to connect to VPN using one of 4 provided connections, Network Manager cannot find a suitable key. Please help, I need this connection badly.

---

### Post by spynappels on 2010-06-24
You will need to edit the ovpn files to point to the location of your .crt and .key files. Then you can open the ovpn file in Network Manager and it will work.

---

### Post by xyepblra on 2010-06-25
> **spynappels said:**
> You will need to edit the ovpn files to point to the location of your .crt and .key files. Then you can open the ovpn file in Network Manager and it will work.Great advise, spynappels, thank you very much!
I didn't pay attention to the last 3 lines in ovpn files, and it turned out I really had to, because those 3 lines were the lines to specify the paths to certificates and key files. Many thanks from behind the Great Wall!

---

