---
title: "ufw : easily ban an ip on all service"
date: 2009-02-24
forum: Server Platforms
---

### Post by mansonthomas on 2009-02-24
Hi,

When I review my logwatch email, I can see some evil chinese/russion hacker is trying hard to break my ubuntu server.

I've some firewall rule already set, but when you add a rule it comes behind all other.

I'd like to put a deny rule above all other in one command, to quickly ban thoses IP.

Any idea of how to do that with ufw?

Or maybe some other way exists to achieve that?

Thomas.

---

### Post by AliTabuger7 on 2009-02-24
I have to assume that the attacks are trying to get access using SSH. If that's the case, there are some great applications that will take care of that.

fail2ban
sshguard
denyhosts

They're in the Ubuntu repo, so they're easy to install. I can't speak for all of them, but at least some of them do not need any configuration.

I don't know how to block an individual IP using ufw, but the bigger problem is brute force attacks, and it would just be better to secure against all future ones, not just block the the attempts that have already happened. Know what I mean?

---

### Post by hictio on 2009-02-25
> **mansonthomas said:**
> Hi,

When I review my logwatch email, I can see some evil chinese/russion hacker is trying hard to break my ubuntu server.

I've some firewall rule already set, but when you add a rule it comes behind all other.

I'd like to put a deny rule above all other in one command, to quickly ban thoses IP.

Any idea of how to do that with ufw?

Or maybe some other way exists to achieve that?

Thomas.

You can use fail2ban, or any other tool to block brute force attacks.
But, if you want to edit your ufw rules, you can edit, via sudo, the file '/var/lib/ufw/user.rules' and then issue a:

```

sudo ufw reload ENTER

```

to reload the new edited rules.

As usual, if you only have remote access to the box you are editing the rules on, double and triple check for typos before issuing the reload.

---

### Post by HermanAB on 2009-02-25
It is also possible to automatically ban abusive scripts/users by using the iptables rate limit module.  That requires only a single line of code in /etc/rc.d/rc.local:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit -burst 5 -j ACCEPT

Rate limiting is an effective way to make any brute force attack infeasible.

Cheers,

Herman

---

### Post by mansonthomas on 2009-02-25
Thanks both,

I'll have a look on these tools !

Thanks for the tip on ufw ;)

Thomas

---

### Post by mansonthomas on 2009-02-25
Well I tryed sshguard, but there's not very much doc/howto to enable it.

So I'll try fail2ban.

Thomas

---

