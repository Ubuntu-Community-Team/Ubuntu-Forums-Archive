---
title: "Hi re:deleted canonical partner in other software sources in Maverick update Manager"
date: 2011-03-06
forum: Security
---

### Post by Mat11 on 2011-03-06
Hi one of the Canonical Partners in system, admin,update manager,other software/software sources has vanished.Still have the one mentioning Canonical partners source code underneath its says software packaged by Canonical for their partners.

Need to find out how to recover the other one in software updates as the updates have now completely failed. I know i didn't make error because i double checked there was only one tick in google chromes box no where else !!!

Can you let me know what you see in other software sources in Maverick 10.10 ?
Think this might be a security issue as well.

Would really help Thanks.

Mat

---

### Post by cariboo on 2011-03-06
The line should look like this:

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

you can even click the link above to see what is in the partner repositories.

---

### Post by Mat11 on 2011-03-06
Many thanks for your help cheers. What is the best way to fix it --should i use the Desktop CD or Just make an entry somewhere ?

---

### Post by cariboo on 2011-03-06
The easiest way is to just copy and paste the line into /etc/apt/sources.list. To do this, press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

The above command will open the text editor as root, so that you can edit /etc/apt/sources.list. Copy the line from my previous post, and paste it into the bottom of the list. Once you're save the file, and close gedit. Now you can reload the list, using the Software Center, Synaptic Package Manager, or the command line.

---

### Post by Mat11 on 2011-03-07
Hi :D yes it worked did exactly your instructions -- initially when i went into synaptic i got this :

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Could not resolve ‘gb.archive.ubuntu.com’

So i tried reload a couple of times with no joy, then i clicked repair broken packages and it did it brilliant thanks all is well.

---

### Post by cariboo on 2011-03-07
You may want to try  a different server, go to System->Administration->Synaptic Package Manager->Settings-> Repositories, and in the Download from drop down, choose a different server.

---

