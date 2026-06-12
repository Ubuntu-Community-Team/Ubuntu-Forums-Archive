---
title: "UFW has stopped logging blocked packets"
date: 2010-03-17
forum: Security
---

### Post by kmr on 2010-03-17
Greetings,

On April 10, 2010, I upgraded some packages on my Ubuntu 9.04 server. This included an upgrade to "ufw 0.27-0ubuntu2". I rebooted the server, and all appeared to be fine.

Now I've noticed that UFW is not logging blocked packets since that reboot. It used to do this. It is still logging the allowed packets that I've configured it to log.

Here's what a "ufw status verbose" says:

```
Status: active
Logging: on (low)
Default: deny
New profiles: skip

(my rules are here)

```

Any suggestions? Not really sure what else to look at.

Thanks for any help!

kmr

---

### Post by kmr on 2010-03-17
> **kmr said:**
> 
On April 10, 2010, I upgraded some packages on my Ubuntu 9.04 server. This included an upgrade to "ufw 0.27-0ubuntu2". I rebooted the server, and all appeared to be fine.


Sorry, that should have read March 10. 

kmr

---

### Post by bodhi.zazen on 2010-03-17
What is it you are wanting exactly ?

IMO logging packets with iptables in the long ter is futile as I get thousands of packets.

IMO this is a job for snort. Snort sifts through your network traffic and "alerts" you to suspiscious traffic, you then spend your time investigating problems.

If you use iptables in this way you are going to be overwhelmed by innocuous traffic and eventually stop reading the logs -> so might as well turn logging off.

If you need a NIDS -> snort

If you need short term logging to debug rules, that can be helpful.

At any rate, see man ufw :

[http://manpages.ubuntu.com/manpages/jaunty/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/ufw.8.html)

Under the logging section, low ;

> 
  **low**    logs  all  blocked packets not matching the default policy (with
              rate limiting), as well as packets matching logged rulesSo, to give you more specific answers we would need to know what behavior you are wanting, what your rules are, and what is not working for you.

You can try ```
sudo iptables -L -v
```

But really you have not explained your goals, what is broken, what you expect, or posted your rules, so we can not really answer your question.

---

