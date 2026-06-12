---
title: "Ubuntu use of sudo"
date: 2010-04-09
forum: Security
---

### Post by prezbedard on 2010-04-09
I just read an article saying some unflattering things about Ubuntu's use of sudo. My question is this true?

[http://blogs.techrepublic.com.com/opensource/?p=1415&tag=nl.e011](http://blogs.techrepublic.com.com/opensource/?p=1415&tag=nl.e011)

---

### Post by -humanaut- on 2010-04-09
Sudo vs Su debate will never end it's like debating politics just goes in circles I personally think having a separate root account with an SH shell is the way to go.

---

### Post by snowpine on 2010-04-09
Did you read the article you linked to??

> sudo is just a tool, and it is very good at what it does

---

### Post by cariboo on 2010-04-09
+1 if you really read the article beyond the first paragraph, the article has nothing but good to say about sudo.

---

### Post by prezbedard on 2010-04-11
I read the article in its entirety. I am not a Linux guru and was looking for opinions. I would think it would be safer to not log in with the root account interactively if the same work could be done by using sudo. Is it good that Ubuntu by default does not allow root to log in locally? I do know you can change that if you desire.

---

### Post by adam814 on 2010-04-11
For me the whole point of FOSS is choice.  It's not impossible to use su and activate a root account in Ubuntu, just that the "official" community forum won't host tutorials for doing it.  I personally agree with the rationale that if you need/want to and know how to you should, but it's a security risk for new users migrating from Windows that are accustomed to logging into the desktop as "Administrator".

Personally I like a lot of the features of sudo.  I can specify what commands which groups/users can run as root and when they do so it gets logged.

---

### Post by bodhi.zazen on 2010-04-11
> **prezbedard said:**
> I read the article in its entirety. I am not a Linux guru and was looking for opinions. I would think it would be safer to not log in with the root account interactively if the same work could be done by using sudo. Is it good that Ubuntu by default does not allow root to log in locally? I do know you can change that if you desire.

The answer to yoru question is an opinion , so you will need to do your research and decide for yourself.

The debate is almost pointless as there needs to be some method of accessing the root account and almost all of what people say in the su vs sudo debate applies equally to both (for the most part they have the same vulnerabilities).

IMO the greatest two advantages of sudo are :

1. finer grained control of access to root. su is all or none. You may configure sudo to allow some but not all commands to be run as root.

2. sudo has superior logging.

to put it in simple terms, sudo is more flexible

[http://www.sudo.ws/sudo/intro.html](http://www.sudo.ws/sudo/intro.html)

There has been no convincing argument that su is more or less secure then sudo .

---

