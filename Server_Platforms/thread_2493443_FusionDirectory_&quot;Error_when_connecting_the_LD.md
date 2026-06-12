---
title: "FusionDirectory: &quot;Error when connecting the LDAP. Server said...&quot;"
date: 2023-12-15
forum: Server Platforms
---

### Post by civilpolisen on 2023-12-15
> [IMG]http://lynx.vertel.se/fusiondirectory/geticon.php?context=status&icon=dialog-error&size=32[/IMG]                                         **Fatal error**
              FATAL: Error when connecting the LDAP. Server said 'Could  not bind to cn=admin,dc=nodomain (while operating on LDAP server  ldap://localhost:389)'.

              Please fix the above error and reload the page.

We've had this error for quite some time. One day, November 22, it was just there..! At the time we were not connected to the server doing different things...
I was installing SSSD clients at some laptops... there were some errors while installing SSSD, but I thought it was me doing something wrong or different.

I've dome major research... We thought it was certificates and those were updated, but actually, they were fine! Due in January 2024.We thought it might 
be the database itself that was wrong. I have replaced the database with a working one. No difference...

The error remains and I'm out of ideas of what could fail!

---

