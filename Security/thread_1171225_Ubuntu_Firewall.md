---
title: "Ubuntu Firewall"
date: 2009-05-27
forum: Security
---

### Post by okayneil on 2009-05-27
Hey everyone, to my shock i only realised that ubuntu's firewall needed to be configured as it wasnt activated out of the box :(

...so i grabbed "Firestarter" from the repository and configured the firewall accordingly. My question though is, do i need to run "Firestarter" everytime i boot into my machine or was configuring firewall through "firestarter" a one off i.e it will be activated all the time now?

---

### Post by lukjad on 2009-05-27
Wow, you managed to change your avatar in the time it took me to find the answer :)

First off from what I have heard "Firestarter" is not a good program to use to configure your firewall (iptables). Secondly, you already have firewall of sorts installed, if not activated. It is called [iptables]("http://en.wikipedia.org/wiki/Iptables"). From what I heard, messing with firestarter will cause you more problems then it is worth. What firestarter does is configure them. However, it's like using a word processor to make webpages. The configurations can get messy, and with time, especially if you start using another program to edit the iptables, can really foul up. [Example]("http://ubuntuforums.org/showthread.php?t=1116345").

---

### Post by ibuclaw on 2009-05-27
> **okayneil said:**
> Hey everyone, to my shock i only realised that ubuntu's firewall needed to be configured as it wasnt activated out of the box :(

...so i grabbed "Firestarter" from the repository and configured the firewall accordingly. My question though is, do i need to run "Firestarter" everytime i boot into my machine or was configuring firewall through "firestarter" a one off i.e it will be activated all the time now?

This is a common misunderstanding.

Ubuntu **has** a firewall, it is called **iptables**, but it is unconfigured OOB. Not that it really needs to be configured anyway if you only plan to use it for desktop usage...

By default, there are no services listening on your ports, thus, it gives the impression that there are no open ports on your machine. Although, as you install this package or and that application, there may be the chance that a new service will be installed along with it that will begin listening.

If you are behind a router, and you don't portforward any services, then the use of configuring a firewall becomes less so, as you will only be protecting yourself from people in your own network from connecting to you willingly. (Even if they can connect to you, most services that give access to your system - ie: ssh, telnet - require credentials).

Iptables starts everytime you boot your computer, so once you have configured your firewall, you can just leave it. Firestarter, UFW, and other "dumbed-down" frontends to the powerful (yet so inconceivable) iptables are only applications which configure iptables, they aren't a "firewall" themselves.

I don't really recommend firestarter. **GUFW** is a better, easier solution for the new user.


If you are at all confused by anything that I have said, then consult our [Ubuntu Security Thread]("http://ubuntuforums.org/showthread.php?t=510812").

That should clear up all confusing you currently have about security and Ubuntu.

Regards
Iain

---

### Post by okayneil on 2009-05-27
Thank you for the quick reply both of you. 

What i did know is that firestarter wasnt a firewall itself, simply a config tool. Ive taken your advice and added **GUFW **which although has a lot less config options just simply gets the job done.

Now that it has been configured, will it remain that way, or will i need to "switch it on" everytime i reboot?

:)

---

### Post by okayneil on 2009-05-27
> **okayneil said:**
> Thank you for the quick reply both of you. 

Now that it has been configured, will it remain that way, or will i need to "switch it on" everytime i reboot?

:)

Found the answer :)

> A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. **This is untrue !** Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest

---

### Post by ajgreeny on 2009-05-27
> Now that it has been configured, will it remain that way, or will i need to "switch it on" everytime i reboot?
No, that is all you need to do.  Everytime you startup it will be set exactly as you left it, with ports opened as you want, etc etc.

I have to admit, however, that with a single desktop machine with nothing networked to it other than a router, I have never bothered to use a firewall configuration app of any kind;  I just leave the default setup as it is.

---

### Post by lovinglinux on 2009-05-27
> **ajgreeny said:**
> No, that is all you need to do.  Everytime you startup it will be set exactly as you left it, with ports opened as you want, etc etc.

I'm not sure about this, because I remember when I was still using Firestarter, that I had to make it start at boot to apply the rules and there are a few threads about how to save iptables rules between sessions. I could be wrong tho, because I'm currently using moblock, which loads at boot and applies my iptables script automatically. Unfortunately, I can't reboot right now to test this hypothesis.

Anyways, if you ant to know if the rules will stick after a reboot, do it and paste the output of the command below without starting Firestarter or Gufw:

```
sudo iptables -L
```

> **okayneil said:**
> Found the answer :)

Yes, but that doesn't mean it will work after reboot. It means the firewall works even after closing the firewall manager interface. The problem is that, as far as I know, iptables rules are deleted between boots, unless you create a script to make them stick. Firestarter and Gufw will not forget the rules you create, but they won't apply them until you start the program again. That's what I think, but I could be wrong. Run the command I have posted above before running any firewall manager so we can check if the rules are sticking.

---

### Post by okayneil on 2009-05-27
> **lovinglinux said:**
> 

Anyways, if you ant to know if the rules will stick after a reboot, do it and paste the output of the command below without starting Firestarter or Gufw:

```
sudo iptables -L
```

This is what it spat out :)

> [FONT=monospace]sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination[/FONT]

---

### Post by lovinglinux on 2009-05-27
If you reboot and ran the command above without starting Gufw, then you are good to go and my theory was wrong :)

The rules created by Gufw are still present, so you are still protected.

Sorry about my paranoia.

---

### Post by okayneil on 2009-05-27
> **lovinglinux said:**
> If you reboot and ran the command above without starting Gufw, then you are good to go and my theory was wrong :)

The rules created by Gufw are still present, so you are still protected.

Sorry about my paranoia.

Ive actually rebooted a few times so if the output is correct then im all protected :)

---

### Post by lovinglinux on 2009-05-27
> **okayneil said:**
> Ive actually rebooted a few times so if the output is correct then im all protected :)

Good to know.

---

### Post by okayneil on 2009-05-27
> **lovinglinux said:**
> Good to know.

Thanx for your help mate ;)

---

