---
title: "dovecot and Likewise-Open"
date: 2009-12-03
forum: Server Platforms
---

### Post by pytheas22 on 2009-12-03
I have a server running Ubuntu 9.04.  I joined it to my local Windows domain using Likewise-Open, following the instructions at [https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html).  I'm now able to log in to the machine using any account from the Windows domain, as well as using Linux accounts created locally on this particular machine (i.e., accounts whose credentials are stored in /etc/passwd rather than on the Windows domain server).

I also have a dovecot mail server on this machine, and use Squirrelmail to log in and check mailboxes.  I can log in to Squirrelmail using local accounts with no problem, but when I try to log in using an account from the Windows domain, it fails and logs the following to mail.err:
```

Dec  3 15:14:00 memail dovecot: imap-login: Aborted login (auth failed, 1 attempts): method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
```

(Note that there's no "user=<...>" value in the log message, which seems strange.)

I've tried a variety of combinations for logging in to Squirrelmail with accounts from the Windows domain, including just the username, username@domain, domain\username, and 'domain\username'.  None of them works, even though I can for example ssh 'domain\username'@localhost with no problem.

I'd be very grateful for any advice on solving or troubleshooting this further.  I can't find anything at all on Google involving authenticating with dovecot via Likewise.

I'm also happy to provide configuration files (dovecot.conf, etc.) if needed.

---

### Post by yvovandoorn on 2009-12-04
pytheas,

It sounds like the pam file for dovecoat needs to be updated to also point at the Likewise PAM module (lsass). I can assist you in this or you can give it a shot by looking at the other PAM files Likewise configures for you in /etc/pam.d

Regards,

Yvo van Doorn
SE with Likewise Software

---

### Post by pytheas22 on 2009-12-05
yvovandoorn: many thanks for your response.  I will take a look into this myself and post back if I need more help (or if I figure it out, I'll post what I did).

---

### Post by pytheas22 on 2009-12-10
Finally figured this out.  I found most of the answer in this [PDF file]("http://www.google.com/url?sa=t&source=web&ct=res&cd=2&ved=0CAsQFjAB&url=http%3A%2F%2Fwww.ubuntu.com%2Fsystem%2Ffiles%2FAD_whitepaper_20090807.pdf&ei=vlEhS6biMIyylAfrxfT9CQ&usg=AFQjCNHBK0B95LLNfx2WWLW8F2_sZqjnvA&sig2=NVfEUB6Phwz0A6NNrFvskw") from Canonical.  The solution was actually really simple.

After setting up Likewise-Open and joining my mail server to the domain, all it came down to was editing /etc/dovecot/dovecot.conf so that the auth_username_chars variable is uncommented, and adding a backslash (\) to that value, so that the whole line reads:
```

auth_username_chars = \abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
```

Importantly, I found that it was necessary to add the backslash to the front of the string of values.  The instructions in the PDF that I linked to above tell you to add it to the end, but doing that caused dovecot not to start properly because of errors in the configuration file.  I'm not sure what exactly its problem was, but I imagine that having a \ at the end of a line was screwing something up.

Users from my domain are now able to log in to the mail server using Squirrelmail (haven't tried an offline client yet but I assume it would work fine) using:
```

domain.example.com\username
```

as their username, along with their passwords from Active Directory.

Many thanks to the Likewise team for making such a great and easy-to-use piece of software available under a Free license.

---

