---
title: "IPtables Script Import Order"
date: 2012-04-04
forum: Server Platforms
---

### Post by geudrik on 2012-04-04
I have a script that is several hundred lines long full of iptables rules (I've spent way too much time on this, and had far too much fun testing it) but when I run the script, the rules go in wrong - that is, when I do...
```

iptables -vnL
```
The order (being that iptables starts at the top of the chain and works its way down) is out of order, but it's ordered properly in the script.  Is there something I can do to fix this easily?

Here's a comparison... [ see attachments ]

So, though the rules in the script are ordered properly, when I run the script the Jump to ACCEPTED is listed BEFORE the logging rules.  Why is this?

---

### Post by geudrik on 2012-04-04
Another, asside question... How the heck do I change the default logging location of iptables?  I don't want it logging to /var/log/syslog... I want it logging to /var/log/iptables.log
Thoughts?

---

### Post by dfreer on 2012-04-04
You are using -I instead of -A to insert your rules. -I is an insert command, -A is append. Rules are being inserted at the beginning of every chain, instead of being appended to the end of the chain.

I'm not entirely sure if iptables allows you to change it's logging location. However, you can use --log-level and --log-prefix to help format your log messages, and then use rsyslog rules to redirect all output into /var/log/iptables.log.

P.S. If you are going to advise people in your signature to read the ******* manual, which is against the spirit of these forums, I'd advise you to do the same.

---

### Post by geudrik on 2012-04-06
You're absolutely right - I'm using -A in all rules except the block I posted and I cannot believe I missed that!  Thanks for pointing it out.

Problem solved - that was indeed the issue for that set of rules.

---

### Post by Vishal Agarwal on 2012-04-06
Your script looks very interesting and it looks like that you have actually invested a lot of time to that.
Can you add your script here so that others can also appreciate and learn from your deep  and hard working.

---

