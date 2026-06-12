---
title: "How to start a dhcp server"
date: 2008-03-26
forum: Server Platforms
---

### Post by quarkhirad on 2008-03-26
hello . I am an absolute newbie in Dhcp servers. Infact this is the first time i am setting up a dhcp server. Hence please be patient and explain in detail . Thank you 


I got hold of a desktop and installed ubuntu 7.04. Then i did the following 

```
sudo apt-get install dhcp3-server and gdhcpd 
```

Now what do i have to enter in the various fields after running the following command

```
sudo gdhcpd 
```

thank you 

:) :) :)

---

### Post by cdenley on 2008-03-26
I've never used a GUI for a dhcp server, but I would imagine you need to enter things like the IP range, DNS server, and gateway IP. All these depend entirely on your network. How is your router configured? Do you already have a DHCP server on your network?

---

