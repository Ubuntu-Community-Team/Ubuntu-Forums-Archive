---
title: "simple scp to /var/www without extra steps"
date: 2009-05-03
forum: Server Platforms
---

### Post by NewbuntuUser777 on 2009-05-03
If I use scp to transfer files to an ubuntu lamp server it automotically puts the files in the home directory.  

Pages are served from /var/www in apache, so I want to scp the files there.  When I try I get 'permission denied'.

I saw in a thread in another forum that one must scp the files to the home directory, then login with SSH and manually copy the files from home to /var/www.

This seems extreme to me.  I want to be able to as simply as possible send files from my desktop to the server so I can open them in a browser.  Simple I think.

I know there are lots of ways to do this, but are the best ways?

---

### Post by Stupendoussteve on 2009-05-03
You get permission denied because your user doesn't have access to that directory. You could add the user to the group that owns /var/www and make sure that directory is read/write/execute for the group, then you should be able to put files in there.

---

### Post by John Cheng on 2009-05-04
What is the exact command you used? Like the previous poster said, this may be a problem with your user not having access to /var/www.

---

### Post by defaria on 2009-05-04
If you don't have write access to /var/www then you can't do it. If you have access to root then the following should work:

```
$ scp mynewwebpage.html root@<server>:/var/www
```

---

