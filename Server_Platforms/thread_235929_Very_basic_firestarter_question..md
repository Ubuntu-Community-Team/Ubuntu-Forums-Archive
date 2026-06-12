---
title: "Very basic firestarter question."
date: 2006-08-13
forum: Server Platforms
---

### Post by Buzzygirl on 2006-08-13
Greetings all, quick question. I'm running Ubuntu 6.06 and just downloaded Firestarter. So far as I can tell, upon reboot, I need to manually invoke the Firestarter application itself to start it. How do I configure Firestarter to run every time I start up my computer? 

Thanks, 

Jackie

---

### Post by 23meg on 2006-08-13
You don't have to start it every time; it will start whenever you start Ubuntu and do its job. You only need to launch its graphical interface to configure its settings; after you configure, just close it and Firestarter will keep working.

To see its status at any time, type ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by bonjun on 2006-08-13
as far as i know it runs on background your setup is detected

---

### Post by Buzzygirl on 2006-08-13
Cool, that answers my question. Thanks for the very fast answer!

---

