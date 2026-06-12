---
title: "Likewisopen and AD"
date: 2009-11-04
forum: Server Platforms
---

### Post by T1z3R on 2009-11-04
hi all,
new here and relatively new to linux.

my admin account in AD is my full name and has a space in it seperating fore and surnames. when i use this account with the domainjoin-cli command to join the domain it is leaving out the second name. so instead of firstname [EMAIL="lastname@domain.local"]lastname@domain.local[/EMAIL] it is putting  [EMAIL="firstname@domain.local"]firstname@domain.local[/EMAIL] meaning it cant find my account.

is there something im overlooking to use my AD account to join this domain?

looking forward to having the obvious pointed out to me :)

---

### Post by koenn on 2009-11-04
try quotes 
eg
```
domainjoin-cli join domain 'fistname lastname'

```

---

### Post by T1z3R on 2009-11-05
> **koenn said:**
> try quotes 
eg
```
domainjoin-cli join domain 'fistname lastname'

```

many thanks.
worked like a charm :D

i should have thunk about it a bit longer :p

---

### Post by koenn on 2009-11-05
:)

---

