---
title: "How to allow SMTP for LAN?"
date: 2005-02-19
forum: Server Platforms
---

### Post by robmoore on 2005-02-19
I have a router that has the ability to send logs to an email address periodically. Unfortunately, it expects the SMTP server it uses to not require a login to send mail. I thought this wouldn't be a problem -- I'd just let it use my Ubuntu box as an SMTP server. I have postfix properly configured, but then discovered I can't connect to port 25 from other machines (it works fine as localhost). I poked around at the postfix config and noticed it limits connections on port 25 to localhost, so I changed this to allow anybody to connect to port 25 in master.cf (I'm behind a firewall, BTW, so no worries there). However, after I restarted postfix I find I still can't connect from another box. Does anybody know how I can get the SMTP port open?

Thanks,

Rob

---

### Post by Rottweiler on 2005-02-19
[QUOTE=robmoore]I poked around at the postfix config and noticed it limits connections on port 25 to localhost, so I changed this to allow anybody to connect to port 25 in master.cf (I'm behind a firewall, BTW, so no worries there).[/QUOTE]To make mine work I added this to master.cf:
  
[font=Courier New]  192.168.0.XXX:smtp inet n -     -       -       -       smtpd[/font]
  
  (replace XXX with the addr of the smtp box)
  
  I also had to add this to main.cf:
  
[font=Courier New]  mynetworks = 127.0.0.0/8, 192.168.0.0/24
 [/font]  
  I believe that's all it takes.

---

### Post by robmoore on 2005-02-19
Thanks, Rottweiler.

I changed the master.cf to

```
smtp inet n - - - - smtpd
```

which is supposed to be wide-open according to the header in the master.cf file.

I also had added the line

```
mynetworks = 192.168.0.100/28, 127.0.0.0/8
``` 
  
to my main.cf. The machine I'm trying to telnet from for testing is 192.168.0.100, so I think I should work, but it doesn't.

Rob

---

### Post by Rottweiler on 2005-02-19
[QUOTE=robmoore]
  I changed the master.cf to
  
  ```
smtp inet n - - - - smtpd
```
  
  which is supposed to be wide-open according to the header in the master.cf file.
  
  I also had added the line
  
  ```
mynetworks = 192.168.0.100/28, 127.0.0.0/8
``` 
    
 to my main.cf. The machine I'm trying to telnet from for testing is 192.168.0.100, so I think I should work, but it doesn't.[/QUOTE]The 192.168.0.100/28 is not right. It's a *network* specification, not a host specification. Just copy mine above - it should work assuming you're using a standard 192.168.0.xxx network.
 
 What is the address of the machine you're trying to connect to it from?

---

### Post by robmoore on 2005-02-20
[QUOTE=Rottweiler]The 192.168.0.100/28 is not right. It's a *network* specification, not a host specification. Just copy mine above - it should work assuming you're using a standard 192.168.0.xxx network.
 
 What is the address of the machine you're trying to connect to it from?[/QUOTE]

My router starts DHCP addresses at 192.168.0.100, so does 192.168.0.0/24 cover that address? I tried making the change you suggested and I still can't connect (from 192.168.0.100).

FWIW, I tried a portscan and port 25 doesn't seem to be open. Not sure what that means since I can connect locally via telnet to port 25...

```

rkm@antec:~ $  nmap -sT 192.168.0.101

Starting nmap 3.50 ( http://www.insecure.org/nmap/ ) at 2005-02-20 09:44 CST
Interesting ports on 192.168.0.101:
(The 1650 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
22/tcp    open  ssh
53/tcp    open  domain
80/tcp    open  http
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
3306/tcp  open  mysql
9090/tcp  open  zeus-admin
10000/tcp open  snet-sensor-mgmt

Nmap run completed -- 1 IP address (1 host up) scanned in 0.392 seconds

```

---

### Post by Rottweiler on 2005-02-20
[QUOTE=robmoore]My router starts DHCP addresses at 192.168.0.100, so does 192.168.0.0/24 cover that address?[/quote]No. That would tell it the subnet was smaller than it really is. The ".0" and ".255" addresses are "special" and changing the mask changes where .0 and .255 fall.
    
 > FWIW, I tried a portscan and port 25 doesn't seem to be open. Not sure what that means since I can connect locally via telnet to port 25...Change master.cf to
    
    [font=Courier New]  192.168.0.101:smtp inet n -     -       -       -       smtpd
    
    [font=Verdana]Assuming the smtp machine is still .101. When the address is in mine port 25 is open when it just says 'smtp' port 25 is closed. Tho that seems contradictory to the explanation in master.cf.
    [/font][/font]

---

### Post by robmoore on 2005-02-20
Indeed, that solved it! I guess the problem I was having when I initially tried it was the fact it was set to listen on the loopback device (localhost) rather than 192.168.0.101.

Thanks again, R.

Rob

---

