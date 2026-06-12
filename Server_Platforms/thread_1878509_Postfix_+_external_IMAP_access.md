---
title: "Postfix + external IMAP access"
date: 2011-11-09
forum: Server Platforms
---

### Post by balagosa on 2011-11-09
The situation:
Static IP + Postfix Mail + Postfix relay + Firewall (with corresponding port exceptions)

The problem:
1) The SMTP of my relay is OK, the IMAP of my relay is not OK.
2) I have tried to set the port forward of IMAP to my actual mail server, it WORKS. Is it safe to do this?
3) If #2 is not SAFE, how can I enable my IMAP on relay to be OK?

Any tips and suggestions is highly appreciated.

---

### Post by balagosa on 2011-11-10
bump

---

### Post by SeijiSensei on 2011-11-11
Postfix is only an SMTP server.  If you want to support IMAP, you'd need to run a server like dovecot or imapd as well as Postfix.

---

### Post by balagosa on 2011-11-11
let me check on that.

but still the issue remains, will it be safe to open my port to the mail server for IMAP transactions?

---

### Post by SeijiSensei on 2011-11-11
What you're really asking, I suspect, is whether the IMAP server software is secure.  I have publicly-accessible machines running dovecot and have never been compromised.  You will see the occasional "dictionary" attack against it, where an attacker will attempt to log in to the server with dozens or even hundreds of common user names.  You can control this to a degree by "wrapping" dovecot in [xinetd]("http://www.linuxfocus.org/English/November2000/article175.shtml") and using its "per_source" and "cps" directives.  An even better solution is to make sure your mail accounts have robust passwords.

You can install xinetd from the repositories.

---

### Post by lisati on 2011-11-11
I, too, run a publicly accessible machine that uses Postfix and Dovecot for IMAP. One of the precautions I have taken is to install [fail2ban]("https://help.ubuntu.com/community/Fail2ban") and amongst other things, I have configured it to block IP addresses which make multiple failed login attempts.

---

### Post by balagosa on 2012-01-06
> **SeijiSensei said:**
> What you're really asking, I suspect, is whether the IMAP server software is secure.  I have publicly-accessible machines running dovecot and have never been compromised.  You will see the occasional "dictionary" attack against it, where an attacker will attempt to log in to the server with dozens or even hundreds of common user names.  You can control this to a degree by "wrapping" dovecot in [xinetd]("http://www.linuxfocus.org/English/November2000/article175.shtml") and using its "per_source" and "cps" directives.  An even better solution is to make sure your mail accounts have robust passwords.

You can install xinetd from the repositories.

Hey, do you have a guide or a tutorial on how to implement xinetd?

Xinetd is already installed on my Fedora server by default, no need to download.

---

### Post by SeijiSensei on 2012-01-06
RH-flavored machines use service-specific definition files stored in /etc/xinetd.d.  I created a file called "imap" in this directory with the following:

```

service imap
{
        flags           = REUSE
        socket_type     = stream
        wait            = no
        user            = root
        server          = /usr/libexec/dovecot/imap-login
        log_on_failure  += USERID
        disable         = no
        per_source      = 10
        rlimit_cpu      = 5
}

```

If you take this approach, you cannot run dovecot as a daemon process since there can be only one listener on the IMAP port.  xinetd listens on the port and invokes the dovecot login processor when a connection is made.

See "man xinetd.conf" for details on the various options.  The last two were the ones I added to control attempted login bursts.  I've given thought to switching to lisati's approach using fail2ban, but haven't done so yet.

---

