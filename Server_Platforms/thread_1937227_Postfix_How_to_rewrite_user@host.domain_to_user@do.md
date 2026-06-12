---
title: "Postfix: How to rewrite user@host.domain to user@domain"
date: 2012-03-07
forum: Server Platforms
---

### Post by Demented ZA on 2012-03-07
Hi, I have an Ubuntu server with a dynamic ip :( running postfix. Postfix is set up to use my ISP's smtp server for mail relaying. Trouble is that when I send a mail from say root, my ISP's smtp server rejects it stating that [email]root@server.mydomain.com[/email] refers to an unknown domain.

```
host smtp.myisp.net[123.123.123.123] said:
    550-<root@server.mydomain.com>:Sender address rejected: 550 Domain
    not found (in reply to RCPT TO command)
```

smtp.myisp.net and [email]root@server.mydomain.com[/email] is not the true values for privacy reasons.

I believe I can use postfix's rewrite rules to rewrite [email]root@server.mydomain.com[/email] to [email]root@actualdomain.com[/email]? Is this the right way of doing it? Keep in mind, my server's actual domain is something like actualdomain.dyndns.org, since its on a dynamic IP.

I'm looking [here]("http://www.postfix.org/ADDRESS_REWRITING_README.html") for the answers, but its a lot of information for a n00b at mail servers.

Any help would be appreciated!

---

### Post by nsnidanko on 2012-03-09
You can accomplish this by canoical_mappings. There is a simple how to:

[http://ubuntuforums.org/showthread.php?t=38429](http://ubuntuforums.org/showthread.php?t=38429)

---

### Post by Demented ZA on 2012-03-09
Awesome, thanks! I'll give it a try and report back

---

### Post by Demented ZA on 2012-03-17
Just want to say thank you. That was exactly what I needed. Within a minute, I did the configuration, and it worked exactly as expected.

It would have taken me a long while on my own to find that canonical mapping was what I was looking for. I was researching address rewriting and masquerading for a week. Target fixation blinded me, I guess.

Thanks again.

---

