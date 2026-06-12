---
title: "Tell my server to run a command?"
date: 2008-10-20
forum: Server Platforms
---

### Post by linuxisevolution on 2008-10-20
I would like to view my headless servers' mem and cpu usage. Its running debian 4. I have nfs setup on it, but if i run 'xterm top' from the file browser in /home/winrid/mountedserver I get the stats of my pc. So, if anyone could tell me how to run a command over the network or viewing my servers' memory usage that'll be just dandy. Thanks.:guitar:



EDIT: I never got vncserver to work right. After 5 hours of trying that, don't even mention it lol ](*,)

---

### Post by bobyo134 on 2008-10-20
well i think u should get new server one that is not 900mhz and 9gb lol and make it run ubuto sever edition bye now:lolflag:

---

### Post by linuxisevolution on 2008-10-20
> **bobyo134 said:**
> well i think u should get new server one that is not 900mhz and 9gb lol and make it run ubuto sever edition bye now:lolflag:

Actually, smart ***, my server is 550mhz, 128mb ram. Its Debian 4, which is lighter, so you know. Maybe you should go to the home page, stare at the logo, and hit the refresh button a few thousand times. Good day.

---

### Post by linuxisevolution on 2008-10-20
Just so everyone knows, boby is someone I know. We were just playing around, so please, don't ban us. lol. Back to topic...

---

### Post by lykwydchykyn on 2008-10-20
- install openssh-server on the server
 - enable X11 forwarding in the servers /etc/ssh/sshd_config
 - Run on your workstation:
```

ssh user@workstation xterm -e top

```

After entering the password, you will get an xterm popping up with top.
Of course, I guess there's no need to forward X11 over ssh, you could just do:

```

xterm -e "ssh user@server top"

```

That works too.

---

### Post by linuxisevolution on 2008-10-21
> **lykwydchykyn said:**
> - install openssh-server on the server
 - enable X11 forwarding in the servers /etc/ssh/sshd_config
 - Run on your workstation:
```

ssh user@workstation xterm -e top

```

After entering the password, you will get an xterm popping up with top.
Of course, I guess there's no need to forward X11 over ssh, you could just do:

```

xterm -e "ssh user@server top"

```


What now? Thanks for your time.
That works too.


The second command brings up xterm, but immediately closes. When I run the first command given, I get:

> ssh 192.168.1.125 xterm -e top
ssh: connect to host 192.168.1.125 port 22: Connection refused


What next? Thanks for your time.

---

### Post by TreeFinger on 2008-10-21
> **linuxisevolution said:**
> The second command brings up xterm, but immediately closes. When I run the first command given, I get:



What next? Thanks for your time.

why don't you just ssh into the server and type 'top'

---

### Post by lykwydchykyn on 2008-10-21
Did you install openssh-server on the server?

---

### Post by linuxisevolution on 2008-11-07
> **lykwydchykyn said:**
> Did you install openssh-server on the server?

Openssh would not work, but ssh does. Thanks :)

---

### Post by lykwydchykyn on 2008-11-08
Well, ssh is the command, openssh-server is the package that needs to be installed.  Just FYI.  Glad it worked.

---

### Post by scottuss on 2008-11-13
> **TreeFinger said:**
> why don't you just ssh into the server and type 'top'

That makes more sense

---

