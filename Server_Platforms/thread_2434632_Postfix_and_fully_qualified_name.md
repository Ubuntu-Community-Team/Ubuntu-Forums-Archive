---
title: "Postfix and fully qualified name"
date: 2020-01-08
forum: Server Platforms
---

### Post by fangorn2 on 2020-01-08
Hello,
I purchased a server from a hosting provider and I need to configure it. I also purchased a domain, say 'fireworks.com' and I decided to call my server 'ubuntu-18.04'.
How am I expected to edit /etc/hosts?

127.0.0.1   localhost
203.0.113.10   fireworks.com   ubuntu-18.04

or

127.0.0.1   localhost.localdomain   localhost
203.0.113.10   ubuntu-18.04.fireworks.com   ubuntu-18.04

?

Also, Postfix during initial configuration, asks to enter the fully qualified name of my domain.
Considering I want my email addresses be of in the form of [EMAIL="sam@fireworks.com"]sam@fireworks.com[/EMAIL] and not [EMAIL="sam@ubuntu-18.04.fireworks.com"]sam@ubuntu-18.04.fireworks.com[/EMAIL], what am I expected to enter as fully qualified name of my domain?

---

### Post by SeijiSensei on 2020-01-08
You need to configure an MX record in your DNS zone file that designates ubuntu-18.04.fireworks.com as the host that accepts mail for fireworks.com.

```
$ host -t mx ubuntu.com
ubuntu.com mail is handled by 10 mx.canonical.com.
```

Usually you want to accept mail for both fireworks.com and for ubuntu-18.04.fireworks.com. See the "mydestination" parameter in /etc/postfix/main.cf: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination). In fact, you should read all of that document at least twice.

And yes, use the second entry for /etc/hosts.  You might also want to include fireworks.com as an alias. These entries are purely local to your machine. They have no relevance for people sending you mail from outside. For that, the MX record is used.

---

### Post by fangorn2 on 2020-01-08
Thank you [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") for your reply.
With this configuration, will I be able to receive email sent to [EMAIL="sam@fireworks.com"]sam@fireworks.com[/EMAIL], or the email should be sent to [EMAIL="sam@ubuntu-18.04.fireworks.com"]sam@ubuntu-18.04.fireworks.com[/EMAIL]?
Also, what is the fully qualified name of my domain for Postfix?

---

### Post by SeijiSensei on 2020-01-08
If the MX record is correctly configured, and the "mydestination" parameter includes fireworks.com in the list of valid names, you can receive mail as [email]sam@fireworks.com[/email].

---

### Post by fangorn2 on 2020-01-08
Thanks [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195"), I would use as you suggested ubuntu-18.04.fireworks.com as destination of my MX record.
This is the first time I edit my DNS zone: would that be OK? Or it would be better to use fireworks.com or 2 MX records, one for ubuntu-18.04.fireworks.com and one for fireworks.com?

---

### Post by SeijiSensei on 2020-01-08
Mail for specific hosts don't require an MX record. You want to add an MX record for the domain:
```

@     IN     SOA     fireworks.com.     root.fireworks.com. (
[stuff]
)

      IN     MX      0 ubuntu-18.04.fireworks.com.

[etc.]

```
The "0" is a priority. You can have multiple MX hosts with different priorities.  The numbers establish a simple rank order. The lowest value will be tried first. If it's offline, remote servers will try the next server in the list.

Trailing periods are important.  You can specify the host as simply "ubuntu-18.04" or with a fully-qualified name like "ubuntu-18.04.fireworks.com". The trailing period refers to the root nameservers.

---

### Post by fangorn2 on 2020-01-08
Thank you [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")!

---

### Post by SeijiSensei on 2020-01-09
Let us know if this all works for you.  And if it does, mark the thread [SOLVED] using the Thread Tools drop-down above.

---

