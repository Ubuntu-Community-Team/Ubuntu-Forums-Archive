---
title: "iptables processing order"
date: 2007-07-23
forum: Server Platforms
---

### Post by murraymca on 2007-07-23
Hi,

I was wondering if anyone had any insight or could confirm the order iptables uses when running from a script.  I've tested this but perhaps I'm wrong but I found:

-  If I manually enter the commands (iptables -A INPUT etc, iptables -A OUTPUT etc) then the last command entered goes above the previous.  I'm very unclear so will try to give an example:
command 1:  drop
command 2:  accept
The accept command will 'match' first since it will be above the drop command (since drop was entered into the database first).

I have a script run at startup that has all my iptables commands, just like above, except it seems to be run a little different:
command 1:  drop
command 2:  accept
The drop command will 'match' first since it is on the very top...so it seems if running from a script the last command entered does not go above the previous.

Is this normal or am I doing something way wrong (if anyone can figure out what I'm talking about that is :P )

Apologies, I tried to make this as clear as possible :(

Thanks for any tips!

---

### Post by dreadlord_chris on 2007-07-23
using the **-A** switch should *append* the rule to the end of the chain referenced:
> 
-A, --append chain rule-specification
              Append one or more rules to the end of the selected chain.  When the source and/or
              destination names resolve to more than one address, a rule will be added for  each
              possible address combination.

so it should work the way you are expecting. You can inspect you iptables rulechains by:
```

sudo iptables -L | less

```

---

### Post by murraymca on 2007-07-23
Thanks for the quick reply, sorry for not reading the manual myself :(

Perhaps it is a bug, I'm running version 1.3.3...if I do this from a terminal:

sudo iptables -A INPUT -i lo -j DROP
sudo iptables -A INTPUT -o lo -j DROP
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INTPUT -o lo -j ACCEPT

I can successfully ping localhost (as the accept rules are added on top of the drop rules).

If I put the same into a script, I *can't* ping localhost, as it seems to be applied in the order above (not reversed as it is when entered at a terminal).

Has anyone else experienced this?

Thanks.

---

### Post by k_grdn on 2007-07-24
Hi murraymca,

When inputing iptables rules from a script the rules are processed in order of preference, so in simple terms the first rule hit wins other matching rules will be ignored.

Better practice is to set the default policy of the filter chain to DROP then you'll only need to add ACCEPT rules in order of preference placing heavily used services high up the chain.

A rule of thumb I always use is to allow unlimited traffic on the loopback interface before setting the default polices to DROP.

In a terminal as noted rules are appended to the end of the chain, it's also bad practice to apply rules from the terminal to a running firewall.

When entering these rules from the terminal what is your default policy set to?  Are you Flushing the chains?  Resetting the default polices?

Regards,

k_grdn

---

### Post by murraymca on 2007-07-24
Hi k_grdn,

Thanks for the information and quick response, and patience with my silly question.

I don't and have never entered rules from a terminal.  The main reason I tried was I read a tutorial on iptables and didn't realise that when you entered from a terminal, the last rule you entered is placed 'on top'.  So the loopback stuff I've posted was just to quickly test and confirm how things worked.  I just find it strange that it seems to behave differently when entering from a terminal or simply running the script.

Thanks again.

---

### Post by koenn on 2007-07-24
> **murraymca said:**
> Hi k_grdn,

Thanks for the information and quick response, and patience with my silly question.

I don't and have never entered rules from a terminal.  The main reason I tried was I read a tutorial on iptables and didn't realise that when you entered from a terminal, the last rule you entered is placed 'on top'.  So the loopback stuff I've posted was just to quickly test and confirm how things worked.  I just find it strange that it seems to behave differently when entering from a terminal or simply running the script.

Thanks again.

Weird  - can you reproduce it ? 
To my knowledge, -A (append) statements are added to the end of the chain, and statements are processed top to bottom until a match is found. Whether is at a prompt or from a script doesn't make a difference : 
Here's a demo. notice how the tcp stateme,t with 'destination' remains on top. 
```
# iptables -A FORWARD -p tcp -d 192.168.1.0/24 -j ACCEPT
# iptables -A FORWARD -p udp -s 192.168.1.0/24 -j ACCEPT
# iptables -L
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             192.168.1.0/24
ACCEPT     udp  --  192.168.1.0/24       anywhere

```
Same with loopback interface
```

# iptables -A INPUT -i lo -j DROP
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

# ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.

--- localhost ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

# iptables -A INPUT -i lo -j ACCEPT
# ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.

--- localhost ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2013ms

```
so the ACCEPT, given after the DROP, doesn't have any effect. 

And then, some of your statements don't make sense and should have produced an error : you can't use an output interface (' -o ') on an INPUT chain. You didn't get that error ? 
```
# iptables -A INPUT -o lo -j DROP
iptables v1.3.3: Can't use -o with INPUT

```

The only whay you can have the 2nd statement come before the first, as you say, is by using 'insert' , like iptables -I  (i.s.o. -A). It inserts on top by default.

---

### Post by murraymca on 2007-07-24
Hi,

Thanks, sorry those are not my configurations I just typed them in, and would have meant either one to be changed to -i or OUTPUT...thanks for picking it up all the same.

Just tested what I have been doing and now it is producing the same results as yourself:

muz@mlc:~$ sudo iptables -A FORWARD -p tcp -j ACCEPT
muz@mlc:~$ sudo iptables -A FORWARD -p udp -j ACCEPT
muz@mlc:~$ sudo iptables -L


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             anywhere


muz@mlc:~$ sudo ./test
muz@mlc:~$ sudo iptables -L
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             anywhere

Running from the script now produces the same results, however before testing this I did get an update to my packages...or maybe I was just dreaming.

My apologies for all this wasted time, I just re-read the article more slowly, and found that I'm a stupid moron, and wasted everyones time - please forget everything I've said hehe.

Thanks for your help and patience.

---

