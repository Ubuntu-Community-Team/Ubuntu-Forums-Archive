---
title: "apache server exec per user"
date: 2009-02-28
forum: Server Platforms
---

### Post by martien on 2009-02-28
Hello everybody. I have a little question. I have my apache server configured with php and such other mods. PHP is configured as a module, not as CGI. I have a few clients on separate virtualhosts for each client domain/subdomain/etc. The problem is that i want to make every php script that is runned in apache to be logged by its owner. I can add SuExecUserGroup in each virtualhost but that will log only cgi requests. I want to do it with the php scripts to watch the system load. Any ideas?

---

