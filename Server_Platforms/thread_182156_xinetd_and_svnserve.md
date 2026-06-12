---
title: "xinetd and svnserve"
date: 2006-05-25
forum: Server Platforms
---

### Post by wardjame on 2006-05-25
Hi all,
I have a nice new ubuntu server up and running but I would like to add svnserve to the mix and have it keep that process going.

I got svnserve working fine from the command line with:
svnserve -t

I can connect and use my repositories.

I would like to have svnserve running in tunnel mode all the time so I installed xinetd and followed these instructions to add svn:
[http://www.unix-girl.com/blog/archives/001486.html](http://www.unix-girl.com/blog/archives/001486.html)

But when I restart xinetd it svnserve is not running.  Is there a log file I can check somewhere to get a better idea of what the problem may be?  Since svnserve works fine from the command line I'm guessing my problem is with my xinetd setup.

Any help would be much appreciated.

---

### Post by joshuapurcell on 2006-05-25
I don't think xinetd is installed by default in Ubuntu (at least I don't see it and haven't used it in my current Dapper install). The link you posted doesn't say anything about how to install xinetd (only how to add svnserve to the xinetd daemon), so what did you do to get xinetd installed and configured?

You could just create a standalone svnserve service (in /etc/init.d) that is set to run at runlevel 2 startup. Or you could just put the command that starts svnserve at the end of your existing /etc/rc.local file. I haven't configured svnserve to start automatically yet... I just turn it on when I need it on my current install. On a previous install (using Red Hat), I just added the needed line to /etc/rc.local instead of going through the trouble of creating a new service... seemed to be the easiest way to get the job done.

---

### Post by wardjame on 2006-05-25
Sorry I didn't give more info.  I read some other posts that recommended  using xinetd prior to the one I listed above.  I just installed it with apt-get and didn't make any changes.

I don't have an rc.local file anywhere that I can find.

So you are suggesting that I use init.d over xinetd?  Any particular reason why one would be prefered?  Please provide some instructions for getting it running with init.d.

Thanks.

---

### Post by cgjones on 2006-06-02
Try [this](http://svnbook.red-bean.com/) for more information. I use SVN+SSH, so I can't help you directly.

---

### Post by wardjame on 2006-06-22
Thanks I already own a copy of that book.  I am using svn+ssh now and it seems like a much better option.  Thanks for trying to help.

---

### Post by reformist on 2006-09-30
As Joshua said, you can create a standalone svnserve init.d script. I've written one here, along with details about how to use it:
[http://philisoft.com/blog/a-subversion-initd-script-for-ubuntu-linux/]("http://philisoft.com/blog/a-subversion-initd-script-for-ubuntu-linux/")


Hope it's useful.

---

