---
title: "Changing language settings for a single ssh account"
date: 2009-11-22
forum: Server Platforms
---

### Post by karmakowski on 2009-11-22
How to change language settings for a single ssh account? Not locale, not encoding, just the language. 

The server is Ubuntu 9.10 (64 bit if that matters), the default language is something different than English. I would like my, and only my, account to be in English, including all errors and messages returned by commands too. 

What is the right way to do it? Without confusing applications, avoiding problems with encoding and any other pitfalls that might lead to. Solution that works for any shell used would be best but I use mostly bash.

---

### Post by Lars Noodén on 2009-11-24
That would entail creating an alternate system for that user to log into.  You can create a new ubuntu system within your ubuntu system using debootstrap.  You'll have to search around for a distro where the programs and manual pages have been translated.  

Once debootstrap has created the new system, make a symlink in it to the user's real home directory.  Then chroot just that account to that new system.

So if you have made a directory /alternatelanguage/polish containing the polish language localizaton and a group englishusers, then chrooting them to that directory *should* give you what you want.  Just a guess.

```

Match Group englsihusers
	ChrootDirectory /alternatelanguage/english

```

Keep in mind that it really is a separate system and that it will have to be updated and maintained just like the main system.

---

