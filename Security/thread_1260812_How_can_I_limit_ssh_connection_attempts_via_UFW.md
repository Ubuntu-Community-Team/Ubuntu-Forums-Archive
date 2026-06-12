---
title: "How can I limit ssh connection attempts via UFW?"
date: 2009-09-08
forum: Security
---

### Post by jocampo on 2009-09-08
I am trying to accomplish this but via UFW

```

sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

```

Can I do the same with UFW rules? I am just trying to minimize or reduce Brute Force Attacks. Right now I have two main rules using UFW: one allowing SSH and other one allowing WWW (port 80) I would like to keep those but limiting the number of ssh connections per min also with above mentioned iptable rules...

Thanks in advance,

---

### Post by cdenley on 2009-09-08
```

sudo ufw limit ssh/tcp

```
From:
```

man ufw

```
> 
ufw  supports  connection rate limiting, which is useful for protecting
       against brute-force login attacks. ufw will deny connections if  an  IP
       address  has attempted to initiate 6 or more connections in the last 30
       seconds.   See  [http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)   for
       details.


---

### Post by bodhi.zazen on 2009-09-08
Or you can add those (iptables) rules in the ufw config files 

/etc/ufw/before.rules

---

### Post by jocampo on 2009-09-08
cdenley / bodhi

Thanks for reply, couple of questions ...

1. What's the purpose of "limit" when using UFW?
2. How can I add UFW tables, via "iptable" command?

This is what I was trying to do and for some reason is not working.

```

udo ufw allow ssh
sudo ufw allow www
sudo ufw default deny

sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP
```

The UFW lines work, but when I try to edit the iptables so I can restrict the number of ssh loging attempts to 3/min, it does nothing. I want to block all traffic but ssh and www but at same time, restrict the login attempts 'cause I recieve brute force attacks almost every day. Yes I am using denyhosts, no! I won't and I can not change port 22 :-)

I want to limit the login attempts via iptables but combining that with UFW rules.

---

### Post by cdenley on 2009-09-08
1.
```

sudo ufw limit ssh/tcp

```
The above command effectively does the same thing as
```

sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 30 --hitcount 6 --rttl --name SSH -j DROP

```

2.
If you append rules after UFW already created iptables rules, then your rules will only be checked if a UFW chain hasn't already accepted the packet. If you want to add the rules using the "iptables" command, use insert (-I) instead of append (-A).

If you want to configure UFW to add those custom iptables rules, add this to /etc/ufw/before.rules before "COMMIT":
```

-A ufw-before-input -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A ufw-before-input -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP

```

---

### Post by jocampo on 2009-09-08
[QUOTE=cdenley;7917578]1.
```

sudo ufw limit ssh/tcp

```

Thanks for reply

But, where do you specify the max attempts, like 3 per min, etc... and the timeframe, 60secs on this case

---

### Post by cdenley on 2009-09-08
> **jocampo said:**
> But, where do you specify the max attempts, like 3 per min, etc... and the timeframe, 60secs on this case

It does not appear that you can with the ufw command. It only filters after "6 or more connections in the last 30 seconds".

---

### Post by jocampo on 2009-09-08
> **cdenley said:**
> It does not appear that you can with the ufw command. It only filters after "6 or more connections in the last 30 seconds".

Got it, so ... in order to accomplish my goal, should I?

```

sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

```

and then ...

```

sudo ufw default deny

```

---

### Post by cdenley on 2009-09-08
No, that will still append your rules after UFW's chains. You want to insert your rules before the UFW chains.
```

sudo iptables -I 1 INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -I 2 INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

```

---

### Post by jocampo on 2009-09-08
Ok :-)

Let me try ... i understand UFW a bit but the way IPTABLES work, CHAINS, rules inside chains and precede, etc, is kind of confusing.... 

Thanks a lot for your help so far

---

### Post by bodhi.zazen on 2009-09-08
Thank you cdenley for your assistance.

@ jocampo

See : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

To see your rules, you should ;

```
sudo iptables -L -v
```

Please note, UFW is a nice set of rules, but it is a bit complicated to follow as they use a number of user specified chains.

---

### Post by jocampo on 2009-09-08
Still! No success....](*,)

Here's is what I'm doing in that order....

```

sudo iptables -I INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -I INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP
sudo ufw default deny
sudo ufw 

```

I can not connect via ssh! I tested with nmap and says 

```

PORT   STATE    SERVICE
22/tcp filtered ssh

```

which of course, results on my connection problem... :confused:

---

