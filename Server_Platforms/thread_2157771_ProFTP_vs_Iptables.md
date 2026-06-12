---
title: "ProFTP vs Iptables"
date: 2013-06-26
forum: Server Platforms
---

### Post by Di0g0 on 2013-06-26
Hi

For some reason I can't understand I'm having problems connection to FTP server!

My filezilla client can connect to the server but then it gives an error:

```
[COLOR=#323D4F][FONT=Lucida Grande]Response:    227 Entering Passive Mode ([/FONT][/COLOR]192,168,234,128,211,102[COLOR=#323D4F][FONT=Lucida Grande])[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Command:    MLSD
[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]Error:    Connection timed out[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Error:    Failed to retrieve directory listing[/FONT][/COLOR]
```

IPTABLES Rules:

```

*filter

-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT


iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#FTP
-A INPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT


#SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

#TS3 Server
iptables -A INPUT -p udp --dport 9987 -j ACCEPT  --> TS3
iptables -A INPUT -p tcp --dport 10011 -j ACCEPT  --> TS3
iptables -A INPUT -p tcp --dport 30033 -j ACCEPT  --> TS3
iptables -A INPUT -p udp --dport 30033 -j ACCEPT  --> TS3

#MTA Server
iptables -A INPUT -p tcp --dport 22005 -j ACCEPT --> MTA
iptables -A INPUT -p udp --dport 22003 -j ACCEPT --> MTA
iptables -A INPUT -p udp --dport 22126 -j ACCEPT --> MTA 


#Minecraft Server
iptables -A INPUT -p udp --dport 25565 -j ACCEPT --> Minecraft
```

Can someone teach me what is wrong here?

Thanks!

---

### Post by Doug S on 2013-06-26
Do you have the nf_conntrack_ftp module loaded? I think it is needed for passive mode.
You can probably delete the port 20 line, as passive mode doesn't use it, and it should have been --dport anyhow.

[Here]("http://ubuntuforums.org/showthread.php?t=2116042&highlight=passive+ftp+iptables") is fairly complete and thorough thread.

---

### Post by Di0g0 on 2013-06-27
How can I test that? Now I have passive ports opened, but doesn't work :S

---

### Post by Di0g0 on 2013-06-27
modprobe ip_conntrack gives error: 

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module ip_conntrack not found ubuntu

---

