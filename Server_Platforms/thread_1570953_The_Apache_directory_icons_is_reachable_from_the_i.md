---
title: "The Apache directory /icons/ is reachable from the internet, how do I turn that off"
date: 2010-09-08
forum: Server Platforms
---

### Post by MechaMechanism on 2010-09-08
EDIT: Solved.  I simply renamed my /usr/share/apache2/icons/ directory to a gibberish name, example, /usr/share/apache2/dh5u456uj.


I saw in my logs that someone had accessed the Apache /icons/ directory.  No other file system directory is reachable as the /www/ is the root directory for the web server.  How do I prevent users from accessing any directory except for /www/ and sub directory in /www/.


The indexes I figured out.  So ignore this.  Used a2dismod to remove index.
Also if I want to turn off directory listing I use -Indexes thats dash Indexes right?  No dash allows directory listing, am I correct.

---

