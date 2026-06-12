---
title: "Some kind of RCS/Development Hub server"
date: 2012-04-12
forum: Server Platforms
---

### Post by lykwydchykyn on 2012-04-12
Here's the problem:  I have amassed a fair number of development projects at work, and the code is all over.  I want to centralize it in one server.  There is also another developer here who works mostly in SQL and expressed interest in having some kind of repository we can both access.  I use git for version control, though I have a few legacy projects in subversion.

My thought was to set up something like github that would:

 - Allow easy viewing and distribution of the code in our organization
 - Allow easy set-up of new repositories (especially for people not familiar with git)
 - Allow easy import/rebase of existing repositories

I tried redmine so far, but it isn't quite what I want.  It seems to be more of a bug-tracker and project portal, and doesn't seem to have tools to set up new git repos by default.

I also looked at indefero and gitlab.  Gitlab looks closer to what I want, but the setup is a real chore at this point, and I'm wondering if it's all that stable.

There's also a gitosis plugin for redmine, but it looks abandoned and is stamped with all sorts of "it might not work for you" caveats.

Is there a solution staring me in the face that I'm missing, or what would you recommend?

---

### Post by roelforg on 2012-04-12
Make a simple cgi-app or php-app or shell script (like i did, i ssh in to my server and run "./git.sh add-repo <repo_name_here>", combining that with pubkey auth and a wrapper that does nothing more then calling the real one over ssh and passing its args and it's a dead-simple process to use it).
Make it simple to use and you're done.

---

### Post by Jonathan L on 2012-04-12
Hi lykwydchykyn

> Make a simple cgi-app or php-app or shell script... 

I thought roelforgs suggestion was excellent.  We've had very good results from this kind of thing, for small numbers of developers, with git over ssh to a server in the cloud, also running gitweb for browsing purposes.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by lykwydchykyn on 2012-04-12
I was kind of hoping not to have to write something...

---

### Post by lykwydchykyn on 2012-04-13
Bump.... any other suggestions?

---

