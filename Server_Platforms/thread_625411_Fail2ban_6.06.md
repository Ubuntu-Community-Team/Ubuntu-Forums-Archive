---
title: "Fail2ban 6.06"
date: 2007-11-27
forum: Server Platforms
---

### Post by flyboy320 on 2007-11-27
Hello All,

I was wondering if Fail2Ban 0.6.0-3 is the only version that will work on LTS 6.06 or will 0.8.1-3 work as well?

Thanks in advance.

Alan

---

### Post by HermanAB on 2007-11-28
IMHO utilities like fail2ban is the wrong solution to the problem.  You can easily prevent most all kinds of abuse with a one line iptables rate filter:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT
```

Put that at the end of rc.local to load on every reboot.

Cheers,

Herman

---

### Post by smileypaul on 2007-11-28
Along the same lines as HermanB..

[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/)

Follow that.. it will auto add the rules when the interface is brought up, and cleanly remove them when the interface is brought down.

---

### Post by MJN on 2007-11-28
IPTables is no good for stopping brute-force Apache authentication attacks, and indeed many other application-layer authentication (such as PHP logins).
 
I use it and it works well, extremely well.
 
Mathew

---

### Post by flyboy320 on 2007-11-28
Thanks for the emails.  I would like to stick with Fail2Ban and am wondering if anyone has gotten a version other than 0.6.0-3 to work on Ubuntu Dapper 6.06?

Thanks.

Alan

---

### Post by HermanAB on 2007-11-29
Note that you need not stop a brute force attack.  It is sufficient to slow it down to the point where it becomes impractical.  If you wish to protect a specific application that you compile yourself, judicious use of a few sleep(10) commands, can foil any brute forcer.

---

### Post by Cavalierdevache on 2007-11-29
> **flyboy320 said:**
> Thanks for the emails.  I would like to stick with Fail2Ban and am wondering if anyone has gotten a version other than 0.6.0-3 to work on Ubuntu Dapper 6.06?

Thanks.

Alan

The newest version of fail2ban (0.9 branch) is supposed to be coming soon, and it should work on 6.06 since it will use Python 2.3. 

fail2ban 0.8 doesn't work on Dapper since it  uses Python 2.4.

[http://www.fail2ban.org/wiki/index.php/Requirements](http://www.fail2ban.org/wiki/index.php/Requirements)

---

### Post by MJN on 2007-11-29
That's good to know - thanks for the heads up.
 
(Personally, I intend to upgrade to Hardy so it might not arrive before then anyway)
 
Mathew

---

