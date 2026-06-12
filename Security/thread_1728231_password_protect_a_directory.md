---
title: "password protect a directory"
date: 2011-04-13
forum: Security
---

### Post by ELD on 2011-04-13
Is it possible under Ubuntu 10.10 to password protect a directory?

---

### Post by HermanAB on 2011-04-13
Howdy,

Yes you can.

That being said, you need to do a Threat Risk Assessment:
Who are you protecting your files against?
1. Your little kid sister.
2. Other users of a managed multi-user system.
3. The system administrator of the machine - assuming that the machine is managed by someone else.
4. Commercial competitors.
5. A government entity with unlimited funding.

The first one can be handled by giving your little kid sister her own user account and not letting her use your account.

The second one should not be a problem, since the other users should already have their own accounts, so it is essentially the same as the previous one.

You can also do a variation on the theme, by making a new user account and changing the owner and group of the specific folder to the new account.

The other options, need more serious treatment, using encryption.

Linux offers various encryption systems varying from Zip and GPG, to TrueCrypt to LUKS to EncFS.  All of them are secure.

Pick your poison!

---

### Post by ELD on 2011-04-13
Is there no way to just set a folder as password protected?

---

### Post by bodhi.zazen on 2011-04-13
> **ELD said:**
> Is there no way to just set a folder as password protected?

By default they are password protected. As long as you have the proper permissions no one but you and root can read the files / directory.

So as herman outlined, it depends on what to need beyond that (linux permissions). 

On Linux the advice is to move to encryption. Take a look at cryptkeeper.

---

### Post by HermanAB on 2011-04-14
Howdy, 

The absolutely simplest method to provide additional protection to files, is to make an encrypted Zip file of the directory:

Double click the file browser Nautilus on your desktop. Right click on the folder that you want to protect. Select Compress..., select Zip format, Select Other Options, Type in a password.  Then, once the Zip archive is made, delete the original directory.

These type of archives work very well with Nautilus, pretty much transparently, so it is very convenient.

---

### Post by sTpny on 2012-05-28
You can, but its hard(ish) Easier way to protect a folder of sensitive info is to create a password protected archive.. Jush right click, pick compress, choose zip, add a password, delete the original, empty the trash, and your done.  You can then brouse the archive whenever you want, but only if you have the password. To everyone else, its inaccessable. Its not a locked folder, but the effect is the same.

---

### Post by overdrank on 2012-05-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

