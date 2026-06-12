---
title: "Samba file access denied"
date: 2015-08-13
forum: Server Platforms
---

### Post by marcus34 on 2015-08-13
Hello, i am trying to make a samba public share file and when i open the file it tells me access denied 

```

[Share]
path = /public
public = yes
writable = yes
read only = no

```

---

### Post by nerdtron on 2015-08-13
What is the folder permission of /public?
```
ls -l /public
```

---

### Post by marcus34 on 2015-08-14
thank you it worked

---

### Post by cariboo on 2015-08-14
@marcus34, could you let us know what you did to solve the problem?

---

### Post by TheFu on 2015-08-15
> **cariboo said:**
> @marcus34, could you let us know what you did to solve the problem?

And please mark the thread as "solved" to save time for other helpers AND people looking for answers?

---

