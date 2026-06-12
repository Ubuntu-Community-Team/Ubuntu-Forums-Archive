---
title: "File sync without a service?  Aquaris M10 &lt;-&gt; Debian &lt;-&gt; Fedora"
date: 2016-05-05
forum: Ubuntu Phone and Tablet
---

### Post by icewater on 2016-05-05
I would like to sync files between my M10 and my various linux machines, but don't want to use a service like dropbox etc.  Is there a preferred way?

I had been using owncloud with Android devices but would be willing (interested even) in using something else. 

The other devices are running Debian and Fedora.

---

### Post by Tao_Joannes on 2016-05-05
Owncloud works, there's even a pretty good scope available in the store, or you could use rsync in the terminal

---

### Post by myname9 on 2016-06-15
Just got an Aquaris M10 (newbie, excited) and would also like to transfer files without using dropbox, etc.

If I connect Aquaris M10 to my Ubuntu desktop with USB, the device appears in the file manager as &#8220;cooler&#8221;, but I do not see contents. Same happens with Windows Vista.

I can eject the microSD and view its contents from outside the tablet. Tried syncing Clementine (new user there, also) to the device with the same behavior. I can sync to the card, if outside the tablet.

---

### Post by krusty8 on 2016-06-19
> **icewater said:**
> I would like to sync files between my M10 and my various linux machines, but don't want to use a service like dropbox etc.  Is there a preferred way?

I had been using owncloud with Android devices but would be willing (interested even) in using something else. 

The other devices are running Debian and Fedora.

I'm dabbling with [syncthing]("https://syncthing.net/"). It kinda works. I'm not sure I remember all the details off of the top of my head, but I think I just installed it on UT with apt (yes, after mounting readwrite) and on the PC as well with apt and then played with the settings until I got it to work. Maybe you could also install it in a chroot/ a libertine container.

I'd be happy to hear/assist someone else trying it!

Edit: Maybe you need neither readwrite, nor chroot. Looking at this: [https://forum.syncthing.net/t/keeping-syncthing-running-ubuntu-upstart/30/13](https://forum.syncthing.net/t/keeping-syncthing-running-ubuntu-upstart/30/13) sounds like getting the executable into your home dir should suffice

---

