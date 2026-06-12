---
title: "Password Protect folders"
date: 2008-10-27
forum: Security
---

### Post by GmAz on 2008-10-27
Is there a program available that will allow me to password protect a specific folder.  It would be nice if it would work on Windows as well as I have the drive set up as a network share and access it from a Windows machine as well.  

Also, on a different topic, I am running 8.10 beta and I can no longer lock my screen when I leave my machine.  It just does nothing.  Is this broken.  I know, its beta, but it seems like a small thing to be broken.

---

### Post by cariboo on 2008-10-27
Remember just because it is a release candidate, doesn't mean that all the bugs have been swatted. It just means that the version is locked and no new programs will be added. If you feel this is a bug, create a bug report here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

The developers can't fix a problem if they don't know about it. If you do create a bug report, add as much information as possible, such as video hardware, any error messages you are getting and any thing else you can think of.

Jim

---

### Post by KeyserSoze93 on 2008-10-27
> **GmAz said:**
> Is there a program available that will allow me to password protect a specific folder.  It would be nice if it would work on Windows as well as I have the drive set up as a network share and access it from a Windows machine as well.  

Also, on a different topic, I am running 8.10 beta and I can no longer lock my screen when I leave my machine.  It just does nothing.  Is this broken.  I know, its beta, but it seems like a small thing to be broken.

I think the trick would be to create a new user who owns the folder, with a different account to you current one. Then use smbpasswd to create samba users for your two accounts, and add them in your /etc/samba/smb.conf as valid users, so you could log in with either, but only user2 or whatever would be able to access these folders.

---

### Post by hyper_ch on 2008-10-28
what do you mean by password protect a folder? against whom?

---

### Post by DaveTuborg on 2008-10-29
[Folder Password Expert can do the job of password protecting folders.]("http://www.folder-password-expert.com")

---

### Post by MaindotC on 2009-03-06
> **hyper_ch said:**
> what do you mean by password protect a folder? against whom?

It's called "I don't want my girlfriend to find my stash of porn".

---

### Post by bodhi.zazen on 2009-03-06
> **strAlan said:**
> It's called "I don't want my girlfriend to find my stash of porn".

:lolflag:

There are other reasons to password protect a directory, legal documents, financial documents, medical, etc.

It is just that people in Linux are used to either permissions or encryption. Windows is more open and does not have permissions, so password protecting a directory in windows is as close as it comes to Linux permissions (outside of the admin account for sys admin).

---

### Post by HermanAB on 2009-03-06
Geez, nobody answered the guy's question, everybody is just giving him sh@t!

You should use TrueCrypt.  It is in the repos.

Cheers,

Herman

---

