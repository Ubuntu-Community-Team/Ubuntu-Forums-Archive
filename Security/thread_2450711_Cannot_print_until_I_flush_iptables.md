---
title: "Cannot print until I flush iptables"
date: 2020-09-19
forum: Security
---

### Post by manorbarndavid2 on 2020-09-19
I have installed iptables-persistent, done iptables -F, iptables-save to /etc/iptables/rules.v4 and 6, reboot.  I find I cannot print on a network connected printer, or log in to my router, but I can access the internet.  If I flush iptables again, it all works.  If I compare the listing of iptables before and after reboot, they are different.  Ubuntu 20.04.1, connected to network by ethernet.    How can I fix this

---

### Post by TheFu on 2020-09-19
Look through the rules for issues?
Do you do an iptables-restore /etc/iptables/rules.v4 just after networking is started?

---

### Post by manorbarndavid2 on 2020-09-19
If I do the restore after login it does work, but needs sudo to do it, I would like it to happen automatically so my wife as a non-techy can use the system without my help.

---

### Post by TheFu on 2020-09-19
> **manorbarndavid2 said:**
> If I do the restore after login it does work, but needs sudo to do it, I would like it to happen automatically so my wife as a non-techy can use the system without my help.

Yes, you should make it part of the network startup steps.  In the old days, that was trivial. Just add a post-up stanza to the interfaces file and be done.  In the new systemd world, you'll probably want to make a "unit" file and screw with all the dependencies for network startup.  No need for sudo at this level. Everything runs as root that way.

---

### Post by manorbarndavid2 on 2020-09-19
I am not familiar with the start up at that level, and would appreciate some pointers. Thank you

---

