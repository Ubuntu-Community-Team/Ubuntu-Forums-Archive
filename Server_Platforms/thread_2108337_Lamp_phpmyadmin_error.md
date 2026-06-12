---
title: "Lamp phpmyadmin error"
date: 2013-01-24
forum: Server Platforms
---

### Post by mrfiras on 2013-01-24
every thing works in lamp , but after installing skype . 127.0.0.1/phpmyadmin
give me this error ```
**Not Found**

 The requested URL /phpmyadmin was not found on this server.
  Apache/2.2.22 (Ubuntu) Server at 127.0.0.1 Port 80
```  
please lGive me a solution , I have a big project .

---

### Post by oldfred on 2013-01-24
Moved to your own thread.

Old thread was on sql and 3 years old.

---

### Post by louis vitton on 2013-01-24
Try adding this time to your apache2.conf file location /etc/apache2/
```
# PhPMyadmin include
Include /etc/phpmyadmin/apache.conf
```also add 
```

ServerSignature Off
ServerTokens Prod
```for security if you like - this will prevent people from seeing what sort of server your running and the version that yours shows;
```
Apache/2.2.22 (Ubuntu) Server
```

---

