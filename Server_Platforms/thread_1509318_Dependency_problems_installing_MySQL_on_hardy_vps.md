---
title: "Dependency problems installing MySQL on hardy vps"
date: 2010-06-14
forum: Server Platforms
---

### Post by [censored] on 2010-06-14
Hi got ubuntu 8.04 LTS installed on a vps. I'm trying to install mysql but I'm getting dependency errors. 

```
apt-get install mysql-server mysql-client libmysqlclient15-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmysqlclient15-dev: Depends: zlib1g-dev but it is not going to be installed
  mysql-client: Depends: mysql-client-5.0 but it is not going to be installed
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Broken packages
```

FYI, I'm doing this as part of a server howto I'm following. My /etc/apt/sources.list file is as per the one posted on this howto......

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3)

Any help would be appreciated thanks.

---

