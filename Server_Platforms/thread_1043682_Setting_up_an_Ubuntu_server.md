---
title: "Setting up an Ubuntu server"
date: 2009-01-18
forum: Server Platforms
---

### Post by Veebee6651 on 2009-01-18
I have been using K/ Ubuntu for a while now, (but still somewhat of a noob).

I have Ubuntu 8.04 x64 Server edition installed on one f my (5) machines, and wish to learn how to set it up as a server here at home.
I would like to eventually move OUR website onto it (if possible) and also build/ host a few more (small) websites.

I need a guide , in plain english, for "step by step" on how to do this , if possible.
I have scoured all the Linux/Ubuntu forums/ helpsites etc and they are all aimed at people who obviously are totally fluent in linux/ command line etc

I simply wish to host sites and use 'web-builder" software/ programs to make them (i have a number of free web build programs).

Any help would be greatly appreciated... as I am doing this to keep myself amused during a protracted custody/ property fight and an impending medical retirement from the best job in Australia.

Thanks
Veebee6651

---

### Post by baruch60610 on 2009-01-18
Hi.  I think that using Ubuntu as a server is a good idea, but it's somewhat different from using a graphical version.  I've got 8.04 LTS (Long Term Support) on one computer.  It has no GUI - no graphical user interface.  It requires me to use the command line.

Depending on your needs, you will have to learn a few things.  First and foremost, you'll need to become comfortable with using the command line.  This can be trying, but it's really just a matter of practice.  I use the 'bash' shell.  The 'shell' is the program that handles the command line entries.  'bash' is one of the common ones, and I recommend it.

Try to Google for 'bash howto' or 'bash reference', or even 'bash tutorial'.  That should give you some ideas about how to use the command line, and also how to write shell scripts.

If you're going to use your server for a Website, you'll likely need to run the Apache Web Server.  Others exist, but I like Apache because it is robust and secure.  it's not all that difficult to learn, but it would require some effort.  Apache is what would serve your Web pages.  Apache offers complete documentation on the Apache Website.

If you've got certain types of script-based features (such as blogging software, a wiki, etc.), you'll probably need to use PHP.  Installing that is easy (I'll explain in a minute).  Using it?  Well, it's yet another programming language.  It takes time and effort, though you can use pre-packaged products such as Wordpress that don't require you to know much.  Use Google to get more information about PHP.

Then there is MySQL, a database that many of those blogging softwares use.  Again - easy to install, but requires some knowledge of SQL.  As always, Google is your friend.

The systems I mentioned, Linux, Apache, MySQL, and PHP, form what is known as the LAMP platform.  This is a popular and effective way of serving up dynamic Websites, but it's not something you just start right off the bat.

To install any of these programs (except for Linux, of course), you can use the command line instruction 'apt-get'.  For example, to install MySQL, you'd first check for its existence and proper name:

```
sudo apt-cache search mysql
```Since this produces quite a bit of information, you might want to revise this somewhat to:

```
sudo apt-cache search mysql | less
```This would allow you to scroll up and down the text to find the entries about mysql.  They include:

```
mysql-admin - GUI tool for intuitive MySQL administration
mysql-gui-tools-common - Architecture independent files for MySQL GUI Tools
mysql-navigator - GUI client program for MySQL database server
mysql-proxy - proxy for high availability, load balancing and query modification
mysql-query-browser - Official GUI tool to query MySQL database
mysqltcl - Interface to the MySQL database for the Tcl language
mytop - top like query monitor for MySQL
mysql-client - MySQL database client (meta package depending on the latest version)
mysql-client-5.0 - MySQL database client binaries
mysql-common - MySQL database common files
mysql-server - MySQL database server (meta package depending on the latest version)
mysql-server-5.0 - MySQL database server binaries

```The ones of interest are mysql-client and mysql-server.  So type:

```
sudo apt-get install mysql-client mysql-server
```That will install the most recent versions of the server and client.  You can install PHP and Apache the same way - but you really need to know what to do with all of this, and that will require learning about each of them.

This may seem overwhelming, and if you try to do it all at once, it *will* be overwhelming.  But if you approach it in the time-honored way of "divide and conquer", it is possible.  

Tackle one thing at a time.  Learn it reasonably well, then go on to another thing.  There are all sorts of online help texts available, as well as forums and wikis.

I hope you find useful.

---

### Post by DylanW on 2009-01-18
to add to what baruch said, google is your friend

---

### Post by aheckler on 2009-01-18
As a side note, running ```
tasksel install lamp-server
``` will install Apache, MySQL, and PHP all at once.

However, I agree with baruch60610: some learning about each is needed before opening up your box to the Internet.

---

### Post by blueridgedog on 2009-01-18
I would encourage you to break your mission down into smaller parts that others can assist with.  It has been a while since I installed Ubuntu server, did you get a desktop environment?

From there, I would work on learning each element that you need in turn.  It sounds from your post that the first you want to learn will be how to use/setup/publish to the Apache web server.  There are many documents on the web that will help, I suggest you search for a "guide" for apache and you will find many such as:

[http://www.bjnet.edu.cn/tech/book/apache/index.htm](http://www.bjnet.edu.cn/tech/book/apache/index.htm)

Also from your post, I sense that you may want some good solid advice on basic system administration.  For that, you may want to find a Linux Users Group near you:

[http://www.linux.org.au/](http://www.linux.org.au/)

If you get your focus on some of the parts, then this group will probably be a great fit.  For example, in place of the generic "I am trying to setup a server" you can say "I am trying to setup Apache and am having a problem with X".  

I also recommend the Oreilly books:

[http://oreilly.com/](http://oreilly.com/)

In particular, you would be well served with there Linux in a nutshell, the Apache books and their system administration books.  Head down to the local book store and browse.

---

### Post by jimmy the saint on 2009-01-18
Just pick the features you need though.
[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

---

### Post by cmnorton on 2009-01-18
First,here is a link:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Ubuntu server is more stripped down than Ubuntu desktop. I do not know if this link causes build-essential to be installed, but Ubuntu server would also need that.

Basically, Ubuntu server lacks a window manager like Gnome and KDE and has PHP, Apache, and MySQL installed. There is more too it than that, but that's the basic jist of it.

---

### Post by blueridgedog on 2009-01-18
> **jimmy the saint said:**
> Just pick the features you need though.
[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

Excellent link...very comprehensive

---

### Post by Bachstelze on 2009-01-18
Moved to Server Platforms.

---

### Post by Veebee6651 on 2009-01-18
> **baruch60610 said:**
> Hi.  I think that using Ubuntu as a server is a good idea, but it's somewhat different from using a graphical version.  I've got 8.04 LTS (Long Term Support) on one computer.  It has no GUI - no graphical user interface.  It requires me to use the command line.

 


I do have the gnome desktop running with the server  edition.
Thanks for all these quick replies guys (and gals ??) I shall go through themall...
Fortuneately, it isn't a rush project , so I can take my time with it...
Some of the links look very helpful.... any more which will help are greatly appreciated
As was advised, I think breaking the project down into stage will be the best way
, but I shall advise of my "progress" here as it happens.
Thx again !

---

