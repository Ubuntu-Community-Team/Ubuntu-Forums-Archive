---
title: "Portforwarding Apache on Linksys router"
date: 2010-07-19
forum: Server Platforms
---

### Post by gluxon on 2010-07-19
I'm trying to port forward apache on a Linksys router. The apache2 installation is the default that came with ubuntu server 10.04

I've forwarded ports 80 and 443, but when I go to my external IP, I get redirected to my internal.

Meaning **.***.***.*** goes to 192.186.1.124, which is what I have set to a static IP.

When someone from outside my network, accesses the external ip, they get the same thing. Which is "Firefox can't find the server at 192.168.1.1244."

Thanks

---

### Post by spynappels on 2010-07-20
So you have the following setup?

Internet <---> Linksys Router (aaa.bbb.ccc.ddd) <---> server (192.168.1.124)

For someone to access the server, you need to forward ports from aaa.bbb.ccc.ddd to 192.168.1.124, which you say you have done. Then when someone from the internet puts in aaa.bbb.ccc.ddd into their browser, they should see the webpage served by the server, they should not see the internal IP at all.

I presume you have checked Apache is running and working correctly? you can see the webpage inside the LAN when you point the browser to 192.168.1.124?

---

### Post by lisati on 2010-07-20
> **gluxon said:**
>  Which is "Firefox can't find the server at 192.168.1.[COLOR="Red"]1244[/COLOR]."
Is that the actual error message or a typo? It looks like there's an extra 4 there.

---

### Post by sfr on 2010-07-21
So connecting to your public ip gives an error message referring to an internal ip? This is something that should never happen.

To make useful comments to this some more information would be required, like afore mentioned if apache is running and serving pages on the local network for starters.

from the little information available I would lean towards the port forwards being in some way mis-configured.

---

### Post by stlsaint on 2010-07-21
Sounds like two possible issues:
1. You didnt setup port forwarding correctly.
2. You dont have apache2 installed/started

If one than go back to your router and double check your port forwarding configuration to ensure your forwarding to the correct ip. 

For apache2 make sure you have it installed and started. Try going to: 192.168.1.124 in your browser when your connected to your network and you should be brought to an all white page with the letters: It Works! in the top left. If you do not get this than you have not either installed apache2 or it is not started:
to start apache2 run this command.(if you are as root than exclude the sudo.)
```
sudo /etc/init.d/apache2 restart
```

---

### Post by gluxon on 2010-07-24
Yeah, the extra 4 was a typo. I have apache2 running perfectly fine, considering 192.168.124 shows me my site. Sorry, I thought I mentioned it earlier.

Here's a screen-shot of my config.
[http://a.imageshack.us/img812/96/portrangeforward1280009.png](http://a.imageshack.us/img812/96/portrangeforward1280009.png)

To clarify more, entering my external ip changes the url to the internal ip, which is the ip I have set in my settings. This causes people outside the network to get a 404, but everything works fine from inside the network.

---

### Post by Bachstelze on 2010-07-24
192.168.x.x is a private IP, it is not accessible from outside your LAN.  Someone outside your LAN must use your public IP.

---

### Post by gluxon on 2010-07-24
> **Bachstelze said:**
> 192.168.x.x is a private IP, it is not accessible from outside your LAN.  Someone outside your LAN must use your public IP.

I realize that >_<

---

