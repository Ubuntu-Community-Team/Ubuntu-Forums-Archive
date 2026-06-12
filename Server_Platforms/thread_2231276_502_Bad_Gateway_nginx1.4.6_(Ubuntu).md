---
title: "502 Bad Gateway nginx/1.4.6 (Ubuntu)"
date: 2014-06-24
forum: Server Platforms
---

### Post by mroussin51 on 2014-06-24
Greetings,

Thank you to all the contributors that make all of this possible! 

I have version 14.04 64 bit. Upon running a system update I was greeted by 502 Bad Gateway nginx/1.4.6 (Ubuntu) on my Chrome and Firefox Browsers when trying to access my website. So I 

```
tail -f /var/log/nginx/error.log
```

where I learned that nginx was looking for /var/run/php5-fpm.sock  

```
2014/06/24 13:59:51 [crit] 953#0: *69 connect() to unix:/var/run/php5-fpm.sock failed (2: No such file or directory)
```

The file in /var/run/ was actually php5-fpm.sock. with the trailing period.

 So I executed 

```
sudo mv /var/run/php5-fpm.sock. /var/run/php5-fpm.sock
```

Then I got a new error!

```
2014/06/24 14:44:18 [crit] 953#0: *114 connect() to unix:/var/run/php5-fpm.sock failed (13: Permission denied) while connecting to upstream,
```

So I changed the permissions on 

```
/var/run/php5-fpm.sock to chmod 666 /var/run/php5fpm.sock
``` 

Now I have access to my website.

My quest is how to fix  this permission discrepancy without making /var/run/php5-fpm.sock world writable. 

Thanks again,

Mike

I have realized something else. Every time I execute:

```
service php5-fpm restart
```

The permissions is set back to 660 from 666 and the 502 Bad Gateway returns.

I also learned that nginx runs as user www-data.

So with the permission of 660 I am able to run the following.

```
chgrp www-data /var/run/php5-fpm.sock
```

Then again I have access to my website again and no world read write of: /var/run/php5-fpm.sock

However, the group is changed back to root upon executing:

```
service php5-fpm restart
```

I don't know what else to try at this point. I appreciate that you have looked at this.

regards,

Mike

Hello,

I found this website which gave me the simple solution to my problem.

[HTML]http://www.nginxtips.com/php5-fpm-sock-failed-13-permission-denied-error/[/HTML]

The solution is to:

```
vi /etc/php5/fpm/pool.d/www.conf
``` then;

change ```
; [COLOR=#404040][FONT=Courier 10 Pitch]listen.owner = www-data[/FONT][/COLOR]
``` to ```
[COLOR=#404040][FONT=Courier 10 Pitch]listen.owner = www-data[/FONT][/COLOR]
``` and;

change ```
; [COLOR=#404040][FONT=Courier 10 Pitch]listen.group = www-data[/FONT][/COLOR]
``` to ```
[COLOR=#404040][FONT=Courier 10 Pitch]listen.group = www-data[/FONT][/COLOR]
``` then;

```
service php5-fpm restart
``` Then;

All is well with nginx and php5-fpm should now play nice together.

I am a little puzzled by why this happened I hope that others that experience the same can benefit from my head scratching!

regards,

Mike

---

