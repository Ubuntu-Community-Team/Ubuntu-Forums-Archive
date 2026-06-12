---
title: "apt-get install to specific directory"
date: 2011-04-06
forum: Server Platforms
---

### Post by Loki57701 on 2011-04-06
Hi everyone, hopefully someone can help me out with this.

Using apt-get can I install java and tomcat into specific directories, instead of the default way apt would do it?

Thanks

---

### Post by SeijiSensei on 2011-04-06
No, because then the system wouldn't be able to update the software from the repositories when needed.  You can build things from source, or download binaries, and install them where you like, though /usr/local or /opt are the usual places.

The quick answer to questions like these is to look at the "man" page for a program and see if there is an option that meets your needs, e.g.,"man apt-get".

Unless you have a very unusual application that demands a particular location for files, you're always best off letting apt manage where things are located.  Usually that's under /usr.

---

