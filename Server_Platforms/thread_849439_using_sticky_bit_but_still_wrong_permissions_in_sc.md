---
title: "using sticky bit but still wrong permissions in script"
date: 2008-07-04
forum: Server Platforms
---

### Post by anty on 2008-07-04
I want to reload the httpd.conf file of my Apache2 server by calling "/etc/init.d/apache2 reload". Because I want to do this in PHP I wrote a script and executed the following two commands on it:

chown root apache2-reload.sh
chmod 4755 apache2-reload.sh

Now I don't get asked for the root password when I start the script in my shell. In PHP however, I get the same error messages as I would call it with insufficient permissions:

```
* Reloading web server config apache2
4271
httpd not running, trying to start
   ...fail!
```

I start the script with the following PHP command:
exec('/absolute/path/to/apache2-graceful.sh');

The script has the following content:
```
#!/bin/bash
/etc/init.d/apache2 reload
```

What am I doing wrong here?

Thanks,
anty

---

