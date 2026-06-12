---
title: "How to make an apparmor profile for a ruby gem or for npm, node.js?"
date: 2015-11-04
forum: Security
---

### Post by a-you on 2015-11-04
I'm wondering if it's possible to make an apparmor profile for for example a ruby gem like jekyll. I have installed gem itself from the repositories with apt-get but jekyll was installed without sudo, just by gem. How would one go about making such a profile?? The application to be confined is I suppose ruby, or is it jekyll?

Similarly I have installed npm/node.js without sudo so they are in subfolders of home. Also I'm using the javascript task runner grunt, which then runs modules installed in the folder containing the web project one is working on.

Would it be possible to use apparmor to prevent those things from accessing anything except the folders they are supposed to work directly in??

Hopefully what I'm getting at here is clear, and thanks in advance for any thoughts. And if anybody has a link to an apparmor profile for any of these that would be appreciated too (thanks).

---

