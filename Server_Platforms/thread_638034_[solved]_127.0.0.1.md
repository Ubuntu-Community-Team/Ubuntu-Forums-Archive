---
title: "[solved] 127.0.0.1"
date: 2007-12-11
forum: Server Platforms
---

### Post by gishaust on 2007-12-11
hi everyone I have setup apache2 web server on  unbuntu.

If I ping apache across the network 192.***.***.1 it works perfectly. but on the machine  that apache is on it won't work  on 127.0.0.1 or localhost. 

Can anyone give me a hint where I need to go  to fix this as I use this computer to create webpages with blue fish  and I am sick of going else where to test the web pages.

Thanks gishaust

---

### Post by umattu on 2007-12-11
Generally speaking, if you ping 127.0.0.1 or localhost. you are pinging that machine. If you ping that addy and you are not getting a reply, it usually means you have a bad nic.

In other words, you cannot ping another machines loopback address. It is reserved for the machine that you are at.

Apache works off of a IP or a name, if you want to view pages from the machine that apache is running on, use the actual IP  of the apache server, even if you are sitting at the keyboard of the apache server.

---

### Post by gishaust on 2007-12-11
Thanks for the relpy

when I netstat -r in the terminal  127.0.0.1 does not show but everything else is fine. Say it wasn't a hardware issue where would Iook to makes sure that it was setup properly.

---

### Post by rennen01 on 2007-12-11
The fact that you can ping the IP from another host means the NIC should be fine.

```
vi /etc/network
```

and make sure the localhost entry is in there.

---

### Post by gishaust on 2007-12-11
thanks for the reply but  in the /etc/networks directory what am I looking for exactly. If I am looking for localhost it does not exist. So what  is the next step

---

### Post by p_quarles on 2007-12-11
I believe that rennen1 meant this:
```
sudo vim /etc/network/interfaces
```
The line that normally runs the localhost interface should read like so:
```
# The loopback network interface
auto lo
iface lo inet loopback
```
If you're unfamiliar with the vi/vim text editor, I suggest replacing that command with "nano," which is slightly easier to figure out.

---

### Post by gishaust on 2007-12-12
Thank you for your reply. I entered
```

# The loop back network interface
auto lo
iface lo inet loop back

```
into 
```

/etc/network/interfaces

```
As it did not exist at all. Then restarted the computer and tried 127.0.0.l from the browser still did not get anything. If I netstat -r the loop back still does not show.
Has anyone got any ideas

---

### Post by p_quarles on 2007-12-12
> **gishaust said:**
> Thank you for your reply. I entered
```

# The loop back network interface
auto lo
iface lo inet loop back

```
into 
```

/etc/network/interfaces

```
As it did not exist at all. Then restarted the computer and tried 127.0.0.l from the browser still did not get anything. If I netstat -r the loop back still does not show.
Has anyone got any ideas
If you entered it exactly as shown in your post, then the problem may be that you have "loopback" as two separate words. That will throw things off.

If you entered it correctly, then I'm afraid I'm at a loss.

---

### Post by rennen01 on 2007-12-12
> **p_quarles said:**
> I believe that rennen1 meant this:
```
sudo vim /etc/network/interfaces
```


Yea that :-D

---

### Post by wirelessmonkey on 2007-12-12
You may also want to look at your /etc/hosts file, and make sure 127.0.0.1 is listed there too.

---

### Post by rsw686 on 2007-12-12
Do you have apache binded to just your 192... IP? If so you won't be able to access it with 127.0.0.1. Check your apache configuration.

---

### Post by gishaust on 2007-12-13
thank you for all your support. I had put the space in.

---

