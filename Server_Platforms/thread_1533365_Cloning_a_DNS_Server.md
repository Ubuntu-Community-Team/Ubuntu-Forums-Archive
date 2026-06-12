---
title: "Cloning a DNS Server"
date: 2010-07-17
forum: Server Platforms
---

### Post by [d3v] on 2010-07-17
Hi All,

I am having problems with my DNS host and would like to setup BIND to handle my domains. The problem is I don't want to have to type in all of the entries by hand.

Is there some way I could clone the DNS records from the remote server? I do not have access to the remote DNS server.

Cheers

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
I can't answer your question directly....
but why not use OpenDNS or Google's public DNS (8.8.8.8, 8.8.4.4)?

---

### Post by [d3v] on 2010-07-17
Hi,

I forgot to mention that this is on a remote server that currently has DNS records set up in my hosts DNS server. I can no longer manage the DNS records through their systems so I would like to set up my own DNS server that has the same settings. I will then update my domain names to use this new DNS server.

Cheers,

---

### Post by JohnnyC35 on 2010-07-17
I use dnsmasq to store my IP info

sudo apt-get install dnsmasq

then
sudo gedit /etc/dnsmasq.conf
Replace #resolv-file=
with
resolv-file=/etc/resolv.dnsmasq.conf
 
then
    sudo cp /etc/resolv.conf /etc/resolv.dnsmasq.conf[FONT=monospace]
[/FONT]    sudo gedit /etc/resolv.conf[FONT=monospace]
[/FONT]and then add[FONT=monospace]
[/FONT]   nameserver 127.0.0.1
to the top of the list

I usually have 127.0.0.1, then OpenDNS, and then my provider.
I find OpenDNS to be better.

Doing this should store any websites IP locally. If it's not on your drive then it will goto OpenDNS,and then in my case, my providers DNS.

Hope that helps a bit

---

### Post by Bachstelze on 2010-07-18
If the server doesn't allow you to AFXR the zone files, you're pretty much out of luck, I guess...

@Others: OP wants to setup a DNS server with the same DNS records as an existing DNS server, nothing to do with OpenDNS or suchlike.

---

### Post by [d3v] on 2010-07-18
Thank you for the response. This has actually become a moot point now as my host has overridden my DNS settings with invalid records (simply a wildcard and an invalid mx record).

Cheers,

---

