---
title: "mod_python apache2 sessions"
date: 2010-09-21
forum: Server Platforms
---

### Post by Mickeysofine1972 on 2010-09-21
Hi All

I'm having a problem with sessions not storing info I'm inserting

I have done some looking and it appears I've got between 6 to 10 instances of apache running after doing a /etc/init.d/apache2 restart or when I boot up:


ps aux | grep apache2
root      6041  0.2  0.3  38020 10036 ?        Ss   11:51   0:00 /usr/sbin/apache2 -k start
www-data  6045  0.0  0.1  38020  5876 ?        S    11:51   0:00 /usr/sbin/apache2 -k start
www-data  6046 10.4  0.5  47020 16996 ?        R    11:51   0:00 /usr/sbin/apache2 -k start
www-data  6047  0.0  0.1  38020  5876 ?        S    11:51   0:00 /usr/sbin/apache2 -k start
www-data  6048  0.0  0.1  38020  5876 ?        S    11:51   0:00 /usr/sbin/apache2 -k start
www-data  6049  0.0  0.1  38020  5876 ?        S    11:51   0:00 /usr/sbin/apache2 -k start
mike      6068  0.0  0.0   3372   748 pts/0    S+   11:51   0:00 grep apache2


is this normal? or could this be why my sessions a screwed up?

Also, how can I stop this from happening as I'm not getting a proper restart which is making it so I have to killall instances.

Thnaks in advance

Mike

---

