---
title: "I broke PAM"
date: 2008-05-29
forum: Security
---

### Post by carbonrodney on 2008-05-29
Ok, so I was going through this tutorial that was for an earlier version or something, anyway a bunch of things weren't 100% accurate (and... probably I stuffed up somewhere, but lets not focus on that).

I was editing all the files in pam.d and now I can't authenticate... AT ALL! updates, sudo (including editing the changed files) I cannot do. The way I see it, I would have to replace those files with the originals somehow (because I can't run aptitude) without gaining root privilige through conventional means....

I'm using Xubuntu 8.04. I'd really prefer not to reinstall the entire OS... so if anyone has any ideas please please please reply.

Actually I just had one... I can be root from the livecd so if someone can link to the original pam.d files then that would be greatly appreciated...

---

### Post by carbonrodney on 2008-05-29
ok, so ive replaced all those files (all the ones i edited) with the ones present on the livecd which I am assuming are the same as the ones installed on a default system... no dice.

but as expected now i cant log in. :'(

---

### Post by carbonrodney on 2008-05-29
OK, I just reinstalled linux. I'd still be interested to know what might have gone wrong with copying the files from the 8.04 livecd to the harddrive.

---

### Post by HalPomeranz on 2008-05-29
> **carbonrodney said:**
> I'd still be interested to know what might have gone wrong with copying the files from the 8.04 livecd to the harddrive.

I haven't confirmed this myself, but it's conceivable to me that the PAM configuration for the LiveCD environment is actually a bit different from the PAM configuration for a system installed on the harddrive.  Now that you've re-installed your system, you could boot off of the LiveCD and compare the PAM configs between the LiveCD and your installed image (the diff command is probably what you want to use here).

In the future, it's always a good idea to make a backup copy of any system configuration files before you start making changes.  That way if things get messed up you can always revert to the original version of the file:

```

sudo cp /etc/pam.conf /etc/pam.conf-dist
sudo vi /etc/pam.conf

```

If you think you're going to be making lots of changes, you might even consider using a revision control system like RCS.  CVS and/or Subversion would probably be overkill, but RCS is convenient for keeping a version history of individual config files.

---

### Post by carbonrodney on 2008-07-29
Thanks for the tip. I did actually make backup files, but I couldn't replace the existing ones without root privilege.

---

