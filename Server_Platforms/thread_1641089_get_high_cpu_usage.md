---
title: "get high cpu usage"
date: 2010-12-08
forum: Server Platforms
---

### Post by yconselvan on 2010-12-08
hi everybody,

i have a program that parse a text file and insert data into mysql.

when i run the program in my notebook running ubuntu desktop 10.04 the program gets high cpu usage, just like i want.

but when i run the program in a computer running ubuntu server 10.04 the program doesn't get high cpu usage and take too much time to process the files.

what could be happening? there are any scheduling diference that i'm not considering?

thanks

---

### Post by yconselvan on 2010-12-09
solved my problem.

the mysql variable innodb_flush_log_at_trx_commit = 1, forcing mysql to write every transation to disk was causing my problem.

i think that in my notebook the disk is faster than the disk of the other computer, so that was the problem.

thanks

---

