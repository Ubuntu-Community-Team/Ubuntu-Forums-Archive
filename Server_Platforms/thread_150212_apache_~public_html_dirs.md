---
title: "apache ~/public_html dirs"
date: 2006-03-25
forum: Server Platforms
---

### Post by peanut butter on 2006-03-25
when i access one it worksbut for all others it gives me a 403 error
i have chmoded as much as possible even reclusive.

---

### Post by Kurt` on 2006-03-25
Perhaps you have directory listing disabled by default for userdirs? (in the apache config file)

Try putting a (readable) index.html file into the userdir and visiting it in the browser.

---

### Post by peanut butter on 2006-03-25
there is one

---

### Post by Kurt` on 2006-03-25
Can you post your <Directory /home/*/public_html> section from the apache2.conf file?

---

### Post by peanut butter on 2006-03-26
[QUOTE=Kurt`]Can you post your <Directory /home/*/public_html> section from the apache2.conf file?[/QUOTE]
i figured it out. i hadent acyually loged on as either of the users after i sshed into te server as them it worked like a charm.8)

---

