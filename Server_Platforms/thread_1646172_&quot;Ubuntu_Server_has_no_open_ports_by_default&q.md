---
title: "&quot;Ubuntu Server has no open ports by default&quot;"
date: 2010-12-15
forum: Server Platforms
---

### Post by jackycs on 2010-12-15
"Ubuntu Server has no open ports by default" -  [http://www.ubuntu.com/server/features/security](http://www.ubuntu.com/server/features/security)

does this mean right after a 10.04 Server Edition installation, if a user wants to start a web service e.g. a Java process to listen on say port 8080, he would have to configure the firewall first? 

Thanks,
J

---

### Post by surfer on 2010-12-15
no, it just means there is no service listening to any port.

apache is not installed (unless you ask for it during the installation) and no other webserver. therefore nothing is listening on port 80. 

and there is no firewall that prevents any connections by default. (why should there be as there are no services listening?).

---

