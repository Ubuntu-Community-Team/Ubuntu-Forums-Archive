---
title: "Lost my ununtu /etc/postfix directory"
date: 2008-11-08
forum: Server Platforms
---

### Post by omid1979 on 2008-11-08
hi all,  
I was lost my /etc/postfix directory and I am trying to reinstall using apt-get remove postfix 
apt-get install postfix , apt-get install mailx to rebuild it , but this directory don't create , 
any one can help me how I can install rebuild this directory ? 
waiting for quick reply 

regards 
omid hosseini

---

### Post by pdwerryhouse on 2008-11-08
Perhaps:

```
apt-get --purge remove postfix
apt-get install postfix
```

---

