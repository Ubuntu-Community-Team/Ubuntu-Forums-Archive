---
title: "Port 80 inbound"
date: 2008-07-22
forum: Ubuntu Christian Edition
---

### Post by Cyclops_ on 2008-07-22
Hey,

Did the Hardy install of Just the DG gui.  All's swell (although did the install on 64 bit, so I don't actually get the GUI... but that's fine with me as all I wanted was for it to install the rest of the stuff for me).

My main point of interest at the moment is that I am really having trouble opening my web server up to the outside world.  (In other words, I have apache installed, and I'm trying to serve up a simple web page from my machine, accessible from outside my home.)

When I navigate to the URL, it just spins and eventually gives me a white page.

However, when I turn off Firehol, I get my webpage.

I have entered into Firehol the following:
```

server http accept

```and have even tried:
```

server all accept

```and also my own variation:
```

server_myhttp_ports="tcp/80"
client_myhttp_ponts="default"

...

server myhttp accept

```Still nothing...

BUT... I can open port 8081, and all is well, i can get to http://<mywebserver>:8081 ... Just not to port 80.

Can anyone help?

Thanks!!!

---

### Post by thschiavo on 2008-07-22
Isn't it the port 80 the problem? I can't set servers at port 80 here.

---

### Post by Cyclops_ on 2008-07-22
Well port 80 works and Apache serves web pages when I turn off Firehol....

---

### Post by Cyclops_ on 2008-07-23
...  anyone?

---

### Post by Yuki_Nagato on 2008-07-23
Are you using a router?  Or a single-computer modem?

---

### Post by Cyclops_ on 2008-07-23
A router.  I have it forwarding the ports correctly.  (I can tell cuz everything works right with FH off)...

---

### Post by Cyclops_ on 2008-07-23
I've even put this as the first line in my /etc/firehol/firehol.conf:

```

iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT

```

i see the rule... but it still doesn't help  :(

---

### Post by Cyclops_ on 2008-07-25
*bump*

---

### Post by Cyclops_ on 2008-07-25
Got it!

In firehol.conf changed line:

transparent_squid 8080 "root root"

to 

transparent_sqid 8080 "root root" inface not "eth0 ath0"

---

