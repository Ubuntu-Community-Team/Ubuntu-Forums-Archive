---
title: "Repos selection during install?"
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by redcylon on 2012-02-12
Is it possible to select repos during install? Believe that during install , ubuntu will select the nearest repos..hence in my case its quiet slow.

---

### Post by MacUntu on 2012-02-12
It selects the repository according to the time zone selection AFAICT.

---

### Post by redcylon on 2012-02-12
> **MacUntu said:**
> It selects the repository according to the time zone selection AFAICT.

Thanks, that's what I thought so. Maybe next time I'll try just to select a different time zone then.

---

### Post by ranch hand on 2012-02-12
You may not have to do that.  Depends on what repo you want of coarse.

Here in the Mountain time zone the the default is Denver.  If I select a town in Canada in the same time zone I get the Calgary repo instead of the US repo.  This is under Debian but it would also work with Ubuntu and its repos the same way with Ubuntu repos.

I discovered this using Ubuntu-testing releases.  Here in Montana it is many times faster to use the Canadian repo so I just moved the town designation to one in Canada.  This is usually closer to where I live anyway.

---

### Post by MacUntu on 2012-02-12
IMO they should just set the repository to the main servers during development. That would also help preventing the distribution of bad uploads (libc-like ;)).

---

