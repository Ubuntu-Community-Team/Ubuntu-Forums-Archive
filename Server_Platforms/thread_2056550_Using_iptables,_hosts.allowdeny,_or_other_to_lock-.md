---
title: "Using iptables, hosts.allow/deny, or other to lock-down a system"
date: 2012-09-11
forum: Server Platforms
---

### Post by ricomoss on 2012-09-11
I have a server running Ubuntu 12.04.1 LTS (Server).  Ultimately I want to try and lock-down this server so that the following occurs:

Allow communication from all sources via ports 443 and 80 (https and http)

Allow communication from a specific set of IP addresses on port 22 and 5432 (ssh and postgresql)

Close all other ports for all communications.

Can anyone offer some solutions as to how I can accomplish this?  I'm familiar with iptables, hosts.allow and hosts.deny but I've never done extensive editing of these.

If there is another solution that I should pursue please let me know.

Thanks in advance.

---

### Post by ricomoss on 2012-09-11
Is it not possible to lock-down a system using these files?  Maybe I need another approach?

---

### Post by darkod on 2012-09-11
I would say iptables is enough. How familiar are you with it?

I would use a file to hold the rules, for example /etc/iptables.rules and load that file in /etc/network/interfaces. For example, in the group of commands where you specify the eth0 network details, you use:
```
post-up iptables-restore < /etc/iptables.rules
```That would load the rules as soon as the interface is brought up.

As for the content of the file, you are looking at something like:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 443 -j ACCEPT
-A INPUT -i eth0 -p tcp -s <source ip> --dport 22 -j ACCEPT
-A INPUT -i eth0 -p tcp -s <source ip> --dport 5432 -j ACCEPT

```That should sort out the basics. It also depends whether you want to route any traffic through that server (for example from interface eth0 to eth1) or not.

PS. Very important, if you don't have physical access to the server, only remote, be careful when playing with iptables since you can easily lock yourself out. If the server is in front of you, you can always log in and change things, but remotely, it's difficult.

---

### Post by SeijiSensei on 2012-09-11
You only need iptables for this; darkod gave you a good starting point.

I've only used hosts.[allow|deny] when I have "wrapped" a daemon with xinetd.  That can be useful when you want to apply rules that key on symbolic names like hosts or domains.  But if your rules are limited to IP addresses and ports, then iptables will do everything you need.

For details on the hosts.* files see "man hosts.allow".

---

### Post by Lars Noodén on 2012-09-12
When working with iptables you need to be sure not to get locked out.  You can use an [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1posix.html) job and iptables-restore   to restore the last known good set of rules.  

Or you could try using [iptables-apply](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-apply.8.html)

---

### Post by ricomoss on 2012-09-12
Thank you for the responses.  Unfortunately I don't have physical access to the server so I will test this on my home desktop before I apply this to the server I'm trying to lock-down.

I don't have much experience with iptables, in general, so I may be back with follow-up questions if things take a turn for the worse.

---

### Post by SeijiSensei on 2012-09-12
A quick and easy insurance policy against being locked out is to put a rule at the top of the set that grants your computer's full access like this:

```
iptables -A INPUT -s your.own.ip.address -j ACCEPT
```

If that is the first rule in the set, you'll be able to survive problems later on in the script.

---

### Post by darkod on 2012-09-12
> **SeijiSensei said:**
> A quick and easy insurance policy against being locked out is to put a rule at the top of the set that grants your computer's full access like this:

```
iptables -A INPUT -s your.own.ip.address -j ACCEPT
```If that is the first rule in the set, you'll be able to survive problems later on in the script.

On this subject, how does iptables-restore react to a rule with a syntax error? Does it load correctly all rules up to the problematic one?

I noticed with ufw that it seems it doesn't load any rules if there is an error in one, so it can be a real problem with remote servers. I used it for a project since at that time iptables looked too complicated for me, but because of this "issue" with rules and wrong syntax, I would stay clear of ufw from now on.

How is iptables-restore in that field? Can I count on it loading all rules correctly up to the problematic one?

---

### Post by SeijiSensei on 2012-09-12
I write my own scripts to handle iptables rule generation, but yes, I believe iptables-restore simply goes down the ruleset from top to bottom.  All the rules before the syntax error should be installed.

The scripts I've written generate the rules using various lists of addresses.  So, for instance, I have a file called /etc/firewall/permitted_remotes that contains the IP addresses of remote machines to which I want to grant full access.  Then the script runs a block of code like this:

```

cd /etc/firewall
[ -s permitted_remotes ] && PERMITTED_REMOTES=$(cat permitted_remotes)
for addr in $PERMITTED_REMOTES
do
    iptables -A INPUT -s $addr -j ACCEPT
done

```

I have lots of other similar iterations for permitted ports, blocked remote addresses, blocked internal addresses, etc., etc.  When you have a firewall in front of a couple hundred users with varying needs, it can get complicated quickly.

---

### Post by darkod on 2012-09-13
Here is another idea that can help you when creating your /etc/iptables.rules file.

Until you are sure it's working fine, don't let it execute with the post-up command in /etc/network/interfaces.

Instead, load the rules once by hand, with:
sudo iptables-restore < /etc/iptables.rules

If it locks you out, you only need to restart the server and those "wrong" rules will not be loaded on boot because you never set up the post-up.

Now, depending on the provider, you might have access to restart the server yourself, or you might need to call them to do it for you, but it's at least one way to get out of a locked out situation.

When you see that the rules are definitely not locking you out, you can do the post-up.

The above, together with the iptables-apply option mentioned earlier, gives you few options for testing until you are sure you have the rules right. Basically, the rules allowing you access are most important, as long as you have access, you can sort out other rules that are not working as you want them to.

---

