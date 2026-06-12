---
title: "Wordpress and mail"
date: 2005-11-14
forum: Server Platforms
---

### Post by Mortious on 2005-11-14
I have set up an Ubuntu server and have wordpress installed (PHP and mySQL installed also) and everything seems to be functioning normally.

However when a new user signs up, they are suppose to recieve an email with their password, but this hasn't been happening.

Is there something else I need to install on the server that will allow sending of mail (I don't need to recieve email just send)?

Thanks

Chris

---

### Post by lafnlab on 2005-11-15
You might want to check the Wordpress forums on this one. IIRC, Wordpress requires some sort of mail setup, like Sendmail, although it might be something else. I might be wrong. I use Wordpress for my blog ([www.gottahavacuppamocha.com](www.gottahavacuppamocha.com) :p ), but it's been awhile since I set it up, so I don't remember the exact requirements. :???: 

I would go to the Wordpress forums to find out what is needed, then maybe come back here if you need any help setting up whatever is called for, though it should be as easy as using apt-get and maybe reading some man pages. Sorry I couldn't be of more help.

---

### Post by grendelkhan on 2005-11-15
I want to say that there was an option I plugged in during the install that specified either postfix or sendmail, but it's been awhile for me too.

---

### Post by cedjo on 2005-11-15
you should install & configure postfix or sendmail (but postfix is easier!, in my humble opinion)

---

### Post by Mortious on 2005-11-15
Thanks guys Ill try that out and report back what I find.

---

### Post by senectus on 2005-11-16
make sure you do.. cause I'm doing the exact same thing right now :-)

***Edit : Whoops.. I just noticed that when you install wordpress from the repository it pulls in postfix as a dependency :-)

---

