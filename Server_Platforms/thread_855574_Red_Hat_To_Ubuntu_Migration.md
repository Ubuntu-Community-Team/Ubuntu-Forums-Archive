---
title: "Red Hat To Ubuntu Migration"
date: 2008-07-10
forum: Server Platforms
---

### Post by cmnorton on 2008-07-10
Does a migration guide exist that would cover moving from a Red Hat to Ubuntu Server?

---

### Post by k_grdn on 2008-07-10
Hi,

What services is this server running?

Ideally it will be just the services that you migrate.


Regards,

k_grdn

---

### Post by ixus_123 on 2008-07-10
what do you need to migrate?

can you just migrate the data and install ubuntu on a fresh pair of disks?

if you are talking about simpler things like OS diferences, then some paths are different - like paths to ifcfg-etho for example and there is also no "service" command in Ubuntu

---

### Post by cmnorton on 2008-07-10
> **ixus_123 said:**
> what do you need to migrate?

can you just migrate the data and install ubuntu on a fresh pair of disks?

if you are talking about simpler things like OS diferences, then some paths are different - like paths to ifcfg-etho for example and there is also no "service" command in Ubuntu

I was answering a question in another forum and the discussion turned to Red Hat support. As an aside in the post, I was asked what guidelines I had to advise someone on migrating from a Red Hat Enterprise environment to Ubuntu Server. This came up, because I compared Cannonical's support with Red Hat. Cannonical won in the argument.

I moved our tax collection system (Informix 4gl/SE) to Ubuntu, but had to make some changes, non the least of which was changing all #!/bin/sh to #!/bin/bash.

If we have a guide, even if not Red Hat specific, it would be helpful.

---

