---
title: "ufw changes not permanent?"
date: 2010-05-29
forum: Server Platforms
---

### Post by jorge_Y on 2010-05-29
Hi,

I have ufw on a 8.04 LTS machine and I have vsftp running on it. Now, I have a standard deny all but when I do

ufw allow ftp

and restart ufw is ok, I can reach my ftp. But... after reboot I can't and the 21 and 20 ports are not open anymore.
I know it is a shame :-) but I solved it in a very very dirty way. I have a script that takes ip ranges from a list file at boot and makes a blackhole routing for them and then, I included two lines in it commanding ufw to open ftp and restarting it.
It works, but I want to know why were my changes not permament.
thank you

jorge

---

### Post by spynappels on 2010-05-29
when you have the set of rules you want you can save the rules using iptables-save and then run iptables-restore pointing it to the save file as a startup script.

---

### Post by jorge_Y on 2010-05-29
> **spynappels said:**
> when you have the set of rules you want you can save the rules using iptables-save and then run iptables-restore pointing it to the save file as a startup script.
 
hi spynappels, 
thank you for your answer. Then the changes make through ufw are not permanent (and that's normal)? Oops.
Ok, then it is clear. But I don't see a big advantage of using ufw, then. Personally I think it is better to stay working with iptables and make the whole thing with it.
j.

---

### Post by CharlesA on 2010-05-29
I think the main thing with UFW is that it's easier to set rules as opposed to just using iptables itself.

It is a frontend for iptables, so iptables-save and iptables-restore would work fine with it.

---

### Post by spynappels on 2010-05-29
I'm sorry I should have made myself more clear.

Set the rules you want using UFW and then save those rules using iptables-save as CharlesA said. Then use iptables-restore in the startup script.

Although I tend to cheat and use Webmin for administering the firewall on my servers......

---

### Post by jorge_Y on 2010-05-29
ok, I understand.
But I will take a look to webmin anyway. :-)

j.

---

### Post by CharlesA on 2010-05-29
I cheat as well and use webmin to manage my firewall rules, but I'm probably just going to use iptables-save and iptables-restore if I need to screw with the rules in a way that might get me locked out. 

Just be careful about locking yourself out when messing with firewall rules, and you'll be fine. :-)

---

### Post by memilanuk on 2010-05-29
You should not have to use iptables commands in addition to the ufw commands just to have the changes made be persistent... are you sure UFW is enabled?

What does 'sudo ufw status' show?

---

### Post by mituw16 on 2010-05-29
personally I took 2 weeks to sit down and learn iptables in whole, after doing that I wrote a script that does everything I want, and then added a line at the end of /etc/init.d/rc.local to execute the script. 

So you say you want to make ftp ports 20 and 21 open right and drop everything else right?

*** this is an extremely basic and simple script that when executed will allow all outgoing, drop all incoming except for FTP, and ssh if you want ****

Then do this exactly....
1. create a new file in /etc called firewall.sh
2. nano the firewall.sh file and add this to it 

```
 
#!/bin/bash

### open FTP ports
iptables -A INPUT -p tcp -m multiport --dports 20,21 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A INPUT -j DROP


```

*** note, if you access the ubuntu comp via ssh, this will also stop all ssh, you would need to add this to open ssh 

```

iptables -A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

```


Next, 
nano /etc/init.d/rc.local 

add the following to the very end of your rc.local file

```

## execute firewall script
/etc/./firewall.sh

```

Cheers

---

### Post by jorge_Y on 2010-05-29
> **memilanuk said:**
> You should not have to use iptables commands in addition to the ufw commands just to have the changes made be persistent... are you sure UFW is enabled?

What does 'sudo ufw status' show?

I'm not in my office now. I'll post probably at monday what it says exactly.

But of course I have enabled ufw and status says it is loaded and had a list of ports open. I do the sudo ufw allow ftp and restart, and the list has only the 21 and 20 ports open and the other are gone. If I reboot and I have the situation again. 

I allways thought, the changes with ufw were permanent. I was almost sure to had so in a previous version.

j.

---

### Post by memilanuk on 2010-05-29
It'd be real interesting to see an actual screen output of that... because if it is, I'd almost say a bug report would be in order.

---

### Post by wysiwyg31 on 2012-12-03
I have a pretty similar issue (I didnt find this post before so I opened a [new topic]("http://ubuntuforums.org/showthread.php?t=2090759") )

In my case it is for SSH.

I have setup ufw to open:
- All ports to any connexion from local network (192.168.0.0/24)
- Port 22 for all IP (to be able to connect from internet with my smartphone)

it works but after reboot, connexion from internet is impossible.

if I check ufw status (with a connexion from my local network), it is enable and the rule for port 22 is here but my phone is blocked (I can see it in /var/log/ufw.log).

If I restart ufw or delete/re-add the rule, connexion from internet works again.

This is pretty weird

---

