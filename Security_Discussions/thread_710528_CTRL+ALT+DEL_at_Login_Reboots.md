---
title: "CTRL+ALT+DEL at Login Reboots"
date: 2008-02-28
forum: Security Discussions
---

### Post by utahcon on 2008-02-28
I just installed Ubuntu Server 7.10 on my server.

I noticed when I am at the login prompt if I press CTRL+ALT+DEL and the server reboots.

Doesn't this seem as the wrong behavior for the system? I would like to know how I can change this behavior so that an admin must first login to reboot my server. 

Otherwise any yahoo with a keyboard could reboot my server in the datacenter, and that is not good.

I would also assume this works through other connects of the server (possibly SSH?)

Thanks!

---

### Post by k_grdn on 2008-02-28
Hi,

Comment out this line in /etc/inittab:

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

Or replace with something similar:

ca:12345:ctrlaltdel:/bin/echo "CTRL-ALT-DEL is disabled"

Regards,

k_grdn

---

### Post by utahcon on 2008-02-28
Thanks. I don't actually have a file called inittab in /etc though.

Is this supposed to be that way? It doesn't seem to make sense to me to be able to just walk up to any Linux terminal and press CTRL+ALT+DEL and get a reboot.

I would think this is a terrible idea in fact.

Is there are good reason for it? It this limited to Ubuntu or all Linux distros?

---

### Post by arashiko28 on 2008-02-28
CTRL+ALT+DEL doesn't exactly reboot the whole system. Just Xorg, if you have a system monitor, you'll see that the count of the system "up" doesn't reset. Any way, you can make it ignore the action.

---

### Post by k_grdn on 2008-02-28
Hi,

You must have inittab, this file spawns all other processes on the system (pid  1).

Try:

find / -type f -name inittab -print

Regards,

k_grdn

---

### Post by utahcon on 2008-02-28
Great, it was in a completely odd place thanks.

@ arashiko28 :: Actually yes, it was doing a complete reboot on my system. It is as if I login and type "shutdown -r now"

My whole system logs off, powers off (resets), posts and loads linux again.

---

### Post by aysiu on 2008-02-28
> **utahcon said:**
> 
Doesn't this seem as the wrong behavior for the system? I would like to know how I can change this behavior so that an admin must first login to reboot my server. 

Otherwise any yahoo with a keyboard could reboot my server in the datacenter, and that is not good.

> **utahcon said:**
> 
Is this supposed to be that way? It doesn't seem to make sense to me to be able to just walk up to any Linux terminal and press CTRL+ALT+DEL and get a reboot.

I would think this is a terrible idea in fact.

Is there are good reason for it? It this limited to Ubuntu or all Linux distros? Anyone who has physical access to your server essentially has root access and can do anything to it. This is why most servers are physically locked away in a closet or other secure room.

If someone has the ability to plug a keyboard into your server, Control-Alt-Delete is the last thing you have to worry about in terms of security compromise.

---

### Post by utahcon on 2008-02-28
Unfortunately I don't have the funds to afford a private rack, which is why I tested this in the first place.

I am completely aware that having physical access is dangerous to begin with.

Alas, no one has explained _why_ this is the behavior from default. Nor why it would be useful.

Thanks BTW for helping with the inittab piece.

---

