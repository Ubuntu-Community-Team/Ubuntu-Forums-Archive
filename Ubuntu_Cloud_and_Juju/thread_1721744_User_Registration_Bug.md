---
title: "User Registration Bug"
date: 2011-04-04
forum: Ubuntu Cloud and Juju
---

### Post by JasonN on 2011-04-04
Hello Everyone,

I'm not quite sure if this issue has been documented/solved yet or if its an issue at all, but I thought it best to share it just in case.  Additionally, if someone could point me to where to log this error (Hybridfox, Ubuntu, Eucalyptus) that would be much appreciated too.

So yes, the issue: when an admin user is registered through the web interface, I get two different outcomes in what HybridFox shows for that user depending on how they were registered.

[LIST]If a user registers themselves by going through the web interface and then have the admin approve them to be an admin, the user does not see the other users' vm instances or the entire elastic IP (assigned to nobody). 
[/LIST]
[LIST]When an admin user (default admin account) simply creates the user and grants them admin rights, the user can then see the other vm instances initiated by all the users as well as the entire range of Elastic IPs.
[/LIST]

I hope this isn't a huge issue and that I'm only one of very few people who has experienced it. Please let me know if anyone would like any further explanations on what I've experienced.

Thanks everyone,
Jaosn

---

### Post by kim0 on 2011-04-05
Hi Jason,
The behavior you're describing sounds like a bug to me. You can file a bug report at: [https://bugs.launchpad.net/eucalyptus](https://bugs.launchpad.net/eucalyptus)

---

