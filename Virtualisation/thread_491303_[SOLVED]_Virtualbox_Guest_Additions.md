---
title: "[SOLVED] Virtualbox Guest Additions"
date: 2007-07-03
forum: Virtualisation
---

### Post by Cirrocco on 2007-07-03
I've lost my guest additions iso (?)
can someone look at theirs to tell me where in the FileSystem that file is located?

Thanks Muchly

---

### Post by Cirrocco on 2007-07-03
nevermind...

I need a coffee

---

### Post by wormser on 2007-12-05
You should not mark you thread solved with out putting the solution in your post.  I am looking for this answer but it aint here.  One of the main reasons to mark posts solved is so you can search and find the answer instead of reposting the same question.

Update:

Appearently it can take some time for it too appear.  More [here]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/").

>     Devices > Install Guest Additions&#8230;

This sometimes takes a minute so don&#8217;t worry if you don&#8217;t see anything right away. This should then prompt you and say something along the lines of:

    The Guest Additions image is not found on your host. Would you like to download this image now?

We&#8217;ll select YES and let it download the image. The image is downloaded to the host machine and then mounted within the guest. This way it can be shared with future guests without needing to download multiple times. It should also prompt you whether or not you&#8217;d like to mount the image. Again, select YES.

---

### Post by indianethic on 2007-12-24
go to virtual box devices -> Mount Cd/dvd rom -> cd/dvd image , if you find the gues additions iso file then go to ur guest os cd/dvd drive and start the installation of guest additions

Otherwise,  find the guest additions iso file in /usr/share/vitualbox dir and follow the same steps as above.:lolflag:

---

