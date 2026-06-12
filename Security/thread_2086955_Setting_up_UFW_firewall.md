---
title: "Setting up UFW firewall"
date: 2012-11-22
forum: Security
---

### Post by hannuh on 2012-11-22
I am converting our mail server to a "closed circuit" mail server, which will not attempt to send mail to world addresses other than specified in the host.txt file. Similarly, it should not accept mail from machines other than those in the hosts.txt. The server has a working sendmail for smtp, and dovecot for pop3 and imap.
I don't have much experience with iptables or ufw, so I'd like to run this by somebody who knows this stuff.

Would this work:

#!/bin/bash
# disable firewall
ufw disable
# reset all firewall rules
ufw reset
# set default rules
#
ufw default allow incoming
ufw default allow outgoing
# that's to allow all other services as before
#
ufw default deny smtp
ufw default deny pop3
ufw default deny imap
# that's to disable mail services
#
cat "/usr/local/bin/hosts.txt" | while read LINE
do
ufw allow smtp from $LINE to yyy.xxx.yyy.100
ufw allow pop3 from $LINE to yyy.xxx.yyy.100
ufw allow imap from $LINE to yyy.xxx.yyy.100
ufw allow smtp to $LINE from yyy.xxx.yyy.100
ufw allow pop3 to $LINE from yyy.xxx.yyy.100
ufw allow imap to $LINE from yyy.xxx.yyy.100
done
ufw enable
#
cat "/usr/local/bin/hosts.txt" | while read LINE
do
ufw allow smtp from $LINE to yyy.xxx.yyy.100
ufw allow pop3 from $LINE to yyy.xxx.yyy.100
ufw allow imap from $LINE to yyy.xxx.yyy.100
ufw allow smtp to $LINE from yyy.xxx.yyy.100
ufw allow pop3 to $LINE from yyy.xxx.yyy.100
ufw allow imap to $LINE from yyy.xxx.yyy.100
done
# where yyy.xxx.yyy.100 is the mail server and
# host.txt would be something like:
# xxx.yyy.xxx.0/24
# yyy.xxx.yyy.0/24
# xxy.yyx.xxy.0/24
#
ufw enable

As mentioned, I am not sure about my ufw syntax, there seem to be a lot variations that one can use.
All help appreciated,
Hannu

---

### Post by wildmanne39 on 2012-11-22
*Thread moved to **Security Discussions**.*

---

### Post by Ms. Daisy on 2012-11-22
```
ufw default allow incoming
ufw default allow outgoing
# that's to allow all other services as before
```I don't think those lines are doing what you think they're doing. default allow means that any connection that doesn't specifically match a rule will be allowed.  Then you say:

```
ufw default deny smtp
ufw default deny pop3
ufw default deny imap
# that's to disable mail services
```So now the default is to deny those services.  Wouldn't it be easier to replace both of the parts I quoted with:
```
ufw default deny incoming
ufw default deny outgoing

```Then have the rest of the rules.  That way only what you have specified will be allowed.

If you're trying to allow related connections to return, then I believe that ufw does that by default. You only need to write a "related" rule when  you're using iptables. Hopefully someone else can confirm that though.

---

### Post by hannuh on 2012-11-24
> **Ms. Daisy said:**
> I don't think those lines are doing what you think they're doing. default allow means that any connection that doesn't specifically match a rule will be allowed.  Then you say:

[CODE]ufw default deny smtp
ufw default deny pop3
ufw default deny imap


Thank you for your help. The reason I had it that way was to make sure that I am not blocking or limiting other services (bind, apache2, ssh etc.)they should not be firewalled, they have other type of securities.
But then, I specifically deny mail services, and then, open up mail services for the list of IP addresses only.
I don't have full understanding what the ufw default is, does it block something by default or just let everything through unless told differently by new rules? Do you have to deny all first, then allow specified? Or is allowing specified automatically denying all others? If you allow "from" "to" do you also have to allow reverse "to" "from"?
I hope that makes sense ...
Hannu

---

### Post by Lars Noodén on 2012-11-24
You might also use reject instead of drop (deny), especially for rules that are likely to affect your own connections.

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

---

### Post by Ms. Daisy on 2012-11-26
> I don't have full understanding what the ufw default is, does it block  something by default or just let everything through unless told  differently by new rules?  if you write ufw default deny incoming, then it will by default deny every incoming connection.  You can add rules to specifically allow certain services &/or ports, and ufw will allow those while denying everything that doesn't match the allowed rules you set.  If you set it to ufw default allow incoming, then it will allow everything in by default unless you specifically write a rule to prevent something.

I guess the best approach depends on what you're trying to accomplish with your firewall.  My strategy is to default deny all incoming, then allow each service that I specify.  I guess I don't see the point of a firewall if you're going to let all kinds of stuff through & only filter certain things.  In your case, I would default deny all incoming. Then I would allow incoming bind, apache2, ssh etc. Then I would allow the specific IPs over mail.

---

