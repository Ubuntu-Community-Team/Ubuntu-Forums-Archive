---
title: "How can I change EXIM4 config from warn on no reverse DNS to actively rejecting mails"
date: 2013-04-13
forum: Server Platforms
---

### Post by MechaMechanism on 2013-04-13
By default EXIM4 only warns about mails with no reverse DNS.  I need  to block and actively reject mail which has no reverse DNS.  I am  willing to accept that it's possible that some legit mail will be  blocked, however, so far the only mail with no reverse DNS has been  spam.  I'd like to get this setup.  I'm reading the documentation, but I don't want to wait till I figure that out.  Also whoever comes up with a solution if you could tell me how and why it works I'd very much appreciate it, thanks.


  Below is the code for reverse DNS checking from the EXIM4 config.  How do I change this from warn to blocking.

Warn if the sender host does not have valid reverse DNS.
If your system can do DNS lookups without delay or cost, you might want
to enable this.  If sender_host_address is defined, it's a remote call.  If
sender_host_name is not defined, then reverse lookup failed.  Use
this instead of !verify = reverse_host_lookup to catch deferrals
as well as outright failures.

Maybe change warn to block, hmm.
.ifdef CHECK_RCPT_REVERSE_DNS
warn
condition = ${if and{{def:sender_host_address}{!def:sender_host_name}}\
{yes}{no}}
add_header = X-Host-Lookup-Failed: Reverse DNS lookup failed for $sender_host_address (${if
eq{$host_lookup_failed}{1}{failed}{deferred}})
.endif

---

### Post by duesentriebchen on 2013-04-18
change the comment warn to deny :D

---

