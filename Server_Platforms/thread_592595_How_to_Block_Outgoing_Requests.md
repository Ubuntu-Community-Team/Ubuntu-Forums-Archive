---
title: "How to Block Outgoing Requests"
date: 2007-10-26
forum: Server Platforms
---

### Post by fireboxtester on 2007-10-26
Hi guys,

I'm running Ubuntu 7.04 server and Apache to host a web application.  There will also be untrusted users on this server.  I want to be able to prevent them from sending spam, or launching a dos attack.

So I think what I want to do is use iptables to only allow outgoing connections to a whitelist of domains and drop all others.  I'd also want to prevent all outgoing email traffic.

Of course this needs to be set up in such a way that people can still access the web application hosted on Apache without problem.

Is this possible?  How would I set it up?  There's a lot to digest in the iptables documentation, so I'm just looking for some pointers and whether my goal even makes sense.

(For the sake of discussion, let's assume all other security concerns besides the ones mentioned have been handled.)

Thanks,

Greg
:popcorn:

---

### Post by whit on 2007-10-27
You can easily block all outgoing e-mail connections just by blocking destination port 25 for outgoing traffic with iptables. You could also use iptables to limit connections to specific outside IPs, but your description of your goal is vague (what kind of connections to what services?), so it's hard to say whether iptables is the right tool for it there.

---

### Post by fireboxtester on 2007-10-27
I don't know much about how an email server works, but I wouldn't want someone to be able to send email over any port.  Is that possible?  Using an external SMTP server would be ok though.

I'm thinking I now I want to allow outgoing connections to any IP address, but throttle/limit them so it would be impossible to initate a DOS attack.  Does that sound possible?

:guitar:

:-({|=

---

### Post by fireboxtester on 2007-10-28
bounce

---

