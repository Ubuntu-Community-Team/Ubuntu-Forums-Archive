---
title: "Trac with multiple projects"
date: 2011-03-17
forum: Server Platforms
---

### Post by HandleWithCare on 2011-03-17
Hey everyone! Hope this is the right subforum to post this to.
I would very much like your advice on how to set up the following.

I have an ubuntu 10.04 server that runs subversion. There is only one svn-reposirory but it contains many projects (over a hundred).
What I would like to have is a [trac]("http://trac.edgewall.org/")-environment (v0.12) for each of the projects in such a way that I, and my collegues, can log in and have the same privilages on all project. Per project extra users can exist (like the client). Offcourse I want to have the project linked to svn so that browsing source is possible. 

The server runs apache and mysql and I have tried to set it up using [this page]("http://trac.edgewall.org/wiki/TracFastCgi") but no luck so far. All I get is internal server errors, so I must be doing something wrong.
The most ideal would be that [http://serverurl/trac](http://serverurl/trac) shows a list of all prjects and that [http://serverurl/trac/project1](http://serverurl/trac/project1) shows the trac environment for that project. This shouldn't be all that hard but I find that the ducumentation lacks some accuracy here and there and isn't very much up to date.
I would really appreciate any help, whether it is a step by step tutorial (yes please :-P) or a pointer to a good document. 

If more info is needed to answer my question please let me know, then I will provide it asap.

---

