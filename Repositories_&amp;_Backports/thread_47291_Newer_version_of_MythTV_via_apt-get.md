---
title: "Newer version of MythTV via apt-get"
date: 2005-07-08
forum: Repositories &amp; Backports
---

### Post by beatyou on 2005-07-08
Does anyone where can I get a newer version of MythTV ([http://www.mythtv.org/](http://www.mythtv.org/)) via apt-get ? The default ubuntu repo has 0.17-3. Latest MythTV version is 0.18.1. 

Edit: after adding the repos ( deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) unstable mythtv ) and apt-get update I get the following error when attemping apt-get install mythtv.

```
The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (= 0.18.1-3) but it is not going to be installed
          Depends: mythtv-backend (= 0.18.1-3) but it is not going to be installed
E: Broken packages

``` 

Does this mean mythtv-frontend/backend are not ready on the repo?

Thanks.

---

