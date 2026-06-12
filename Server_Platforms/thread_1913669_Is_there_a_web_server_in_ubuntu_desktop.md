---
title: "Is there a web server in ubuntu desktop?"
date: 2012-01-22
forum: Server Platforms
---

### Post by StepNjump on 2012-01-22
I'm on natty. At my local IP address of 192.168.0.101, I noticed a server is running up. It's located at /var/www/index.html

What is this server? Should I shut it off for security reasons?

Thanks in advance,


StepNjump

---

### Post by cariboo on 2012-01-23
It sounds like you installed apache2, a web server. If you don't need it, you can completely remove it using your favorite method of installing/removing software packages. Be sure to stop apache2 before removing it, using the following command:

```
sudo service apache2 stop
```

---

### Post by StepNjump on 2012-01-23
Oh that's awsome.. Thank you very very much!

Pete

---

