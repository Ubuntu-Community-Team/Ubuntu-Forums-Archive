---
title: "Changing Apache port gives error"
date: 2011-01-05
forum: Server Platforms
---

### Post by unsoc on 2011-01-05
My ISP Blocks port 80 so I changed the port to 8081 after I do this and restart Apache and use my IP with :8081 after I get a page saying Not Found The requested URL /index.html was not found on this server. I get this same message if I use my real IP or the IP from my router. What can be casuing this?

---

### Post by 1v82TIn1 on 2011-01-05
You also need to make sure the ports are changed in ports.conf under NameVirtualHost and Listen. You also need to change it in /sites-available/default at the top.

---

### Post by unsoc on 2011-01-05
I forgot all about editing it in sites-available thanks much for your help.

---

