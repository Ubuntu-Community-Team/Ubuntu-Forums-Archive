---
title: "KeepassX - Questions about 2-FA (key-file)"
date: 2014-08-13
forum: Security
---

### Post by markodd on 2014-08-13
Hey ubuntuforums community,

I've a KeepassX database and it's not currently set up to use a keyfile, only a masterpassword.

Is it possible to add a keyfile to the current database? That is, let's say I want 2-Factor-Authentication on my database, but I don't want to create a new one. Can I do it? How?

Also, when adding a key-file, can we choose any file? Can it be a movie? a .doc? a .txt? Anything?

---

### Post by TheFu on 2014-08-13
Make a backup of the password db file.
Try what you want. Did it work?

The key-file can be anything - looked at the "keepassx handbook" in the "Help" menu of the program:  > The key file can be any file on your computer, e.g. a picture or a text document. You can also create a randomly-generated key file by first selecting the key file check box and clicking "Generate Key File...". You can store the key file for example on a USB memory stick, to keep it with you everywhere. 

More details are here: [https://www.keepassx.org/](https://www.keepassx.org/)
They have a forum: [https://www.keepassx.org/forum/index.php](https://www.keepassx.org/forum/index.php)

The manpage for this program is lacking, sadly.

---

### Post by markodd on 2014-08-16
I finally found something that probably allows for a change of master-password and keyfile. I didn't see that in the menu up until now. Any suggestion for a key-file?

---

### Post by TheFu on 2014-08-16
I don't think it matters, but .... something that will be loaded on every system where you need KeePassX to work, isn't too obvious (like a desktop background), but isn't too strange that you won't have it everywhere. If you have music on all your systems ... at least a few hundred files, perhaps 1 of those?

But really - any file can be used - I bet they just use it for input into a hashing algorithm anyway.

---

