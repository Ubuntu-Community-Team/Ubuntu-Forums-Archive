---
title: "&quot;Ubuntu 8.04.3 LTS&quot; Console String"
date: 2009-07-20
forum: Server Platforms
---

### Post by shebangs on 2009-07-20
When you boot Ubuntu Server the last thing it does is execute rc.local then display the below string:



Ubuntu 8.04.3 LTS <hostname> tty1


Where does it get 'Ubuntu 8.04.3' from?  We use JeoS as a base for an appliance we make, and I'd like to add a small string to the end of it.

Thanks

---

### Post by gastly on 2009-07-20
You can get the ubuntu version string from the following commands:
```

lsb_release -a
cat /etc/issue
cat /etc/lsb-release

```

Choose which one works for you the best :)

---

### Post by shebangs on 2009-07-20
I don't want to get the release.

I want to know where the boot console login screen gets it from, so I can append additional text to the end of it.

---

