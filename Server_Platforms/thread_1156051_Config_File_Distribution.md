---
title: "Config File Distribution"
date: 2009-05-11
forum: Server Platforms
---

### Post by locovaca on 2009-05-11
I run a small home network that is 100% Ubuntu based.  When I add a new computer or reformat an existing one I have to go in any make all the same configuration file changes per computer, such as:

1. Copying down my root certificate
2. Installing LDAP and Cached Credentials libraries
3. Configuring said libraries
4. Updating cron jobs
5. Etc.

I'd like to automate this process.  My thought is to set up a package repository which a "Home Network" package which contains the necessary files and depends on all of the other packages which I automatically install anyway.  This way, I not only am able to get it all set up in one clean pass, I have a version control system so that I can push updates out to all the clients.

The one problem I've come up with is how Apt would deal with my package pushing out the same configuration files as the real packages.  Will it complain about a conflict between those two?

---

