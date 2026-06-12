---
title: "how to boot 8.04 into single user mode?"
date: 2010-10-20
forum: Server Platforms
---

### Post by three_jeeps on 2010-10-20
How can I boot 8.04 server into single user mode WITHOUT attaching an external CD drive and booting the live CD?

I want to do this so I can make an image copy of my system disk.  Is putting the system in single user mode a good way to do this? 

Thanks
J

---

### Post by Barriehie on 2010-10-20
Even in single user mode some services are running.  Only way to do it right is via the external boot media.  You can change run level with:
```

/sbin/init 1
```

---

