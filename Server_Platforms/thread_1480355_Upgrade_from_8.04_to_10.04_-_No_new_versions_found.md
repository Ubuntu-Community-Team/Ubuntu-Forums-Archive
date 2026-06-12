---
title: "Upgrade from 8.04 to 10.04 - No new versions found."
date: 2010-05-11
forum: Server Platforms
---

### Post by Porch951 on 2010-05-11
Hi,
Just wanted to point this out in case anyone had the same problem i did.  Following the directions here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

The final step on upgrading 8.04 LTS to 10.04 Server is:
sudo do-release-upgrade --devel-release

This doesn't work!
Instead, this documentation:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

says to use --proposed, which WORKS!

Not sure what the deal is, but there's the solution...

---

### Post by arrrghhh on 2010-05-11
The --proposed was needed because you were on 8.04.  If you were on 9.10 (like I was) do-release-upgrade would work just fine.

Glad to hear you got it workin tho :D

---

### Post by Porch951 on 2010-05-11
Yeah, it makes sense.  The main confusion was that the documentation is wrong!

---

### Post by arrrghhh on 2010-05-11
> **Porch951 said:**
> Yeah, it makes sense.  The main confusion was that the documentation is wrong!

I see... I'm not sure why the discrepancy.  Very odd.

---

