---
title: "UFW : how to manage a port range ?"
date: 2008-04-28
forum: Security
---

### Post by frederictoulouse on 2008-04-28
Hi,

I would like to apply a rule to more that one port at a time with UFW.
For example to open the ports from 1000 to 2000 for a computeur.
I try the folowing syntax :

 ufw allow proto tcp from 192.168.3.5 to any port 1000-2000

but 1000-2000 is not a valid port, as well as 1000:2000, 1000,2000, 1000;2000 etc ....
I don't find the syntax in the documentation :confused:

thanks for your help

---

### Post by RRFarFar on 2008-05-13
Have you found an answer??? I am looking for the same))

---

### Post by pedalwrench on 2008-05-14
I'm looking for the same answer

---

### Post by frederictoulouse on 2008-05-20
No I did not find the answer, I suppose that UFW is to limited to manage a port range [-(

---

### Post by ELMIT on 2008-06-27
Have you found the answer at:

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

Here the syntax is written as:
> ufw allow|deny [proto <protocol>] [from <address> [port <port>]] [to <address> [port <port>]]

I would try instead:
ufw allow proto tcp from 192.168.3.5 to any port 1000-2000


this:

> ufw allow proto tcp from 192.168.3.5 port 1000 to 192.168.3.5 port 2000

---

### Post by beazer on 2008-07-20
The ufw rule

[quote=ELMIT]
ufw allow proto tcp from 192.168.3.5 port 1000 to 192.168.3.5 port 2000 
[/quote]
will only allow 192.168.3.5 port tcp/2000 to accept traffic from 192.168.3.5 port tcp/1000


You could try something like 

```

   -A ufw-before-input -p udp -m udp --dport 1000:2000 -j ACCEPT

```

in  /etc/ufw/before.rules


You will probably need a better rule than this example - this will open up every udp port between 1000 and 2000 to everyone!

Looks like a port range support is being worked on at the moment, but not working in my Ubuntu Hardy yet: 

[http://bazaar.launchpad.net/~jdstrand/ufw/trunk/revision/185](http://bazaar.launchpad.net/~jdstrand/ufw/trunk/revision/185)

---

### Post by Brazen on 2008-09-01
my current solution has been to do this:

```

for i in `seq 1000 2000`; do
  ufw allow $i
done

```

realizing that this will put a thousand rules into your ufw config, but at least it gets the job done.

---

### Post by rogeriopvl on 2008-09-01
Gufw version 0.20.0 allows you to insert port range (ufw will too). it hasn't been released yet. That is, if you prefer to configure ufw in a GUI.

[http://gufw.tuxfamily.org](http://gufw.tuxfamily.org)

---

### Post by Thingymebob on 2008-09-19
> **rogeriopvl said:**
> Gufw version 0.20.0 allows you to insert port range (ufw will too). it hasn't been released yet. That is, if you prefer to configure ufw in a GUI.

[http://gufw.tuxfamily.org](http://gufw.tuxfamily.org)

deb is available for the above though. makes ufw even easier than it already is. Thanks

---

### Post by guywithcable on 2009-07-20
> **frederictoulouse said:**
> Hi,

I would like to apply a rule to more that one port at a time with UFW.
For example to open the ports from 1000 to 2000 for a computeur.
I try the folowing syntax :

 ufw allow proto tcp from 192.168.3.5 to any port 1000-2000

but 1000-2000 is not a valid port, as well as 1000:2000, 1000,2000, 1000;2000 etc ....
I don't find the syntax in the documentation :confused:

thanks for your help

This works in 9.04
```
ufw allow proto tcp to any port 1000:2000
```

---

### Post by lensman3 on 2009-07-21
Looks like UFW uses iptables so the syntax should be the same as IPTABLES.  A range is 6000:6063 for X11.  In IPTABLES the range has to prefixed by source ports and/or  destination ports.

You also can control the TCP/UDP port range used by the kernel with

## Local port range for TCP/UDP connections
   if [ -e /proc/sys/net/ipv4/ip_local_port_range ]; then
        echo -e "1024\t63000" > /proc/sys/net/ipv4/ip_local_port_range
   fi


In this case, I start with 1024 and go to port 63000.  \t is a tab.  Unfortunately, I don't remember if this is the range that "NAT" uses or not.

---

### Post by aebas on 2010-02-09
Hi!

First sorry for my english.

In Hardy you must edit /var/lib/ufw/user.rules and add a rule after the ### RULES ### comment, like this:

```
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
### RULES ###

# my own rule. Open tcp range from 55600 to 55799
-A ufw-user-input -p tcp --dport 55600:55799 -j ACCEPT

### tuple ### allow any 80 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 80 -j ACCEPT
-A ufw-user-input -p udp --dport 80 -j ACCEPT


### END RULES ###
-A ufw-user-input -j RETURN
-A ufw-user-output -j RETURN
-A ufw-user-forward -j RETURN
COMMIT
```

---

### Post by tanoloco on 2010-04-15
This syntax, just for example, works with ufw 0.29-4ubuntu1 on karmic

```
sudo ufw allow proto tcp from any to any port 80,443,8080:8090
```see this link for reference:

[http://manpages.ubuntu.com/manpages/karmic/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/ufw.8.html)

Cheers

---

