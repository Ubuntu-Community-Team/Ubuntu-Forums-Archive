---
title: "Ubuntu desktop 10.04 as a server, antivirus antimail antispam ?"
date: 2011-10-15
forum: Server Platforms
---

### Post by jaho22 on 2011-10-15
I have Ubuntu 10.04 desktop edition on my server.

I have no previous experience with servers, this is a hobby server, no company.

I need to know a bit of how to set antivirus antimail antispam settings right.

What programs to use and what steps i need to setups for all tree.

:D

---

### Post by mörgæs on 2011-10-15
Hi, welcome to the fora.

Thread moved to the server forum.

Before asking general questions, it is a good idea to read as much background stuff as possible, like
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

When you get to the detailed questions, people are ready to help you.

---

### Post by jaho22 on 2011-10-15
I have Ubuntu 10.04 desktop edition on my server.

I am totally newbie with servers, im wondering how to set everything right.

I have LAMP allready set, but now i need those anti vir/spam/mail settings and programs.

---

### Post by mörgæs on 2011-10-15
Don't create multiple posts.

---

### Post by CharlesA on 2011-10-15
You can use both the server and desktop versions as a "server"

Check out the documentation [here]("https://help.ubuntu.com/").

---

### Post by jaho22 on 2011-10-15
What programs i need to set to my server to have a ok setup.

I am planning to serve from apache images, java .jar files, html and php files.

I have a phpbb forum.

I also send activitation email messages and some info email messages from my server.

thats about all i need.

i am a noob with servers

---

### Post by CharlesA on 2011-10-15
You'd probably just start out with a LAMP server (Linux Apache, MySQL, PHP)

You'd need a mail server of some sort - postfix is the default in Ubuntu, I believe.

Not sure what you'd use to serve jar files though.

---

### Post by jaho22 on 2011-10-15
How do i check that the emails i send are without viruses and other extra stuff ?

---

I now have apache installed and it is serving ok, do i need something to check that the files that apache transfers are all ok ?

---

### Post by CharlesA on 2011-10-15
They have mail scanners, but I'm not sure what they are called or how to set them up.

EDIT: I don't think you need to check anything to verify that apache is transfering ok. I haven't done that, but I could be doing it wrong. :p

---

### Post by Gyokuro on 2011-10-15
For Antivirus you can use clamav ([https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)) or f-prot which I recommend ([http://www.f-prot.com/products/corporate_users/unix/linux/mailserver.html](http://www.f-prot.com/products/corporate_users/unix/linux/mailserver.html))

---

### Post by jaho22 on 2011-10-16
How i should check the emails i send, i have a very low budget i go to avg or f-prot only if needed, so im with clamav at start.

Is there anyway i can check my php send emails with clamav-daemon ?

---

### Post by Gyokuro on 2011-10-16
Hi,

this site ([http://php-clamav.sourceforge.net/](http://php-clamav.sourceforge.net/)) should answer your question.

---

