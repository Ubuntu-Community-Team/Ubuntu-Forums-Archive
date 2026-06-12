---
title: "Apache logs"
date: 2012-06-22
forum: Server Platforms
---

### Post by bethafin on 2012-06-22
Hello, 
Just installed apache 2.4 on Ubuntu 10.04 64-Bit server edition. 

For some reason, I get in the apache error log as often as 6 times every second:

[Fri Jun 22 16:08:47.834685 2012] [example_hooks:notice] [pid 20395:tid 140585687512832] x_monitor()

I am completely at a  loss on how to stop this. It looks like a monitor but don't know where it is enabled/configured. 

Does anyone know how to stop this?

Thank you for your help!

---

### Post by Habitual on 2012-06-24
examine the http .conf file(s) under /etc/apache2 for string "example_hooks"
```

grep -iw example_hooks /etc/apache2 -R
```HTH

---

