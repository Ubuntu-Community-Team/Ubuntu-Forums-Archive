---
title: "How do I remove the database 'wordpress' from my LAMP Server"
date: 2009-10-08
forum: Server Platforms
---

### Post by jigglypuff on 2009-10-08
Need help! Total Noob :)

---

### Post by wojox on 2009-10-08
```
DROP DATABASE wordpress
```

---

### Post by jigglypuff on 2009-10-08
do I do this in mysql?

---

### Post by wojox on 2009-10-08
Yes log in to mysql and drop it.

---

### Post by jigglypuff on 2009-10-08
It doesnt seem to be dropping it with DROP DATABASE wordpress

---

### Post by wojox on 2009-10-08
Try:

```
use database wordpress
```

Or 
 
```
use wordpress
```


```
drop database wordpress
```

It's been awhile

---

### Post by wojox on 2009-10-08
You can also issue:

```
show databases
```

To see all databases.

---

