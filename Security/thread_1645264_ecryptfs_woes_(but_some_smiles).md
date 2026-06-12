---
title: "ecryptfs woes (but some smiles)"
date: 2010-12-14
forum: Security
---

### Post by richtl on 2010-12-14
I successfully recovered my encrypted home directory using "su ecryptfs-mount-private"

I can log into my account from a console (ctl-alt-F1) and everything's properly unencrypted.

If I log in from the GUI, it doesn't unencrypt and I only have the Access Encrypted Desktop icon and README.txt. Clicking on the icon or running ecryptfs-mount-private from a terminal don't seem to do anything.

If I'm already logged in from the console when I log into the GUI everything works properly and my directory is decrypted.

So, how do I get the GUI to decrypt without having to log into a console first?

Kind regards,

Rich

---

### Post by richtl on 2010-12-23
> **richtl said:**
> 
I can log into my account from a console (ctl-alt-F1) and everything's properly unencrypted.


Mmm. Perhaps I should just have a conversation with myself, then. Unfortunately not much to add, as I haven't made any progress solving this problem. If I hang on another week or two, maybe one of my other personalities will have some sort of useful insight.

---

### Post by Dave_L on 2010-12-24
You could try this:

Add another user with an encrypted home directory.

Then compare the /home/NEWUSER/.ecryptfs and /home/.ecryptfs/NEWUSER directories with the corresponding directories for your current user account.  Use the diff command or equivalent to do exact comparisons of all files.

---

### Post by bodhi.zazen on 2010-12-24
> **richtl said:**
> I successfully recovered my encrypted home directory using "su ecryptfs-mount-private"

I can log into my account from a console (ctl-alt-F1) and everything's properly unencrypted.

If I log in from the GUI, it doesn't unencrypt and I only have the Access Encrypted Desktop icon and README.txt. Clicking on the icon or running ecryptfs-mount-private from a terminal don't seem to do anything.

If I'm already logged in from the console when I log into the GUI everything works properly and my directory is decrypted.

So, how do I get the GUI to decrypt without having to log into a console first?

Kind regards,

Rich

How did this happen ? Did you perhaps change your password ? from the command line ?

---

