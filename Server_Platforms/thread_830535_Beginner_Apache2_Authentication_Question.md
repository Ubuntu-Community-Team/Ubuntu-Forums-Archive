---
title: "Beginner Apache2 Authentication Question"
date: 2008-06-15
forum: Server Platforms
---

### Post by alexebird on 2008-06-15
I'm trying to have authentication set up for my apache2 server so that everything under a certain directory requires a username/password and that the user is in a certain group.

I have the AuthGroupFile directive set and the Require group mygroup directive as well, but I am confused as to what is going on with my configuration.  The directory that I want to be authenticated and all the files under it are owned by the same user (who is in sudoers, I dont know if that matters) and the group that is supposed to be required for authentication.  For each file in the directory, the permissions are rwxrwx---, so I am expecting the files to be able to be viewed in the browser.

However, I get a permission denied message when I try to view them, which goes away when the permissions are changed to rwxrwxr--.

Thanks in advance and let me know if you need additional information on anything!

---

### Post by Dr Small on 2008-06-15
Check these links out. I think they may be what you are looking for:
[http://httpd.apache.org/docs/1.3/programs/htpasswd.html](http://httpd.apache.org/docs/1.3/programs/htpasswd.html)
[http://en.wikipedia.org/wiki/.htpasswd](http://en.wikipedia.org/wiki/.htpasswd)
[http://www.colostate.edu/~ric/htpass.html](http://www.colostate.edu/~ric/htpass.html)

Dr Small

---

### Post by alexebird on 2008-06-15
Thanks so much!  It turned out, as I found in that last link, that the files needed to be owned by apache2's www-data group instead of the group that I wanted to require for authentication.

---

