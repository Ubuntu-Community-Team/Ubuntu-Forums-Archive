---
title: "Kerberos + LDAP + NFSv4 on Natty - Unable to recover unattended client"
date: 2011-06-16
forum: Server Platforms
---

### Post by BrianTheLion on 2011-06-16
I'm cross-posting from a [Launchpad question]("https://answers.launchpad.net/ubuntu/+source/openldap/+question/160466") here in hopes that somebody will be able to shed some light on what's going on with my Kerberos/LDAP/autofs/NFS stack on Natty.

The gist is that my client machines -- Natty desktop, all -- are getting catastrophically wedged on NFS volumes that go missing when users's Kerberos tickets expire. They are getting so wedged, in fact, that **sudo reboot** fails. I can't imagine that this is intended behavior even with something as heavy-handed as Kerberos, and am left to wonder where my configuration has gone wrong.

Any insight you can offer would be a huge help. Most of the relevant details are in the [Launchpad post]("https://answers.launchpad.net/ubuntu/+source/openldap/+question/160466"), but I'll be happy to reproduce them here as necessary.

Cheers!

---

