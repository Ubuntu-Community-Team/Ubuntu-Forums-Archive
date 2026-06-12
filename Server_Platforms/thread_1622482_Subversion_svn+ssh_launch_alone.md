---
title: "Subversion svn+ssh launch alone"
date: 2010-11-15
forum: Server Platforms
---

### Post by AlexandreSantos on 2010-11-15
Hi,
 
I installed subversion and ssh, but i don't need launch "svnserver -t" for subversion server work, I just need make checkout with correct url and login...
 
and svnserver launch alone the "svnserver -t", "svnserver -d" process...
 
I saw that on "htop"
 
I use Ubuntu Server Lucid (10.4) LTS.
 
anyone seen this?
 
Thanks...

---

### Post by paulsarmiento on 2010-11-15
Hi Alexandre,

I'm trying to pick up what you posted. but what i see is you don't need to launch the svnserver in order to checkout. you just need the 'svn' binaries.

your command will look like:
```

svn co svn+ssh://your.remote-server.com/home/svn/test 
```


the svn+ssh parameter will handle your request.

Paul

---

### Post by AlexandreSantos on 2010-11-15
[COLOR=#000000]this is precisely the problem, because even without running it by ssh svnserver it opens the repository?[/COLOR]
[COLOR=#000000]
Thanks!
[/COLOR]

---

### Post by paulsarmiento on 2010-11-17
Alex,

Maybe because you installed the svn server. You might need to uninstall that so that it will not launch at startup.

Paul

---

