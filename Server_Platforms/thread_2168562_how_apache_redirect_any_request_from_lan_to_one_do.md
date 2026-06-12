---
title: "how apache redirect any request from lan to one domain"
date: 2013-08-18
forum: Server Platforms
---

### Post by chris47 on 2013-08-18
hi my linux friends,
i have one home server with ubuntu server (http,ftp,mail) and i have two lan cards on it with two domains. one domain works perfectly on lan network and the other also works great to access point........ i want when one client from accesspoint connect from wifi and type (google.com) apache redirect him to domain name....... any adrress when typing i want to redirect only to my domain (localhost).......the server not gives internet (i don't want user and password for this or captive portal) 
sorry for my english
friendly 
chris

---

### Post by cartaysm on 2013-08-21
Not exactly sure what you are asking but sounds like setting up a virtual host will fix the issue.  You can direct the user to whatever site you want based off of ServerAlias

---

### Post by chris47 on 2013-08-21
i want when the user connects from wifi access point to the server .....when types from browser (google.com) server redirect to my domain not only google but everything

---

