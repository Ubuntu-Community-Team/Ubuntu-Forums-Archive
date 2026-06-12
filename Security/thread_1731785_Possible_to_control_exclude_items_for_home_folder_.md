---
title: "Possible to control exclude items for home folder encryption with ecryptfs?"
date: 2011-04-17
forum: Security
---

### Post by User4519 on 2011-04-17
Hello :)

I was wondering if someone with more knowledge than me can clarify if it's possible to use a white or blacklist to control which folders are ecryptfs encrypted when you're using the "encrypted home folder" option.

Of course I can always create an extra folder outside of my ~ and then symlink what I don't want encrypted into it, but I'd rather that it's possible to create like, ~/.ecryptsfs/excludelist with a list of paths that shouldn't be encrypted.

Thanks in advance,
Daniel :)

---

### Post by HermanAB on 2011-04-18
Howdy,

EncFS affects a whole 'folder'.  So if you elect to encrypt your home directory, everything will be encrypted.

You can selective encrypt folders using Cryptkeeper.  It is in the repos.

---

### Post by User4519 on 2011-04-18
Righty-o, thanks :) Was expecting that answer as manpages and Google didn't suggest the opposite. Just had to ask ;)

Cheers!

---

