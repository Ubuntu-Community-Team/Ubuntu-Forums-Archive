---
title: "Installing Mysql5?"
date: 2005-11-06
forum: Server Platforms
---

### Post by iluminate on 2005-11-06
Hi people,

Can someone guide me to a link or some other usefull information how to
install Mysql5 Server?
Have tried to search this forum but without any success.
Has someone yet installed it successfully and is it running smooth?

Cheers !

---

### Post by iluminate on 2005-11-06
18 views and not a single reply?
Thanks!

---

### Post by dbee on 2005-11-07
I've tried to install mysql5 ... it's fairly easy as it comes precompiled.

All you have to do is unpack it (I went for the binary install version though, so of course I lost more than a few hours)... 

but anyway ... the best place to start I guess would be mysql.com ...

[http://dev.mysql.com/doc/refman/5.0/en/linux-rpm.html](http://dev.mysql.com/doc/refman/5.0/en/linux-rpm.html)

kinda makes sense when you think about it :) 

good luck

---

### Post by iluminate on 2005-11-07
Think this link is more relavant -http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html
How do I set the PATH envoirment to point to /usr/local/mysql/bin/ ?

Because when I try to scripts/mysql_install_db --user=mysql I recieve an error "Could not find help file 'fill_help_tables.sql' in ./support-files or inside /usr. "
So my guess is that I have to add /usr/local/mysql/bin to my PATH envoirment? Correct?

---

### Post by dbee on 2005-11-09
Either try 
```

export PATH=$PATH:/new/path/here

```
or alternatively if you like to not have to do that everytime you restart your computer, then just put it in your .bashrc file which you'll find in your 
```

/home/user

```
folder, where the value of user is the value you return from doing a 
```

whoami

```
... just restart and then your path should be able to find the executable...

---

### Post by fluffy on 2005-11-09
add:
 deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
to your sources.list and do:
 apt-get install mysql-server-5.0

;)

---

### Post by iluminate on 2005-11-11
[QUOTE=fluffy]add:
 deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
to your sources.list and do:
 apt-get install mysql-server-5.0

;)[/QUOTE]
Great :) and thank you very much.
Tried to find the deb packages earlier but could not find.
You're a star and dbee to! :)

I had my doubts about Ubuntu before but now I'm hooked like a fish 	;-)

---

### Post by dudus on 2005-11-22
I found that the best way to install mysql5, php5 and apache2 (LAMP) would be compilling them...

---

### Post by dudus on 2005-11-22
I wrote a how to compile mysql5 [here]("http://www.ubuntuforums.org/showthread.php?t=93725&page=1&pp=10").

---

