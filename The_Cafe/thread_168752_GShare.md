---
title: "GShare"
date: 2006-05-01
forum: The Cafe
---

### Post by ssam on 2006-05-01
[http://yimports.com/~cpinto/projects/gnome/gshare](http://yimports.com/~cpinto/projects/gnome/gshare)

> 
 Currently file sharing in Linux sucks. If you don’t know much about setting up a Samba share you’re pretty much stuck.

What GShare does is to create a special folder at the user’s home directory (~/Shared Files) and use that as an FTP root for the built-in FTP server.

The FTP service is then advertised on the network through Avahi and the share shows up in Nautilus Network Server browser of another computer. 


anyone tried it yet?

---

### Post by Adrenal on 2006-05-01
I don't think breezy has a new enough version of mono. Or, at the very least, my skill is not enough to get it going(of course, I am partially asleep at the moment). Seems cool, would love a deb though

---

### Post by gatekeeper on 2006-05-03
[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)

Would it just be easier to use Samba that have all that overhead?

---

### Post by ringe on 2006-05-10
No, Samba sucks for Linux file sharing. It's certainly a very good product, but the lack of POSIX permissions is just annoying.

---

### Post by ssam on 2006-07-10
there are now ubuntu .deb packages at [http://yimports.com/~cpinto/projects/gnome/gshare](http://yimports.com/~cpinto/projects/gnome/gshare)

just download, and install by double clicking.

then go to system -> preferences -> file sharing to configure it.

---

### Post by airtonix on 2007-05-20
mmmm needs avahi....isnt that insecure?

---

### Post by reacocard on 2007-05-20
> **airtonix said:**
> mmmm needs avahi....isnt that insecure?

Not really. I think Feisty has Avahi by default anyway.

---

