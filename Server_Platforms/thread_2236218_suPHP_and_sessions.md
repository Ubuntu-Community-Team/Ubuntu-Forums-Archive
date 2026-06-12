---
title: "suPHP and sessions"
date: 2014-07-25
forum: Server Platforms
---

### Post by alfirdaous on 2014-07-25
Hello everybody,

Once I installed suphp, I cannot login into the member area, I think this is dur to sessions, if anyone can help

Thanks in advance

---

### Post by alfirdaous on 2014-07-25
so sort it out, we need to create an htaccess file and put the below code, mentionning the path to php.ini file:

```

<IfModule mod_suphp.c>
suPHP_ConfigPath /etc/php5/apache2
</IfModule

```

and edit the permission in /var/lib/php5

```

ls -l /var/lib/php5
drwx-wx-wt 2 root          root          69632 Jul 25 21:39 php5

ls -l php5
-rw------- 1 alfirdaous alfirdaous   0 Jul 25 21:09 sess_0qei54ev0rav2vo2dq5crsfin3
-rw------- 1 alfirdaous alfirdaous 558 Jul 25 21:40 sess_6gttnqbebfjuuvfms60epfq223
-rw------- 1 root          root            0 Jul 25 21:39 sess_b0asbnb0n6etlao9r2vp3n6v72


```

---

