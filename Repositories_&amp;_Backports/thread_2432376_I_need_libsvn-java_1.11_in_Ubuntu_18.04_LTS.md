---
title: "I need libsvn-java 1.11 in Ubuntu 18.04 LTS"
date: 2019-12-01
forum: Repositories &amp; Backports
---

### Post by jmarkmurphy on 2019-12-01
I am trying to access an SVN repository in Eclipse. I found out how to install libsvn-java and point Eclipse at it. But the error I get is something like a plugin requires libsvnjavahl-1 v.1.11 The standard release for 18.04 is 1.9.

I found a web site that tells how to get 1.11. Unfortunately it doesn't work exactly as I expected. This is the page I found: 
[http://www.neiland.net/blog/article/upgrade-subversion-on-ubuntu-18-04-beyond-1-9/](http://www.neiland.net/blog/article/upgrade-subversion-on-ubuntu-18-04-beyond-1-9/)

The problem shows up when I run ```
sudo apt-get update
```.

Here is the error:
N: Skipping acquire of configured file 'svn111/binary-i386/Packages' as repository 'http://opensource.wandisco.com/ubuntu bionic InRelease' doesn't support architecture 'i386'

Not sure where to go from here.

---

