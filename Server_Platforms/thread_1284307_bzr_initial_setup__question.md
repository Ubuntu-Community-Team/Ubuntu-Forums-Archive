---
title: "bzr initial setup / question"
date: 2009-10-06
forum: Server Platforms
---

### Post by xkaliburx on 2009-10-06
We have 8 webservers in production and the old servers were using subversion (centralized).   All these servers have been re-staged, and running ubuntu-server 8.10 and working great.

I wish to now setup some kind of version control to make life easier (right now I have a few apache vhost changes) and rather than changing, copying files, or changing each, I would like to do what was done in the past.  

Simply change one file, commit and have it update the other webservers.  From my reading so far, the commit is only local to that machine.  The questions, bzr will be setup on each of the servers.

Do I have to setup the /etc/apache2/sites-available on each machine using the bzr init (this one I think is yes!)

Next, if I or someone wants to update, does it matter which of the servers we goto to make that change?

Lastly, once that change is saved, and commited, it looks like it's still local, how do you initiate the new one to replicate to the other servers?

Thanks

---

