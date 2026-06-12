---
title: "git port/time out error"
date: 2011-07-19
forum: Security
---

### Post by ebore215 on 2011-07-19
When I try to clone a repository using git I get an error on port 22 saying that it has timed out.  I have reinstalled git several times and checked the ssh settings.  What could be causing this error.  Here is an example of an repository I have tried to clone.

jebrony@jebrony-desktop:~$ git clone [EMAIL="git@git.phpfog.com:foo.phpfogapp.com"]git@git.phpfog.com:foo.phpfogapp.com[/EMAIL]
Initialized empty Git repository in /home/jebrony/foo.phpfogapp.com/.git/
ssh: connect to host git.phpfog.com port 22: Connection timed out
fatal: The remote end hung up unexpectedly

Thanks

---

### Post by wkulecz on 2011-07-20
Is there a firewall blocking your connection?

I can't use any git servers from work :(
Your error message looks familiar.

---

