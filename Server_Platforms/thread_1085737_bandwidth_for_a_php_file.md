---
title: "bandwidth for a php file"
date: 2009-03-03
forum: Server Platforms
---

### Post by divinequran on 2009-03-03
Hi,

Can i find how much a file consumes bandwidth when the file is executed on the server or when the request is made on the server? i am trying to execute a php file. it take quite a long to get response, is there is any free software to find it

---

### Post by cdenley on 2009-03-03
> **divinequran said:**
> Hi,

Can i find how much a file consumes bandwidth when the file is executed on the server or when the request is made on the server? i am trying to execute a php file. it take quite a long to get response, is there is any free software to find it

PHP scripts usually use very little bandwidth. It only has to send the output of the script back to the user. If you really want to know, you can use wget:
```

wget -O /dev/null http://mydomain.com/myscript.php

```
That will tell you the size of the output, the time it took to download the output, and the speed of the download.

I would guess that any delay you are experiencing is from execution, though. Try running it from the command line on the server, and see how long it takes.
```

sudo apt-get install php5-cli
php /var/www/myscript.php

```

---

