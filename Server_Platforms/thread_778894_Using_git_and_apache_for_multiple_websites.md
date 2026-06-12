---
title: "Using git and apache for multiple websites"
date: 2008-05-02
forum: Server Platforms
---

### Post by altonbr on 2008-05-02
I've never really used git but I've fiddled with SVN. I run a small small web development server and would like to start submitting website changes to git through multiple streams for multiple websites.

I'm looking for:

altonbr/example.com.git
altonbr/ubuntu.com.git

where Apache can host the trunk.

Does anyone have some links of tutorials or thoughts on how it would be best to combine apache, git, gitweb, etc.?

---

### Post by altonbr on 2008-05-03
I found a small tutorial from kernel.org so when I try it, I'll post my results here. Does anyone have experience with this???

[http://www.kernel.org/pub/software/scm/git/docs/howto/setup-git-server-over-http.txt](http://www.kernel.org/pub/software/scm/git/docs/howto/setup-git-server-over-http.txt)

---

### Post by jmandawg on 2008-05-18
Did you get it to work?  I've tried and had no luck with the Hardy release of git, i had to compile the latest release of git 1.5.5 and it worked.
I opened this bug: [https://bugs.launchpad.net/ubuntu/+source/git-core/+bug/231633](https://bugs.launchpad.net/ubuntu/+source/git-core/+bug/231633)

I'm curious as to whether you experienced the same problem.

---

