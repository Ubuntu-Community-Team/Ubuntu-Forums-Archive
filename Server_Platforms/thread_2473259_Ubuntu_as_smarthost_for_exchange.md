---
title: "Ubuntu as smarthost for exchange"
date: 2022-03-29
forum: Server Platforms
---

### Post by gb777 on 2022-03-29
Hi all,

How would I go setting up Ubuntu server as a smarthost for exchange?

I'm trying to do this so that I can also install HAProxy to relieve the TLS 1.3 situation.

Email coming from the internet would go to the Ubuntu server, scanned for viruses and spam, then forwarded to the exchange server.

Outgoing email would be routed from exchange through the Ubuntu server.

Exchange is on premises.

Thank you in advance and regards
GB

---

### Post by DuckHook on 2022-03-29
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by TheFu on 2022-03-29
I don't know of any step by step guide and posting instructions here is simply too much.
I'd suggest looking for 'postfix email gateway' as the starting point.  postfix is postfix is postfix across all Unixen.
[https://www.postfix.org/STANDARD_CONFIGURATION_README.html#firewall](https://www.postfix.org/STANDARD_CONFIGURATION_README.html#firewall)
That is the instructions that I followed for my email gateway.

Scanning for viruses is harder. Spam is well understood - if you use SPF and DKIM to block 99% of email first.  There are lots of other techniques.  AV on Linux is very good, because it doesn't need to be very good. If you really need that - put it on a Windows platform that you can rebuild after it is infected each week.

I get thousands of spam emails on a few gmail accounts, but perhaps 1 per week on the email servers I run with the gateway. OTOH, I'm very willing to use geo-blocking and other language/characterset blocking to protect the 200 or so users.

We don't use MS-Exchange.  That is just too much hassle, especially upgrades.  Instead we use Zimbra and only allow people on our network access.  To remotely access their email, end users must use a VPN, period.  I forced this after seeing thousands of password attempts against the CEO's account.  He was pissed, until I showed him to imap logs. He will still pissed, but didn't want his account disabled after 10 failed attempts, so the VPN was our compromise.

You may want to scan emails at egress time for company sensitive data too, BTW.  It is pretty embarrassing when an employee emails a spreadsheet that contains highly sensitive data on a tab they didn't look at.  Our entire employee name/location/phone/email list was leaked that way years ago, just before the company was listed on the NASDAQ.  The phones kept ringing for 2 solid weeks between reporters and head hunters trying to get a story or steal talent.  At another company where I contracted, the group list was accidentally sent to a vendor by the department admin, but with everyone's hourly rate/salary.  It was interesting to see who was being paid 2x more than other people with higher skills.

---

