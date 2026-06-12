---
title: "How to make postfix block certain hosts?"
date: 2008-10-01
forum: Security
---

### Post by CaptSaltyJack on 2008-10-01
Does postfix look at /etc/hosts.deny?  I'd like postfix to totally dump connections from specific domains or IP address ranges.

How can I do this?

---

### Post by hyper_ch on 2008-10-02
add to the smtp recipient restrictions this here:

        check_sender_access hash:/etc/postfix/sender_checks,

Then create the according /etc/postfix/sender_checks file and edit it according to your liking:

```

# This file must be "compiled" with "postmap"

# Using a domain name
example.tld             554 Spam not tolerated here
# Maybe example2.tld is on a DNSbl, but we want to let their
# email in anyway.
example2.tld            OK

# We get lots of spam from example3.tld, but we have somebody
# there from which we do want to hear
someuser@example3.tld   OK
example3.tld            REJECT

```

then install "postmap" and create a map file
```

cd /etc/postfix
sudo postmap sender_checks

```

then restart postfix
```

sudo /etc/init.d/postfix restart

```

---

### Post by CaptSaltyJack on 2008-10-02
What if I wanted to block all *.cn sites?  Would it just be:

cn  REJECT

---

### Post by CaptSaltyJack on 2008-10-02
> **hyper_ch said:**
> add to the smtp recipient restrictions this here:

        check_sender_access hash:/etc/postfix/sender_checks,



Just to clarify for anyone else reading this thread, this means editing /etc/postfix/main.cf and adding this line:

```

smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/sender_checks

```

Or if there are already several other options listed under smtpd_recipient_restrictions, just add the check_sender_access option to the list, e.g.:

```

	smtpd_recipient_restrictions =
	    reject_invalid_hostname,
	    reject_non_fqdn_hostname,
	    reject_non_fqdn_sender,
	    reject_non_fqdn_recipient,
	    reject_unknown_sender_domain,
	    reject_unknown_recipient_domain,
	    reject_unauth_pipelining,
	    permit_mynetworks,
	    reject_unauth_destination,
	    check_recipient_access pcre:/etc/postfix/recipient_checks.pcre,
	    check_sender_access hash:/etc/postfix/sender_checks,
	    reject_maps_rbl,
	    permit

```

---

### Post by hyper_ch on 2008-10-02
> **CaptSaltyJack said:**
> What if I wanted to block all *.cn sites?  Would it just be:

cn  REJECT

That should work but it will block everything that has a "cn" in (I think). You'd be safer to block

> 
.cn   REJECT   554 Spam not tolerated here


However to be really sure, you'd use pcre (regular expressions) to block all of it.

Or a list of all IPs in China and Korea can help, have a look here:  [http://www.fadden.com/techmisc/asian-spam.htm](http://www.fadden.com/techmisc/asian-spam.htm)

---

### Post by CaptSaltyJack on 2008-10-03
Whew, I just have to point out, this is totally wrong.

The entry to modify is smtpd_sender_restrictions, NOT smtpd_recipient_restrictions!

From /etc/postfix/main.cf:

```

...
...
smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/sender_checks

```

---

### Post by CaptSaltyJack on 2008-10-13
Looks like losers from hinet.net can still connect to my mail server, despite the above config.  Any ideas?

---

### Post by emmanux on 2013-04-04
> **CaptSaltyJack said:**
> Looks like losers from hinet.net can still connect to my mail server, despite the above config.  Any ideas?
Check your logs, may be they're using a valid server as relay (abusing it).

---

### Post by oldos2er on 2013-04-04
Closed, please don't bump old threads.

---

