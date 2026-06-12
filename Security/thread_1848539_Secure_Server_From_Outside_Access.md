---
title: "Secure Server From Outside Access?"
date: 2011-09-22
forum: Security
---

### Post by Jonj1611 on 2011-09-22
Hi,

Basically I installed Ubunutu server today with mediatomb to act as a media server for my house. I also installed Openssh and webmin plus mediatomb of course.

The server will only be operating on the internal network.

Is there anyway to stop Ubuntu accepting any connections that are not on the internal network. Basically I still want to use the server to get updates from the internet but thats it, I dont want it to have any other outside access at all and I will never want to access it away from home, its strictly for internal use.

Is there anyway to do this, does it do it already perhaps?

Sorry if that sounds newbish, Linux isn't really something I have got to know well.

Thank you for any help
Jon

---

### Post by Dangertux on 2011-09-22
> **Jonj1611 said:**
> Hi,

Basically I installed Ubunutu server today with mediatomb to act as a media server for my house. I also installed Openssh and webmin plus mediatomb of course.

The server will only be operating on the internal network.

Is there anyway to stop Ubuntu accepting any connections that are not on the internal network. Basically I still want to use the server to get updates from the internet but thats it, I dont want it to have any other outside access at all and I will never want to access it away from home, its strictly for internal use.

Is there anyway to do this, does it do it already perhaps?

Sorry if that sounds newbish, Linux isn't really something I have got to know well.

Thank you for any help
Jon

You can do it using UFW (Uncomplicated FireWall). For a minute we're going to assume your internal network is 192.168.1.x (change this if it's different) and the IP of your server is 192.168.1.200

So on your server you would do the following.

```

sudo ufw enable
sudo ufw allow from 192.168.1.0/24 to 192.168.1.200 port 22,80,1900,10000 proto tcp
sudo ufw allow from 192.168.1.0/24 to 192.168.1.200 port 1900 proto udp
sudo ufw deny from any to 192.168.1.200
sudo ufw disable && sudo ufw enable

```There you go, change the ip's as necessary. This will allow any ip on your internal network (192.168.1.0) to access your server on ports 22 tcp , 80 tcp, 1900 tcp and udp and 10000 tcp. While dropping incoming traffic from external ip addresses.

Port 22/tcp : SSH
Port 80/tcp: http webmin
Port 1900/tcp & udp: default media tomb port
Port 10000/tcp: ssl for webmin

Hope that helps.

---

### Post by Jonj1611 on 2011-09-22
That is fantastic, thank you so much for helping out, I will try that in the morning.

Thanks once again, its really appreciated

Regards
Jon

---

### Post by Dangertux on 2011-09-22
No problem if you have any issues just ask :-)

---

### Post by Jonj1611 on 2011-09-22
Thank you, I will do :)

---

### Post by FuturePilot on 2011-09-22
If you're behind a router, there isn't really anything to do.

---

### Post by Jonj1611 on 2011-09-23
I thought that FuturePilot but a friend of mine was receiving multiple attacks direct to their server, though I am not sure what OS they were running so I was just trying to tighten mine as much as possible.

Dangertux, my mediatomb port is 49153, do I just change the 1900 to 49153?

Regards
Jon

---

### Post by spynappels on 2011-09-23
> **Jonj1611 said:**
> 
Dangertux, my mediatomb port is 49153, do I just change the 1900 to 49153?


That is correct.

---

### Post by Jonj1611 on 2011-09-23
Ideal, thank you :)

---

### Post by FuturePilot on 2011-09-23
> **Jonj1611 said:**
> I thought that FuturePilot but a friend of mine was receiving multiple attacks direct to their server, though I am not sure what OS they were running so I was just trying to tighten mine as much as possible.

It sounds to me like your friend had an Internet facing server and from your description, your server is only going to be on you LAN. So unless you forward ports in your router to your server there isn't anyway anyone could access it from the outside.

---

### Post by Dangertux on 2011-09-23
> **FuturePilot said:**
> It sounds to me like your friend had an Internet facing server and from your description, your server is only going to be on you LAN. So unless you forward ports in your router to your server there isn't anyway anyone could access it from the outside.

While that is generally true , that is not the rule.

Example : There are two machines behind a NAT router. A server, and a laptop someone uses for browsing the web. The laptop encounters a malicious server the server has two DNS A records 211.212.213.214 and 192.168.1.3. Laptop loads a web page, web page contains malicious javascript code, Laptop begins executing it, the code calls for the laptop to send a string of malicious data back to the server it received the javascript from. When it tries to do this, the malicious server sends TCP RST, the Laptop then tries the next IP in the DNS record, which is an internal IP. The NAT router had no ports forwarded.

Go with the firewall.

Also yes just change those ports to whatever port you are using. Sorry for the late response.

---

### Post by FuturePilot on 2011-09-23
> **Dangertux said:**
> While that is generally true , that is not the rule.

Example : There are two machines behind a NAT router. A server, and a laptop someone uses for browsing the web. The laptop encounters a malicious server the server has two DNS A records 211.212.213.214 and 192.168.1.3. Laptop loads a web page, web page contains malicious javascript code, Laptop begins executing it, the code calls for the laptop to send a string of malicious data back to the server it received the javascript from. When it tries to do this, the malicious server sends TCP RST, the Laptop then tries the next IP in the DNS record, which is an internal IP. The NAT router had no ports forwarded.

Go with the firewall.

Yes I did think of that but it's a rare situation.

---

### Post by Jonj1611 on 2011-09-23
Thanks to both for your comments and input :)

---

### Post by Dangertux on 2011-09-23
> **FuturePilot said:**
> Yes I did think of that but it's a rare situation.

Better safe than sorry :-)

And I hope everything worked out for the thread starter.

---

