---
title: "Deleting/Managing Ubuntu One Music?"
date: 2010-06-07
forum: Ubuntu One (CLOSED)
---

### Post by elfortunawe on 2010-06-07
I've only bought a couple of albums off the Ubuntu One Music Store, but I realize that as I buy more these will all be downloaded to all my computers. This isn't a problem on my desktop, but my other computer is a Dell Mini 10v with a 16g solid state drive. I would still like to be able to sync it with Ubuntu One, but I can't have all my music taking up all my drive space. Is there any way to manage my music across the cloud?

I tried just deleting a track from <code>.ubuntuone/Purchased from Ubuntu One</code> on my netbook, but that also removed it from the cloud server (which, I know, I should have realized would happen).

Also, the Ubuntu One interface in Banshee tells me I can download the track 4 more times, and has a link which (presumably) will do just that. I've clicked on that link a few times today and so far nothing has happened.

Thanks in advance for any response.

---

### Post by jehozadakk on 2010-06-08
If you leave your home computer on 25/7, I suggest setting up and SSH server.  With it, you can browse your home hard drive just like a local drive and with a good enough connection, you'll be able to play music directly over the net as well.  At the very least, you'll have access to it and to any other file you might have at home.

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

I use a combination of Ubuntu One, Dropbox, and my own SSH server.  Each works well for different things.

---

### Post by duanedesign on 2010-06-08
You can turn off the syncing of music on your netbook by going to System > Preferences > Ubuntu One or Me Menu > Ubuntu One and uncheck the Music Download option found under the Services Tab.

---

### Post by elfortunawe on 2010-06-08
Thanks. These two suggestions would actually work pretty well together. I do hope, though, that they eventually put more advanced controls into the Ubuntu One Music service.

---

