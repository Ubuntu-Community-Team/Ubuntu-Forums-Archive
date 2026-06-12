---
title: "postfix sending only two messages at a time to recipient domains"
date: 2017-11-12
forum: Server Platforms
---

### Post by 62vette on 2017-11-12
Hi,

I have a server running Ubuntu 16.0.4.2 LTS in AWS, it is running as a mail relay server for an ERP server also running in AWS.

I find when it is relaying messages out to destination domains, it will only deliver two messages at a time, deferring delivery for any remaining queued messages. Each time the mail queue is processed subsequently, only two more messages at a time will be delivered. Mail delivery can be delayed for some considerable time if there are a number of messages awaiting delivery. Deferred messaged are showing in mail server logs as:

status=deferred (connect to blah.mail.protection.outlook.com[n.n.n.n]:25: Connection timed out)

The only config changes I have made from default are around relay settings and internal networks.

I have been using ubuntu and postfix to do this sort of thing for years and have never had this issue before. Is there a parameter I should check for, or should I be looking down the path of some sort of traffic throttling happening at the AWS level?

All suggestions welcome.

Thanks

---

### Post by 62vette on 2017-11-12
It looks like this is an AWS service throttle applied to all EC2 instances by default.

---

