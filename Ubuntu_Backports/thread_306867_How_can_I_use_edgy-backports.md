---
title: "How can I use edgy-backports?"
date: 2006-11-25
forum: Ubuntu Backports
---

### Post by Neophile on 2006-11-25
I'm not sure how the edgy-backports repository can be used. I have enabled the repository and I would like to know if it's being used when I run “apt-get upgrade”. I mean, are the packages from edgy-backports preferred over the ones in edgy? If they're not being used when upgrading, how can I do it?

Also, how can I see what packages are available in the backports repository?

Thanks.

---

### Post by jetthe on 2006-11-25
If you have enabled the repository by adding the correct line to your sources.list file your package manager (apt-get, synaptic, aptitude) will choose packages from the backports repository if there are any newer versions available in that repository. 
Remember to update your packages lists by executing 'apt-get update' before running 'apt-get upgrade'.

You can browse the packages in the repository for Edgy Backports at [http://packages.ubuntu.com/edgy-backports/](http://packages.ubuntu.com/edgy-backports/)

---

### Post by Brazen on 2006-12-06
I think this should be in the sticky.  I had these exact same two questions.

---

