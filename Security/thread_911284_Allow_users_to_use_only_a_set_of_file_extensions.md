---
title: "Allow users to use only a set of file extensions"
date: 2008-09-05
forum: Security
---

### Post by vizualbod on 2008-09-05
Could I restrict a group to use only specific file extensions and refuse all operations on other extensions in their directories.

E.g.: allow all operations on ".txt", ".bla", ".bla2" but no other file extensions.

Is it doable?

---

### Post by vizualbod on 2008-09-05
This is what I DON'T want to do:

% crontab -e
(In crontab)
0 0 * * * find / -iname *.mp3 -exec rm '{}' \;

Root can store files of any extensions anywhere, but users of a specific group can use only specific extensions.

---

### Post by HermanAB on 2008-09-05
Hmm, in general, file name extensions don't mean anything in Linux.  The 'file' program is used to determine what type a file has.  This type is generally based on a magic number (the first two bytes of a file).

Cheers,

Herman

---

