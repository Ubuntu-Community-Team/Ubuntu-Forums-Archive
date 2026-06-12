---
title: "Apache crashes on SSL mutex error after adding CA signed certificate in ISPConfig 3"
date: 2009-09-21
forum: Server Platforms
---

### Post by wouterd on 2009-09-21
Hi,

On my webserver I host a couple of websites on named virtual servers. Two sites have their own IPs configured in the virtual host files and are therefore separated from the others. Today I tried to add an ssl certificate (CA signed) through ISPConfig 3. As soon as I hit Save, Apache2 crashes. Wouldn't come up again, not even after reboot. The Apache error log just tells met this:

```

[error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed

```

Indeed, this file does not exist.

Of course, I googled around a lot before posting :) but there doesn't seem to be any other person connected to the www who has the same problem... :confused:

Anyway, I turned off ssl (a2dismod ssl) and then the server started again, but I really need to install that certficate! What can I do guys?

Thank you for your time.

---

### Post by wouterd on 2009-09-21
Update:

I tried making /var/run/apache2 writable for www-data (apache user) but that did not work either..

---

