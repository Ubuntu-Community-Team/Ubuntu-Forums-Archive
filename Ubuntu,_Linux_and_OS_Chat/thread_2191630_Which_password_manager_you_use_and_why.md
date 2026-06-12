---
title: "Which password manager you use and why?"
date: 2013-12-03
forum: Ubuntu, Linux and OS Chat
---

### Post by gregory12 on 2013-12-03
I'm new to linux and want to jump start my software finding.
If it's something that has android client as well and can sync, even better. 

Anyway, say which one do you use and why, which is the feature you like the most...

---

### Post by Erik1984 on 2013-12-04
I use KeepassX [https://apps.ubuntu.com/cat/search/?q=keepassx&op=](https://apps.ubuntu.com/cat/search/?q=keepassx&op=) myself but I only need it on Windows and desktop Linux. If you want a cross platform solution LastPass might be better. To sync the KeepassX database I use Dropbox. That might sound unsafe but unlocking the database requires two factors that are not stored on Dropbox (the password of the database and a key file).

---

### Post by mJayk on 2013-12-04
Is there a program that will create a random password for each logon and store these ?

---

### Post by Erik1984 on 2013-12-05
KeepassX has a password generator, I use it for all important passwords. Basically you can make those random passwords as long as the service that your account is for allows. You can also set the types of characters the password must consist of. That is a handy feature as more characters means harder to guess but sites often have restrictions or requirements (at least one number and a capital or something like that). I've attached a screenshot of the password generator. It's in Dutch but it shouldn't matter for understanding the basic features. This is from the Windows version as I'm now on Windows but the Linux version is identical.

[ATTACH=CONFIG]248362[/ATTACH]

---

### Post by Irihapeti on 2013-12-06
KeePassDroid (for Android) will open KeePassX files. There are apps for iOS as well. If, like me, you're using an older phone, there's KeePassJ2ME which also reads KeePassX files.

So I can sync my password files between a number of devices, including a Windows install. I prefer to use Unison on my LAN to do the syncing, but there's no reason why you couldn't use a cloud system such as Dropbox or Ubuntu One.

---

### Post by Frogs Hair on 2013-12-06
I use LastPass because I dual boot and I can use it easily for both operating systems or login from anywhere.

---

### Post by gregory12 on 2013-12-06
that's quite helpful, thank you guys!
keepassx seems to be the most popular so far.

By the way, does keepassx lock the database file while using it? 
I mean can it be synced while in use?

---

### Post by gregory12 on 2013-12-07
does it lock the db while in use?

---

### Post by Irihapeti on 2013-12-07
Here's what I've found:

When the program is showing the actual entries in the database, the database is locked. So if you sync at this time, you won't see the changes.

The lock file gets removed when the program locks the database. You can do that deliberately, or set it to do so after a certain length of time. When you unlock the database, the changes become visible.

I've been doing this for months and have never had a problem.

---

### Post by gregory12 on 2013-12-10
great!

I suppose keepassx has the best integration with ubuntu as well?

---

### Post by Irihapeti on 2013-12-10
I'm not quite sure what you mean by integration with Ubuntu. KeePassX is in the Ubuntu repositories, and will install without difficulty. So are a few other password managers. Some have more dependencies than others (i.e. they install more additional libraries that they need).

Probably the best idea is to try them out and see which one works best for you. You shouldn't have any trouble with exporting/transferring passwords between the different programs.

---

### Post by Erik1984 on 2013-12-10
KeepassX is just a Qt application, it has no special integration with Ubuntu, it just works in all Linux DEs (including Unity) I have used (and in other OSes like Windows). Just try it and if you don't like it try LastPass or another password manager.

---

### Post by necromonger on 2013-12-10
I use KeepassX and it works ok for me.

---

### Post by Andrew.Richeson on 2013-12-11
I also Use KeepassX has a password generator. it work very fine for me

---

