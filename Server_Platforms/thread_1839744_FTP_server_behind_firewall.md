---
title: "FTP server behind firewall"
date: 2011-09-06
forum: Server Platforms
---

### Post by Belerophon on 2011-09-06
Hi, I have a problem, and I'm hoping you can help me :)

I've set up freeNAS on a machine inside our private network. FTP is enabled and I confirmed it is working for any machine inside the private network.

Now, I have a public IP, which forwards to a specific private IP inside our network, where I have a machine handling everything which connects to the outside world. I think I may call it the firewall.

This is machine [COLOR="Red"]is different[/COLOR] from the freeNAS server. [COLOR="Red"]From that public IP, I only have ports 20 and 21 open[/COLOR]. 

My goal is just to make FTP work from the outside. I think I have to forward ports using iptables, but I can't find the correct commands. Most of the guides I find are for passive FTP, which is not this case, since I'm working only with ports 20 and 21.

Can anyone guide me through the iptables configuration ?

Thanks in advance!
André Cardoso

---

### Post by Dangertux on 2011-09-06
> **Belerophon said:**
> Hi, I have a problem, and I'm hoping you can help me :)

I've set up freeNAS on a machine inside our private network. FTP is enabled and I confirmed it is working for any machine inside the private network.

Now, I have a public IP, which forwards to a specific private IP inside our network, where I have a machine handling everything which connects to the outside world. I think I may call it the firewall.

This is machine [COLOR=Red]is different[/COLOR] from the freeNAS server. [COLOR=Red]From that public IP, I only have ports 20 and 21 open[/COLOR]. 

My goal is just to make FTP work from the outside. I think I have to forward ports using iptables, but I can't find the correct commands. Most of the guides I find are for passive FTP, which is not this case, since I'm working only with ports 20 and 21.

Can anyone guide me through the iptables configuration ?

Thanks in advance!
André Cardoso

To forward ports with iptables you could do something like this

```

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 20 -j DNAT --to 192.168.0.2:20
iptables -A FORWARD -p tcp -i eth0 -d 192.168.0.2 --dport 20 -j ACCEPT

```for each port, obviously substitute the correct interface and internal ip address. In this case 192.168.0.2 was the address of the machine the port is being forwarded to.

---

### Post by Belerophon on 2011-09-06
I've done this:

```

sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 20 -j DNAT --to 192.168.23.5:20
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.23.5 --dport 20 -j ACCEPT
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 21 -j DNAT --to 192.168.23.5:21
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.23.5 --dport 21 -j ACCEPT

```

However, when trying to access my public ip (from outside my private network) using firefox, it never loads the page. Connection times out.
Also, if I do a
```

sudo iptables -L -vt nat

```
i see the packet count changing in the rule that reads "tcp dpt:ftp". But the packet count on the rule that reads "tcp dpt:ftp-data" remains at zero.

---

### Post by Entilza on 2011-09-06
Try ftp'ing through the command prompt manually and see if the connection will eventually connect rather than through browser.  This will also show you if a connection is being made but then timing out.

---

### Post by Belerophon on 2011-09-06
I tried to do a
```

$ ftp PUBLIC_IP

```

But I get a:
"ftp: connect: Connection timed out"

after some seconds...filezilla shows the same behaviour.

---

### Post by Belerophon on 2011-09-06
Don't know if this is important, but most of the guides assume a rather different setup than the one I have here:

- normally I see guides where the firewall machine has 2 interfaces, one connected to the public IP, and the other connected to the private network.
In my case, [COLOR="DarkRed"]I have just one interface, with a private IP[/COLOR]. The sysadmins of our network, [COLOR="DarkRed"]pointed/forwarded a public IP to that same private IP[/COLOR], in a small set of ports. In this case I have, for example, port 80, 443, 20, 21, 22 pointed to my firewall....

I don't know if this is relevant.

In any case, [COLOR="DarkRed"]I still can only access FTP if I connect directly[/COLOR] to the server. Any connection [COLOR="DarkRed"]through the firewall machine times out [/COLOR]

---

### Post by Entilza on 2011-09-06
Do the other ports forwarded to your machine work, ie: 80 you mentioned.  Is your webserver accessible from the outside world?

---

### Post by Belerophon on 2011-09-06
Yup, I have some services working for some time now... Beside some sites, I can also access the firewall through ssh.

---

### Post by Dangertux on 2011-09-06
Have you checked either netstat or the ftpd configuration to make sure it is binding to the interface that you are forwarding to, and not all interfaces. This usually won't change anything but some software is picky about it.

---

### Post by Belerophon on 2011-09-07
Don't think that of any use because, besides the lo, I have only one interface on all computers.

---

### Post by Belerophon on 2011-09-07
I've just checked that ports 20 and 21 are open on my public IP: I've changed the ssh service to listen on those ports(after clearing out all iptables rules), one at a time, and logged in from the outside, using that same public IP. So, I think I can rule a problem with ports from the outside.

So I think, it must be with a problem with the iptables rules themselves. 

Once again, I only saw packet count rising on the rule handling port 21. Why did packet count remain at zeros in port 20, while the other (21) sees traffic?

Can anyone help me???

---

### Post by Entilza on 2011-09-07
That's good you checked the ports.  Can you disable the firewall entirely for a test just to be sure?  What FTP server are you using?

When you are accessing from the outside world are you sure that ftp is accessible from there?  Maybe have someone else try?

check /etc/hosts.deny  /etc/hosts.allow just to be sure?

---

