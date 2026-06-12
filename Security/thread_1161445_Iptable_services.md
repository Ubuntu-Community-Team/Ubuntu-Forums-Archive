---
title: "Iptable services"
date: 2009-05-16
forum: Security
---

### Post by uupreti on 2009-05-16
Hello All!
I am exploring ubuntu since few weeks. It seems almost similar to other Linux distros like Redhat/Fedora/Centos to which I am more familiar since few years.

Now it's turn to explore **iptables** in ubuntu. Rules and chains seems similar but I just get surprised that I couldn't get any service to **stop **and **start** **iptables**.

This is what I used to do in redhat linux

edit **/etc/sysconfig/iptables** file and restart iptables by using **/etc/init.d/iptables restart| start |stop** or something like that. But I couldn't find any services for iptables in ubuntu. Is there any way to stop and start iptables in ubuntu?

---

### Post by uupreti on 2009-05-16
Hello All!
I am exploring ubuntu since few weeks. It seems almost similar to other Linux distros like Redhat/Fedora/Centos to which I am more familiar since few years.

Now it's turn to explore **iptables** in ubuntu. Rules and chains seems similar but I just get surprised that I couldn't get any service to **stop **and **start** **iptables**.

This is what I used to do in redhat linux

edit **/etc/sysconfig/iptables** file and restart iptables by using **/etc/init.d/iptables restart| start |stop** or something like that. But I couldn't find any services for iptables in ubuntu. Is there any way to stop and start iptables in ubuntu?

---

### Post by gettinoriginal on 2009-05-16
Hope this helps  :p   Welcome to Ubuntu
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by uupreti on 2009-05-16
I am sorry but I already saw that links of couple of others before posting my thread over here. I believe it doesn't cover what I am talking about. 

What if I want to stop iptables service using something like **service iptables stop** or **/etc/init.d/iptables stop**. Is there any way like this to stop service in ubuntu??

---

### Post by bodhi.zazen on 2009-05-16
Take a look at those "scripts". They do not really start or stop iptables, they configure it.

the stop script is basically iptables -F

the start script is however you configured it.

Ubuntu uses ufw

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

Not exactly the same mind you ;)

Personally I manually configue iptables and user iptabeles-save and iptables-restore.

Those scripts in RHEL/Centos/Fedora are a bit of a pain. If for example you add a custom rule, such as blacklisting an ip address, you then need to manually "/etc/init.d/iptables save" or your settings will be lost.

---

### Post by uupreti on 2009-05-16
But in my view if ubuntu assumes iptables as a services then there should be some way to stop services. Does it make sense? and as you suggested iptables -F to stop, it believe it will flushes the rule instead which I dont' want to do. I want to keep my rule as it is but only temporarily stop the services so that I can come back to same point where I left.

I am not sure if I am acting like dumb at this point. Coz I am used to with this thing for several years and couldn't find the way in Ubuntu..

---

### Post by ktrnka on 2009-05-17
ufw is ubuntu's frontend for iptables. So you should only have to enable and disable ufw.

To check if it's running:

```
sudo /etc/init.d/ufw status
```

[https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

---

### Post by bodhi.zazen on 2009-05-17
> **uupreti said:**
> But in my view if ubuntu assumes iptables as a services then there should be some way to stop services. Does it make sense? and as you suggested iptables -F to stop, it believe it will flushes the rule instead which I dont' want to do. I want to keep my rule as it is but only temporarily stop the services so that I can come back to same point where I left.

I am not sure if I am acting like dumb at this point. Coz I am used to with this thing for several years and couldn't find the way in Ubuntu..

I think your understanding of iptables is flawed. iptables is a kernel module not a server or daemon.

/etc/init.d/iptables is a bash script that configures iptables.

> root@Centos:~#/etc/init.d/iptables stop
[B][COLOR=darkred]Flushing firewall rules:                                   [  OK  ]
Setting chains to policy ACCEPT: filter                    [  OK  ]
Unloading iptables modules:                                [  OK  ][/COLOR][/B]

root@Centos:~#/etc/init.d/iptables status
Firewall is stopped.

[COLOR=green]root@Centos:~#iptables -L 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination [/COLOR]As you can see, all that happens is the rules are flushed. iptables is still active, just permissive.

Tell me, what is it you think I stopped with "/etc/inti.d/iptables stop" ?

How is it you configure your firewall ? I assume either you do not or that you use system-config-securitylevel or system-config-securitylevel-gui ? Those tools give you very limited options for iptables and are roughly the same as ufw.

You have been given a link to ufw more then once ;)

---

### Post by uupreti on 2009-05-17
yeah now I got some insights. And I think ufw is the one that I am talking about to enable and disable firewall rule. and I think iptables default nature is allowed, it is permissing everything even if it is disabled right?

I think I have long way to go for ubuntu administration..:(

---

### Post by uupreti on 2009-05-17
> **ktrnka said:**
> ufw is ubuntu's frontend for iptables. So you should only have to enable and disable ufw.

To check if it's running:

```
sudo /etc/init.d/ufw status
```[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

Thank you for clarifying me with good link. This is the exactly what I was looking for.

Thanks to admin also. You guys rocked...

---

### Post by takumaka on 2009-05-31
Usage: ufw COMMAND 

Commands: 
enable                enables the firewall 
disable            disables the firewall 
default ARG            set default policy to ALLOW, DENY or REJECT 
logging ARG            set logging to OFF, ON or LEVEL 
allow|deny|reject ARG        add allow, deny or reject RULE 
delete RULE             delete the RULE 
insert NUM RULE         insert RULE at NUM 
status             show firewall status 
status numbered        show firewall status as numbered list of RULES 
show ARG            show firewall report 
version            display version information 

Application profile commands: 
app list            list application profiles 
app info PROFILE        show information on PROFILE 
app update PROFILE        update PROFILE 
app default ARG        set profile policy to ALLOW, DENY, REJECT or 
               SKIP

---

### Post by uupreti on 2009-06-01
Thank you all guys for guides. Appreciated

---

### Post by Mintnacho on 2009-06-01
This was actually very useful to me as well. thank you

---

