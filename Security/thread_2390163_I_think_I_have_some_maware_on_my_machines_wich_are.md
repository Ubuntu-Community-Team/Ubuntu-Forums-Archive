---
title: "I think I have some maware on my machines wich are repeatatively creating sync_super"
date: 2018-04-26
forum: Security
---

### Post by d.chaudhari on 2018-04-26
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I am facing same knid of pproblem of having sync_supers recreated on my server. which are using high CPU usage[/COLOR]

[COLOR=#000000]4353 www-data 20 0 24392 3888 1012 R 100.0 0.0 13:15.26 [sync_supers][/COLOR]
[COLOR=#000000]5268 www-data 20 0 24392 3888 1012 R 100.0 0.0 9:42.56 [sync_supers][/COLOR]
[COLOR=#000000]4344 www-data 20 0 24264 3744 876 R 99.7 0.0 70:22.26 [sync_supers][/COLOR]
[COLOR=#000000]6792 www-data 20 0 24392 3892 1012 R 85.5 0.0 7:16.08 [sync_supers][/COLOR]

[COLOR=#000000]I have deleted few but again recreated with different pid.[/COLOR]

[COLOR=#000000]Please help.[/COLOR]
[COLOR=#000000]I am not expertise in Ubuntu and linux, so bit difficult to trace the issue.[/COLOR]

[COLOR=#000000]Thank you very much.[/COLOR]

---

### Post by d.chaudhari on 2018-04-26
Waitng for reply.. Please help

---

### Post by QIII on 2018-04-26
Please do not bump your threads so quickly.  It is acceptable to bump your thread if you have not received a response within 12 hours.

---

### Post by SeijiSensei on 2018-04-26
[https://lwn.net/Articles/508212/](https://lwn.net/Articles/508212/) suggests this was fixed years ago.

What Ubuntu version are you running?  Use the command "uname -a" to see what kernel version you're running as well.

---

### Post by d.chaudhari on 2018-04-27
Hi,
Thank you for the link you have provided, bu I dont understand how to write commands on putty to get rid of this thread.
Will you please guide me with commands please. Also the major issue comes up today with Id-linux-x86-64 command using huge CPU usage.

I am using following ubuntu version

3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Today I have got other process with Id-linux-x86-64 command which is using huge cpu utilization.
tmy top result is as below:
```
 58641 www-data  20   0 2617780  77628   1208 S  1526  0.0  17662:19 ld-linux-x86-64
109446 www-data  20   0 2617780  74648   1208 S  1526  0.0  17341:34 ld-linux-x86-64
 38377 mysql     20   0 13.464g 996384   8716 S  82.1  0.6   1640:53 mysqld
  4344 www-data  20   0   24396   3876    992 R  79.2  0.0 976:35.14 [sync_supers]
109839 www-data  20   0   24392   3884   1012 R  75.9  0.0  56:43.42 [sync_supers]
  5259 www-data  20   0   24392   3888   1012 R  71.2  0.0 170:13.19 [sync_supers]
  4353 www-data  20   0   24392   3888   1012 R  67.0  0.0 159:27.87 [sync_supers]
 31187 www-data  20   0  594848  97432  39524 R  63.0  0.1   0:04.60 apache2
 29951 www-data  20   0  594532  96956  39408 R  59.7  0.1   0:02.36 apache2
 30025 www-data  20   0  605100 115404  46980 R  57.4  0.1   0:08.05 apache2
 84674 www-data  20   0   24392   3888   1012 R  57.4  0.0   5:45.47 [sync_supers]
 30019 www-data  20   0  603716 114688  47660 S  45.5  0.1   0:10.65 apache2
 22422 www-data  20   0  614224 124648  47844 R  41.2  0.1   0:09.13 apache2
 30027 www-data  20   0  594596 104816  46916 S  40.9  0.1   0:08.23 apache2
 13365 www-data  20   0  611352 123168  48472 R  32.3  0.1   0:30.92 apache2
  5660 www-data  20   0   24392   3884   1012 S  28.0  0.0 174:39.96 [sync_supers]
127554 www-data  20   0   24392   3892   1012 R  27.7  0.0   1:26.44 [sync_supers]
120259 www-data  20   0  607872 119304  48100 R  26.4  0.1   0:51.82 apache2
111966 www-data  20   0   24392   3892   1012 R  15.2  0.0  67:41.80 [sync_supers]
 33052 www-data  20   0    9084   8780      0 S   8.9  0.0   0:00.27 b
```



Please help me for fixing this issue.

Thanks a lot

---

### Post by d.chaudhari on 2018-05-01
Hi,

I am waiting for reply.
Please help.

Also now I am getting lot of processes with b command as below.
Is it something wrong?

 38031 www-data  20   0    7104   6804      0 S   4.9  0.0   0:00.15 b
 38081 www-data  20   0    7104   6804      0 S   4.9  0.0   0:00.15 b
 38224 www-data  20   0    7108   6808      0 S   4.9  0.0   0:00.15 b
 38368 www-data  20   0    7112   6808      0 S   4.9  0.0   0:00.15 b
 38378 www-data  20   0    7112   6808      0 S   4.9  0.0   0:00.15 b
 38383 www-data  20   0    7112   6808      0 S   4.9  0.0   0:00.15 b
 38000 www-data  20   0    7104   6800      0 S   4.6  0.0   0:00.14 b
 38073 www-data  20   0    7104   6804      0 S   4.6  0.0   0:00.14 b
 38093 www-data  20   0    7104   6804      0 S   4.6  0.0   0:00.14 b
 38133 www-data  20   0    7104   6804      0 S   4.6  0.0   0:00.14 b
 38168 www-data  20   0    7104   6804      0 S   4.6  0.0   0:00.14 b
 38186 www-data  20   0    7104   6804      0 S   4.6  0.0   0:00.14 b
 38228 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38230 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38258 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38269 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38289 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38293 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38309 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38311 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38338 www-data  20   0    7108   6808      0 S   4.6  0.0   0:00.14 b
 38379 www-data  20   0    7112   6808      0 S   4.6  0.0   0:00.14 b
 38510 www-data  20   0    7060   6812      0 S   4.6  0.0   0:00.14 b
 38515 www-data  20   0    7060   6812      0 S   4.6  0.0   0:00.14 b
 89992 www-data  20   0    6928   6816      4 S   3.6  0.0   0:47.86 b


Thanks a lot.

---

### Post by HermanAB on 2018-05-01
Well, the sync_supers threads are not necessarily due to malware, but it could be a symptom of the server being overloaded.

By default apache2 is configured to support 150 concurrent connections. This forces all parallel requests beyond that limit to wait. Especially if, for example, active sync clients maintain a permanent connection for push events to arrive.

How to fix the problem is hard to say.  You could spin up another server and use round robin DNS to be able to handle more users, or you could go the other way and limit connection attempts with iptables to shed users, if you don't really want them.

---

### Post by Habitual on 2018-05-01
"[I am using Drupal 7 and amazon linux server]("https://askubuntu.com/questions/1028367/repeatatively-creating-sync-super-for-www-data-which-is-showing-high-cpu-usage/1028716#1028716")" is "you"?
Drupal 0day "in the wild. if it is "you"

---

### Post by d.chaudhari on 2018-05-03
Yes I am using Drupal 7 and amazon linux server.

my site is getting slower with the repetative processes.
before the was less but now when I kill process , new one is created withing seconds.

Please help.
I am in big trouble.




 83691 www-data  20   0   24384   3888   1008 R 100.0  0.0 378:31.12 [sync_supers]
 84643 www-data  20   0   24392   3892   1012 R 100.0  0.0   1016:53 [sync_supers]
128263 www-data  20   0   24392   3896   1016 R 100.0  0.0   1249:02 [sync_supers]
 51277 www-data  20   0   24392   3892   1012 R  99.9  0.0 868:23.00 [sync_supers]
 63718 www-data  20   0   24392   3932   1048 R  99.9  0.0 886:58.16 [sync_supers]
103743 www-data  20   0   24392   3892   1012 R  99.9  0.0 918:17.53 [sync_supers]
104970 www-data  20   0   24392   3892   1012 R  99.9  0.0 930:28.09 [sync_supers]
127596 www-data  20   0   24392   3888   1012 S  93.6  0.0   1215:25 [sync_supers]
127554 www-data  20   0   24392   3892   1012 R  67.4  0.0   1165:11 [sync_supers]
119618 www-data  20   0  627568 143960  52972 S  55.4  0.1   0:25.85 apache2

---

### Post by SeijiSensei on 2018-05-03
How hard would it be to spin up a new, clean AWS instance and copy over just the website files?

---

