---
title: "aide help"
date: 2009-07-17
forum: Server Platforms
---

### Post by dragos2 on 2009-07-17
I am trying to get aide [http://sourceforge.net/projects/aide/](http://sourceforge.net/projects/aide/) to work on my Ubuntu Server 8.04 64 bit.

I installed aide directly from repositories, then

$ sudo aideinit
which worked fine on 9.04 server but on a production server refuses to ever finish

# we pun the new database in position (would be better secured if moved on a cdrom
or even offline the server)
$ sudo cp /var/lib/aide/aide.db.net /var/lib/aide/aide.db

If aideinit finishes then I can
$ sudo touch /bin/bash

and then to check for changes

$sudo aide -c /etc/aide/aide.cof --check

which states that everything is allright, even if I delete or move any binary from /bin.

So I have 2 questions:

1) Why the check did not reported the changed binary ? 
2) Why aideinit never finished on one of the servers ? Any ideas of how
to strace it ?

Ps: /etc/aide/aide.conf if you want to change some settings.

---

