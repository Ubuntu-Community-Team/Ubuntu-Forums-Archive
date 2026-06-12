---
title: "service says &quot;disabled&quot; after install"
date: 2010-11-18
forum: Server Platforms
---

### Post by rwssoccer1 on 2010-11-18
Hi

i just installed frox ftp proxy for my server using apt-get install frox......after i installed it i did 'sudo /ietc/init.d/frox start" and  got t this  "starting frox:caching ftp proxy server: disabled"

i dont get it LOL

---

### Post by trentscott on 2010-11-18
Is there a config file for it that has an enable/disable on boot flag in it?

---

### Post by rwssoccer1 on 2010-11-19
I figured it out...the file /etc/default/frox was set to not let the init.d script start it..thanks for the help though

---

