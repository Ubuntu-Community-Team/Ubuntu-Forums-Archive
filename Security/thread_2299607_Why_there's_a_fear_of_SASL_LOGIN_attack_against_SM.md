---
title: "Why there's a fear of SASL LOGIN attack against SMTP servers among sysadmins?"
date: 2015-10-19
forum: Security
---

### Post by papakota on 2015-10-19
Hello!
                            
                            I run Postfix on Ubuntu and yesterday I  noticed a SASL LOGIN attack against my server. Basically during about an  hour there was a long list of failed login attempts from the same IP.  An average it's one attempt every 1,5 sec. I have a password that  contains 7 pretty random characters+name (alltogether it's 14 chars).  With such a computation speed, it must take them centuries to  brute-force my password, then why spam robots do it? Looking for a pure  luck? Or a qwerty type of passwords?
                            On the other hand, why sysadmins have this  paranoia? They use fail2ban, other techniques. What for then?
                            Is there something that I'm not taking into account?

---

### Post by SeijiSensei on 2015-10-20
Did the login attempts use different usernames?  That's a pretty-common "dictionary attack."  I see such attempts against my IMAP and, especially, POP3 server using many common names or accounts like "admin."  I don't use fail2ban, but I do use [xinetd]("http://linux.die.net/man/5/xinetd.conf") to "wrap" the services and impose connection limits with the "per_source" and "cps" options.

---

### Post by papakota on 2015-10-20
No, I don't see any usernames. Here's one of 700+ lines with the same content from my mail.log file:
Oct 18 05:44:44 mail postfix/smtpd[17107]: warning: a6.4f.089f.ip4.static.sl-reverse.com[159.8.79.166]: SASL LOGIN authentication failed: authentication failure
If the issue continues, I'll probably turn to fail2ban, which seems to be the most known and most documented tool.

---

### Post by Habitual on 2015-10-22
[Think you have a strong password? Hackers crack 16-character passwords in less than an HOUR]("http://www.dailymail.co.uk/sciencetech/article-2331984/Think-strong-password-Hackers-crack-16-character-passwords-hour.html")

---

### Post by papakota on 2015-10-24
> **Habitual said:**
> [Think you have a strong password? Hackers crack 16-character passwords in less than an HOUR]("http://www.dailymail.co.uk/sciencetech/article-2331984/Think-strong-password-Hackers-crack-16-character-passwords-hour.html")

1) I don't trust mass media too much;
2)  In that article they were talking about cracking a password on a physical computer, not by sending requests online to a distant server. You think that my server (as opposed to the MULTIPLE GPU's as it was written in the article) can serve (process) tens (if not hundreds) of billions queries per second? The only thing that would happen is DoS in the end. But what it has to do with password strength?

So far what I've seen is a ONE query every 1,5 sec. At this rate, it would take them a few centuries at best to brute force my password.

---

### Post by Habitual on 2015-10-26
> **papakota said:**
> The only thing that would happen is DoS in the end. But what it has to do with password strength?
People love to re-use passwords?

fail2ban is a good choice.

---

