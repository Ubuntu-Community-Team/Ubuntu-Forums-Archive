---
title: "Apache Will Not Start"
date: 2008-10-23
forum: Server Platforms
---

### Post by GrandBob on 2008-10-23
Using Hardy on System76 laptop...
No domain in play... using platform for website development.
Have installed Apache2,PHP5,Subversion,Firebird and seen them run...

At some point I am unable to start Apache, (report shown here)

======================================================
sites-available$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.0.104 for ServerName
( 98 )Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs.
======================================================

What's the meaning of "( 98 )Address... "?

Ouch! Everything was going So Good!

---

### Post by cariboo on 2008-10-24
It looks like apache2 is already running. A quick way to determine if it is, type the following in a terminal:

```
ps ax | grep apache2
```

the reult should look like this if apache2 is running:

```
ps ax | grep apache2
19836 ?        Ss     0:00 /usr/sbin/apache2 -k start
19838 ?        S      0:01 /usr/sbin/apache2 -k start
19841 ?        S      0:00 /usr/sbin/apache2 -k start
19842 ?        S      0:00 /usr/sbin/apache2 -k start
19843 ?        S      0:00 /usr/sbin/apache2 -k start
19845 ?        S      0:01 /usr/sbin/apache2 -k start
19855 ?        S      0:00 /usr/sbin/apache2 -k start
26924 pts/0    R+     0:00 grep apache2
```

If you need to restart apache2, in a terminal type:

```
sudo /etc/init.d/apache2 restart
```

Jim

---

### Post by GrandBob on 2008-10-24
Had done that.  Did it again.  It's not running.

---

### Post by volkswagner on 2008-10-24
"unable to open logs".

You may want to make sure all sites-enabled have valid directory's.  Apache2 wont start if in a site config, points to an invalid file.  It could also be a permission issue with the log files (var/log/apache2 directory).

Also is another service set to use port 80?  You could temporarily change the listening port to :8080 or any other unused port to see if it will start.

Not sure of the command to check all services running and ports.

---

### Post by MJN on 2008-10-24
Something is already listening on port 80. Find out what with **sudo lsof -i :80**
 
The domain 'error' is just a warning that you haven't specified what the web server is called (using the ServerName directive) but it needs to know its own identity for a variety of reasons (name-based virtual hosting, loop detection etc) and hence it is deciding this for you. It'll work as it stands but you really ought to explicitly set the name.
 
The logs issue is just a consequence of the Apache parent process not starting and should go away whe you've sorted that out.
 
Mathew

---

### Post by GrandBob on 2008-10-24
To VolksWagner:  Thanks for you reply.  I verified correctness of directory names.  Yes, Apache2 complains if it detects invalid directory references.

---

### Post by GrandBob on 2008-10-24
To MJN: Thank you for your assistance.

Since I initiated this thread, Apache2 starts as it should.  But this come-and-go pattern has been with me for several days now.  Now I am armed with **lsof**, which, by the way, shows Apache connected to :80.

As to your other comments re setting up a proper domain, fear not.  I am now preparing my laptop to become a website development platform.  **localhost** is sufficient.  When I sort all of this business, I'll implement it for production on a soon-to-arrive server box which will be the home of a proper domain.

All of my Apache components work as expected.  These include Apache2, PHP5 and Subversion using file://, svn+ssl://, http:// and https:// protocols.

I hope the problem appears again so I can NAIL IT!

Thanks so much,
Ta-ta

---

### Post by GrandBob on 2008-10-25
AHAH! What do you know?  I have found the problem.

It seems that when you install Apache2, it is marked in **Service**s for automatic startup.  Upon bootup, Apache2/OpenSSl is asking for a pass phrase, but nobody was answering.  So Apache silently waited while holding fast to port :80, hence the ( 98 ) error.

Solution: Remove Apache2 from Services automatic startup.

Thanks again everyone for the help.

---

### Post by MJN on 2008-10-25
> **GrandBob said:**
> Solution: Remove Apache2 from Services automatic startupOr remove the passphrase (encryption) from the private key and make it root-only readable.

This is preferable for unattended machines as if it has to reboot (say, following a power cut) the website will not otherwise be able to restart. Furthermore, some log rotations may also require an Apache restart.

Mathew

---

### Post by GrandBob on 2008-10-25
Yes, I had thought of those things.

Thanks, again.

P.S. I'm not taking your meaning in your footnote, i.e., not to use PM's...

Did I do something untoward?

---

### Post by MJN on 2008-10-26
Don't worry - my signature block is not aimed directly at you... it appears on all my posts!

It is just a request for people not to send me (or others) Private Messages when wanting help as whilst it may help that particular person it doesn't share the knowledge within the community. Furthermore, any advice is then given without peer review which may mean it could be either wrong, or sub-optimal for the person's needs.

Mathew

---

