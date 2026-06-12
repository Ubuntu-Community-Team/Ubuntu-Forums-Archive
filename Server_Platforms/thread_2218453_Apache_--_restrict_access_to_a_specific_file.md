---
title: "Apache -- restrict access to a specific file"
date: 2014-04-20
forum: Server Platforms
---

### Post by bewareofthephog on 2014-04-20
I have a php script that allows me to upload data to a MySQL DB from my mobile device.  Is there a way to limit access to this file so I can tell Apache to allow *x* hostname's to see/execute it?

---

### Post by SeijiSensei on 2014-04-20
Put it in a subdirectory of its own and control access to the directory using the methods described [here](http://httpd.apache.org/docs/2.2/howto/access.html).

---

