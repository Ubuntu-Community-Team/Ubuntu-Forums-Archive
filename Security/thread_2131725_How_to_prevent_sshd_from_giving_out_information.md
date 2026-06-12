---
title: "How to prevent sshd from giving out information"
date: 2013-04-02
forum: Security
---

### Post by stlu on 2013-04-02
Hi,

I've got a fresh install of Ubuntu with the openssh-server package open to the internet.  Being vaguely aware of the fact that this system is definitely in a risky position, I wasn't too surprised when I found it to be under attack today.

While my attacker at 190.85.48.194 continued to attempt root login, I went to the /etc/ssh/sshd_config file and changed PermitRootLogin to No, just to be extra-safe.

To my surprise, the login attempts in /var/log/auth.log stopped showing up as root, and now the attack is using different usernames at random.

It appears that the server is providing information to the attacker about which accounts are invalid, and this concerns me because it could find my real username and then focus on brute-forcing the password.

How do I stop the sshd from giving out this information?

Best I learn now with this system so I can fortify the ones that I actually care about.

---

### Post by CharlesA on 2013-04-02
It's just a bot trying to bruteforce your server. As long as you have a strong password or use keys, you should be ok.

I would suggest setting your firewall to do rate limiting so the logs don't show up as cluttered.

---

### Post by stlu on 2013-04-02
I am looking into an IP-based ban script.

Do you think I am right about sshd giving out information about which usernames are valid?

---

### Post by CharlesA on 2013-04-02
> **stlu said:**
> I am looking into an IP-based ban script.

Fail2ban can do that but I just use a simple rate limiting rule like this:
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

> Do you think I am right about sshd giving out information about which usernames are valid?

Doubt it. I check my server via logwatch and if I forget to reenable my firewall for whatever reason, the report I get looks something like this:

```
 --------------------- SSHD Begin ------------------------ 

 
Couldn't resolve these IPs:
    10.173.72.37.static.swiftway.net [37.72.173.10]: 2 Time(s)
 
 Didn't receive an ident from these IPs:
    180.149.253.167: 1 Time(s)
    222.240.161.179: 1 Time(s)
 
 Illegal users from:
    undef: 1019 times
       root [preauth]: 980 times
       Pos [preauth]: 10 times
       pos [preauth]: 10 times
       POS [preauth]: 4 times
       aloha [preauth]: 4 times
       ALOHA [preauth]: 2 times
       ALOHA1 [preauth]: 1 time
       Pos1 [preauth]: 1 time
       Pos2 [preauth]: 1 time
       Pos3 [preauth]: 1 time
       crashplan [preauth]: 1 time
       pos1 [preauth]: 1 time
       pos2 [preauth]: 1 time
       pos3 [preauth]: 1 time
       rootjar [preauth]: 1 time
    180.149.253.167: 37 times
       Pos: 10 times
       pos: 10 times
       POS: 4 times
       aloha: 4 times
       ALOHA: 2 times
       ALOHA1: 1 time
       Pos1: 1 time
       Pos2: 1 time
       Pos3: 1 time
       pos1: 1 time
       pos2: 1 time
       pos3: 1 time
    222.240.161.179: 1 time
       rootjar: 1 time
 
 Login attempted when not in AllowUsers list:
    root : 980 Time(s)

 Received disconnect:
    11: Bye Bye [preauth]
       180.149.253.167 : 37 Time(s)
       222.240.161.179 : 959 Time(s)
       37.72.173.10 : 2 Time(s)
       92.53.107.245 : 19 Time(s)
 
 ---------------------- SSHD End -------------------------
```

Or this.

```
--------------------- SSHD Begin ------------------------ 

 
 SSHD Killed: 3 Time(s)
 
 SSHD Started: 3 Time(s)
 
 Couldn't resolve these IPs:
    static.vdc.vn(123.30.127.253): 118 Time(s)
 
 Illegal users from:
    undef: 376 times
       root [preauth]: 350 times
       bin [preauth]: 10 times
       oracle [preauth]: 4 times
       crashplan [preauth]: 2 times
       teamspeak [preauth]: 2 times
       test [preauth]: 2 times
       babalau [preauth]: 1 time
       kylix [preauth]: 1 time
       msr [preauth]: 1 time
       nagios [preauth]: 1 time
       postgres [preauth]: 1 time
       zafir [preauth]: 1 time
    123.30.127.253 (static.vdc.vn): 4 times
       oracle: 3 times
       test: 1 time
    199.127.98.22 (199-127-98-22.static.avestadns.com): 6 times
       teamspeak: 2 times
       nagios: 1 time
       oracle: 1 time
       postgres: 1 time
       test: 1 time
    222.241.154.235: 4 times
       babalau: 1 time
       kylix: 1 time
       msr: 1 time
       zafir: 1 time
 
 Login attempted when not in AllowUsers list:
    bin : 10 Time(s)
    root : 350 Time(s)
 
 Received disconnect:
    11: Bye Bye [preauth]
       123.30.127.253 : 118 Time(s)
       199.127.98.22 : 58 Time(s)
       222.241.154.235 : 198 Time(s)
 
 ---------------------- SSHD End ------------------------- 
```

Both these snippets were reports for the previous day.

---

### Post by stlu on 2013-04-02
Thanks for the info,

  If I didn't clearly state my question about sshd giving away info to an attacker, I apologize for not asking clearly.

I checked on the official IRC channel, and someone there assured me that the attacker won't receive any confirmation if they picked a valid username from the system or not.  Likewise, they would not know if root was permitted to log in or not, it was just a freak coincidence that the root login attempts stopped after I made a config change.

I am trying DenyHosts first, since it doesn't use iptables, and should be easier for me to understand what it does.  Later I'll check out fail2ban which does use iptables, and work at understanding it.

---

### Post by CharlesA on 2013-04-02
Gotcha. :)

The only thing that will happen if someone doesn't enter the correct credentials is they get an error message and the attempt is logged.

As far as iptables goes, check this page out:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Azrayal on 2013-04-05
Another use full underused part of openssh is the Match feature, take a look at the base of the openssh config, you can lock down openssh to only allow ssh key users access with some configuration changes. This in turn negates the worry of password brute force attacks.

---

### Post by CharlesA on 2013-04-05
> **Azrayal said:**
> Another use full underused part of openssh is the Match feature, take a look at the base of the openssh config, you can lock down openssh to only allow ssh key users access with some configuration changes. This in turn negates the worry of password brute force attacks.

+1.

I've got my home server set to allow passwords for local connections via match. Quite handy.

---

### Post by HermanAB on 2013-04-06
You don't need any fancy scripts to protect a server. A single rate limit line in iptables will do:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

That will deter any and all idiots.

---

### Post by CharlesA on 2013-04-06
> **HermanAB said:**
> You don't need any fancy scripts to protect a server. A single rate limit line in iptables will do:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

That will deter any and all idiots.

Thanks for the rule. I've been running one like that without '--limit-burst 5' and it's been working fine so far.

---

### Post by HermanAB on 2013-04-08
Suitable rate limiting will prevent most forms of computer abuse.  It even limits spam in a mail server too.  If you configure a mail server to wait 10 seconds before answering any incoming connection, the incoming spam will drop to almost nothing, while legitimate messages will be unaffected.  

One can also use the above iptables rate limiting rule (6/minute) for a mail server instead of hacking the code.  The spammers will think that your server is a horrible crummy overloaded useless piece of junk and go away, while legitimate mail servers will feel an overwhelming pang of enmity and will wait patiently for the poor dear to respond.

---

