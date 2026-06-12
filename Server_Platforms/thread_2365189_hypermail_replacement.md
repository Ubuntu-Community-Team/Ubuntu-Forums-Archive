---
title: "hypermail replacement?"
date: 2017-07-03
forum: Server Platforms
---

### Post by pietbarber on 2017-07-03
Hey. 
I've been operating a web server for a long time. I've got email archives in mbox format going back to 2001.   The server I'm currently running on is CentOS 6, and I'm considering the amount of effort to move everything over to Ubuntu Server. 

While going through all of my requirements, I see that the hypermail package doesn't exist in Ubuntu.  NBD, it doesn't exist in CentOS, either.  I've been rolling my own RPMs for a while in CentOS land; that doesn't scare me. 

But before I go through the effort of coming up with a deb package for hypermail in Ubuntu... is there something out there that would be a good replacement for mbox-to-html that is already out there?  Something that works nicely from cron, doesn't have weekly security updates, and something that actually does nice display of the HTML in email these days, instead of flattening it all to ugly plain-text.

---

### Post by SeijiSensei on 2017-07-04
I still use hypermail on CentOS 6 to build online archives for the listservers I maintain for clients.  I built it from the [source tarball]("http://www.hypermail-project.org/").  It installed cleanly under /usr/local.

---

