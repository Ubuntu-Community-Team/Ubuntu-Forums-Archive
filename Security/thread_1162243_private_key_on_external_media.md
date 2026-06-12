---
title: "private key on external media"
date: 2009-05-17
forum: Security
---

### Post by atfrase on 2009-05-17
Is there a way to configure Seahorse/Nautilus (or is there some other GUI or application I can use instead?) so that it prompts for a private key if it isn't found in the user's keyring on the local filesystem?

I'd like to be able to keep my private key on external media only, and simply provide the media whenever I need the private key, rather than having it always on disk.

But in Seahorse, it seems like I can't delete only the private half of the key.  I can export and then delete the whole key, but then if I use Nautilus to open a file that was encrypted with that key, it just says it doesn't have the right key and doesn't ask me where to find it.

Any ideas?

---

