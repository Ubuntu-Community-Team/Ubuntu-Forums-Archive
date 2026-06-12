---
title: "Subversion server commits mess up permissions - umask needed?"
date: 2009-04-17
forum: Server Platforms
---

### Post by telex4 on 2009-04-17
I've set-up a subversion server following these instructions:

[http://www.howtoforge.org/debian_subversion_websvn](http://www.howtoforge.org/debian_subversion_websvn)

Everyone works nicely, except for one rather big problem. As soon as I make a commit via svn+ssh it changes the permissions on $repository/db/current to be the user and group that I used to make the commit. So then websvn suddenly complains. I have to go back in as root and chown/chmod so it's back to being owned by www-data:subversion.

I've read in [this documentation]("http://svnbook.red-bean.com/nightly/en/svn.serverconfig.multimethod.html") that I could create a wrapper script for svn and svnserve. I've also read elsewhere that I could do this in .bashrc, but I'm not sure how!

Can anyone help? It seems strange that the default configuration would fail like this... have I just done something daft?

---

