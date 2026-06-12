---
title: "audacious needs newer libs"
date: 2006-12-05
forum: Repositories &amp; Backports
---

### Post by costis on 2006-12-05
Hello,...

I 'm trying to install audacious 1.2.2-1vd1, but I'm getting```
Depends: libcairo2 (>=1.2.6) but 1.2.4-1ubuntu2.2 is to be installed
Depends: libfontconfig1 (>=2.4.0) but 2.3.2-7ubuntu2 is to be installed
Depends: libpango1.0-0 (>=1.14.8) but 1.14.5-0ubuntu1 is to be installed
Depends: libxml2 (>=2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
```I hope these libraries be integrated soon...

Thank you :KS

---

### Post by Azakus on 2006-12-08
Try this thread. [http://ubuntuforums.org/showthread.php?t=308286](http://ubuntuforums.org/showthread.php?t=308286)
(Linked in my sig).

---

### Post by costis on 2006-12-11
I'm actually still getting the message```
costis@sangre:~$ sudo apt-get install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  audacious: Depends: libcairo2 (>= 1.2.6) but 1.2.4-1ubuntu2.2 is to be installed
             Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
             Depends: libpango1.0-0 (>= 1.14.8) but 1.14.5-0ubuntu1 is to be installed
             Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
E: Broken packages
```In [http://static.audacious-media-player.org/ubuntu/dists/edgy/main/binary-i386/](http://static.audacious-media-player.org/ubuntu/dists/edgy/main/binary-i386/)   I cannot find any of these libs.

---

### Post by xabbott on 2006-12-12
I got these same errors you had because I copied/pasted the repo url from the website. You have to make sure to change it to edgy/main.

---

### Post by costis on 2006-12-12
Thank you for your responses.
I really wasn't getting it.
The problem was that I had an error:```
:W: GPG error: http://www.linux2go.dk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A278DF5EE8BDA4E3
```
after ```
sudo apt-get update
```
I commented the appropriate line in* /etc/apt/source.list*, did *apt-get update* again and everything was fine with *audacious'* installation.

Thank you very much for your responses.

---

