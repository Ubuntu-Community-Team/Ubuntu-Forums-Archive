---
title: "fail2ban configuration"
date: 2012-02-23
forum: Security
---

### Post by Stvnx7 on 2012-02-23
Hi everyone. I am having trouble getting fail2ban to start banning. I've pasted the config file [here]("http://pastebin.com/vVi7xM8v"). 

The fail2ban-server is running, because I can see it when I run the "ps -e" command. 

My SSH server runs on port 443, so I have changed that in the ssh jail. (Not sure if it is better to edit it in this config file or in /etc/services file).

I want fail2ban to simply block the offending IP address, so I added "action = action_". I am not sure what the different between "banaction" and "action" is. 

Finally, I have never touched "iptables" except to run "iptables -L" to see if fail2ban had banned the IP address I was purposely typing a failed password from. 

Also, I made sure that the file I am editing is "jail.local" **not** "jail.conf".

Finally, it looks like fail2ban is being directed to correct log for ssh - "/var/log/auth.log".


Thank you for anyone that takes the time to help me figure this out.

---

### Post by HermanAB on 2012-02-24
Howdy,

Rather than fail2ban, you could just use a single rate limiting rule in iptables that will protect you against pretty much all brute force attacks:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

KISS

---

### Post by Stvnx7 on 2012-02-24
> **HermanAB said:**
> Howdy,

Rather than fail2ban, you could just use a single rate limiting rule in iptables that will protect you against pretty much all brute force attacks:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

KISS

I think I will implement this solution rather than fail2ban. I don't see the benefit of using another program when it is built into iptables. 

I need a how-to / guide on iptables so that I can understand what that rule is doing. 

However, I would still like to know why the fail2ban configuration seems to be wrong.

---

### Post by HermanAB on 2012-02-24
Just read the iptables man page about ten times.  It will eventually make some sense.

---

### Post by kevdog on 2012-02-24
> **HermanAB said:**
> Just read the iptables man page about ten times.  It will eventually make some sense.


Ha. Was that a joke?

---

### Post by Stvnx7 on 2012-02-24
> **kevdog said:**
> Ha. Was that a joke?

Lol.  I don't think it was a joke.  But I am looking at the man page, also looking at the How-to on the Ubuntu wiki. 

I have a high level understanding of it,   but need more. 

Guess I'll re-read.

---

### Post by Stvnx7 on 2012-02-24
> **HermanAB said:**
> Howdy,

Rather than fail2ban, you could just use a single rate limiting rule in iptables that will protect you against pretty much all brute force attacks:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

KISS

Herman, I am trying to understand your rule-specification. I want to understand what I am doing so please tell me if my interpretation is correct. 

**Assumption 1:** Because you haven't specified a table, iptables will edit the default table, which is "filter"

**Assumption 2:** Because you haven't specified a number after the "-I" command, it will insert the rule-specification as Rule 1. 

So therefore, you are editing the "INPUT" chain [or set of rules] in the "filter" table, and putting our new rule-specification as the first rule. 

**Question 1:** The "-p TCP" parameter specifies that the rule should apply to the TCP protocol. Why are we specifying TCP as the protocol? 

**Question 1B:** Would it be OK to change this to "-p all" so that it applies to all protocols? This seems to be the default, but I do not know what difference it makes, and if doing "-p all" would be more secure. 

The "-m state --state NEW" means that the packet has to open a new connection. 

The "-m limit --limit 30/minute" part specifies that the packet **will **continue to match at most 30 times per minute. After this limit is reached, the packet will no longer match. 

**Question 2:**I do not understand what "--limit-burst 5" actually does. 

The "-j ACCEPT" part says that if the packet matches our rule, then accept the packet. **Question 3:**what happens when our packet doesn't match our rule-specification? If this is the only rule-specification for my INPUT chain, then will iptables start ignoring packets from the offending IP after the limit is reached? 

Thanks for all the help!! I'm really excited to get this up and running. Once I understand this, I will want to further secure my computer, but one step at a time.

---

### Post by Stvnx7 on 2012-02-24
OK, I was trying to find an answer to the question that I posed above:

"The "-j ACCEPT" part says that if the packet matches our rule, then accept the packet. Question 3:what happens when our packet doesn't match our rule-specification? If this is the only rule-specification for my INPUT chain, then will iptables start ignoring packets from the offending IP after the limit is reached?"

I'm not at my computer at the moment (and SSH is not working), so I can't verify this, but it seems that the default policy for INPUT chain in "filter" table is set to ACCEPT. Should this be changed to DROP? 

Otherwise, the rule-specification above is not doing anything, right? If a packet matches my rule-specification, then "-j ACCEPT" means that the packet is accepted. If the packet does not match the rule-specification, i.e., it reaches the end of the INPUT chain, then it is still accepted by default. 

This leads me to believe that to configure iptables correctly, I need to change the default policy of INPUT chain to DROP. 

Any thoughts?

---

### Post by spynappels on 2012-02-24
As the computer is remote, you can avoid yourself becoming locked out by putting a rule at the end of the chain dropping all traffic and leaving the default policy as accept.

