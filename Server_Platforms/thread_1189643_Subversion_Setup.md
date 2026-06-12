---
title: "Subversion Setup"
date: 2009-06-16
forum: Server Platforms
---

### Post by jlbprof on 2009-06-16
I want to use a Subversion Server from my Windows machines using Eclipse to a Subversion Server.  I have no idea how to setup such a server.  I only have experience using CVS servers (not setting them up) and I am lost.

I have followed this link for trying to set the server up:

[https://help.ubuntu.com/community/Subversion]("https://help.ubuntu.com/community/Subversion")

My Windows program cannot share a project it gets a permissions error.

I cannot tell if the problem is because of my server or my windows program.

Since I know nothing about SVN I cannot test if the local copy is properly setup.  I can checkout my empty repository, but do not know if even on my Linux machine I can "share" a project or not.

If I create a trivial hello world project on my linux machine

test/test.c

What is the appropriate command to check this in where no project exists already?  This would force it to write.

This is what I thought should be correct:

In one terminal

```

julian@website7:~$ svnserve -d --foreground -r /home/svn

```

And in another window just above the directory called test.

```

julian@website7:~$ svn import -m "New Import" test svn://192.168.1.26/home/svn/repos/testOnly/test
svn: No repository found in 'svn://192.168.1.26/home/svn/repos/testOnly/test'
julian@website7:~$ svn import -m "New Import" test svn://192.168.1.26/home/svn/repos/testOnly
svn: No repository found in 'svn://192.168.1.26/home/svn/repos/testOnly'
julian@website7:~$ svn import -m "New Import" test svn://192.168.1.26/home/svn/repos
svn: No repository found in 'svn://192.168.1.26/home/svn/repos'
julian@website7:~$ svn import -m "New Import" test svn://julian@192.168.1.26/home/svn/repos
svn: No repository found in 'svn://julian@192.168.1.26/home/svn/repos'

```

Where I have a created repository /home/svn/repos.

Where do I go from here?  I cannot find a log anywhere to read.

Thanx

Julian

---

### Post by jlbprof on 2009-06-16
OK, the issue has moved a little bit.

I had a permissions problem with my directories

/home/svn/repos is now setup as:

```

julian@website7:/home/svn$ ls -ld repos
drwxrwsr-x 6 www-data subversion 4096 2009-06-16 21:47 repos

```

Which now gets me the following error:

```

julian@website7:~$ svn import -m "New Import" test svn://julian@192.168.1.26/repos/testsOnly/test
svn: Authorization failed
julian@website7:~$ svn import -m "New Import" test svn://julian@192.168.1.26/repos/testsOnly
svn: Authorization failed

```

Still have no idea where to go next.

My username julian has an entry in /home/svn/repos/conf/passwd

julian = uhuhnotgonnatellya

But it never asks me for my password, and still dies saying authorization failed.

---

