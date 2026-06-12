---
title: "iptables and --pid-owner option missing"
date: 2010-10-09
forum: Security
---

### Post by sganaway on 2010-10-09
Hello everybody,

i've an ubuntu 10.04 with the kernel 2.6.32-25-generic-pae.

i look that my iptables haven't the owner --pid-owner option! 

Why? there is a way to find it?

---

### Post by BkkBonanza on 2010-10-10
I haven't tested this to see if it's removed but did you read the man page for iptables. It only works in the OUTPUT and POSTROUTING chains and it states the syntax is --uid-owner and --gid-owner not --pid-owner.

---

### Post by bodhi.zazen on 2010-10-10
> **sganaway said:**
> Hello everybody,

i've an ubuntu 10.04 with the kernel 2.6.32-25-generic-pae.

i look that my iptables haven't the owner --pid-owner option! 

Why? there is a way to find it?

This option works, it would be better if you posted your iptables rule and why you think it is not working. Could be anything from a syntax error to a problem with the order of your iptables rules to you not understanding the protocol. 

```
root@maverick:~# iptables -A OUTPUT -m owner --uid-owner root -j ACCEPT
root@maverick:~# iptables -A OUTPUT -m owner --uid-owner bodhi -j DROP

```And it works as expected:

```
[B][B][COLOR=darkred]bodhi@maverick:~$ ping -c1 google.com
ping: unknown host google.com[/COLOR]

[/B][COLOR=green]sudo ping -c1 google.com
PING google.com (74.125.127.105) 56(84) bytes of data.
64 bytes from pz-in-f105.1e100.net (74.125.127.105): icmp_req=1 ttl=63 time=66.6 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 66.655/66.655/66.655/0.000 ms[/COLOR][/B]

```

---

### Post by sganaway on 2010-10-10
thanks for your help! :smile:

i'm looking for the 

    ... owner --pid-owner PID_OF_PROCESS

option.

i'v read about it in the netfilter documentation:

[http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-7.html#ss7.3](http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-7.html#ss7.3)

and i look that this documentation refers to the kernel 2.4 (i haven't found on the netfilter's site documentation about kernel 2.6!).

In this post 

[http://lists.netfilter.org/pipermail/netfilter/2007-January/067852.html](http://lists.netfilter.org/pipermail/netfilter/2007-January/067852.html) 

i've read that some changes introduced with the kernel 2.6.14, had take off this option.

(from [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.14) :

[NETFILTER]: Remove tasklist_lock abuse in ipt{,6}owner
    
    Rip out cmd/sid/pid matching since its unfixable broken and stands in the
    way of locking changes to tasklist_lock.
)

I've read that a similar functionality is provided by the owner --cmd-owner option, but with it i'm in the same situation of pid-owner: it doesn't exist.

So i ask if somebody know a way to get this functionality with the new kernel, or if somebody know a different way to block/allow traffic from a local application to the net...
..?..

---

### Post by bodhi.zazen on 2010-10-10
Hard to help you from that link, it is a long page.

I have already posted a working example of the syntax.

If you would like assistance, pleae provide relevant information.

1. Your current rule set.

2. The exact syntax you are using for your iptables rule.

3. What makes you think it is not working ?

Otherwise I can only post a link in return to your query :

[http://manpages.ubuntu.com/manpages/maverick/en/man8/iptables.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/iptables.8.html)

From your second link, the option "--pid-owner" is no longer supported and, IMHO, the netfilter documentation is often out of date (which is why I linked you to a more current man page).

The alternates are to use --uid-owner or --gid-owner. These option only work in OUTPUT or POSTROUTING and not in INPUT (as far as I know).

iptables does not block per application, for that you need selinux or apparmor.

---

### Post by BkkBonanza on 2010-10-10
Attaching iptables rules to **process id** is probably a bad idea anyway. Since process ids get recycled it's possible that when a process gets terminated the rules will stick around and attached to some other arbitrary process. I suspect problems with this kind of thing is one reason it was removed. You would have to have monitoring to watch processes and alter the rules.

You would be better off to create a special user and run your process under that user and then attach the iptables rules using syntax above to that user. 

That would be far more robust and you wouldn't have to have a monitor daemon to watch the process and alter iptables rules as processes started/died.

---

### Post by bodhi.zazen on 2010-10-10
> **BkkBonanza said:**
> Attaching iptables rules to **process id** is probably a bad idea anyway. Since process ids get recycled it's possible that when a process gets terminated the rules will stick around and attached to some other arbitrary process. I suspect problems with this kind of thing is one reason it was removed. You would have to have monitoring to watch processes and alter the rules.

You would be better off to create a special user and run your process under that user and then attach the iptables rules using syntax above to that user. 

That would be far more robust and you wouldn't have to have a monitor daemon to watch the process and alter iptables rules as processes started/died.

Thank you for adding that, I was considering posting some such information.

Again, if we knew what the OP was wanting to do exactly, we could probably give better advice.

---

### Post by sganaway on 2010-10-11
for BkkBonanza:
I think that you're right, when you say that it's a bad idea define a rule with a dynamic pid (and the cmd-owner is more suitable, if it was available-same problem-). But in my intention, i will control a traffic of a specific application that must be always run, and so its pid remain the same for its activity-time.(maybe i explain this better, in the rows below)

for bodhi.zazen
I haven't problem with iptables(my general script goes good), but i have problem with this ghost option.
The command that i used was:

sudo iptables -A OUTPUT -p TCP -m owner --pid-owner PID_OF_PROCESS -j ACCEPT

First of it,I have blocked all the outgoing traffic, because i will be sure that the only application, with the right to go on the net, is the application with that pid.
But now i understand that there's no way to find that option in the new kernel.

I think that apparmor would be a good solution, but i never use it before.
I start to read something about, and i try to use it for my intention.

thanks guys for your suggestions,
and if somebody know a way to make this control with iptables...tell me please!...

(what do you think, can we consider this post resolved?)

---

### Post by bodhi.zazen on 2010-10-11
iptables is not designed to block on a per application basis and, IMO, this functionality is not needed.

---

### Post by BkkBonanza on 2010-10-11
Besides, we have already indicated how you can do what you want. 
Here it is spelled out,

#create special user with no home or login ability
adduser --shell /bin/false --no-create-home myappuser

# run your app as that user
sudo -u myappuser myapp

# add rules to only allow that user to connect out
sudo iptables -A OUTPUT -m owner --uid-owner myappuser -j ACCEPT
sudo iptables -P OUTPUT DROP

---

### Post by sganaway on 2010-10-12
> **BkkBonanza said:**
> Besides, we have already indicated how you can do what you want. 
Here it is spelled out,

#create special user with no home or login ability
adduser --shell /bin/false --no-create-home myappuser

# run your app as that user
sudo -u myappuser myapp

# add rules to only allow that user to connect out
sudo iptables -A OUTPUT -m owner --uid-owner myappuser -j ACCEPT
sudo iptables -P OUTPUT DROP

:biggrin: Yeah!
thanks BkkBonanza, this is what i'm looking for!
first i haven't considered to use sudo -u for launch the application!

now i can forget the --pid-owner option!

thanks everybody for the help!

---

### Post by nealmcb on 2012-01-25
Another reason people want pid and/or uid information is to allow more detailed logging of connections.  See e.g. [http://superuser.com/questions/34782/with-linux-iptables-is-it-possible-to-log-the-process-command-name-that-initiat](http://superuser.com/questions/34782/with-linux-iptables-is-it-possible-to-log-the-process-command-name-that-initiat)

---

### Post by MarkieB on 2012-03-03
no longer participating in ubuntuforums.org

---

