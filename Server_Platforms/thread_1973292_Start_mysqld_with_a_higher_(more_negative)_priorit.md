---
title: "Start mysqld with a higher (more negative) priority"
date: 2012-05-04
forum: Server Platforms
---

### Post by joe_lovick on 2012-05-04
Hi,
    Could someone tell me how i change my init scripts so that when the mysqld task launches it uses a priority of -10, instead of the default 0.
    my server is almost totally dedicated to mysql and not having to set it by hand, will simplify our recovery procedures

I am using, 3.0.0-17-generic Oneric
  
Thanks
           Joe

---

### Post by poolet on 2012-05-04
> **joe_lovick said:**
> Hi,
    Could someone tell me how i change my init scripts so that when the mysqld task launches it uses a priority of -10, instead of the default 0.
    my server is almost totally dedicated to mysql and not having to set it by hand, will simplify our recovery procedures

I am using, 3.0.0-17-generic Oneric
  
Thanks
           Joe


open up  /etc/init/mysql.conf script and then pass the following at the end:::


```

exec /usr/sbin/mysqld

post-start script

sleep 10
renice -n -10 -p `echo \`pgrep mysqld\` | sed -e 's/ /,/g'`
ionice -c 1 -p `echo \`pgrep mysqld\` | sed -e 's/ /,/g'`

    for i in `seq 1 30` ; do

```**::Note::**
ionice  -c 1 is for real time 
and 
renice -n -10 is for high priority

---

### Post by joe_lovick on 2012-05-05
Thank you so much!

---

