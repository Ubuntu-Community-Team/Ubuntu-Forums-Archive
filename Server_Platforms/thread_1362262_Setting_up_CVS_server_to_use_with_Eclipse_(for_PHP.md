---
title: "Setting up CVS server to use with Eclipse (for PHP)"
date: 2009-12-22
forum: Server Platforms
---

### Post by sdlyr8 on 2009-12-22
I've got my web server running 9.04 and I'm trying to set up a CVS server on it. I use Eclipse for all of my PHP development and I'd like to start versioning my projects. I attempted to set up CVS from this [https://help.ubuntu.com/7.04/server/C/cvs-server.html](https://help.ubuntu.com/7.04/server/C/cvs-server.html) but when I try to connect to the CVS server from Eclipse, my login doesn't work (only trying the root login). I have no experience with CVS so I don't know if I missed anything in setting it up.

After I installed it, I did check to make sure the service was running but that's it. Do I need to create the project on there before I can do anything from Eclipse or what do I need to do?

Thanks!

---

### Post by hessiess on 2009-12-23
You would be better off using Subversion (svn) or one of the distributed VCS's. I am using SVN to version control my web roots and it works well here, with a simple `svn commit' being all that is required to put the working copy live on the web server and it can be checked out and edited from absolutely anywhere, as long as you have an SVN client.

---

