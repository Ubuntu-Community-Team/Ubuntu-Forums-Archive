---
title: "OpenVPN Server, client can't see LAN"
date: 2012-01-03
forum: Server Platforms
---

### Post by JoeGoalie on 2012-01-03
I setup Ubuntu Server 10.04 and installed Zentyal (ebox) on it then setup OpenVPN.  It works in that I can connect the client remotely (that's what I'm on now in fact) and internet still flows.  However, I can not see anything on my LAN.  I still have access to SSH and Zentyal so I hope I can troubleshoot it.  I did check mark client-to-client and I did enable IPv4 forwarding...  Any ideas?  Thanks

---

### Post by JoeGoalie on 2012-01-05
Really, nothing?  I'm sure somebody knows something to point me in the right direction.

---

### Post by SeijiSensei on 2012-01-05
Are you running a script to set up a route to your LAN after the connection is established?  Take a look at the "up" directive for OpenVPN.

You probably need to run this on the client.  Suppose the remote server has a OpenVPN virtual IP of 10.1.1.1, and you're trying to reach the remote's 192.168.1.0/24 network behind the server.  You'd need a script that runs a command like 

```
ip route add 192.168.1.0/24 via 10.1.1.1
```

on the client to tell it how to route packets to the remote network.

Beware that firewalling and other rules may block this connection so be willing to spend some time troubleshooting if it doesn't work right away.

---

### Post by JoeGoalie on 2012-01-05
That's not the issue, but I think you put me on the right path.  In the "how to" I found what you're talking about, but it gets pushed to Windows clients.  I'm connecting with a Windows client.
> 
 Windows clients can accept pushed DHCP options natively, while non-Windows clients can accept them by using a client-side up script which parses the foreign_option_n environmental variable list.
So, I dug in my server's config file and found:
```
push "route 192.168.42.0 255.255.255.0"
```
I forgot I put that into my Zentyal configuration.  I then found this in the how to.
> First, you must advertise the 10.66.0.0/24 subnet to VPN clients as being accessible through the VPN. This can easily be done with the following server-side config file directive:

push "route 10.66.0.0 255.255.255.0"
Next, you must set up a route on the server-side LAN gateway to route the VPN client subnet (10.8.0.0/24) to the OpenVPN server (this is only necessary if the OpenVPN server and the LAN gateway are different machines).
So, it's advertising, but I never setup my router to have that route (I'm not really sure how to do this). Unfortunately, I can't do that from my remote location now anyway.

Could this be my problem?  I also see shares from my server though.  I would think if I'm connected to my server I should at least be able to see my samba shares.

---

### Post by JoeGoalie on 2012-01-06
Again thank you for your help!  I realized I was able to configure my router at home remotely.  I added my OpenVPN server to a static route and it works perfectly now!  Very awesome :D.  Now that I have VPN, Sickbeard, Couchpotato, SABnzbd, and Plex all I really need is a way to do client backups and I've 100% replaced my Windows Home Server 2011. It was crap other than the client backup, and data dedup even for the backups).

---

