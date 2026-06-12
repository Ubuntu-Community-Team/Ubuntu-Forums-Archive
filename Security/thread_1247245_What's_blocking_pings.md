---
title: "What's blocking pings?"
date: 2009-08-22
forum: Security
---

### Post by pierrefar on 2009-08-22
Hi

I run a very well-functioning server that I cannot ping. I was curious to see why the pings were blocked after some users reported being unable to even reach the webserver.

So I dug around and disabled ufw and selinux, and even messed with iptable rules, and nothing. I still cannot reach the server with icmp.

So what gives? Do I need to reboot the server for the new rules to take effect? Am I missing some default setting or installation?

It's Ubuntu 9.04 32-bit.

Thanks,
Pierre

---

### Post by duanedesign on 2009-08-22
If your server is pesky about pings try reaching it with this nmap command.
```
nmap -v -A -PN  ip_address
```


To apply changes to your iptable
```
sudo iptables-save > /etc/iptables.rules
```

You may then change your iptables configuration by writing or editing your saved rules. To test them when you are done.
```
sudo iptables-apply < /etc/iptables.new_rule_set
```

To restore your settings when rebooting, edit /etc/rc.local and add this command anywhere above the line "exit 0"
```
iptables-restore < /etc/iptables.rules
```


One idea is
1.you could save your iptables (using the command above)

2.Flush them

```
iptables -F
```

3.try to ping the server while the iptables are flushed. If your ping is successful  then you know it is a problem with the iptable rules. If you cant ping then the problem lies elsewhere.

4.don't forget to iptables-restore to keep out the "Script Kiddies" :)


If it is your tables post the results of
```
iptables -L
```
-
-

---

### Post by lisati on 2009-08-22
Other than checking iptables settings, the best thing I can think of at the moment is to check your router's firewall settings and that ports are being forwarded properly.

---

### Post by pierrefar on 2009-08-23
Thanks for the help.

I flushed the rules, ping'ed and all packets were still lost. I can ping localhost but can't ping the server directly from itself (i.e. SSH in and ping server.com).

nmap finds only ports 22 and 80 open, so no surprises there.

I'm starting to think it's my host. I cannot ping any other site I know that's hosted with them, but I can reach all the ones I tried normally in a web browser.

---

### Post by koenn on 2009-08-23
it's possible the tcp/ip stack in the kernel is set to ignore pings, as can be seen in the value of /proc/sys/net/ipv4/icmp_echo_ignore_all

background: [http://ipsysctl-tutorial.frozentux.net/chunkyhtml/icmpvariables.html](http://ipsysctl-tutorial.frozentux.net/chunkyhtml/icmpvariables.html)

---

### Post by pierrefar on 2009-08-23
> **koenn said:**
> it's possible the tcp/ip stack in the kernel is set to ignore pings, as can be seen in the value of /proc/sys/net/ipv4/icmp_echo_ignore_all
Hi koenn

The value in that file is set to zero, which I assume means "don't ignore" and should let pings through.

As a side question: would changing this value (and otehr kernel settings) require rebooting?

Cheers,
Pierre

---

### Post by koenn on 2009-08-23
Yes, 0 means the feature is turned of. 
It's not really a file, it's a part of the kernel in RAM, represented as a file so you can manipulatate it with file tools. Because it's "live" you don't need to reboot when you change it.

you can set it to 1 with
```
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```
maybe give it a try, just in case 0 means 'true' and therefore 'ignore pings'

I once set a machine to not allow ping by running Bastille, a server hardening script. Maybe if you look through it, you'll find a yet another way to block pings, and you can check if your server has the corresponding setting somewhere

---

### Post by pierrefar on 2009-08-23
Thanks for the info. Setting it to 1 didn't fix it.

I know I don't have Bastille installed. I've looked at each process (as reported by htop) to see what it is and what it is doing. Nothing is running apart from the server, the PHP FCGI processes, and a few admin things like syslogd and DHCP.

---

### Post by koenn on 2009-08-23
I didn't mean you were running bastille. it's not even something you have running. You run it once, and it lets you set a number of settings, such as umask, tcpwrappers, file permissions on critical files, ... If I remember well, it also asks if you want to reply to pings. 

If you figure out how bastille turns of 'reply to ping', you can look there and see if your server has the same setting, whether it was set there by bastille, by hand, by another application, by cosmic rays, by squirrels, ...

---

### Post by wojox on 2009-08-23
pierrefar, was this all working before and just suddenly stopped?

---

