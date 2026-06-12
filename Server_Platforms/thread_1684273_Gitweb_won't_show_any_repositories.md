---
title: "Gitweb won't show any repositories"
date: 2011-02-08
forum: Server Platforms
---

### Post by kwarxy on 2011-02-08
So I have been trying to get gitweb to work on an ubuntu dapper server.
The git repositories are under /git and are all named <project>.git.
/etc/gitweb.conf
```

#!/usr/bin/perl
# path to git projects (<project>.git)
$projectroot = "/git";
# directory to use for temp files
$git_temp = "/tmp";
# target of the home link on top of all pages
$home_link = $my_uri;
# html text to include at home page
$home_text = "indextext.html";
# file with project list; by default, simply scan the projectroot dir.
$projects_list = $projectroot;

```gitweb.cgi is located in /usr/lib/cgi-bin and my apache config is just standard with localhost/cgi-bin/ mapped to /usr/lib/cgi-bin. When I browse to localhost/cgi-bin/gitweb.cgi it loads up the page but does not show any projects. In the apache error log is this entry for each git repository in /git.
```

[Tue Feb 08 18:27:00 2011] [error] [client IP_ADDRESS] fatal: Not a git repository
[Tue Feb 08 18:27:00 2011] [error] [client IP_ADDRESS] fatal: Not a git repository
[Tue Feb 08 18:27:00 2011] [error] [client IP_ADDRESS] fatal: Not a git repository

```I have looked in the gitweb.cgi and am pretty sure the error is coming from the git_read_commit function when it tries the "git-cat-file" command. 

Any ideas on how to fix this?
Thanks

---

