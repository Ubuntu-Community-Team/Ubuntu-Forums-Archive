---
title: "Trouble getting Sendmail to forward"
date: 2008-04-28
forum: Server Platforms
---

### Post by RHAnthony on 2008-04-28
Hey guys.  Real simple goal I'm shooting for I think but can't seem to find any tutorial or documentation that addresses it specifically and I just can't read all of the complex tutorials and get what I need out of them... Hoping it's a quick answer someone can give me here.

I want Sendmail to accept mail for a few domains, and forward them back out to other email addresses.  Not looking to have local users really at all at this point.

I have 10 domains configured for it, all with MX records pointing to it, and using it as their NS server infact.

How can I get this done, in the simplest, straight forward way?

Side question... is there anything "better" in your varied opinions than Sendmail?

---

### Post by bigal99 on 2008-04-29
Beware of quick answers <g>.

Here is part of the 'Configuration' doc from sendmail.org.

"...
+-----------------------------------+
| ACCEPTING MAIL FOR MULTIPLE NAMES |
+-----------------------------------+

If your host is known by several different names, you need to augment
class {w}.  This is a list of names by which your host is known, and
anything sent to an address using a host name in this list will be
treated as local mail.  You can do this in two ways:  either create the
file /etc/mail/local-host-names containing a list of your aliases (one per
line), and use ``FEATURE(`use_cw_file')'' in the .mc file, or add
``LOCAL_DOMAIN(`alias.host.name')''.  Be sure you use the fully-qualified
name of the host, rather than a short name.

If you want to have different address in different domains, take
a look at the virtusertable feature, which is also explained at
[http://www.sendmail.org/virtual-hosting.html](http://www.sendmail.org/virtual-hosting.html)


+--------------------+
| USING MAILERTABLES |
+--------------------+

To use FEATURE(`mailertable'), you will have to create an external
database containing the routing information for various domains.
For example, a mailertable file in text format might be:

	.my.domain		xnet:%1.my.domain
	uuhost1.my.domain	uucp-new:uuhost1
	.bitnet			smtp:relay.bit.net

This should normally be stored in /etc/mail/mailertable.  The actual
database version of the mailertable is built using:

	makemap hash /etc/mail/mailertable < /etc/mail/mailertable

The semantics are simple.  Any LHS entry that does not begin with
a dot matches the full host name indicated.  LHS entries beginning
with a dot match anything ending with that domain name (including
the leading dot) -- that is, they can be thought of as having a
leading ".+" regular expression pattern for a non-empty sequence of
characters.  Matching is done in order of most-to-least qualified
-- for example, even though ".my.domain" is listed first in the
above example, an entry of "uuhost1.my.domain" will match the second
entry since it is more explicit.  Note: e-mail to "user@my.domain"
does not match any entry in the above table.  You need to have
something like:

	my.domain		esmtp:host.my.domain

The RHS should always be a "mailer:host" pair.  The mailer is the
configuration name of a mailer (that is, an M line in the
sendmail.cf file).  The "host" will be the hostname passed to
that mailer.  In domain-based matches (that is, those with leading
dots) the "%1" may be used to interpolate the wildcarded part of
the host name.  For example, the first line above sends everything
addressed to "anything.my.domain" to that same host name, but using
the (presumably experimental) xnet mailer.

In some cases you may want to temporarily turn off MX records,
particularly on gateways.  For example, you may want to MX
everything in a domain to one machine that then forwards it
directly.  To do this, you might use the DNS configuration:

	*.domain.	IN	MX	0	relay.machine

and on relay.machine use the mailertable:

	.domain		smtp:[gateway.domain]

The [square brackets] turn off MX records for this host only.
If you didn't do this, the mailertable would use the MX record
again, which would give you an MX loop.  Note that the use of
wildcard MX records is almost always a bad idea.  Please avoid
using them if possible.
..."

---

### Post by RHAnthony on 2008-05-03
I just said screw it and went to postfix.  
all is well now with virtual_aliases
took about 5 minutes to setup and test various domains / setups.

---

