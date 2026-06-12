---
title: "Which is better? Suffer through bad amanda-server package or install from scratch?"
date: 2013-08-05
forum: Server Platforms
---

### Post by matthewboh on 2013-08-05
I started to use the repository to install amanda-server and amanda-client but quickly discovered that there's a few problems with the package. First, it creates the user "backup", but the xinetd.d config file references the amandabackup user, which is the user account referenced in all the Amanda documentation.

Also, there's an error with the script because some of the values for the paths are incorrect.

So, is it better to try and fix these and other items or just pull the source code and install outside of apt-get?

---

### Post by LHammonds on 2013-08-05
FYI - I don't use Amanda but I have a feeling my experience applies nonetheless.

When just trying to get familiar with new things, I tend to use the packages for simplicity in evaluating and testing.  However, for the most part, I tend to do custom installs for production-level servers mainly because the pre-packaged deals are rarely what I need.  For example, to setup MediaWiki or Bugzilla, they expect you to install LAMP which places all services on the same machine.  I have a dedicated MySQL server setup to backup/restore all databases/tables and is quite secure.  I like to make use of such an existing setup rather than having multiple databases all over the place.  So in order to make use of my dedicated database server, I cannot install the repo packages...I have to install them manually.

LHammonds

---

