---
title: "fail2ban php-url-fopen ignore regex help"
date: 2011-06-10
forum: Security
---

### Post by krosswindz on 2011-06-10
I am running fail2ban on my LAMP server. I am also hosting a forum and whenever there is a external url I display a warning that the user is being redirected from this forum. The problem that is happening is that all those users get banned as part of the php-url-fopen filter. I tried playing with the ignoreregex but I am unable to get the right regex.

sample log
```

xxx.xxx.xxx.xxx - - [10/Jun/2011:15:20:39 +0200] "GET /forums/cron.php?rand=1307712039 HTTP/1.1" 200 352 "http://domain.net/forums/externalredirect.php?url=http://foo.com" "Mozilla/5.0 (Windows NT 6.1; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"

```

any help on this is appreciated.

---

