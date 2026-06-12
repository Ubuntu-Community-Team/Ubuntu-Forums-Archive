---
title: "apt-get via ssh tunnel"
date: 2008-12-17
forum: Server Platforms
---

### Post by nuckymcnuck on 2008-12-17
Is it possible to update apt via an ssh tunnel?

I have a server  - Alice lets say - on a network with a public internet IP address (140.x.x.x), it's also connected to a private switch (192.168.0.2).

I recently got Bob, a new server (Ubuntu 8.04 x64) which I don't want to have a public IP.

How would I tunnel the apt-get through Alice to get to Bob?

Thanks

---

### Post by Dr Small on 2008-12-17
If Alice and Bob are on the same network, ssh into Alice via the pubilc IP address, (you are now on the local network) and then ssh into Bob's private IP to run any commands you wish.

---

### Post by nuckymcnuck on 2008-12-17
Thanks for the swift reply, but sshing from Alice to Bob via the Public IP, then running apt-get on Bob still throws up "Could not resolve 'security.ubuntu.com'" on apt-get

---

### Post by doobiest on 2008-12-17
I would do one of 3 things.

Is there a specific reason why Bob doesnt have internet access? Like is that intentional for security or something?

1) If not, set up NAT between Alice and Bob. So that bob will route traffic to alice then to the net.

2) Set up a VPN from Alice to Bob and use alice as the default gateway, which should route all internet traffic through the vpn then to the internet

3) Pretty sure apt just does wgets over port 80 so you could do an ssh tunnel forwarding port 80 but I really dont think that'll work. port forwarding is more so for forwarding traffic directed to localhost:port to a destination on the ssh server's network.

---

### Post by nuckymcnuck on 2008-12-17
Intentional, I want to restrict access... plus I don't want to fill out the paper work.

How would one setup a VPN?

---

### Post by doobiest on 2008-12-17
I'll see if I can google a tutorial after lunch. But seriously if both computers are on the same internal network you'd be way better off to do nat translation. Which is just configured between those two boxes, nothing else required so I'm not sure why you'd need to do paperwork for something like that.. assuming it's for work.

---

### Post by nuckymcnuck on 2008-12-17
Which ever you think is easiest. The machine will just be running GIMPS, and since our office is closing on Friday for the holidays I want to have everything setup nice and neatly before relaxing!

---

### Post by doobiest on 2008-12-17
This article should do it.

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by nuckymcnuck on 2008-12-17
Thanks!

---

### Post by doobiest on 2008-12-17
Yup and keep in mind this can be a temporary or permanent setup depending on what you want. And if you really want to restrict internet access you could read up more about iptables and make it so the only internet traffic allowed is to the ubuntu repositories for updates

---

### Post by cdenley on 2008-12-17
Install privoxy (might be a little difficult without internet)
```

sudo apt-get install privoxy

```
Add this line to /etc/privoxy/config:
```

forward-socks4 / localhost:8080 .

```
restart privoxy
```

sudo /etc/init.d/privoxy restart

```
Now you're all set. To establish your tunnel and use it with apt:
```

ssh -D 8080 myserver
export http_proxy=http://127.0.0.1:8118
sudo apt-get update
sudo apt-get upgrade

```

---

