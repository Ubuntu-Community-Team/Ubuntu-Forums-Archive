---
title: "DNS questions"
date: 2009-08-19
forum: Server Platforms
---

### Post by wvw on 2009-08-19
Hello Everyone

I have configured my Ubuntu 8.04 Server to serve as a pri DNS server using this URL: [http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html](http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html)

It works a treat, but I still have 2 questions.

The first question is regarding setting up DNS for my private WAN. Can I add the IPs and hostnames in my server's resolv.conf file? I do not want the WAN hostnames & IPs be advertised so I do not want to add them into the /etc/bind/db.xxx  files.

The other question I have is regarding securing my server's DNS port. What would be the best way to prevent people from accessing the server on the DNS port? I was thinking of enabling ufw (uncimplicated firewall) and deny telnet to port 53, but I would like to get input from other users to see if they agree or perhaps if they have a better way of securing a DNS server.

TIA
wvw

---

### Post by jocampo on 2009-08-19
> **wvw said:**
> Hello Everyone

I have configured my Ubuntu 8.04 Server to serve as a pri DNS server using this URL: [http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html](http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html)

It works a treat, but I still have 2 questions.

The first question is regarding setting up DNS for my private WAN. Can I add the IPs and hostnames in my server's resolv.conf file? I do not want the WAN hostnames & IPs be advertised so I do not want to add them into the /etc/bind/db.xxx  files.

The other question I have is regarding securing my server's DNS port. What would be the best way to prevent people from accessing the server on the DNS port? I was thinking of enabling ufw (uncimplicated firewall) and deny telnet to port 53, but I would like to get input from other users to see if they agree or perhaps if they have a better way of securing a DNS server.

TIA
wvw

Private WAN? :-)  or you mean, Private LAN? ...

You put your IPs and Hostnames under /etc/bind directory on your DNS server. If your DNS server is well configure, no one will check your IP/Hostname information.

Now, to protect your DNS server (network layer) via ufw, you can do this (I'm assuming you want to connect via ssh also, if not, ignore that line)

```

sudo ufw allow ssh
sudo ufw allow domain
sudo ufw default deny
sudo ufw enable
sudo ufw status

```

---

