---
title: "Feisty Server Won't Completely Start Up"
date: 2008-06-19
forum: Server Platforms
---

### Post by Oysterville on 2008-06-19
Odd little thing with my server.  The server seems to boot through completely, but it won't get to a login prompt unless I press enter.  There's no prompt to press enter, but that's what it takes.  The server won't even respond to ssh requests, or apparently ANY remote requests, including Apache.

Any idea what might be causing this?  It's been going on since Edgy, and tonight I wanted to remotely work on the thing but then I had to reboot. :(

---

### Post by gtdaqua on 2008-06-20
broken packages perhaps??

can you try:
```

sudo apt-get update
sudo apt-get upgrade -f

```

and 

```

sudo apt-get install -f

```

---

### Post by Oysterville on 2008-06-20
Thanks for the reply.  All came back clean with no updates.  I presumed that sudoa was a typo of sudo.

---

### Post by gtdaqua on 2008-06-20
> **Oysterville said:**
> Thanks for the reply.  All came back clean with no updates.  I presumed that sudoa was a typo of sudo.

Yeah, sorry. It is 'sudo' and not 'sudoa'. Its corrected now.

Ok, try this good old method of fixing things. Remove and install again. But do this from the console and not via SSH.

```

sudo apt-get remove openssh-server openssh-client --purge
sudo apt-get install openssh-server openssh-client

```

Also, post the output of 

```

cat /etc/network/interfaces

```

Btw, why are you still on Feisty? Not meaning to say that this is why the problem is happening though!

---

### Post by Oysterville on 2008-06-21
Ooops!  Guess this is Gutsy that the server is running.  Now that I'm home I can see that.

Here's my interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
	pre-up iptables-restore < /etc/iptables.rules
	post-down iptables-save > /etc/iptables.rules

# The extended interfaces
auto eth1
iface eth1 inet static
address 192.168.10.1
netmask 255.255.255.0

I'll reinstall openssh later on, when I can get a monitor hooked up to it.  I do appreciate the help.

---

### Post by wwood on 2008-07-01
Why are you still on Gutsy and not on Hardy?

I think the problem is much simpler than you think. I think it has already printed out a login prompt, but then it prints out a bunch of other startup stuff, which hides the prompt.

Try not pressing enter, but instead typing your username, then press enter - it should ask for password. You follow?

I agree it is a bug, but doesn't really seem important to me.

ben

---

### Post by windependence on 2008-07-02
> **wwood said:**
> Why are you still on Gutsy and not on Hardy?

I think the problem is much simpler than you think. I think it has already printed out a login prompt, but then it prints out a bunch of other startup stuff, which hides the prompt.

Try not pressing enter, but instead typing your username, then press enter - it should ask for password. You follow?

I agree it is a bug, but doesn't really seem important to me.

ben

No offense but the latest and greatest is not always the best option. There are many applications that don't yet have support for Hardy. Lots of folks, especially in the server space are still on dapper.

-Tim

---

### Post by Oysterville on 2008-07-03
It's important to me because if I need to remotely reboot the server I'd like it to come up completely and be operational without my having to go to where the server is and press the Enter key.

---

### Post by gtdaqua on 2008-07-03
> **Oysterville said:**
> It's important to me because if I need to remotely reboot the server I'd like it to come up completely and be operational without my having to go to where the server is and press the Enter key.

This is needless because, your server is already operational at that stage. You dont have to press 'enter' and then think the server will become active. All processes and services are loaded on the background. You can still ssh to it if you want to connect.

Of course, if you are using the console, it is still ready for you. 

But anyway, at that 'stage', your server is ready.

---

### Post by Oysterville on 2008-07-03
I wish that was the case, but it is not.  As I said before, the server will not respond to http or ssh requests (maybe others, but these are the only two that I'm using at the moment) until I press enter.  After that, it's all fine.

---

