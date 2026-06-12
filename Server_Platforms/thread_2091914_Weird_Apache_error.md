---
title: "Weird Apache error"
date: 2012-12-06
forum: Server Platforms
---

### Post by Owdy on 2012-12-06
I moved my debian server to new Ubuntu server. Right after that, my Apache log is full of these:

```
client denied by server configuration: /home/public_html/forum/cache/df.php
```

Any idea whats that? I don even have such file.

---

### Post by chadk5utc on 2012-12-06
> **Owdy said:**
> I moved my debian server to new Ubuntu server. Right after that, my Apache log is full of these:

```
client denied by server configuration: /home/public_html/forum/cache/df.php
```

Any idea whats that? I don even have such file.

Is this from the error log or access log? more info could help. I have seen similar lines in my own logs and determined that in my case its some luser fishing for pages/exploits in pages that do not exist on my own servers.

---

### Post by Owdy on 2012-12-06
> **chadk5utc said:**
> Is this from the error log or access log? 

acces.log

---

### Post by SeijiSensei on 2012-12-06
Aren't you missing a user name there, like "/home/username/public_html"?  Or did you create a user called "public_html"?

---

### Post by Owdy on 2012-12-06
> **SeijiSensei said:**
> Aren't you missing a user name there
yes, i removed it from post..

---

### Post by SeijiSensei on 2012-12-06
Try "sudo a2enmod userdir" and restart Apache.  Access to the public_html directories is not enabled by default for security reasons.

---

### Post by Owdy on 2012-12-06
> **SeijiSensei said:**
> Try "sudo a2enmod userdir" and restart Apache.  Access to the public_html directories is not enabled by default for security reasons.
Its has to be enabled, my site is working.

---

