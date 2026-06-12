---
title: "ssh connection timeout issue"
date: 2012-05-06
forum: Server Platforms
---

### Post by xihad76 on 2012-05-06
hellow,

while i was trying to set some basic iptables rules in my recently purchased vps, i forgot to change the ssh port in sshd_config too and exit the ssh terminal because i was failing to save the rules. my intention was to log in as root again and save the iptables rules . then the next time i wanted to login to ssh it always shows a connection timeout error. Is it happening due to unchanged sshd_config or i made any mistakes in my iptables rules. what can i do to resolve this issue? I am a total newbie on vps configuration and any help will be greatly appreciated. thanks in advance.

the iptables rules look like below:

```
*filter
:INPUT ACCEPT [15:1712]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [15:9376]
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/255.0.0.0 -i ! lo -j REJECT --reject-with icmp-port-unreachable
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 999 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -j DROP
-A FORWARD -j DROP
-A OUTPUT -j ACCEPT
COMMIT

```

---

### Post by darkod on 2012-05-06
I am not too experienced in this, but it looks to me like you locked yourself out. Do you have a file that is loading these rules on every boot? If not, restarting the VPS might let you in again.

You didn't allow port 22 for SSH (or another port if you plan to change it) in the rules. So, it is blocking you too.

Also, the last three rules are sort of redundant. Usually you would set that with the general policy (first three lines), and not adding a rule at the end to drop packets. Something like:
*filter
:INPUT DROP
:FORWARD DROP
:OUTPUT ACCEPT

Then all the packets that are not accepted with one of the -A rules, will get dropped in the input and forward chains without having the drop commands at the end. Because the policy is set to drop.

---

### Post by xihad76 on 2012-05-06
> **darkod said:**
> I am not too experienced in this, but it looks to me like you locked yourself out. Do you have a file that is loading these rules on every boot? If not, restarting the VPS might let you in again.

You didn't allow port 22 for SSH (or another port if you plan to change it) in the rules. So, it is blocking you too.

Also, the last three rules are sort of redundant. Usually you would set that with the general policy (first three lines), and not adding a rule at the end to drop packets. Something like:
*filter
:INPUT DROP
:FORWARD DROP
:OUTPUT ACCEPT

Then all the packets that are not accepted with one of the -A rules, will get dropped in the input and forward chains without having the drop commands at the end. Because the policy is set to drop.

HI there,
thanks for the suggestion . it worked . after a restart i can login to ssh again. But all my iptables rules are gone as i failed to save them earlier with a user account other than the root. i want to set some pretty basic rules for now keeping http and ssh port open and i tried the command below:


```
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -i ! lo -d 127.0.0.0/8 -j REJECT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A OUTPUT -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
sudo iptables -A INPUT -p tcp -m state --state NEW --dport 999 -j ACCEPT
sudo iptables -A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
sudo iptables -A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
sudo iptables -A INPUT -j DROP
sudo iptables -A FORWARD -j DROP

```

and after that i got that timeout issue. can you please exactly tell me where to make some necessary changes on the above commands. thanks again

---

### Post by darkod on 2012-05-06
First of all, adding rules like that is temporary, after restart they are gone. Which helped you unlock yourself right now. :)

What you would usually do is create a file to store the rules, for example /etc/iptables.rules. You edit it with sudo permissions:
sudo nano /etc/iptables.rules

In there you put all your rules. You can load them yourself with:
sudo iptables-restore < /etc/iptables.rules

To make them load on every boot, the easiest way is to add a command in /etc/network/interfaces in the lo section (the loopback interface), like:
post-up iptables-restore < /etc/iptables.rules

That will load them at every boot just after the lo interface is loaded.

As far as rules are concerned, usually you would start by configuring DROP policy for the input and forward chains, and ACCEPT for the output chain.

Then you start adding rules only for traffic that you need to allow. Don't forget to allow the SSH connection. In those rules you don't have a rule for ssh. If your port is still 22, not changed, the rule you need would be like:
-A INPUT -p tcp --dport 22 -j ACCEPT

If you have a static public IP at home (always the same one), you can make it additionally secure by allowing only your IP but be careful since if the provider changes it, you are locked out again. And this time a restart won't help. :) The rule accepting ssh only from your IP would be like:
-A INPUT -p tcp -s <your public IP> --dport 22 -j ACCEPT

---

### Post by Lars Noodén on 2012-05-06
You can use [iptables-apply](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-apply.8.html) to help test the rules and ensure that you don't get locked out by your changes.  (There's another way using [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1posix.html) and [iptables-restore](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-restore.8.html), too.)

For your SSH connection you can do some rate limiting to defend against [brute force attacks](http://bsdly.blogspot.com/2012/04/if-we-go-one-attempt-every-ten-seconds.html):

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

The SSH rules can go about anywhere, say right after the WWW rules.

Also at the end, I would [change the rules from DROP to REJECT](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).

```

-A INPUT -j REJECT
-A FORWARD -j REJECT

```

It will make it easier to diagnose problems.

---

### Post by xihad76 on 2012-05-06
Thank you very much, guys!

So , the modified rules should be looked like this? 

```

*filter
:INPUT ACCEPT [15:1712]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [15:9376]
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/255.0.0.0 -i ! lo -j REJECT --reject-with icmp-port-unreachable
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -j REJECT
-A FORWARD -j REJECT
-A OUTPUT -j ACCEPT
COMMIT
```

---

### Post by darkod on 2012-05-06
Looks OK to me. Lets wait for Lars to confirm that rule for 22 is OK. I haven't used it like that.

As I said, if you saved these rules in a file, you can activate them immediately with:
sudo iptables-restore < /path/filename

Not sure how exactly iptables-apply works to test them first, but it sounds like a good idea. Anyway, if you don't configure the file to load the rules yet, even if you lock yourself out again a restart will delete the rules and let you in.

---

### Post by xihad76 on 2012-05-06
> **darkod said:**
> Looks OK to me. Lets wait for Lars to confirm that rule for 22 is OK. I haven't used it like that.

As I said, if you saved these rules in a file, you can activate them immediately with:
sudo iptables-restore < /path/filename

Not sure how exactly iptables-apply works to test them first, but it sounds like a good idea. Anyway, if you don't configure the file to load the rules yet, even if you lock yourself out again a restart will delete the rules and let you in.

Thanks Darko.

---

### Post by Lars Noodén on 2012-05-06
Looks fine, but test to be sure that it does what you want.  I'm not sure if it makes any difference but it could go after the WWW rules since presumable the WWW rules are going to be used much, much more than the SSH rule.

---

### Post by xihad76 on 2012-05-06
it seems like everything is working well so far. tried iptables-apply and it seems ok. Also i have been able to re-login after applying the rules. Thank you very much, guys!

Now my last question. as Darko mentioned above, to apply the rules on every reboot i need to place this command: 

```
post-up iptables-restore < /etc/iptables.rules

```

Besides, On a tutorial i found over internet someone suggested to use:

```
pre-up iptables-restore < /etc/iptables.rules

```

So, what actually pre-up / post-up does and which one should i use?

---

### Post by CharlesA on 2012-05-06
I use post-up on my server.

---

### Post by kevdog on 2012-05-07
The difference between post-up and pre-up in this example -- would be that the iptable ruleset is restored prior to bringing up the network interface or after bringing up the network interface.  I'm not sure if it really matters in this case since without a network interface up -- what purpose would net filter packets serve (except for possibly packet forwarding)? (Watch for a barrage of explanations on this one).

I usually just use post-up as well.

---

