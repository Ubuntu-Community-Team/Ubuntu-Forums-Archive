---
title: "Asking for advice: How to manage a small open source project?"
date: 2008-02-01
forum: The Cafe
---

### Post by mohamedafattah on 2008-02-01
Having some ideas that turned to be projects with my friends, with most of them are easy ones and most of the time specific to our university, we decided to manage them the open source way. We needed a tool to manage those projects easily. I tried gforge (and didn't work) on my local ubuntu machine but seemed too big for what we were intending (especially the CVS and SVN which will be much overhead for tiny commits). All what we need is:

* The ability to make a new project, each with certain users as super users who can do everything
* For each project, we need a forum, a wiki to be created automatically with a unified naming pattern
* The ability to upload source code for super users, download for everybody else.

As you see, all what I want is this simple functionality which is basically to tie mediawiki, phpBB2, and an upload download script together. Can you please give me names of the tools usually used by the open source community to lead such functionality?

---

### Post by bruce89 on 2008-02-01
May I suggest git for revision control? Branching in git is cheap, so go nuts.

```

git checkout -b mad-feature
[hack]
git commit -a
[more hacking and commits]
git checkout master
git merge mad-feature
git branch -d mad-feature

```

[LIST]
[*]Create a new branch and switch to it
[*]Commit changes
[*]Switch to the main branch
[*]Merge the feature branch
[*]Delete feature branch
[/LIST]

---

### Post by PartisanEntity on 2008-02-01
Why not use sourceforge or launchpad?

---

### Post by mohamedafattah on 2008-02-01
Thanks to both of you.

Well, we can't use launchpad or sourceforge as most of the projects are too specific to our needs, some of them will be just creating a wiki page. Other ones will be just boring standard libraries (sockets in python how to, or using qt, gtk). Rarely we have a project that has a shape, and I can assure you, once it is shaped you will find it in either one. :)

@ bruce89: Oh, the file uploads / downloads are preferably a web interface, but I will try also to see how to make the best use of git.
EDIT: Oh, I can see gitweb that does this job.

Any further suggestions?

---

