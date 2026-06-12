---
title: "SubVersion - almost"
date: 2006-11-06
forum: Server Platforms
---

### Post by kochen on 2006-11-06
Hi,
I've followed [this]("http://www.howtoforge.com/debian_subversion_websvn") guide to install SVN on my Ubuntu 6.06 Server.
I have the example repos, & also the WebSVN working just fine.

but I can figure out how to access the repos. from my PC with TortoiseSVN...

can some1 help me out?

---

### Post by skirkpatrick on 2006-11-06
That takes a bit of doing.  I've got it working on my work laptop but I do not have all the steps written down.  It does involve installing and correctly setting up Putty on Windows to get a ssh tunnel working.

---

### Post by kochen on 2006-11-07
> **skirkpatrick said:**
> That takes a bit of doing.  I've got it working on my work laptop but I do not have all the steps written down.  It does involve installing and correctly setting up Putty on Windows to get a ssh tunnel working.

I don't need or want SSH with PUTTY (or any other SSH application).
I already have a SSH application running on my Windows PC, & I also have TortoiseSVN installed.

I just want to be able to use it...

---

### Post by skirkpatrick on 2006-11-07
I'm at my work laptop now, let's see if I can help out at all.  First, you need to setup your SSH application to create a tunnel to your SVN server.  The SVN port is 3690.  Then, you need to change TortoiseSVN's network setting to use the correct program to open/close the tunnel.  That should be it.

---

### Post by kochen on 2006-11-07
> **skirkpatrick said:**
> I'm at my work laptop now, let's see if I can help out at all.  First, you need to setup your SSH application to create a tunnel to your SVN server.  The SVN port is 3690.  Then, you need to change TortoiseSVN's network setting to use the correct program to open/close the tunnel.  That should be it.

[LIST]
[*]Have SSH
[*]I've managed to read a repository with TortoiseSVN
[*]but not to commit - I get an Authentication Error (although I'm the owner of the repo.)
[/LIST]

---

### Post by skirkpatrick on 2006-11-07
I assume you've added to SVN's user list the user you are logging in as?

---

### Post by kochen on 2006-11-08
> **skirkpatrick said:**
> I assume you've added to SVN's user list the user you are logging in as?
of course.
I'm also the repository-directory owner.

---

### Post by skirkpatrick on 2006-11-08
That's weird.  Unfortunately, I don't admin our SVN setup so I can't help you on that end.

---

### Post by kochen on 2006-11-08
thanks...

any1 else...?

---

### Post by kochen on 2006-11-11
the problem is defenitly a permission problem.
I've changed svnserve.conf to have:
```
anon-access = write
```
it works...

what I need to have, is a group-based access.

how?

---

