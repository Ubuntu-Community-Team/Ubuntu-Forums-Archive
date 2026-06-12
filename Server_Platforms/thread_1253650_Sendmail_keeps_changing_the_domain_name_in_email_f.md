---
title: "Sendmail keeps changing the domain name in email fields"
date: 2009-08-30
forum: Server Platforms
---

### Post by skelooth on 2009-08-30
I'm a little confused, been googling and not finding.

When I send an email using php mail on a very 'vanilla' install of ubuntu server, any address that has "@mydomain.com" in it turns into "@lix.members.linode.com"

I've tried using -f reply@mydomain but still no good. It changes the address both for the to and from fields!

Can anyone help? I have set up servers in the past but have never encountered this.

SOLVED:

It's always the simple things we over look. I took the incorrect domain name out of my hosts file and everything resolves properly now. Apologies for the board clutter.

---

