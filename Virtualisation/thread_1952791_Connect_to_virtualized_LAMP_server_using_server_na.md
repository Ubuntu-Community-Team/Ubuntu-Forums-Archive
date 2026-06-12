---
title: "Connect to virtualized LAMP server using server name"
date: 2012-04-05
forum: Virtualisation
---

### Post by jatwood on 2012-04-05
Hello everyone,

I have a virtualized LAMP server(as a guest) in VirtualBox 4.1 on my Ubuntu host OS. I am able to access MySQL and Apache by manually connecting to the server's IP address. I'm using the 'bridged adapter' option in VirtualBox.

The only problem is that I would like to simply type in the server name into my web browser, nautilus, etc. (in this case 'userver') without the DNS server from the ISP getting in the way. Since I use WIFI at home, coffee shops, and other places, the DHCP IP changes constantly.

Is there any way to connect to my server by referencing its name instead of the IP address (which always changes) ? For example; user@userver.

Any comments or suggestions are much appreciated.

---

### Post by papibe on 2012-04-05
Hi jatwood.

If both computers are running avahi services (by default in most versions), it may work accessing the server using the zero configuration protocol:
```
userver.local
```
Tell us if it works or you need more ideas.
Regards.

---

### Post by dcstar on 2012-04-05
> **jatwood said:**
> 
............
Is there any way to connect to my server by referencing its name instead of the IP address (which always changes) ? For example; user@userver.

Any comments or suggestions are much appreciated.

```
man hosts
```

---

### Post by jatwood on 2012-04-05
> **dcstar said:**
> ```
man hosts
```

I added a new line to the /etc/hosts file:

```
192.168.x.xxx  userver
```

That's fine and all, but what happens if I utilize a different WiFi spot, with a different router? I'll have to change the IP address inside the /etc/hosts file--not something I want to do every time I use a different WiFi spot.

One thing I wanted to mention about the virtualized server; I'm using the 'bridged adapter' option.

Is there a way to connect to the virtualized server through a static IP, consistently?

---

### Post by CharlesA on 2012-04-05
The hosts thing would only work if you are at one place. If you use multiple hot spots, you'd be better off sticking the VM in NAT mode and using port redirection to access it from the host.

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by papibe on 2012-04-05
> **CharlesA said:**
> The hosts thing would only work if you are at one place.+1

I think bridge VM and avahi services may work (although, I haven't tested it myself).

Just a thought.
Regards.

---

### Post by CharlesA on 2012-04-05
> **papibe said:**
> +1

I think bridge VM and avahi services may work (although, I haven't tested it myself).

Just a thought.
Regards.

It might, but tbh, I wouldn't want a LAMP server on an unknown network, which is exactly what would happen if you used bridged networking when connected to a random hopspot.

---

### Post by dcstar on 2012-04-05
> **jatwood said:**
> 
.........
Is there a way to connect to the virtualized server through a static IP, consistently?

Use localhost.

---

### Post by jatwood on 2012-04-05
> **dcstar said:**
> Use localhost.

How? Should I modify the /etc/network/interfaces file or enter .locallhost extension in the web browser, or what?

---

### Post by CharlesA on 2012-04-06
> **jatwood said:**
> How? Should I modify the /etc/network/interfaces file or enter .locallhost extension in the web browser, or what?
Using localhost would only work if you are trying to access the web server from inside the VM itself.

---

