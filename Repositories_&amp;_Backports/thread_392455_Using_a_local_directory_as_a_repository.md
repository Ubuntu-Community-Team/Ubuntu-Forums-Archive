---
title: "Using a local directory as a repository"
date: 2007-03-24
forum: Repositories &amp; Backports
---

### Post by Screevo on 2007-03-24
So I have a server running Ubuntu 6.06 LTS, and Its going in a rack in a server room that I won't always have access to. However, I wanted to always be able to add or remove software from the CD using apt-get and such.

However, I don't want to keep the CD in the computer all the time, so I copied the full contents of the cd to /media/ubuntu.

Now, i'd like to use that directory as a repository that I can access using Apt-Get. What do I need to put into /etc/apt/sources.list to access that?

SM

---

### Post by aysiu on 2007-03-25
[This HowTo](http://www.ubuntuforums.org/showthread.php?p=98665#post98665) is about two years old, but the same principle should work for newer versions of Ubuntu.

---

### Post by Screevo on 2007-03-25
That was how to make your own CD repository. I want the repository to reside on the local machine.

Now, the server IS running apache, so theoretically, I could have the cd in the www directory if that makes it easier, but right now, the files all reside in /media/ubuntu.

---

