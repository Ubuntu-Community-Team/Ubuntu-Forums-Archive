---
title: "Trusted ppa's and fixing things"
date: 2013-03-23
forum: Security
---

### Post by alvinmoneypit on 2013-03-23
I'm continually amazed at the volume and depth of geeks out there posting helpful articles and HowTo's for Ubuntu and linux in general.  A problem I've been seeing is there are so many different thing posted on how to fix a specific problem and no traceability on which ones work, which are old, outdated etc.  Most have the distribution they are addressing, but not all.  I realize we may not be able to do anything about that, but I'm just acknowledging that is the way it is.  

I recently had a tempting reply to a question I asked on [ask Ubuntu]("http://askubuntu.com/") where I got a response to try [this HowTo]("https://launchpad.net/~makson96/+archive/fglrx").  He or she is asking me to install his or her personal ppa.  I really don't wish to do that but is there really any other choices?  I'd like to see his/her solution in the Ubuntu Canonical umbrella, but haven't found it there yet.  Any info or experience with this person or ppa?

---

### Post by cariboo on 2013-03-23
This subject (use of ATI/AMD legacy drivers) has come up many times on the forum, and the solution in the ppa is the right one, it just makes it easier for you to downgrade the x-server to a version that the legacy driver can use. Whether you weant to use the ppa is up to you, but my personal preference would be to use the ppa, instead of some random web site on the internet.

---

### Post by alvinmoneypit on 2013-03-23
Thanks for this reply.  Just two other questions - can I delete the ppa after I get what packages I need (I assume yes) and can I delete the packages after I complete the installation, or are they needed to maintain the drivers/programs once they are installed?

---

### Post by cariboo on 2013-03-23
You can remove the ppa from your sources list, but if there are any updates (you never know) you won't get them. Removing the packages from the archive is as easy as opening a terminal and typing:

```
sudo apt-get clean
```

I would suggest archiving the packages to a cd, just in case you need them in the future.

---

### Post by alvinmoneypit on 2013-03-24
Thanks for the considerate reply, Cariboo.

---

