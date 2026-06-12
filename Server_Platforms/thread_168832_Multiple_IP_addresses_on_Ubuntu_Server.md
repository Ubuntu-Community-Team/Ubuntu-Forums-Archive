---
title: "Multiple IP addresses on Ubuntu Server"
date: 2006-05-01
forum: Server Platforms
---

### Post by OneSeventeen on 2006-05-01
As of now, I have about 3 IP addresses on my Ubuntu 5.10 server, the primary one I set up during install, and 2 secondary ones I set up by typing:
```
ifconfig eth1:0 123.456.789.012 netmask 255.255.255.0
ifconfig eth1:1 123.456.789.013 netmask 255.255.255.0
```

Of course, each time I reboot the server, this goes away, and I have to type it in again.  (so yes, I just wrote a bash script to do this for me, but I want it to be more automated)

Is there a file I can modify?  Or should I just add the bash script to startup?

If so, how do I make the script launched at startup?

---

### Post by Koybe on 2006-05-01
I think you can set this in your /etc/network/interfaces script. Just follow the syntax of your primary interface. ;-)

---

