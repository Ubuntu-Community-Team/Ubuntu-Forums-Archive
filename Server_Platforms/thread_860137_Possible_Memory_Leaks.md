---
title: "Possible Memory Leaks"
date: 2008-07-15
forum: Server Platforms
---

### Post by matdavey on 2008-07-15
Hi All, 

Many apologies if this has been posted before, Ive been playing with python 2.52 and mysql (5.0.45 and 5.051a)  on ubuntu 8.04. The following examples of code seem to cause a memory leak. I was wandering if anyone had come accross this.

Example 1 - Python shelve

import shelve
while 1:
    f = shelve.open("/tmp/x")
    f.close()

For the code below you will also need mysqldb

Example 2 - Mysql - Mysqldb and Python
import MySQLdb
while 1:
    try:
        conn = MySQLdb.connect(host="127.0.0.1",user="user",passwd="password", db="database")
        conn.close()
    except:
        pass


(many apologies for the tabbing). conn is equal to the mysqldb.connect line

I have updated to the very latest updates from the ubuntu repository. Execute each script and then view the memory usage using “top” or “free –m”. Script 1 uses memory very quickly. Script 2 needs a working MySQL database and takes several minutes before memory usage is noticeably higher.

Regards

Mat

---

### Post by GarthofNEaB on 2008-07-15
I'm not a python expert, in fact I barely know any python, but that looks like an infinite loop to me. 
while 1: seems like it would loop whatever is put into it forever, which would explain why you're experiencing memory problems since it would continue running that code until you stopped it.

---

### Post by matdavey on 2008-07-15
Hi GarthofNEaB

Many thanks for your answer, I realise that this is an infinite loop. This code is mainly used as a test to highlight the memory leak. To my understanding the code should not consume all of the system memory, which is what I have been experiencing.

Regards

Mat

---

### Post by GarthofNEaB on 2008-07-15
I figured it was something along that order, I just figured I should make sure. My mistake, sorry for that.

---

