---
title: "timimg out with ssh"
date: 2010-03-02
forum: Server Platforms
---

### Post by jmsgz on 2010-03-02
hi folks
  have good connection between desktop and server via (eth0) using remote desktop viewer, but when trying to connect via ssh connect to server i get
"Timed out when logging in" ???? 

can you point me in the direction to fix?
thanks in advance :-)
jmsgz

---

### Post by byStanderone on 2010-03-02
...check port 22, a firewall may be blocking it

---

### Post by jmsgz on 2010-03-02
i have disabled ufw via gufw.

---

### Post by jmsgz on 2010-03-02
also getting host key verification failed

---

### Post by byStanderone on 2010-03-03
...well, have you configured your remote desktop under system>preferences?

---

### Post by jmsgz on 2010-03-03
ok, figured it out!!! for you folks that have the same problems. The contents of the ~/.ssh/known_hosts file. on the client machine needed to be sent to > "null" Then looged back in and the ssh authorization system worked correctly with client. 

REF: See a GREAT BOOK The Linux® Command Line
       William E. Shotts, Jr.

this book has helped me more than all refrences so far, not counting this forum
can be downloaded from net

thanks folks :-)

---

### Post by Iowan on 2010-03-03
> **jmsgz said:**
> REF: See a GREAT BOOK The Linux® Command Line
       William E. Shotts, Jr.Got a link? :p

---

### Post by William Shotts on 2010-03-11
> **Iowan said:**
> Got a link? :p

I have one.  I wrote it.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by jmsgz on 2010-03-11
> **William Shotts said:**
> I have one.  I wrote it.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Yes Mr Shotts, i have read many books since arriving her in the linux 
community and still do. YOUR BOOK in my opinion, for me, is the most useful that i have read. (up to date, great examples and great subject flow). I can tell, "you" really enjoy "your" work. I have it in my home directory for continuous reference. I can't tell you "how much" i appreciate it. Folks, this is an example of open source community documentation. This book is a fine example of an individual and individuals who define excellence in giving back to the community.

jmsgz :-)

---

