---
title: "Apache Error Log"
date: 2009-07-25
forum: Server Platforms
---

### Post by zemon_ on 2009-07-25
Im recieving this error in my apache log.

```
[Wed Jul 22 03:38:27 2009] [error] [client 127.0.0.1] File does not exist: /var/www/scrape
[Wed Jul 22 03:38:28 2009] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Wed Jul 22 03:39:48 2009] [error] [client 127.0.0.1] File does not exist: /var/www/announce

```

Could anyone explain the reason for this?

---

### Post by gombadi on 2009-07-25
> 
[Wed Jul 22 03:38:27 2009] [error] [client 127.0.0.1] File does not exist: /var/www/scrape


Something on the local machine is making a request that maps to /var/www/scrape but that path does not exist. Do ls -l /var/www/scrape to confirm if you want.

What was the url that you went to?
My guess is that there is no vhost entry with a hostname that matches so apache sent the request to the default vhost which looked in the /var/www directory and did not find scrape.

---

### Post by zemon_ on 2009-07-27
How can I make my error log ignore this?

---

### Post by khatkarrohit on 2010-07-16
I have the similer problem , i think it caused by bittorrent application because of local peer discovery. I am running utorrent then this accur.

Have u got the solution.

I found this : [http://ubuntuforums.org/archive/index.php/t-352857.html](http://ubuntuforums.org/archive/index.php/t-352857.html)

[Sat Jul 17 07:01:29 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 07:31:49 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:01:53 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:01:54 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:08:34 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:09:18 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:19:53 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:39:23 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:39:24 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Sat Jul 17 08:49:28 2010] [error] [client 127.0.0.1] File does not exist: /var/www/announce

---

