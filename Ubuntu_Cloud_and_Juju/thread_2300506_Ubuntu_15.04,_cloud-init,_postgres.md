---
title: "Ubuntu 15.04, cloud-init, postgres"
date: 2015-10-26
forum: Ubuntu Cloud and Juju
---

### Post by Lasse_Westh-Nielse on 2015-10-26
Hey,

This follows from a stackoverflow post: [http://stackoverflow.com/questions/33306475/ubuntu-15-04-postgresql-doesnt-start](http://stackoverflow.com/questions/33306475/ubuntu-15-04-postgresql-doesnt-start)

Tl;dr: I am trying to get postgres working on Ubuntu 15.04 with cloud-init. But I cannot get the service to start. I'll refer to the stackoverflow post for details.

It seems that, when I run stuff under cloud-init, there is a problem with the systemd/ service scripts in that they will claim to run, and claim that the postgres service has started, but that nothing actually runs. And the exact same service start/ stop/ status calls work perfectly fine when running from prompt, i.e. after cloud-init has finished.

Any help is greatly appreciated!

Regards,

Lasse

---

