---
title: "ubuntu lamp server or ubuntu with apache?"
date: 2012-01-05
forum: Server Platforms
---

### Post by nickos on 2012-01-05
So for a web server should i use ubuntu LAMP server with command line or a regular ubuntu release with installed packages and stuff?im already on ubuntu server and face lots of problems with rooting and ip's in my lan so what do you think is best?

---

### Post by Lars Noodén on 2012-01-05
It depends, if you are going to be sitting physically at the computer and you feel you need the training wheels of a GUI, then just add the web server to a regular Ubuntu release.  

It may take a little more to get started with, but learning your way around the shell is *very* well worth the effort.  It's both powerful and flexible.  You can always come here for help with both simple questions and harder ones.

Which web server are you thinking of running Apache (the #1 server) or nginx (the #2 server)?  Are you planning on getting started with scripting with Perl/Python/PHP right way or mastering static pages first?

---

### Post by nickos on 2012-01-05
> **Lars Noodén said:**
> It depends, if you are going to be sitting physically at the computer and you feel you need the training wheels of a GUI, then just add the web server to a regular Ubuntu release.  

It may take a little more to get started with, but learning your way around the shell is *very* well worth the effort.  It's both powerful and flexible.  You can always come here for help with both simple questions and harder ones.

Which web server are you thinking of running Apache (the #1 server) or nginx (the #2 server)?  Are you planning on getting started with scripting with Perl/Python/PHP right way or mastering static pages first?

of course,the reason i installed ubuntu server was because i wanted to learn more about how the server works rather than the ready to server GUI,but im facing many problems with rooting and thats why i am thinking a gui would be better (id be happy if someone could help to at least help me get connected to the server!)

i am running apache with mysql,phh.I have a slight knowledge of php i dont want to focus on learning scripting languages(except javascript which i know pretty well) but because i wanted to host some websites at home instead of paying for a hoster (mainly to get some experiece with servers)

---

### Post by Lars Noodén on 2012-01-05
Well, the best way to connect to the server is via SSH.  If you want to stick with a graphical editor, like Geany or Kate, then have it forward X, where *xx.yy.zz.aa* is the IP number of your server:

```

ssh -X *xx.yy.zz.aa*
sudo kate /etc/apache2/sites-enabled/000-default

```

That way you can still run graphical programs over on your server, but have the interface locally on your desktop.  

You'll also want to know how to check your Apache configuration for correct syntax:
```

/usr/sbin/apache2ctl configtest

```

One last thing is to know how to monitor the logs.  Log in another window and use [tail](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tail.1posix.html) to track the additions to the log file:

```

tail -f /var/log/apache2/access.log

```

The same can be done for the error log, [font=Courier New]error.log[/font]

What are the first three tasks you wish to accomplish with Apache?

---

### Post by nickos on 2012-01-05
> **Lars Noodén said:**
> Well, the best way to connect to the server is via SSH.  If you want to stick with a graphical editor, like Geany or Kate, then have it forward X, where *xx.yy.zz.aa* is the IP number of your server:

```

ssh -X *xx.yy.zz.aa*
sudo kate /etc/apache2/sites-enabled/000-default

```That way you can still run graphical programs over on your server, but have the interface locally on your desktop.  

You'll also want to know how to check your Apache configuration for correct syntax:
```

/usr/sbin/apache2ctl configtest

```One last thing is to know how to monitor the logs.  Log in another window and use [tail]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/tail.1posix.html") to track the additions to the log file:

```

tail -f /var/log/apache2/access.log

```The same can be done for the error log, [FONT=Courier New]error.log[/FONT]

What are the first three tasks you wish to accomplish with Apache?



many many thanks for your help.i will keep these in note. (: 
is there any good book to buy or should i rely on ubuntu's server online documentation?
I will post another thread with the ip problem i have when connecting to the server(i dont know the ip it returns is the one i did set to it but when i try to connect nothing happens)

---

### Post by Lars Noodén on 2012-01-05
I don't know of any good books but that is because there are no good bookstores anywhere near me and the best one in my home town went bankrupt.  One perpetual problem with printed material on computing is that it is nearly always at least partially out of date by the time it hits the printing press. 

The online guides, if they are recent, are good, but watch out for the ones recommending [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  

Apache has some good guides for specifics, like Server-Side Includes ("PHP without PHP") or name-based virtual hosts.  If you work with Server-Side Includes to make your standardized headers, footers or menus, be sure to use the "IncludesNOEXEC" option for safety.  
[http://httpd.apache.org/docs/2.3/](http://httpd.apache.org/docs/2.3/)

There was a lot of good material for Apache 1.3 which hasn't been updated to Apache 2.  It's still relevant but the configuration has been made more modular, so you can't follow the steps blindly.  By default Apache2 sets you up with one virtual host and the configuration file is [font=Courier New]000-default[/font].  You can add others or change it around if you wish.

---

