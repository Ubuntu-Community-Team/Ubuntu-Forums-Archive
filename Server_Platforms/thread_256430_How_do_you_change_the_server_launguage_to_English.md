---
title: "How do you change the server launguage to English?"
date: 2006-09-13
forum: Server Platforms
---

### Post by RackNetz on 2006-09-13
Does any one know how to change the unbuntu desktop server system launguage from French to English?

Kind Regards,

---

### Post by fnjordy on 2006-09-13
You can select on a menu on the GDM login screen, alternatively via a terminal update /etc/environment, something like these two settings:

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

---

