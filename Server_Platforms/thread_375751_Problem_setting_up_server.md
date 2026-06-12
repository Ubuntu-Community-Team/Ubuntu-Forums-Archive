---
title: "Problem setting up server"
date: 2007-03-04
forum: Server Platforms
---

### Post by radu_berbece on 2007-03-04
Hello,
I have just installed feisty and also set up apache, php5, and mysql. I copied my websode to /var/www/, I access it in the browser and it gives me this error:

[B]Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/catalog/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/B]

what is this? what can I do?

---

### Post by jtc on 2007-03-04
My best guess is that Apache/PHP simply don't have the file permissions to read your file. Since the webserver generally runs as its own user, you then want to make your web files globally readable. 

```

chmod 755 /var/www/catalog
chmod 644 /var/www/catalog/index.php

```

On another matter. Are you sure you want to run Feisty, still being Alpha, as a server?

---