This way you won't get locked out by an (accidental) sudo iptables -F.

---

### Post by Stvnx7 on 2012-02-24
> **spynappels said:**
> As the computer is remote, you can avoid yourself becoming locked out by putting a rule at the end of the chain dropping all traffic and leaving the default policy as accept.

This way you won't get locked out by an (accidental) sudo iptables -F.

I hadn't thought about what would happen if I did run "sudo iptables -F". Great catch, and a very simple solution. 

I was worried that I had missed something logically in HermanAB's rule-specifiction. 

Another solution, which I think is a bit more 'elegant' since it is still only one rule, is to use the limit module with the "!" flag and change the target to "-j DROP", so that the packet **will not match** unless it reaches the limit, and once the limit is reached, it will match and be dropped. 

Would this be the right implementation of that rule:

"-m !limit --limit 30/minute -j DROP"

I'm not sure if the "!" flag means "don't match until limit is reach" or if it means "ignore the limit module completely".

---

### Post by kevdog on 2012-02-24
"-m !limit --limit 30/minute -j DROP"

I don't think you can write your rule that way -- I think it would be

! -m limit --limit 30/minute -j DROP

However this is just the double negative of the former statment:

-m limit --limit 30/minute -j ACCEPT

Both do the same.  When you write your iptable ruleset (you initally feed in your iptables rules through a script, you usually specifiy a default policy for the input/output/forward chain.  There are two basic schools of thought -- allow everything and write rules to DROP packets, or allow nothing (default policy drop) and then write rules that would explicitly allow packets.

Referring to the statements above -- your double negative statement would be more appropriate with a default ACCEPT policy whereby the 2nd rule would be more appropriate with a default DROP policy.

I hope that might help you.  Have you seen examples of script files set up to populate iptables?

---

### Post by Stvnx7 on 2012-02-24
> **kevdog said:**
> "-m !limit --limit 30/minute -j DROP"

I don't think you can write your rule that way -- I think it would be

! -m limit --limit 30/minute -j DROP

However this is just the double negative of the former statment:

-m limit --limit 30/minute -j ACCEPT

Both do the same.  When you write your iptable ruleset (you initally feed in your iptables rules through a script, you usually specifiy a default policy for the input/output/forward chain.  There are two basic schools of thought -- allow everything and write rules to DROP packets, or allow nothing (default policy drop) and then write rules that would explicitly allow packets.

Referring to the statements above -- your double negative statement would be more appropriate with a default ACCEPT policy whereby the 2nd rule would be more appropriate with a default DROP policy.

I hope that might help you.  Have you seen examples of script files set up to populate iptables?

kevdog, I have not seen many examples of script files yet. I'm still in my infancy of understanding iptables. However, I think we are saying the same thing. I'm trying to understand the rule-specification suggested by HermanAB (post #2), instead of just blindly copying it. 

I think what HermanAB failed to mention is that his rule-specification would require that the default policy for the INPUT chain is DROP. Otherwise (assuming that this is the only rule) after the limit is reached, and iptables cannot find a rule-specification to match the packet, the default policy would be to ALLOW anyway. Which means that with "-m limit --limit 30/minute -j ACCEPT" and default policy = ALLOW, we are doing absolutely nothing. 

The reason I bring this up is because the default policy in iptables is ALLOW, and HermanAB never mentioned that his rule-specification would work only if the user actively changes the default policy to DROP.

---

### Post by kevdog on 2012-02-24
I see your point.  I'm sorry he wasn't more complete.  It seems you are starting to grasp the use of iptables.  When using iptables, I always set my default policy as DROP.  Sometime this detail is overlooked when you are discussing specific rules.

---

### Post by Stvnx7 on 2012-02-25
> **kevdog said:**
> I see your point.  I'm sorry he wasn't more complete.  It seems you are starting to grasp the use of iptables.  When using iptables, I always set my default policy as DROP.  Sometime this detail is overlooked when you are discussing specific rules.

I think most users configure the firewall with the policy changed to DROP. I think that this is viewed as "turning on" the firewall.  I understand that this is not the case,  since iptables is never "off, " its just not doing anything by default.

I want to stick with policy set to ACCEPT by default because I just want to protect against brute force on an open port, and let the router firewall take care of the rest.  The trick is how to use the limit module when the policy on the chain is set to ACCEPT.

---

### Post by Stvnx7 on 2012-02-27
OK so the correct format to negate the limit is as follows:

"-m limit ! --limit 5/s"

The negate sign ("!") comes before --limit. 

This means that the rule **will** match **after** the limit is reached. This would be useful if the policy on that chain is set to ACCEPT, and you set the target for this rule to DROP. So, to say it another way, the rule would say "do not drop (i.e., do not match) until the limit is breached. After that limit, match the packet and drop it."

My source for this information is the [iptables tutorial.]("http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#LIMITMATCH")

So to recap: The "-m limit ! --limit 5/s" means **do not match**until the limit is reached, after which you can drop (-j DROP). 

The other rule "-m limit --limit 5/s" means **match** up to the limit, but not after.

---

