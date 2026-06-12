---
title: "Local network package cache"
date: 2009-10-01
forum: Server Platforms
---

### Post by undecim on 2009-10-01
In my house, we have a total of 4 laptops and a server, each of which run either Karmic or Jaunty. On my server (jaunty) I have set up apt-mirror, and have a repository mirrored for the Jaunty, Karmic, WineHQ and TOR repositories.

The problem I have with this is that I am downloading a lot of packages to my server that will never be used. This is taking up disk space and bandwidth, and I'm looking for an ideal solution, but can't find one...

Ideally, I could add one repository (though I'm not completely opposed to adding more) to each of my laptops and have all of my cached repositories combined there. Packages should only be downloaded from the internet if they are requested by a client, in which case they will be permanently stored and regularly updated.

Does anyone know of a program or script like this, or should I start writing my own?

Thanks in advance for any help!

---

### Post by cariboo on 2009-10-01
Instead of apt-mirror, you may want to have a look at apt-cacher, it is in the repositories. It will do what you want.

---

### Post by undecim on 2009-10-02
Thanks for the reply.

From what I'm reading, that is not quite what I'm looking for. It is definitely much closer than apt-mirro, but not quite it. I'll have to try it out first though.

It will at least work until I finish my perfect script. Thanks

EDIT: Hmm... reading the description in aptitude, it looks like this will work perfectly! thank you!

---

