---
title: "apache not allowing write"
date: 2010-04-30
forum: Server Platforms
---

### Post by blakep2 on 2010-04-30
I am using php on my website and i am trying to use the code fwrite but it dosent seem to be working.  I am using apache2.

---

### Post by Bachstelze on 2010-04-30
Make sure the user Apache is running as (www-data by default) has write permissions to wherever you are trying to write.

---

### Post by blakep2 on 2010-04-30
> **Bachstelze said:**
> Make sure the user Apache is running as (www-data by default) has write permissions to wherever you are trying to write.
how do you do that.

---

