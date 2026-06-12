---
title: "Sporadic server timeout problems."
date: 2011-04-24
forum: Server Platforms
---

### Post by JackRabid on 2011-04-24
Post edited after resolution...

I was having a problem where my server would go unresponsive to it's No-IP redirected name while access via local net IP was unaffected.

Access via the No-IP name would usually be restored within 5 minutes or so.

---

### Post by JackRabid on 2011-04-25
Post edited after resolution...

Issue was due to having installed and config'ed the server before setting up the No-IP redirect. After setting up the No-IP redirect I then forgot to update /etc/hosts with the new host.

Issue Solved.

---