### Post by Doug S on 2013-06-27
I'm not sure what you are asking. Test what? If you want to test if you have the nf_conntrack_ftp module loaded, there is an example in post #9 of the link I gave, and here is my case (but I don't have it loaded, as I don't use ftp):```
doug@doug-64:~$ l[COLOR=#ff0000]smod | grep connt[/COLOR]
nf_conntrack_ipv4      19716  14 iptable_nat,nf_nat
nf_conntrack           81926  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
```Or maybe just force load it without even checking:```
sudo modprobe nf_conntrack_ftp
```Example:```
doug@s15:~/c$ [COLOR=#ff0000]lsmod |grep conntr[/COLOR]
nf_conntrack_ipv4      14487  2
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack           89998  6 xt_state,ipt_MASQUERADE,iptable_nat,nf_conntrack_ipv4,nf_nat_ipv4,nf_nat
doug@s15:~/c$ [COLOR=#ff0000]sudo modprobe nf_conntrack_ftp[/COLOR]
[sudo] password for doug:
doug@s15:~/c$ [COLOR=#ff0000]lsmod |grep conntr[/COLOR]
[COLOR=#ff0000]nf_conntrack_ftp[/COLOR]       13309  0
nf_conntrack_ipv4      14487  2
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack           89998  7 [COLOR=#ff0000]nf_conntrack_ftp[/COLOR],xt_state,ipt_MASQUERADE,iptable_nat,nf_conntrack_ipv4,nf_nat_ipv4,nf_nat
```If you are asking how to test/debug what you have now because it isn't working, I would be tempted to use tcpdump (or wireshark, if you prefer) and start looking at things at the packet level. Also maybe add some temporary logging statements in your iptables rule set to add insight into what is going on.

---

### Post by Di0g0 on 2013-06-27
Yap, but when I try to load it gives the error:

[COLOR=#000000]WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.[/COLOR]
[COLOR=#000000]FATAL: Module ip_conntrack not found ubuntu[/COLOR]

---

### Post by Doug S on 2013-06-27
I was writing my previous reply for awhile and never saw your post #4 until now.
What version of ubuntu are you running? Example:```
doug@doug-64:~$ [COLOR=#ff0000]uname -a[/COLOR]
Linux doug-64 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:43:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
doug@doug-64:~$ [COLOR=#ff0000]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise
doug@doug-64:~$
```

---

### Post by Di0g0 on 2013-06-27
Linux 2.6.18-308.el5.028stab099.3 #1 SMP Wed Mar 7 15:56:00 MSK 2012 x86_64 x86_64 x86_64 GNU/Linux



No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

---

### Post by Doug S on 2013-06-27
It is not clear to me why you are trying to load ip_conntrack, unless you still have the old names for things. Here is what I get for the various modules:```
doug@doug-64:~/init$ [COLOR=#ff0000]modinfo nf_conntrack[/COLOR]
filename:       /lib/modules/3.2.0-48-generic/kernel/net/netfilter/nf_conntrack.ko
license:        GPL
srcversion:     FAFCB79D3EBD373F9A5C8FA
depends:
intree:         Y
vermagic:       3.2.0-48-generic SMP mod_unload modversions
parm:           tstamp:Enable connection tracking flow timestamping. (bool)
parm:           acct:Enable connection tracking flow accounting. (bool)
parm:           expect_hashsize:uint
doug@doug-64:~/init$ [COLOR=#ff0000]modinfo nf_conntrack_ftp[/COLOR]
filename:       /lib/modules/3.2.0-48-generic/kernel/net/netfilter/nf_conntrack_ftp.ko
alias:          nfct-helper-ftp
alias:          ip_conntrack_ftp
description:    ftp connection tracking helper
author:         Rusty Russell <rusty@rustcorp.com.au>
license:        GPL
srcversion:     6569E3F9B93C4683D64A333
depends:        nf_conntrack
intree:         Y
vermagic:       3.2.0-48-generic SMP mod_unload modversions
parm:           ports:array of ushort
parm:           loose:bool
doug@doug-64:~/init$ [COLOR=#ff0000]modinfo ip_conntrack[/COLOR]
ERROR: modinfo: could not find module ip_conntrack
```

---

### Post by Di0g0 on 2013-06-27
I'm confused, very confused. 

I installed VSFTPD on a Virtual Machine for test purposes, and created this rules:

```
*filter

#  General
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/8 -j REJECT


#  Accept all inboud connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


#  Allow all outgoing traffic
-A OUTPUT -j ACCEPT


#  Allow HTTP & HTTPS
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT


#  Allow SSH
-A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT


#  Allow ping
-A INPUT -p icmp -j ACCEPT


#  Logs iptables
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7


#FTP
-A INPUT -j ACCEPT -p tcp &#8211;-dport 20:21 -m state &#8211;-state NEW,RELATED,ESTABLISHED


#TS3
-A INPUT -p udp --dport 9987 -j ACCEPT
-A INPUT -p tcp --dport 10011 -j ACCEPT 
-A INPUT -p tcp --dport 30033 -j ACCEPT 
-A INPUT -p udp --dport 30033 -j ACCEPT


#Minecraft
-A INPUT -p udp --dport 25565 -j ACCEPT
-A INPUT -p tcp --dport 25565 -j ACCEPT


#SAMP
-A INPUT -p tcp --dport 7777 -j ACCEPT
-A INPUT -p udp --dport 7777 -j ACCEPT


#  Drop all the other traffic
-A INPUT -j DROP
-A FORWARD -j DROP


COMMIT
```

Using this rules I can connect to my Virtual Machine via FTP without any problem! But when I try on my VPS I can't connect via FTP with the error given on the #1 post.

I tried a rules with the passive ports to but doesn't resolved the problem.

I can't understand what is bad on this iptables rules :o

---

### Post by Doug S on 2013-06-28
It sounds as though you are using active FTP on your Virtual machine and passive FTP on your VPS.
Have a look at [this]("http://slacksite.com/other/ftp.html") article.

---

### Post by Di0g0 on 2013-06-28
It's on passive mode on the VM.

Off topic:

If I SSH chroot users, they can execute game servers? Or they can't?

---

### Post by Doug S on 2013-06-28
> **Di0g0 said:**
> It's on passive mode on the VM.O.K. I'm stumped. I do not know why it is working on your VM.
For your chroot question, I don't know.

---

### Post by Kujua on 2013-06-28
Di0g0,

Firewall rules look okay. If you have nf_conntrack_ftp loaded, this rule you mentioned in post #10 should take care of the passive data connection:
```
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
Active FTP should anyway work since all out-bound connections are allowed.

Can you add a log rule right before '-A INPUT -j DROP', to know what packet the server is dropping?

Seems unlikely, but also ensure that there is nothing wrong on the client side.

---

### Post by Di0g0 on 2013-06-28
[COLOR=#000000]" If you have nf_conntrack_ftp loaded"

How can I see that?[/COLOR]

---

### Post by Kujua on 2013-06-28
I thought you had already loaded nf_conntrack_ftp and confirmed it as per Doug S's instructions. Please check post #5.

---

### Post by insidus on 2013-06-28
I have the same setup, heres what works for me.

Iptables
> -A INPUT -p tcp -m state --state NEW -m tcp --dport 49152:49252 --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT
-A INPUT -p tcp -m tcp --sport 1024:65535 --dport 20 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --sport 1024:65535 --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --sport 1024:65535 --dport 49152:49252 -m state --state RELATED,ESTABLISHED -j ACCEPT


Proftpd
> 
 PassivePorts                  49152 49252


Hope that helps.

/Insidus

---

### Post by Di0g0 on 2013-06-28
> **Kujua said:**
> I thought you had already loaded nf_conntrack_ftp and confirmed it as per Doug S's instructions. Please check post #5.

Ahh, but as I said when I try to load it gives an error:

```

[COLOR=#000000][COLOR=#000000]FATAL: Module nf_conntrack not found ubuntu[/COLOR][/COLOR]
```

---

### Post by Di0g0 on 2013-06-28
> **insidus said:**
> I have the same setup, heres what works for me.

Iptables


Proftpd


Hope that helps.

/Insidus

Worked!!!! Thank you VERY VERY VERY MUCH! 

I searched on the web for days and in 5 minutes you solved my problem :D, thank you one more time!

---

### Post by Kujua on 2013-06-29
Glad to know that you got it working now. Just wanted to point out one caveat.

Problem is that you have opened up all the passive ports. In the example of post #17 ports 49152 to 49252 are always open.
With your firewall rules, you were trying to restrict access to only some valid ports chosen by you. Now if you open up all passive ports, doesn't it beat your original goal of having a strong firewall?

The purpose of nf_conntrack_ftp module is to solve this problem. With it you have to open only port 21. The data port will be opened automatically (only) when required, enabling all FTP traffic to pass through while blocking the rest.

But if nf_conntrack_ftp is not present on your system, then I guess you don't have any other option.

---

