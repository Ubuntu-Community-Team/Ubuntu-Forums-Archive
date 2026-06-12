---
title: "svn+ssh and eclipse not working (username and password)"
date: 2013-08-18
forum: Server Platforms
---

### Post by kr6511292 on 2013-08-18
I just setup an svn server on 13.04 and it works fine through apache, but I really need it to work with eclipse from my windows machine.  After downloading the svn plugin for eclipse I tried svn+ssh://ip/svn/repo then the username and password that I defined while setting up the svn server, it said my login information was incorrect.  I then tried with my Ubuntu username/password since it's working over ssh and I still get the same results.  Is there some setting I might be missing in dav_svn.conf or maybe somewhere else?

---

### Post by kr6511292 on 2013-08-18
Edit: This was solved, I accessed the repo from the url listed above and used that in eclipse.  The path I needed in eclipse was svn+ssh://ip/var/svn/repo, where the actual location of my svn repo was.

---

