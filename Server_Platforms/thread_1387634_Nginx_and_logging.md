---
title: "Nginx and logging"
date: 2010-01-22
forum: Server Platforms
---

### Post by commandergc on 2010-01-22
A few weeks ago I decided to ditch apache2 for nginx, so far it has been good but for one little problem.

I had apache configured to not log specified IP and host names. I was wondering how I can do this with nginx as the documentation doesn't seem to be very clear on how it should be done.

In nginx.conf in the http part i added the following:
```

geo $loc {
        default 0;
        192.168.0.0/24 1;
        127.0.0.0/24 1;
}

```
then in the host config file in the location '/' part i added the following:
```

if ($loc) {
      access_log off;
}
```

this didn't work, what have I missed?

---

