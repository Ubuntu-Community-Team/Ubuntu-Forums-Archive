---
title: "how to enable url rewriting in apache2"
date: 2009-12-17
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-17
I want to know what should be done so that URL rewriting is enabled in Apache2 I have a .htaccess file which has the required entries but do not know which file in apache2 to touch.

---

### Post by Dratir on 2009-12-17
Hey tapas_mishra!
Did you enable the required module for apache?

```
sudo a2enmod rewrite
```

---

### Post by tapas_mishra on 2009-12-17
I had enabled my site using that may be I have done it but in a page it is not showing me navigation to other pages hence  how do I check it whether I have enabled it or not because once I make sure it is not the issue from apache2 I will check in PHP files.

---

