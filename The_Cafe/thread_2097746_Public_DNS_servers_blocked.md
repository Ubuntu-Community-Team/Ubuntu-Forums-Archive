---
title: "Public DNS servers blocked"
date: 2012-12-24
forum: The Cafe
---

### Post by tkoco on 2012-12-24
AT&T has decided to block DNS requests going to any outside DNS server, including their own server. 

Is there a way around this issue besides changing ISPs?

---

### Post by Dr. C on 2012-12-24
Does installing bind9 and running one's own DNS work? ```


sudo apt-get install bind9
```

---

### Post by sammiev on 2012-12-24
This is what I use as listed above by Dr. C not sure if it will help with AT&T. I'm just adding to his post. :)

```
sudo apt-get install bind9
```

set your DNS to 127.0.0.1 (in your browser)

```
sudo /etc/init.d/bind9 restart
```

---

### Post by Primefalcon on 2012-12-24
you know my feeling is they're probably prepping up to stop people from getting around their upcoming 6 strikes agreement thing with the MPAA... so they're probably going to block access to sites that the MPAA don't like by doing this

---

### Post by Old_Grey_Wolf on 2012-12-24
Some how-to's for bind9:

[https://help.ubuntu.com/10.04/serverguide/dns-configuration.html](https://help.ubuntu.com/10.04/serverguide/dns-configuration.html)

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

I used bind9 when I had an ISP with unreliable and slow DNS servers.

---

### Post by tkoco on 2012-12-24
> **Primefalcon said:**
> you know my feeling is they're probably prepping up to stop people from getting around their upcoming 6 strikes agreement thing with the MPAA... so they're probably going to block access to sites that the MPAA don't like by doing this

Thanks for the heads up about torrents and RIAA/MPAA. Just the same, it is annoying that they would stoop to blocking external DNS requests.

Thank you to everyone else for the tips about bind9. I guess that I will have to set up my own DNS servers and tell AT&T to take a flying leap off a short pier while wearing lead (the heavy metal) pants.

---

### Post by Dr. C on 2012-12-24
There is one more point on setting up bind9. Once the Ubuntu or other GNU/Linux computer is set up to be a DNS. Then the other computers and devices on the local network can also use it as their DNS. 

What I do is configure DNS on one computer with a static IP on the local lan and then use it for DNS for all the devices and computers on the local lan. This can be done by setting the DNS on the router or other DHCP server to the local IP of the DNS computer. It works for any device or computer including mobile devices, Windows computers, blu-ray players, TVs, game consoles etc.

---

### Post by mr john on 2012-12-24
That sucks. I use ssh tunneling most of the time, because I need some websites to think I'm in the UK.  Tunneling probably wont do you much good though as you would need to have a server set up in another location or with a different isp. I wouldn't trust going down that or the VPN route unless you know the host very, very well.

---

### Post by mips on 2012-12-25
Are you guys saying AT&T are blocking all DNS related traffic if it does not go to their servers? So you can't use for example OpenDNS servers?

Something smells fishy here, I find it hard to believe that they would deliberately block traffic to other DNS servers. If they do it for border on illegal imho.

---

### Post by mike acker on 2012-12-25
couple of tests.....

...can you ping the DNS you're looking to use ?

...do you have the IP for us ? we can run some additional ping tests to see if the DNS is active or maybe it just went offline

---

