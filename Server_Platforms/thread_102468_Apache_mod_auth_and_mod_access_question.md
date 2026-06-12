---
title: "Apache mod_auth and mod_access question"
date: 2005-12-12
forum: Server Platforms
---

### Post by nemesa on 2005-12-12
Hi!

Is it possible to give the (AuthType Basic) Password popup only those host which are not in a specific ip or domain range?

Ie.: I want to let 193.123.123.123 - 193.123.123.130 hosts to see my page without any authentication, and let in anybody else with pass.

Thank you!

---

### Post by nemesa on 2005-12-19
I've found the solution...

require valid-user
order deny,allow
Deny from All
allow from 193.123.123.123
satisfy any

---

