---
title: "Digsby... for Linux?"
date: 2010-07-31
forum: The Cafe
---

### Post by Shibblet on 2010-07-31
I recently saw that Digsby had a version available for Apple and Linux. 

This is great, except I don't like loading software into my Ubuntu machine without being able to remove it easily... in otherwords, I won't load it unless there is a PPA.

Now, I can't find a PPA on Launchpad.  Am I going about this wrong?

---

### Post by pwnst*r on 2010-07-31
Um, where did you see that?

[http://www.digsby.com/signup/maclinux/?os=linux](http://www.digsby.com/signup/maclinux/?os=linux)

---

### Post by chriswyatt on 2010-07-31
Did you click on the link on the Digsby website?  It says 'coming soon' if you click on it.  It's been 'coming soon' for years now.

I too was quite interested in Digsby and was eager for the Linux version, but I'm bored of waiting now.

---

### Post by koleoptero on 2010-07-31
If you install something by the classic configure, make, sudo make install way, you can later sudo make uninstall it. Just keep that folder somewhere.

---

### Post by chriswyatt on 2010-07-31
> **koleoptero said:**
> If you install something by the classic configure, make, sudo make install way, you can later sudo make uninstall it. Just keep that folder somewhere.

That's the trouble though, you have to keep the installation folders.  Me, I'm always just extracting tarballs all over the place in random folders all over my computer, some of those folders get deleted, some don't.  So it still is easier with a PPA if you're chronically disorganised like myself.

---

### Post by DoktorSeven on 2010-07-31
Instead of **sudo make install**, install and use **checkinstall**.  It creates a Debian package (and installs it) from the configure/make process that you can easily remove.

---

### Post by Shibblet on 2010-08-01
> **chriswyatt said:**
> Did you click on the link on the Digsby website?  It says 'coming soon' if you click on it.  It's been 'coming soon' for years now.

I too was quite interested in Digsby and was eager for the Linux version, but I'm bored of waiting now.

Yep.  Looks like it's not even a program...  So, no problems anymore.  ;)  Still happy with empathy.

---

### Post by pwnst*r on 2010-08-01
ffs

---

### Post by chriswyatt on 2010-08-01
> **DoktorSeven said:**
> Instead of **sudo make install**, install and use **checkinstall**.  It creates a Debian package (and installs it) from the configure/make process that you can easily remove.

Handy.  I'll try and remember that, thanks.

---

