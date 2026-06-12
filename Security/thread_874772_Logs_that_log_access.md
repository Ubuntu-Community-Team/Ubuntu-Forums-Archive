---
title: "Logs that log access"
date: 2008-07-30
forum: Security
---

### Post by CrusaderAD on 2008-07-30
Does anyone know if there are any system logs for things like network access? I have a shared drive and I want to know who accesses it.

---

### Post by Dr Small on 2008-07-30
Do you mean, for like Samba?

---

### Post by CrusaderAD on 2008-07-30
Yeah, I know Samba has it's own logs. It is possible to monitor one folder?

---

### Post by CrusaderAD on 2008-08-20
bump

---

### Post by LUS93 on 2008-08-20
Sure 

```

grep 'folderName' /var/log/samba/* | grep user

```

---

