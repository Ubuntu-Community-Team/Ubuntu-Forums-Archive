---
title: "Trying to Authenticate Dovecot against Kerberos"
date: 2010-06-14
forum: Server Platforms
---

### Post by Lucky. on 2010-06-14
I recently followed [this howto](https://help.ubuntu.com/community/POP3Aggregator) on installing Dovecot & setting up an aggregation service.  It works great for plaintext passwords, but I was hoping to try Kerberos out (I already have a functioning domain & kdc - works great).

I tried following [these instructions](http://wiki.dovecot.org/Authentication/Kerberos), but didn't have any luck.  I still can't authenticate with GSSAPI.  When I type

```

a authenticate GSSAPI

```

I receive...

```

a NO [UNAVAILABLE] Temporary authentication failure.

```

Makes me think that the dovecot server can't find the KDC, but my current user logged in has a ticket granted...so that's working.

Anybody try this before?

---

### Post by Lucky. on 2010-06-18
Okay, I figured this out in case anybody else has a problem.

For starters, you need a correct DNS entry going to your Dovecot server.  Probably reverse lookups as well.  In my test environment the fully qualified domain name Dovecot server was:

vmserver.luckylan

That is, the server name was "vmserver", and it was on the "luckylan" domain.

Then I needed to create a principal for the server.  According to [this document](http://wiki.dovecot.org/Authentication/Kerberos), it needed to be prefaced with "imap/" since I was running Dovecot as an imap server.  Likewise "pop/" or "smtp/" would be required for other types of services (it's in the doc).  So I used kadmin to create a principal.

```

kadmin
addprinc -randkey imap/vmserver.luckylan
quit

```

Then I went to the Dovecot server "vmserver" (it's not the same server as my Kerberos server), and used kadmin to add the service ticket to my key tab.

```

kadmin
ktadd imap/vmserver.luckylan
quit

```

Then I edited /etc/dovecot/dovecot.conf once again per [this document](http://wiki.dovecot.org/Authentication/Kerberos).  I changed the args a bit to fit my own scenario, but even if they don't work you can still test authentication and get the args right later.

```

auth default {
  mechanisms = gssapi
  userdb static {
    args = uid=vmail gid=vmail home=/var/vmail/%u
  }
}

```

The part that kept killing me was that Dovecot uses "gethostname()" by default to get my server name to use for my service ticket.  I tested this function in a quick C program I slapped together, and noticed I wasn't getting my fully qualified domain name.  So instead of getting "vmserver.luckylan", it was getting "vmserver".  But my service ticket wasn't "imap/vmserver", it was "imap/vmserver.luckylan".

Furthermore creating a new principal called "imap/vmserver" was no good as my DNS didn't have a record of "vmserver" in it...it only had "vmserver.luckylan" in it.  (I suppose I could have solved the problem that way).

I fixed this by ditching the defaults and specifying my host name in /etc/dovecot/dovecot.conf.  I set "auth_gssapi_hostname" to:

```

auth_gssapi_hostname = vmserver.luckylan

```

I could have used "$ALL" for a value as well, which is the quick and dirty way.  But specifying my FQDN was good enough.

That solved it for me.  I am now able to authenticate with GSSAPI.

---

