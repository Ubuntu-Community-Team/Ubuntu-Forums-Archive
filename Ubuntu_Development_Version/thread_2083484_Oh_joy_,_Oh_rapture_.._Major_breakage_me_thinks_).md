---
title: "Oh joy , Oh rapture .. Major breakage me thinks :)"
date: 2012-11-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-12
Apt-get 'failed for some reason'

Oh man , this one is a beaut! :)

```

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: jconti recent-notifications
Warning:  Could not find package list for PPA: jconti recent-notifications
ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by ventrical on 2012-11-12
f/p.. It's an old one :)

---

### Post by toobuntu on 2012-11-15
Seems like either some of your repos are down or your network connection is spotty. You might want to run [FONT="Courier New"]apt-get update[/FONT] in a [FONT="Courier New"]while[/FONT] loop to make life easier. Here's what I use to update and upgrade my system:
```
while ! ( date && sudo apt-get update ) ; do sleep 10s ; done && sudo apt-get upgrade ; date
```

---

### Post by ventrical on 2012-11-16
> **toobuntu said:**
> Seems like either some of your repos are down or your network connection is spotty. You might want to run [FONT=Courier New]apt-get update[/FONT] in a [FONT=Courier New]while[/FONT] loop to make life easier. Here's what I use to update and upgrade my system:
```
while ! ( date && sudo apt-get update ) ; do sleep 10s ; done && sudo apt-get upgrade ; date
```

 Thanks .. I purged the repo and all is well once again ! :)

---

