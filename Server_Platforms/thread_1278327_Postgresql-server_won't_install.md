---
title: "Postgresql-server won't install"
date: 2009-09-29
forum: Server Platforms
---

### Post by rsciw on 2009-09-29
Ahoi there :)

I am trying to install postgresql, however encountering a problem so far installing the server component.

The Server is a VPS, runnig 8.04 LTS 64.

Executing 
sudo apt-get install postgresql, I receive:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  postgresql-8.3 postgresql-client-8.3 postgresql-client-common postgresql-common
Suggested packages:
  postgresql-doc-8.3
The following NEW packages will be installed
  postgresql postgresql-8.3 postgresql-client-8.3 postgresql-client-common postgresql-common
0 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/4849kB of archives.
After this operation, 20.1MB of additional disk space will be used.
Do you want to continue [Y/n]?        

```Continuing, it of course installs everything listed.

However, no server itself has been started, there's no output for
ps aux | grep postgresql (or pgsql, or psql)

executing
sudo /etc/init.d/postgresql-8.3 status 
returns nothing, not even a single letter :|
same with start or stop.

Wanted to look at config file in 
 /etc/postgresql/8.3/main
however there are no files/directories in there,
same with
 /var/lib/postgresql/ 
only /etc/postgresql-common/ exists.

rechecking the components installed and what is available, I noticed the
postgresql-server missing
sudo apt-get install postgresql-server however returns this:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package postgresql-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package postgresql-server has no installation candidate

```so now I'm stuck not being able to install pgsql via apt.

sources.list is configured for 8.04 hardy.
Tried as well with Intrepid,Jaunty and Karmic, but no change either.

Does anyone have an idea what's missing there?
Am I forgetting something, or is something else borked along the lines?

Thx,

rs

---

