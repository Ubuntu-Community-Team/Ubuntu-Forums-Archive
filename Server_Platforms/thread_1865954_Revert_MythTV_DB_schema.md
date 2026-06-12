---
title: "Revert MythTV DB schema"
date: 2011-10-20
forum: Server Platforms
---

### Post by wesg on 2011-10-20
My server runs 9.10 and MythTV 0.22 and plays along just fine with my primary frontend, XBMC on Win 7. Just now I checked my upcoming recordings and noticed that mythfilldatabase hadn't run in a while and realized my DB schema had changed and I couldn't connect with mythtv-setup or mythfilldatabase.

```
Error: MythTV database has newer TV schema (1264) than expected (1244).
```

When Ubuntu 11.10 came out, I installed it on a VM and tried to use the legit frontend to access my server. What I think happened was that after connecting, the DB schema was updated to use the newer version, leaving the actual MythTV install out of the loop.

What are my options? If I kill the database, will MythTV be able to pick up my previous recordings?

---