### Post by jocampo on 2009-09-08
Found a workaround but disappointed with myself :-(  My main goal was combine that with UFW but for some reason is not working. Part of the problem was the virtual machine itself; UFW was not working properly, I discovered that with "nmap". So I uninstall and reinstall and that fixed the problem. However, when combining UFW and IPTABLES something happen that the ssh port become filtered instead of open.

My workaround is with IPTABLES only

```

iptables -A INPUT -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -p tcp --dport ssh -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP
iptables -A INPUT -j DROP
iptables -I INPUT 1 -i lo -j ACCEPT

```

In that specific order. 

Honestly? not so sure about the syntax like what NEW, recent or update is for, but I'll investigate.

Armed with denyhost plus these basic rules the script kiddies will go away or think twice when checking how to break into my server ;-)

---

### Post by bodhi.zazen on 2009-09-09
You are having two problems

1. UFW re-writes your rules. So when you enable ufw you are removing your manual rules you added with your iptables command.

To add them with ufw you will need to edit /etc/ufw/before.rules

```
-A ufw-before-input  [FONT=monospace][/FONT]-i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
```

and on ...

IMO you are best using one or the other, not both.

2. I think this has been mentioned in this thread already, but ...

ORDER of the rules is CRITICAL

When you put

-p tcp -dport ssh -j ACCEPT 

that is is, ssh is accepted, no further rules are processed.

3. Random comment: You probably do not need both a rule to limit ssh in iptables / ufw and deny hosts, one or the other.

---

### Post by cdenley on 2009-09-09
> **jocampo said:**
> 
```

sudo iptables -I INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -I INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP
sudo ufw default deny
sudo ufw 

```

You're inserting the second rule before the first. The "-I" switch inserts the rule at the top, unless you specify the position to insert it at.
[http://ubuntuforums.org/showpost.php?p=7917735&postcount=9](http://ubuntuforums.org/showpost.php?p=7917735&postcount=9)
```

man iptables

```
If you want to allow connections to a server, you do have to configure UFW to allow it.
```

sudo ufw allow ssh/tcp
sudo ufw status
man ufw

```
> **bodhi.zazen said:**
> 
1. UFW re-writes your rules. So when you enable ufw you are removing your manual rules you added with your iptables command.

I think it used to, but UFW in jaunty seems to leave the INPUT, OUTPUT, and FORWARD chains intact so it will not interfere with user-defined rules. However, I also suggest using /etc/ufw/before.rules so the rules are persistent and they are put in the right place.
> **cdenley said:**
> 
If you want to configure UFW to add those custom iptables rules, add this to /etc/ufw/before.rules before "COMMIT":
```

-A ufw-before-input -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A ufw-before-input -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 --rttl --name SSH -j DROP

```

Also, I agree that using denyhosts and iptables rate-limiting is a bit redundant. I can't imagine a scenario where limiting connections would offer more security if they are banned after a few failed authentication attempts anyway, except perhaps a DoS attack which didn't involve authentication.

---

### Post by jocampo on 2009-09-09
Well, my issue is that for some reason, no matter of the already configured threshold for my denyhost file, people are running brute force attacks and server allow them to check for passwords 6,7 or 8 times, not using the limit I put. After that is blocked, yes, but wanted to enforce the rule via iptables.

I saw this article and thought was a good one: [http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/") but you folks are telling me, if 1st rule allow, 2nd one limiting will never be applied.

I would like to use UFW only in fact, on my www server is configured that way, but UFW does not provide the limit I am looking for, just IPTABLES let me customize that (3 attempts every 60 seconds)

On my webserver (besides denyhosts) UFW was configured and is working, this way

```

sudo ufw allow ssh
sudo ufw allow www
sudo ufw default deny
sudo ufw enable

```

Allows www traffic, let me connect via ssh, but block the rest ...

---

### Post by bodhi.zazen on 2009-09-10
> **cdenley said:**
> I think it used to, but UFW in jaunty seems to leave the INPUT, OUTPUT, and FORWARD chains intact so it will not interfere with user-defined rules. However, I also suggest using /etc/ufw/before.rules so the rules are persistent and they are put in the right place.

Thank you for that information. You are correct, UFW does not change the default INPUT OUTPUT or FORWARD tables.

I would have to look at the ufw chains though to see it simply adding a limit to INPUT would work, or if the ufw-before rules would accept ssh connections (sudo ufw allow ssh).

In general, I advise you use one or the other. Adding a few "simple" rules to ufw-before rules is what I needed to do in the past.

---

### Post by tagwolf on 2013-03-19
You can also use fail2ban and not have to deal with bruteforce attacks at all.

---

### Post by cariboo on 2013-03-19
4 year old thread closed.

---

