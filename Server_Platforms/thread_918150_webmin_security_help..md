---
title: "webmin security help."
date: 2008-09-12
forum: Server Platforms
---

### Post by hockey97 on 2008-09-12
Hi I have webmin installed and I want it to be only accessed by localhost.

Meaning only myserver.

can anyone help me out???

---

### Post by volkswagner on 2008-09-12
From the webmin interface.

>Webmin>Webmin configuration>Ip Access Control

From there you can select x-only from

Then enter the desired ip address(s).

---

### Post by hockey97 on 2008-09-12
ok I see. got it.  But why is my files able to be downloaded???

talking about apache.

I notice I can download any file like javascript and css and even photos.

Is there a way where I can lock these files but still be able to show them on my website???

---

### Post by windependence on 2008-09-13
You have to edit your apache2.conf file

To turn off automatic directory indexing, remove the Indexes keyword from the appropriate Options line. To turn off directory listing for a particular subdirectory, you can use Options -Indexes. For example:

```
<Directory /path/to/directory>
   Options -Indexes
</Directory>
```

Let me know if you need any help.

-Tim

---

