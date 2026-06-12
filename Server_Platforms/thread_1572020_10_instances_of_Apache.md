---
title: "10 instances of Apache"
date: 2010-09-10
forum: Server Platforms
---

### Post by SirKonstantine on 2010-09-10
Ok, I was running Magento on a LAMP server with ISPConfig as its control panel and the server would get EXTREMELY slow after a few days of being on. Also, Apache would be EXTREMELY slow and buggie. I checked on top and realized that there were about 10 instances of apache running.

I thought this was a problem with ISPConfig so I just migrated everything to a new LAMP server with VirtualMin as its control panel. The same thing is happening. Here is the outputs of top from this new server:

> PID USER      PR  NI  VIRT  RES  SHR S &#xCP;U &#xME;M    TIME+  COMMAND
12945 www-data  20   0  383m  40m 1312 S    0  8.2   0:05.39 apache2
12944 www-data  20   0  299m  37m 1712 S    0  7.6   0:05.62 apache2
13351 www-data  20   0  285m  28m  428 S    0  5.8   0:04.13 apache2
14490 www-data  20   0  281m  25m 1464 S    0  5.2   0:02.45 apache2
10592 www-data  20   0  278m  23m  400 S    0  4.8   0:05.73 apache2
13074 www-data  20   0  296m  21m 1444 S    0  4.3   0:04.90 apache2
14284 www-data  20   0  274m  20m 1520 S    0  4.2   0:01.32 apache2
14481 www-data  20   0  279m  15m  516 S    0  3.1   0:01.29 apache2
13320 www-data  20   0  286m  14m  428 S    0  3.0   0:04.43 apache2
13354 www-data  20   0  278m  10m  340 S    0  2.1   0:02.67 apache2
  320 mysql     20   0  292m 6924  284 S    0  1.4   0:22.40 mysqld
This is without any products added to the server. The first server had 1,500 products and apache was using up 90% of my physical memory as well as 50% of my swap. I am afraid that this new server will do the exact same thing when I add products to it.

Since this is a fresh install of Ubuntu on this server also, I think it might be something wrong with the server? Am I suppose to see this many instances of Apache? I thought one instance was good enough. Thanks.

---

### Post by Joe of loath on 2010-09-10
I think it's normal, my server (Debian 5.04 running on a Celeron 1.8ghz with 512mb of RAM) says this:

```

joe@terrence-server:~$ ps -ef | grep apache
root      2522     1  0 Sep04 ?        00:00:11 /usr/sbin/apache2 -k start
www-data  8306  2522  0 Sep07 ?        00:00:23 /usr/sbin/apache2 -k start
www-data 10152  2522  0 Sep08 ?        00:00:21 /usr/sbin/apache2 -k start
www-data 10843  2522  0 Sep08 ?        00:00:24 /usr/sbin/apache2 -k start
www-data 11160  2522  0 Sep08 ?        00:00:21 /usr/sbin/apache2 -k start
www-data 11754  2522  0 Sep08 ?        00:00:24 /usr/sbin/apache2 -k start
www-data 14571  2522  0 Sep09 ?        00:00:20 /usr/sbin/apache2 -k start
www-data 14718  2522  0 Sep09 ?        00:00:15 /usr/sbin/apache2 -k start
www-data 14919  2522  0 Sep09 ?        00:00:19 /usr/sbin/apache2 -k start
www-data 15653  2522  0 05:47 ?        00:00:14 /usr/sbin/apache2 -k start
www-data 17354  2522  0 18:29 ?        00:00:00 /usr/sbin/apache2 -k start
joe      17461 17447  0 19:11 pts/0    00:00:00 grep apache

```

---

### Post by terazen on 2010-09-10
Yeah it's normal.  You can tweak apache for this in /etc/apache2/apache2.conf under the area around "StartServers" and "MaxClients".

You can try to tweak these settings if you know what you are doing (I don't).  The only time I've ever had apache eating up cpu was moodle/drupal either getting slammed or a buggy module I enabled in moodle.

---

### Post by Vegan on 2010-09-10
The more instances of Apache, the busier the server is.

They will go away once the session is done.

---

### Post by SirKonstantine on 2010-09-14
Ok thanks guy I was really worried about that. But I have been looking deeper into my system and there is a HUGE problem!

```
[Tue Sep 14 15:33:29 2010] [warn] child process 6990 still did not exit, sending a
 SIGTERM
[Tue Sep 14 15:33:29 2010] [warn] child process 8166 still did not exit, sending a
 SIGTERM
[Tue Sep 14 15:33:30 2010] [error] child process 13970 still did not exit, sending
 a SIGKILL
[Tue Sep 14 15:33:30 2010] [error] child process 6990 still did not exit, sending a SIGKILL
[Tue Sep 14 15:33:30 2010] [error] child process 8166 still did not exit, sending a SIGKILL
[Tue Sep 14 15:33:31 2010] [error] could not make child process 13970 exit, attempting to continue anyway
[Tue Sep 14 15:33:31 2010] [error] could not make child process 6990 exit, attempting to continue anyway
[Tue Sep 14 15:33:31 2010] [error] could not make child process 8166 exit, attempting to continue anyway

```

My Apache stopped responding this morning and I think its due to that. I looked this up on google and it says that it could be due to a faulty script. This makes total sense why my last server was using up 100% RAM and 50% swap. 
There must be a buggy script in Apache somewhere, and since I migrated servers, the script followed it. That is why apache has been acting up for me. So its not the fact that there are 10 instances of Apache, but there is a few buggie scripts.
So, how do I find out which script is causing this? I am running VirutalMin on this server with Magento eCommerce. Both apps are quite complex.

Also, is it possible for me to set up a warning system, so that when my memory is at 75% I get an email saying "APACHE IS HOGGING MEMORY!" or something like that? It'll be nice to get a warning before everything goes down.

Thanks guys!

---

### Post by Richard1979 on 2010-09-14
If these scripts are PHP, check for the string "ignore_user_abort":

> grep 'ignore_user_abort' * -R

That function is kinda evil.
[http://php.net/manual/en/function.ignore-user-abort.php](http://php.net/manual/en/function.ignore-user-abort.php)

---

