---
title: "iptables for Squid proxy server"
date: 2012-01-30
forum: Server Platforms
---

### Post by redjam on 2012-01-30
Hi all :)

Looking for some help...

I have set up Squid on a couple of my servers by following this guide:
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

All worked seamlessly on the first server ("server1") and I didn't have to make the suggested changes to iptables.

I then followed the same procedure on "server2" but it's not working - the service is running but the client connection is timing out.

The only difference is that server1 is using 10.04 / Squid 2.7.STABLE7 and server2 is using 9.04 / Squid 2.7.STABLE3.

I have looked at the iptables of each server and it looks like server2 is a lot stricter (see below).

So my questions are...

1. What can I do to fix server2 to make Squid work properly? Is this likely to be an iptables issue or is there some other problem?
2. Is server1 likely to be secure in its current state?

Sorry for the stupid questions - I'm supposed to be a humble programmer so this is something of a learning curve for me.

Thanks in advance for any help.


server1 iptables:

```

*filter
:INPUT ACCEPT [142666:39949925]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [22430:6840843]
:fail2ban-ssh - [0:0]
-A INPUT -p tcp -m multiport --dports 22 -j fail2ban-ssh 
-A fail2ban-ssh -j RETURN 
COMMIT

```


server 2 iptables:

```

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [5:370]
:fail2ban-ssh - [0:0]
-A INPUT -i lo -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -j ACCEPT  
-A INPUT -p tcp -m tcp --dport 80 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 443 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 53 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 53 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 69 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 69 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 25 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 110 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 143 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 123 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 20 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 21 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 3306 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 3306 -m state --state NEW -j ACCEPT 
-A INPUT -j DROP 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 
COMMIT

```

---

### Post by ruffEdgz on 2012-01-30
The reason why server2 isn't working correctly is because of the iptables rule set.

If you look at it closely, its saying:
> 
Any input TCP traffic with a destination port of 22, jump to 'fail2ban-ssh'...
'fail2ban-ssh' jumps to RETURN but doesn't any other rules to follow it

Here is what the man page for iptables says about RETURN:
> 
RETURN means stop traversing this chain and resume at the next rule in the  previous (calling) chain. If the end of a built-in chain is reached or a rule in a built-in chain with target RETURN is matched, the target specified by the chain policy determines the fate of the packet.

If you want server2 to be exactly like server1, I would just make sure the iptables rules are the same.

I would complete the following steps:
[LIST=1]
[*]Backup both of your iptables to a file using the 'iptables-save' command
[*]Take the saved iptables file from SERVER1 and scp it to SERVER2 (you can physically do this as well with a USB drive if needed)
[*]Use the SERVER1 iptables saved file to restore those rules onto SERVER2 using the 'iptables-restore' command
[*]Check the new iptables rules with 'iptables -L --line-numbers'
[*]If they match, try and complete what you need on SERVER2 to make sure it works the way it needs to
[/LIST]

Security is in the eye of the beholder. For example, you have a lot of ports that can be used on SERVER1 but that might be alright if you are using all of them to communicate to the server. If you aren't using some of those ports, it would be wise to remove them ASAP for security reasons. You can always tighten up those rules by placing in specific source addresses that can access a port and deny/reject the rest. That would be even better but totally up to you. You would have to take a look at your infrastructure/environment and see what else you can do to tighten security. I would just advise updating your system as much as possible to restarting the kernel whenever there are kernel updates.  

Hope this helps.

---

### Post by redjam on 2012-01-30
ruffEdgz, thanks a lot for the reply - appreciated.

Only thing is... I just realised that I made a mess of my original post and pasted the iptables the wrong way round :oops: Have fixed this now (it's one of those days). So the iptables list I said wasn't working IS working and vice versa.

Any ideas? Will scp the file from server1 to server2 and restore if nobody has any other suggestions :)

Thanks again

---

### Post by ruffEdgz on 2012-01-30
> **redjam said:**
> ruffEdgz, thanks a lot for the reply - appreciated.

Only thing is... I just realised that I made a mess of my original post and pasted the iptables the wrong way round :oops: Have fixed this now (it's one of those days). So the iptables list I said wasn't working IS working and vice versa.

Any ideas? Will scp the file from server1 to server2 and restore if nobody has any other suggestions :)

Thanks again

Well that is odd since I feel like the iptables on SERVER2 (this time around) would work better then SERVER1 but I guess the rules on SERVER1 isn't much and will let it through if it doesn't match.

If you want to stick with SERVER2's iptables rules, I would just append a logging rule to help pin point the problem you are having. I would still save your rules before applying this rule onto SERVER2 so you can always revert back:
```

# Find the line number for the -A INPUT -j DROP rule 
iptables -L --line-numbers

# Use that number to place the log rules above it
iptables -t fail2ban-ssh -I INPUT <num> iptables -j LOG --log-level <0-7>

```

Change the <num> to the number you found on the DROP rule. The <0-7> is the log level you want to set it for iptables logs to come in as (I like level 5 or 6 but it might generate a lot of logs so make sure you are able to revert back to the old rules or remove the LOG part quickly if it causes any slow downs). Having those rules will only print the connections that aren't accepted and will drop it after logging. From there, you can pin point why your connection keeps dropping and adjust the rules.

Hope this helps.

---

