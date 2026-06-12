---
title: "Remote SSH in rescue mode?"
date: 2012-06-02
forum: Server Platforms
---

### Post by Empire-Phoenix on 2012-06-02
Well, I managed to lock myself out due to a false iptables entry.
Now the question is, if I let my hoster boot the server in rescue mode, will I be able to ssh into it and change that iptables entry? (openssh is installed without any real modifications)

In short: Does rescue mode start the sshd service?
Does it not use iptables (rules are set up in rc.local due to kvm)
So will the rc.local be executed? (If so i guess rescue mode wont help me)

Server is running the 12.somewhat version of 64bit ubuntu server.

Anyone knows any of those answers? I tried googleing around, but found no definite answer for both.

---

### Post by stlsaint on 2012-06-02
Resuce mode gives you root access but i do not think it will start ssh be default. You will be best to work with your provider in resolving this issue.

---

### Post by Cheesemill on 2012-06-03
Does your host provide any out-of-band access?

With my Linodes I can connect via a special IP/user/password that will let me SSH into my machines even if the networking is down.

[http://www.linode.com/faq.cfm#do-you-provide-console-access](http://www.linode.com/faq.cfm#do-you-provide-console-access)

As far as I recall booting in rescue mode doesn't even start the network, let alone SSH.

---

### Post by Empire-Phoenix on 2012-06-03
I cantacted them, and I can get kvm over ip, so I guess it will be solved.

---

### Post by Lars Noodén on 2012-06-03
Two things for future use: one is that you can use [iptables-apply](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-apply.8.html) to test your rules and let yourself back in if there is a mistake.  Or you can use [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1posix.html).

```

iptables-save > /tmp/works.iptables
echo "iptables-restore < /tmp/works.iptables" | at now +3
# now have 3 minutes to test new rules

```

---

### Post by Empire-Phoenix on 2012-06-03
Oh nice didn't knew that one, will definitly use that in the future

---

