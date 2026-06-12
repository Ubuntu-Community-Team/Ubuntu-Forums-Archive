---
title: "Mirror with apt-mirror, bad practice?"
date: 2011-04-04
forum: Server Platforms
---

### Post by Duologic on 2011-04-04
Hello everybody on the Ubuntu Forums, this is my initial post, so don't be to hard on me.

I'm setting up a Debian and Ubuntu mirror for a university in Ethiopia. I've started with the Debian mirror [1], they have a set of scripts available that use Rsync. I took a while to figure it out, but I got it working.

Now I've set up a Ubuntu mirror with apt-mirror [2]. While it is downloading I notice it uses wget to fetch the packages. Following the Debian site, that would be a bad practice [3]. If so, can anyone point me out to some documentation on a Ubuntu mirror with Rsync?

1. [http://www.debian.org/mirror/ftpmirror](http://www.debian.org/mirror/ftpmirror)
2. [http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
3. [http://www.debian.org/mirror/ftpmirror#how](http://www.debian.org/mirror/ftpmirror#how)

---

### Post by Duologic on 2011-04-05
bump because of no answer and already on page 3 in 'Server Platforms'

---

