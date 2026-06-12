---
title: "How to join Hardy Desktop to Samba Domain Controler"
date: 2008-10-02
forum: Server Platforms
---

### Post by smullie on 2008-10-02
Hello all,

Can someone point me to the solution to Join a Hardy Desktop, or linux desktop, to a Samba Domain Controler.

I found a lot of stuff of joining to a windows domain controller, but i cannot seem to get it to work with a Samba Domain Controler.

Let me tell you the situation:
I have a mixed windows/linux enviroment.
We use Ubuntu/Debian servers as PDC and other stuff.

Windows joint to the domain perfecly, but how to use the Linux Desktops in the same way as the Windows Desktops, with kind of roming profiles.
I meen, authenticate by the samba domain, and use samba shares, diffrent per user.

Hope one of you can help me out here,

Thanks,

Richard.

---

### Post by windependence on 2008-10-02
Give us an idea of what you have tried so far and what errors, if any you are encountering.

-Tim

---

### Post by smullie on 2008-10-02
I have follow some how to's for joining a windows domain.

When i try to join it give an error or that a number of ports are closed, but it is not. Firewall was off.

Or something like,
Cannot join a standalone computer

I cannot remeber what i have done exacly, it was some day's ago, but if you can point me to the correct way, i would be pleased.

---

### Post by windependence on 2008-10-02
What is in your /var/log/messages?

I'm thinking it may be an appamor problem. Also, AFAIK, you cannot just "turn off" the firewall, you have to zero out all the rules. I wish you could just turn it off. ;)

-Tim

---

### Post by smullie on 2008-10-02
Good thinking,

I thought i desabled appamor, but i wil check.
I have resinstalled the desktop several times, perhaps i forgot it once.

But you think that the guides for joining a Windows Domain wil work on a Samba domain?

---

### Post by windependence on 2008-10-02
Not sure about the guides but make sure you have your DNS set up correctly on your PDC so the boxes can be recognized also. Just trying to cover all the bases. I'm still looking for more info.

-Tim

---

### Post by smullie on 2008-10-02
I have a perfect DNS/DHCP system.

I have tried this my hardy box:
apt-get install likewise-open
aa-complain /etc/apparmor.d/*
domainjoin-cli join server1.example.com root

error:
required ports cannot be contacted, please update firewall settings
make sure the following ports are open to server1.example.com
88 UDP
137 UDP
389 UDP
464 UDP
88 TCP
389 TCP
464TCP
(No firewall on the server b.t.w)

The i tried:
/etc/init.d/apparmor stop
domainjoin-cli join server1.example.com root

Same error,

Any idea's?

---

### Post by windependence on 2008-10-02
One thing I don't like about Ubuntu server is you CANNOT elect to not install the firewall. You may not think you have it on, but you probably do. Try this:

Save firewall rules

```
sudo iptables-save > /root/firewall.rules
```

Now type the following commands:

```
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

Also make sure the firewall is dropped on the PDC and the client machine.

-Tim

---

### Post by smullie on 2008-10-02
It is not working,

I think the way with likewise-open is not working with samba domains.

---

