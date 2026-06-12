---
title: "Can't connect to my server?"
date: 2018-03-30
forum: Server Platforms
---

### Post by toastedtoastplays on 2018-03-30
I can't SSH into my Ubuntu Server or even connect to the game server. It is a fresh install and I could do it earlier but I don't know what makes it work. Please help!

---

### Post by darkod on 2018-03-30
We need much more information than that...

Is this a VPS hosted with a provider? Is it a physical or virtual server at your home?

The first thing to make sure of is that the machine is ON. Is it?

---

### Post by toastedtoastplays on 2018-03-30
It is a home server and yes, it is turned on. P.S. I have tried pinging it with 100% packet loss.

---

### Post by darkod on 2018-03-30
Does it have static IP address? If it uses dhcp maybe the address changed. Server should always use static IP.

Also it might be better if you connect monitor and keyboard to it and see what is going on.

---

### Post by toastedtoastplays on 2018-03-30
I have a keyboard and monitor plugged in, how do I switch my IP to static and how do I know if I already have?

---

### Post by darkod on 2018-03-30
Well, if you set it up you should already know... :)

You probably left it as dhcp during install. You can check it in /etc/network/interfaces.

To set it to static there are many tutorials and blogs online. Here is the basic one from ubuntu help: [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

Make sure you select an IP outside of the router dhcp range.

---

