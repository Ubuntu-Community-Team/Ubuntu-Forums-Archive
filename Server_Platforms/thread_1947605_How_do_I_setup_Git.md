---
title: "How do I setup Git?"
date: 2012-03-26
forum: Server Platforms
---

### Post by pepsifx357 on 2012-03-26
Hey all,

I've got some Music related projects the me and my friend are wanting to colaborate on.  Git seems to be the way to go, however, I seem to be having problems setting Git up.

I am installing the Git server on the same machine as the client.  I keep having errors.

```
root@daw:/home/ben# git clone gitosis@10.1.1.3:gitosis-admin.git
Initialized empty Git repository in /home/ben/gitosis-admin/.git/
gitosis@10.1.1.3's password: 
fatal: 'gitosis-admin.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly
```

If I try the command from my username I get the same thing:

```
ben@daw:~$ git clone gitosis@10.1.1.3:gitosis-admin.git
Initialized empty Git repository in /home/ben/gitosis-admin/.git/
gitosis@10.1.1.3's password: 
fatal: 'gitosis-admin.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly
```

Any Ideas?


Thanks,

Ben

---

### Post by kevdog on 2012-03-27
Does this link help:
[http://book.git-scm.com/4_setting_up_a_private_repository.html](http://book.git-scm.com/4_setting_up_a_private_repository.html)

---

### Post by pepsifx357 on 2012-04-04
Total fail for me.  I guess Git wasn't the right thing for us.  I can't believe how complicated the process was and it didn't even work.

---

### Post by rubylaser on 2012-04-04
> **pepsifx357 said:**
> Total fail for me.  I guess Git wasn't the right thing for us.  I can't believe how complicated the process was and it didn't even work.

Did you try following the [Ubuntu Docs]("https://help.ubuntu.com/community/Git")?  I've went the server route a few times, and it's never seemed too difficult.  But, after seeing how awesome/easy merging is in GIT, I'd never go back to SVN.

As a different option, you could also just init with a local repository that you put into a shared Dropbox folder and bypass the server setup altogether.

---

### Post by markbl on 2012-04-04
> **pepsifx357 said:**
> Total fail for me.  I guess Git wasn't the right thing for us.  I can't believe how complicated the process was and it didn't even work.
Well you posted here asking about setting up git when clearly your problem is that you have not set up gitosis correctly. Gitosis is not git, it is another independent tool. Read a setup guide for gitosis, e.g. [http://www.howtoforge.com/setting-up-gitosis-on-ubuntu](http://www.howtoforge.com/setting-up-gitosis-on-ubuntu).

---

