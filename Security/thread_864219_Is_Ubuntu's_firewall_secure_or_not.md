---
title: "Is Ubuntu's firewall secure or not?"
date: 2008-07-19
forum: Security
---

### Post by SSVegito888 on 2008-07-19
I read somewhere that Ubuntu uses ufw for its firewall.

Is this true?

Is it secure?

Also, I use the GUI gufw to access the firewall.  Is this a good GUI to use?


OK, I have one more question.

If I use gufw (GUI) to configure the firewall, will it automatically block Denial of Service attacks.


PS: I have the firewall to deny incoming traffic. I don't know if this helps;I thought I would just tell you anyway.

---

### Post by hyper_ch on 2008-07-19
are you sure you need to alter the default configuration?

And no, Ubuntu does not use ufw as firewall. The firewall is a package filtering program called iptables. UFW is just one (of a few different) ways to alter its settings.

What kind of traffic do you need to deny?

---

### Post by brian_p on 2008-07-19
> **SSVegito888 said:**
> I read somewhere that Ubuntu uses ufw for its firewall.

Is this true?

It is part of the default install. The choice to use it is yours.

> Is it secure?

ufw configures rules for netfilter. netfilter is secure. ufw bugs are at

[http://packages.ubuntu.com/hardy/admin/ufw](http://packages.ubuntu.com/hardy/admin/ufw)

Do you see any security related ones?

> Also, I use the GUI gufw to access the firewall.  Is this a good GUI to use?

It's competent.

> OK, I have one more question.

If I use gufw (GUI) to configure the firewall, will it automatically block Denial of Service attacks.

No.


> PS: I have the firewall to deny incoming traffic.

Why?

---

### Post by SSVegito888 on 2008-07-19
How do i protect against DoS attacks with ufw.  Is there a way to do it with the gui gufw.

Or do I need something like firestarter?


Also, does firestarter use iptables?


The reason I want to modify ufw settings is because I am going to add openssh server.


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-19
you can't really do anything against DoS attack...

But I guess you mean against brute-force attack... well, to secure ssh against brute-force use (1) a secure password for your user account and (2) an auto-ban service like denyhosts or fail2ban

firestarter and ufw are tools to "conventiently" configure iptables. ufw is the new recommended way to do it.

---

### Post by SSVegito888 on 2008-07-19
I tried firestarter a little while ago.  It said something about something about restricting ICMP and this might help block DoS attacks.


What exactly does denying incoming traffic do?


Do I even need to deny incoming traffic?


If not, how do I revert all changes I have made to firewall?


PS:I when I first started using gufw, it said firewall was disabled.


Thanks,

SSVegito888

---

### Post by hyper_ch on 2008-07-19
well, you have to know if you need to deny incoming traffic. well, ping and traceroute use icmp and with those you can see if there is actually a computer at the other end. So if you deny icmp the other won't know for sure if there is something operating at the IP....

but a DoS won't happen on a private person anyway... why should it happen.... so I don't really see a problem in that. With a DoS attack or DDoS attack you do not try to gain access to a machine but you try to "cut it off" from the internet by using all it's bandwidth so it will not be reachable by other computers also. That is something different than brute-forcing and as I said, I see not a big point in a DoS attack on a private computer.

well, you could delete all rules from iptables... that's how it is "configured" upon installtion - which means nothing is being filtered.

---

### Post by SSVegito888 on 2008-07-19
How do I delete all rules from iptables?


Also, I am still not sure if I need to disable incoming traffic?

What are some reasons that someone would need to disable incoming traffic?



Thanks,

SSVegito888

---

### Post by Dr Small on 2008-07-19
> **SSVegito888 said:**
> How do I delete all rules from iptables? [...]

Try:
```
sudo iptables -F
```

---

### Post by kevdog on 2008-07-19
If your computer is not sitting behind a router -- exposed to the internet -- you may want to filter incoming connections if you are running daemons with listening processes -- ie ssh, ftp, http, etc.

---

