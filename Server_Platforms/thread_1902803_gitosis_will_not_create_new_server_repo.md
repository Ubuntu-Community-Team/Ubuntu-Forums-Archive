---
title: "gitosis will not create new server repo"
date: 2011-12-31
forum: Server Platforms
---

### Post by mslinn on 2011-12-31
I followed [these instructions]("https://help.ubuntu.com/community/Git") to the point where I push my new repo to origin. The instructions were fine except that [FONT="Lucida Console"]gitosis-admin.git[/FONT] was available under the [FONT="Lucida Console"]git[/FONT] directory, like this:
```
gitosis@domain.com:git/gitosis-admin.git
```
The instructions had said that the URL should be:
```
gitosis@domain.com:gitosis-admin.git
```
I was able to edit [FONT="Lucida Console"]gitosis.conf[/FONT] and push to origin.
```
$ cat gitosis.conf
[gitosis]

[group gitosis-admin]
members = gitosis,mslinn@asylum,mslinn@lhotse
writable = gitosis-admin
writeable = empathyworks

[repo empathyworks]
gitweb = no
description = blah
owner = Mike Slinn
daemon = no

```

When I push the new project, however, I get this:
```

$ git push origin master
fatal: 'git/empathyworks.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly

```
I tried editing the new git repo's [FONT="Lucida Console"].git/conf[/FONT] file and removed the [FONT="Lucida Console"]git[/FONT] directory, like this:
```
url = gitosis@domain.com:empathyworks.git
```
... but I still get the same type of message:
```
$ git push origin master
fatal: 'empathyworks.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly

```
I even tried creating the directory of the new repo in [FONT="Lucida Console"]/srv/gitosis/repositories/empathyworks.git[/FONT] and copying in the contents of the [FONT="Lucida Console"].git[/FONT] directory from my local machine but no joy.

---

### Post by consaor on 2012-02-07
Have you solved this problem? I'm having the same issue :(

---

### Post by mslinn on 2012-02-07
No, I gave up and hosted the repo on GitHub.

Mike

---

### Post by upul.godage on 2012-06-20
For future readers.

Do the following in the server directory where you have the repositories to create a bare repository.

git init --bare REPONAME.git

---

