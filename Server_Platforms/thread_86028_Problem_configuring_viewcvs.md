---
title: "Problem configuring viewcvs"
date: 2005-11-04
forum: Server Platforms
---

### Post by igb on 2005-11-04
I have used viewcvs on several other versions of Linux with no problems. I have compiled the latest development version and am trying to set it up with subversion.

I can see my repository roots fine, but when I click on a root to browse the code I get the following error:

Traceback (most recent call last):
  File "/usr/local/viewcvs-1.0-dev/lib/viewcvs.py", line 3370, in main
    request.run_viewcvs()
  File "/usr/local/viewcvs-1.0-dev/lib/viewcvs.py", line 265, in run_viewcvs
    import vclib.svn
  File "/usr/local/viewcvs-1.0-dev/lib/vclib/svn/__init__.py", line 28, in ?
    from svn import fs, repos, core, delta
ImportError: No module named svn

Here are the relevant bits of my viewcvs.conf:

```
svn_roots = svn: /var/lib/svn/repos
root_parents = /var/lib/svn/repos : svn
```

Has anyone got a working config they can post?

---

### Post by wolfg on 2006-09-23
install  python2.4-subversion and python-subversion

---

