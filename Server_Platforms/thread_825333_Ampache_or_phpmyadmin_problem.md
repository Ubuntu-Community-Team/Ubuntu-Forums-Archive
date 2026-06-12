---
title: "Ampache or phpmyadmin problem"
date: 2008-06-10
forum: Server Platforms
---

### Post by AngryMallard on 2008-06-10
Hey guys, not even sure if this is the appropriate forum for this, mainly because I have no idea what the problem is, but here goes. 

I followed the "Ampache The Easy Way" guide on Ubuntu Forums but right after I got done following the instructions for setting up phpmyadmin I went to [http://localhost/ampache](http://localhost/ampache) and I get the following:

```
Warning: require_once(lib/class/database_object.class.php) [function.require-once]: failed to open stream: No such file or directory in /usr/share/ampache/www/install.php on line 28

Fatal error: require_once() [function.require]: Failed opening required 'lib/class/database_object.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/ampache/www/install.php on line 28
```

Anyone have any clue? I couldn't turn anything up anywhere.

---

### Post by samosamo on 2008-06-10
this is not a phpmyadmin problem.  phpmyadmin is it's own separate installation, it has nothing to do with ampache or other scripts.

hmm, it looks like you are missing pear but i don't think that is required by ampache.  did you read this?  [https://help.ubuntu.com/community/ampache](https://help.ubuntu.com/community/ampache)

---

### Post by AngryMallard on 2008-06-16
I followed those instructions to the letter and still come up with the same error message. [http://localhost](http://localhost) displays the "It Works!" but [http://localhost/ampache](http://localhost/ampache) displays that error message.

---

### Post by AngryMallard on 2008-06-20
Anyone?

---

