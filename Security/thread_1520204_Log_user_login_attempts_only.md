---
title: "Log user login attempts only?"
date: 2010-06-29
forum: Security
---

### Post by lunit2 on 2010-06-29
Hi,


 How can I set up snort to only log and detect/capture logins using  root or any of the "homeusers" login accounts or names?


 I am new to snort.





 Thanks.

---

### Post by bodhi.zazen on 2010-06-29
> **lunit2 said:**
> Hi,


 How can I set up snort to only log and detect/capture logins using  root or any of the "homeusers" login accounts or names?


 I am new to snort.





 Thanks.

What are you wanting exactly ? Logins via what service ssh ? How is it you want snort to work ? are you asking if snort will log in a user who uses GDM (pam) ?

```
grep sshd /var/log/auth.log
grep root /var/log/auth.log
```

---

### Post by lunit2 on 2010-06-29
What I would log snort to do is log login attemps, on any port really that may be open.
So suppose someone would try to hack in and eventually try root or any of the homeuser's name (like regular users with a home directory, I call them homeusers) than I would want snort to detect and log it.

---

### Post by bodhi.zazen on 2010-06-29
> **lunit2 said:**
> What I would log snort to do is log login attemps, on any port really that may be open.
So suppose someone would try to hack in and eventually try root or any of the homeuser's name (like regular users with a home directory, I call them homeusers) than I would want snort to detect and log it.

Hmm ....

If that is all you want, I would not use snort, I would watch /var/log/auth.log

You would need to identify:

1. What services are you running that you want to monitor ? If you are not running a ssh server, who cares if someone tries to log into a non-existent ssh server as root ?

2. What users are you wanting to monitor.

From there you will need to write a few custom snort rules.

There are sample rules here :

[http://www.grape-info.com/doc/linux/config/snort-2.3.3-2.html](http://www.grape-info.com/doc/linux/config/snort-2.3.3-2.html)

At the very bottom of the page.

See also :

[http://packetstormsecurity.nl/papers/IDS/snort_rules.htm](http://packetstormsecurity.nl/papers/IDS/snort_rules.htm)

Search that second page for "login".

You then need to decide how you are going to deploy snort, where are you going to log the alerts ? a log file ? Barnyard ? Acid/Base ?

If you do not want to receive any other alerts, eliminate all other snort rules.

Honestly, snort may not be the right tool for the job, you may want to look at fail2ban, denyhosts, or watch the logs.

---

### Post by lunit2 on 2010-06-29
Yes that was good and helpful. Only the problem is that I want to watch any login on any port/service.

I was thinking something like:

```

log tcp any any -> 192.168.1.0/24 1:65535 (content: "user root"; msg:  "LOGIN/PORT root login";) 
log tcp any any -> 192.168.1.0/24 1:65535 (content: "USER root";  msg: "LOGIN/PORT root login";)

```

And "192.168.1.0/24" is my own IP address I guess? Because I want it to watch the external interface and IP.

Is that possible somehow?
I looked at fail2ban and denyhost but that is not exactly what I am looking for.

---

### Post by unspawn on 2010-06-29
> **lunit2 said:**
> I want to watch any login on any port/service.
Given the nfo provided and questions asked already could this mean you're either stubborn or do you need to complete a homework assignment regardless of it making sense or not?..


> **lunit2 said:**
> I looked at fail2ban and denyhost but that is not exactly what I am looking for.
That's because wanting to watch any login on any port/service *is a pointless exercise in futility*. No software counterpart exists for that ;-p
On a properly managed and hardened machine running a current distribution release there are easier, supported, more standardized, more efficient ways to accomplish what you're trying to. Fail2ban and denyhost can be part of that.


If you're going to write Snort rules then at least find yourself a recent version of the "Writing Snort rules" doc and use the Snort Community / Emerging Threats rulesets as documentation. Use existing variables like EXTERNAL_NET, HOME_NET and "any" as much as possible, use the "nocase" argument to keep you from having to write duplicate upper, lower, camel or whatever else case, use multiple "content" filters and always use a SID outside the already designated ranges: 
```
alert tcp $EXTERNAL_NET any -> $HOME_NET any (msg:"LOGIN/PORT root login"; content:"user root"; content:"|75 73 65 72 20 72 6f 6f 74|"; nocase; flow:to_server,established; sid:50001 rev:1;)
```

---

### Post by lunit2 on 2010-07-08
Alright so bodhi.zazen as you said "/var/log/auth.log" for checking and watching login attempts from users outside my net, is that correct?

Because what I was hoping for is some sort of IDS, Intrusion Detection system in the sense the word, that if someone has hacked/accessed the system using for example root that it would monitor and keep track of everything he does.
So like for example executing commands, uploading/downloading and changing/modifying files. You know what I mean?

Do you know some nice software to do that?


Thanks.

---

### Post by OpSecShellshock on 2010-07-08
> **lunit2 said:**
> Alright so bodhi.zazen as you said "/var/log/auth.log" for checking and watching login attempts from users outside my net, is that correct?

Because what I was hoping for is some sort of IDS, Intrusion Detection system in the sense the word, that if someone has hacked/accessed the system using for example root that it would monitor and keep track of everything he does.
So like for example executing commands, uploading/downloading and changing/modifying files. You know what I mean?

Do you know some nice software to do that?


Thanks.


To be honest, if anyone did manage to do that they'd be able to just shut off the tracking process anyway. But the risk of having that done remotely is low as long as there are no services listening for connections from the web.

---

### Post by lunit2 on 2010-07-08
Yes but than the idea would be that the person doesn't know of course. :)


I find it very useful.

---

### Post by bodhi.zazen on 2010-07-08
> **lunit2 said:**
> Yes but than the idea would be that the person doesn't know of course. :)


I find it very useful.

See : [http://la-samhna.de/](http://la-samhna.de/)

[http://la-samhna.de/samhain/index.html](http://la-samhna.de/samhain/index.html)

It runs in "stealth mode", so hard(er) to deactivate.

---

