---
title: "question on setting up userpage on my webserver"
date: 2011-10-15
forum: Server Platforms
---

### Post by kustomjs on 2011-10-15
Hey Guys
I have a question about how to setup a userpage on my webserver and here is how I want it be setup as domain.com/~username now how would I setup that under Ubuntu server?

---

### Post by vasile002 on 2011-10-16
you need to enable the userdir module
Here's how you can do it:
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart

```

---

