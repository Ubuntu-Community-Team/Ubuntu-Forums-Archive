---
title: "Question about updates"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by larrypg on 2012-02-04
Hello,

I have a dumb question about what is considered a partial update.  I installed the fist alpha iso and then have just been updating it since (which I think also updated it to alpha 2).  Is this considered a partial update or just regular updates?

By the way with the exception of the scroll wheel in firefox I am seeing no problems whatso ever.

---

### Post by paul_in_london on 2012-02-04
> **larrypg said:**
> Hello,

I have a dumb question about what is considered a partial update.  I installed the fist alpha iso and then have just been updating it since (which I think also updated it to alpha 2).  Is this considered a partial update or just regular updates?

By the way with the exception of the scroll wheel in firefox I am seeing no problems whatso ever.

Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

EDIT: I'd suggest using synaptic to update/upgrade (or apt-get/aptitude) instead of update manager.

---

### Post by larrypg on 2012-02-04
Hello,

I guess I worded the question wrong.  I use apt-get update and then apt-get upgrade.  Is there a problem in doing it this way or is the correct way to download the daily's and install it each time?  The only reason I am asking is because things are going so smooth which I do not expect for an alpha cycle.  So far nothing has broken and have not had any problems which makes me wonder If I am actually installing fully (although it seems I have).

---

### Post by paul_in_london on 2012-02-04
> **larrypg said:**
> Hello,

I guess I worded the question wrong.  I use apt-get update and then apt-get upgrade.  Is there a problem in doing it this way or is the correct way to download the daily's and install it each time?  The only reason I am asking is because things are going so smooth which I do not expect for an alpha cycle.  So far nothing has broken and have not had any problems which makes me wonder If I am actually installing fully (although it seems I have).

You don't need to keep downloading daily or milestone (alpha/deta) builds. Just keep updating using apt-get all the time and you'll end up with the final release. With apt-get, you should normally do this to update properly:

```
apt-get update
apt-get **[COLOR="Red"]dist-upgrade[/COLOR]**
```

but if there are broken packages it may want to remove stuff that it shouldn't remove. If that happens and you're not sure cancel that action and run:

```
apt-get update
apt-get **[COLOR="Red"]upgrade[/COLOR]**
```

instead. You can keep trying apt-get dist-upgrade every so often until any dependency issues are resolved.

---

