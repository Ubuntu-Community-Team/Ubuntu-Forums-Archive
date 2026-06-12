---
title: "GitLab cannot load mysql2 adaptor"
date: 2014-07-01
forum: Server Platforms
---

### Post by sandyd on 2014-07-01
I am installing gitlab using this guide -> [https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/install/installation.md](https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/install/installation.md)

Ive gotten to the section about running gitlab-shell, and I am getting```

LoadError: Could not load 'active_record/connection_adapters/mysql2_adapter'. Make sure that the adapter in config/database.yml is valid. If you use an adapter other than 'mysql', 'mysql2', 'postgresql' or 'sqlite3' add the necessary adapter gem to the Gemfile.
...

```
This is an installation with RVM with ruby 2.1.2, and I have already installed the mysql, mysql2, and activerecord-mysql2-adapter without success.

---

