---
title: "Compiling PHP for Ubuntu Server"
date: 2008-02-05
forum: Server Platforms
---

### Post by xrvjorn on 2008-02-05
I need to recompile PHP for Ubuntu Server (because I need the full GD2 monty), and the six A4-size pages of configure-switches make me quite bewildered. Does anyone know the switches with which PHP was compiled in the default 6.06LTS setup? If I knew them, then I could just add "--with-gd" and I've got it made!

---

### Post by cdenley on 2008-02-05
I don't have a computer running dapper, but you can try:

```

apt-get source php5
gedit php5*/debian/rules

```

---

### Post by sflemi17 on 2008-02-05
Unfortunately, i can tell you, but if you have php currently installed you can view the configure string used by creating a new php page with [PHP]
<?php
   phpinfo();
?>[/PHP]

View the page in your browser, in the top section you should be able to see the configure string used to complie it previously.

Hope this helps.

---

