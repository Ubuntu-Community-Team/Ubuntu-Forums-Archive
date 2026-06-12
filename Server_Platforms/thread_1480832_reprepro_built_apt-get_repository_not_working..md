---
title: "reprepro built apt-get repository not working."
date: 2010-05-12
forum: Server Platforms
---

### Post by ivaldes1 on 2010-05-12
Hi, 

At a real road block/standstill getting an apt-get repository working. I built a apt-get repository using reprepro here:

[http://174.143.246.200/ubuntu/](http://174.143.246.200/ubuntu/)

using these instructions:

[http://www.jejik.com/articles/2006/09/setting_up_and_managing_an_apt_repository_with_reprepro/](http://www.jejik.com/articles/2006/09/setting_up_and_managing_an_apt_repository_with_reprepro/)

containing two packages gtm and astronaut-wv-server-beta

It doesn't seem to work at all even though it seems as though it should.

-- IV

---

### Post by ivaldes1 on 2010-05-12
Finally it works!

The problem was that if you have a tag in the control file like Conflicts: with no value it will not warn you and will tell you (far) downstream that something is wrong with dependencies but that is all. So the problem was simply a Conflicts: with no values. Removed it and it all works now. 

-- IV


> **ivaldes1 said:**
> Hi, 

At a real road block/standstill getting an apt-get repository working. I built a apt-get repository using reprepro here:

[http://174.143.246.200/ubuntu/](http://174.143.246.200/ubuntu/)

using these instructions:

[http://www.jejik.com/articles/2006/09/setting_up_and_managing_an_apt_repository_with_reprepro/](http://www.jejik.com/articles/2006/09/setting_up_and_managing_an_apt_repository_with_reprepro/)

containing two packages gtm and astronaut-wv-server-beta

It doesn't seem to work at all even though it seems as though it should.

-- IV

---

