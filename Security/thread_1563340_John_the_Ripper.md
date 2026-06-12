---
title: "John the Ripper"
date: 2010-08-29
forum: Security
---

### Post by Jonny87 on 2010-08-29
I'm trying to get John the Ripper working on my desktop to test my password strengths. But I keep getting > No password hashes loaded Does any one know what I need to do to get it going? I've tried looking it up but havn't found anything that seem to have helped.

---

### Post by cariboo on 2010-08-29
See this [post]("http://ubuntuforums.org/showpost.php?p=9370013&postcount=2"), it will explain why john doesn't work.

---

### Post by Jonny87 on 2010-08-29
Thanks. I have checked the article cited in that post and I think its a bit beyond me. I still havn't had a chance to learn about compiling things from source. I guess I've got a bit of study to do.

---

### Post by cariboo on 2010-08-29
I know we like to play with programs in the repositories, but an online password strength checker would tell you just as much as john.

---

### Post by Jonny87 on 2010-08-29
> **cariboo907 said:**
> I know we like to play with programs in the repositories, but an online password strength checker would tell you just as much as john.

Do you know of any that are trust worthy? I'd feel kind of iffy entering a password on something like that online.

---

### Post by cariboo on 2010-08-29
There is a discussion in the [Cafe]("http://ubuntuforums.org/showthread.php?t=1563389"), on this very subject.

---

### Post by Jonny87 on 2010-08-29
Thanks.

---

### Post by nixor01 on 2011-05-08
In case anyone is still wondering. I use 'sudo apt-get install john' and it came with version 1.7.3
which doesn't support certain functionalities, resulting in 'No password hashes loaded'

However if you download the latest john source code now and compile it, you get the ver 1.7.7, then it works like a charm.

---

