---
title: "changing port number in iptables"
date: 2008-07-24
forum: Security
---

### Post by sp0nge on 2008-07-24
So I'm new to iptables, just configured today. I have gotten it to work correctly to this point. Now I want to change the port number for ssh. I have been able to add but I don't think I understand how to change the port that has already been established.

---

### Post by kevdog on 2008-07-24
The port the ssh daemon listens on is controlled via the sshd_config file.  Access to the port (any listening port) is granted by default unless you close access to ports with iptables.

---

### Post by sp0nge on 2008-07-24
Thank you for the input. I set everything as the default when I configured the server. SSH is working just fine. But now that I'm working to harden the server, I wanted to change the port number. I have already configured access through IPtables upon initial config, but now I'm wanting to change this. 

I changed /etc/ssh/sshd_config to listen on the proper port, I have opened the port through the router. Now all I need to do is to open the port via iptables (and close port 22), and I should be able to connect remotely again.

---

### Post by kevdog on 2008-07-24
How are you configuring your iptables?  Through a script?  Do you have a default drop policy?  If so then you just need to remove access to the port 22.

Do you want to supply limits to those connecting through the port (like attempted connections and such), or just open the port up for any one to access.

The simplest example would be (without any limits)

iptables -A INPUT -p tcp --dport <WHATEVER PORT SSH IS RUNNING ON> --syn -m state --state NEW -j ACCEPT

---

### Post by sp0nge on 2008-07-25
When I configured iptables, the only drop policy was to drop all ports other than the 2 I opened (being 22 and 80). I did this all manually, entering the commands one rule at a time:

```
$ sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
$ sudo iptables -A INPUT -j DROP
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,EST  LISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Can I change the ssh port as simply as: 
```
$ sudo iptables -A INPUT -p tcp --dport (MY PORT# HERE) -j ACCEPT
```

:confused:

---

### Post by kevdog on 2008-07-25
First its easier to put all those commands in a shell script file so you can avoid typing them.  And yes instead of using ssh, use the exact port number.

The script would be something like:

#!/bin/sh

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
$IPTABLES -A INPUT -i eth1 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

exit
### EOF ###

Again you need to modify the above to your needs, but that gives you a head start

---

### Post by sp0nge on 2008-07-26
Thanks for the input. 

After reading your suggestions, I am curious- 

do you see a benefit of writing the shell script over inputting my changes, saving the file, and setting the saved file to run on startup?

---

### Post by kevdog on 2008-07-26
There is nothing wrong with your method with the iptables-save and iptables-restore commands.  However what if you want to make changes in the future or modify the command set?  For me (maybe not for others so just remember my point of reference), its easier for me to make changes to my shell script and add or delete ports I want to open or close.  The beginning of the script flushes the old rules contained within iptables and then adds them.  

Either way will work, but for me I find the shell script method easier.

---

### Post by The Cog on 2008-07-28
> **sp0nge said:**
> do you see a benefit of writing the shell script over inputting my changes, saving the file, and setting the saved file to run on startup?

I see one big benefit. When writing your own scripts, you can add comments. Not a biggie, you might think, but as the list of comments gets longer, having a comment in there saying why you did certain things can become very important. Even just a note mentioning that this port is being allowed because of such-and-such application can save lots of heartache in 6 months time. iptables-save/restore cannot save comments.

---

### Post by kdorf on 2008-07-28
> **kevdog said:**
> There is nothing wrong with your method with the iptables-save and iptables-restore commands.  However what if you want to make changes in the future or modify the command set? 

You can do this by manually changing the iptables-save file.

However, as the above poster noted, shell scripts are nice for comments.

---

