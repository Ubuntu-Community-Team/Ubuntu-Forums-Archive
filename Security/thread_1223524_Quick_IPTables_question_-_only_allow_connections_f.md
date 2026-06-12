---
title: "Quick IPTables question - only allow connections from specific IP block?"
date: 2009-07-26
forum: Security
---

### Post by kitcar on 2009-07-26
I'd like to restrict access to two ports on my machine to specific IP block (i.e. 67.234.*.*) .
 
I can't seem to figure out how to do this - I have found a tutorial on blocking a range ( [http://www.v7n.com/forums/dedicated-servers/3126-linux-block-ip-address-using-iptables.html](http://www.v7n.com/forums/dedicated-servers/3126-linux-block-ip-address-using-iptables.html) ) But want I want to do is the opposite - block everybody BUT a range.

Any help is appreciated -

---

### Post by alenis on 2009-07-26
Set policies to DROP, then open the two ports.

```

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
...


```

---

### Post by bodhi.zazen on 2009-07-26
Just a small piece of advice about setting your default policy to DROP ( -P ) ...

While this may seem "efficient" at first, I prefer to leave the Default policy as ACCEPT and add a rule at the end of the input chain to drop all.

iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

If you set your policy as DROP, and you flush your rules with iptables -F , you will lose all connectivity to the server =) . Not that that *ever* happened to me =)

---

### Post by koenn on 2009-07-27
> **kitcar said:**
> I'd like to restrict access to two ports on my machine to specific IP block (i.e. 67.234.*.*) .
 
I can't seem to figure out how to do this - I have found a tutorial on blocking a range ( [http://www.v7n.com/forums/dedicated-servers/3126-linux-block-ip-address-using-iptables.html](http://www.v7n.com/forums/dedicated-servers/3126-linux-block-ip-address-using-iptables.html) ) But want I want to do is the opposite - block everybody BUT a range.

Any help is appreciated -

block everything (by policy or with a catch-all rule as in bodhi.zazen's post), then write an accept rule for the range you want. Syntax will be the same as for blocking a range, except that you'll '-j ACCEPT' i.s.on '-j DROP' (or '-j REJECT')

---

### Post by kitcar on 2009-07-27
Thanks for all the help - I am a real newbie when it comes to IPTables - where do I put the port number and where do I put the approved IP address range in the above code?

Here's what I got so far, but it doesn't seem to work (i.e. for blocking access to the POP3 port to only domains which start with 216 - 

iptables -A INPUT -p tcp -m state --state NEW --dport 110 --source 216.0.0.0/8 -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW --dport 110 -j DROP

Any idea what I'm doing wrong?

---

### Post by kevdog on 2009-07-28
Do you have rules prior to these two rules that may have a drop stance?  Your two rules posted look good!

---

### Post by kitcar on 2009-07-28
I just tried cleaning my chain and re-entering the rules and it seems to be working properly now - well at least its blocking my IP block at home. Now to check to see if its letting the right ones through -  thanks everyone for the help!

---

