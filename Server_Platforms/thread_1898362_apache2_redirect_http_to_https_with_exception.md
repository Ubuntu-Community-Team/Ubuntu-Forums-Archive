---
title: "apache2 redirect http to https with exception"
date: 2011-12-21
forum: Server Platforms
---

### Post by chrone on 2011-12-21
dear all,

i've read the documentation to redirect all http to https using apache2 redirect module.

the question is, i managed to redirect all http traffic to https using the Redirect / [https://mydomain/](https://mydomain/) rules in the 000-default config, but i want to exclude /ubuntu folder since i mirrored the repository and could not get apt-get worked if redirected to https.

i tried to add Redirect /ubuntu [http://mydomain/ubuntu](http://mydomain/ubuntu) on top of the http to https redirect rule but with no luck.

is there a better rule to be use on the virtualhost *:80 to redirect all http to https with an exception for one particular folder (ubuntu) to be not redirected to https?

thanks in advance. good day! :)


/chrone

---