### Post by TheFu on 2020-09-19
[https://www.cyberciti.biz/faq/how-to-save-iptables-firewall-rules-permanently-on-linux/](https://www.cyberciti.biz/faq/how-to-save-iptables-firewall-rules-permanently-on-linux/)
The bottom half is systemd.

---

### Post by manorbarndavid2 on 2020-09-19
Thank you I will give it a try

---

### Post by manorbarndavid2 on 2020-09-20
Still no luck.  Booted up, flushed iptables, sudo iptables-save to /etc/iptables/rules.v4 and ip6tables to v6.  Reboot, no access to printer or to log in to router.  Sudo iptables-restore and ip6tables-restore from the rules files above.  Now it all works ok.  So the problem seems to be not loading the rules on start up, despite both iptables-persistent and netfilter-persistent both enabled

---

### Post by TheFu on 2020-09-20
How do I say this nicely.

Prove what you are claiming.

Please.

There are all sorts of claims, without any proof provided.  From here, it seems that what is being said is
> I did everything. It doesn't work.
Please show the proof, step-by-step, for what you've done.  Use select/pasted text inside code tags, not images. Nobody can correct issues when images are provided.

---

### Post by manorbarndavid2 on 2020-09-20
Yes, I will do that

---

### Post by The Cog on 2020-09-20
You can use the command **sudo iptables-save** to see what the current rule set is. You can save this to a file to do before/after comparisons like this:
```
sudo iptables-save > before.txt
iptables-restore /etc/iptables/rules.v4
sudo iptables-save > after.txt
```
Of course, the contents of after.txt should match the contents of /etc/iptables/rules.v4 but you might want to check that too.

---

### Post by TheFu on 2020-09-20
**meld** is a handy tool to visually compare two text files.
If you are on a server without any GUI, use **sdiff file1 file2** for a side-by-side diff.

People sometimes forget all the built-in text file and text processing tools that are built into every Unix-like OS.  There must be 100+ text processing, comparison, tools on your system already.  

This is partially why Unix people don't like using databases to store stuff.  If the data is inside a text file, we can parse, slurp, re-order, sort, search, exclude, chop, swap, the data inside easily.  Most of these things are easily handled with just a few tools "piped" together. More complex data can be handled with perl, python, ruby scripts that aren't too long.

---

### Post by manorbarndavid2 on 2020-09-20
It would seem to be a problem with iptables-persistent.  I checked the status, and it couldn't find the service.  I tried to re-intstall, and it tells me the latest version is already installed.  The netfilter-persistent service was active.

---

### Post by SeijiSensei on 2020-09-20
i don't see how we can really help if you don't post the complete ruleset.
```

sudo iptables -L -vn
sudo iptables -t nat -L -vn

```

---

### Post by The Cog on 2020-09-20
Are you using nftables instead of iptables? Does this command output anything?
```
sudo nft list ruleset
```

---

### Post by manorbarndavid2 on 2020-09-21
It looks as though iptables-persistent might be the problem.  I systemctl status and it told me it me the service was not found.  I did apt install and that said it was already the latest version.  netfilter-persistent service was active.

---

### Post by manorbarndavid2 on 2020-09-21
Thank you I will try both of those

---

### Post by The Cog on 2020-09-21
It may be that your installation is using nftables rather than the legacy iptables, and therefore using iptables->nftables compatibility translation when you enter iptables commands. That would explain why nftables-persistent is running.
So I think it would be a good idea to create and compare files containing the output of "nftables list ruleset" and see if the difference is there.
```
sudo nftables list ruleset > nft-before.txt
sudo nftables list ruleset > nft-after.txt
```
I think (from memory) that the nftables rules are saved in /etc/nftables.conf. 
You might also check to see whether package iptables-nftables-compat is installed:
```
apt search iptables-nftables-compat
```

---

### Post by manorbarndavid2 on 2020-09-21
This is the iptables -L -vn at startup

```
Chain INPUT (policy ACCEPT 368 packets, 248K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  302  262K ACCEPT     all  --  enp4s0 *       194.35.233.140       0.0.0.0/0           
   33  6382 DROP       all  --  enp4s0 *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 438 packets, 49639 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  374 63409 ACCEPT     all  --  *      enp4s0  0.0.0.0/0            194.35.233.140      
  125 11893 DROP       all  --  *      enp4s0  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination
```         

and this is the iptables -L -vn after restoring from /etc/iptables/rules.v4

```
Chain INPUT (policy ACCEPT 19 packets, 1877 bytes)  pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 18 packets, 2045 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination    
```     
 I tried to append the screen shot of Terminal entries but it won't let me post it

---

### Post by The Cog on 2020-09-21
Please use code tags when you paste code like that. It makes a big difference to readability, and preserves indentation which can be critical. While editing, click Go Advanced then you can highlight code and use the "#" button.

The OUTPUT chain before flushing is blocking all outgoing packets. That's wrong. I suggest that you edit /etc/iptables/rules.v4 and delete the lines that add those INPUT rules.

I'm not sure about the interaction between iptables and ufw, but I don't think the saved rules are what ufw would write. So I think you have a conflict between manually edited iptables rules and ufw generated rules. Hopefully someone more familiar with ufw can advise there.

---

### Post by manorbarndavid2 on 2020-09-21
The second part of the code was after restoring from rules.v4, so none of the restrictions are there to delete.  The content of rules.v4 is not being loaded into iptables on start up.  Netfilter-persistent service is active, and although I installed iptables-persistent, it is not recognised as a service.  Is there anywhere else the content of iptables could be coming from?

---

### Post by The Cog on 2020-09-21
I don't know. The restored one has fragments of ufw configuration in it, but not the full set of stuff that ufw normally configures. Have you knowingly used ufw? Could it be that ufw has a mangled configuration? I might be tempted to "sudo apt purge ufw", reboot and if you still want to use it, "sudo apt install ufw". But I don't know how ufw interacts with raw iptables configuration. 

Maybe you should remove iptables-persistent if you are using ufw to configure iptables. I don't know. Maybe someone familiar with ufw can help - I've never used it, so I don't know how ufw persists its iptables.

---

### Post by manorbarndavid2 on 2020-09-22
Thank you I will try purging ufw and see what happens

---

### Post by manorbarndavid2 on 2020-09-22
I purged ufw, then rebooted, no access to print, and could not ping the main router, but able to access internet through it.  Ran a shell script as sudo which restores iptables from /etc/iptables/rules.v4 and ip6tables  from v6, can now print and ping main router

---

### Post by manorbarndavid2 on 2020-09-22
```
david@david-NewDesk1:~$ sudo iptables -L
[sudo] password for david: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  unn-185-59-221-81.cdn77.com  anywhere            
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             unn-185-59-221-81.cdn77.com 
DROP       all  --  anywhere             anywhere            
david@david-NewDesk1:~$ sudo iptablesrest
david@david-NewDesk1:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
david@david-NewDesk1:~$ cat /sbin/iptablesrest
/sbin/iptables-restore < /etc/iptables/rules.v4
/sbin/ip6tables-restore < /etc/iptables/rules.v6
david@david-NewDesk1:~$ 



```
this is the terminal window from new start.  I don't know where the information in the iptables comes from, certainly not from rules because the lower set is obtained from restoring the rules. until I run the iptablesrest script I can't print or ping my main router, both work after running the script

---

### Post by SeijiSensei on 2020-09-22
Well, if this is one of your active rules, it's the likely culprit.

```

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             unn-185-59-221-81.cdn77.com 
DROP       all  --  anywhere             anywhere            

```
This allows outbound traffic to that one host and blocks all other output. If the default policy is ACCEPT, you don't need any other OUTPUT rules.  Just delete any rules that target the OUTPUT chain.

---

### Post by manorbarndavid2 on 2020-09-22
That's the point I am making, I have tried flushing it, which then allows it to operate, and saved the flushed tables, but when it reboots that rule has been changed again, and the one host it allows is one of a range of sites which I have no idea where they come from.  Netfilter-persistent is active and has the iptables plugins working

---

### Post by manorbarndavid2 on 2020-09-23
In the end, I have removed iptables and installed nftables and the problem has gone away.   Thanks to all those who have tried to help

---

### Post by kevdog on 2020-09-25
Hmm I dont know about nftables -- always used iptables. Glad you got if figured out.

---

