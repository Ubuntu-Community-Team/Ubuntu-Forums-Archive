---
title: "Can repeated adding FNEK Signature auth tokens damage home directory encryption links"
date: 2010-10-03
forum: Security
---

### Post by rocksockdoc on 2010-10-03
Can repeated adding FNEK Signature auth tokens damage home directory encryption links

**[COLOR=DarkRed]That is, what is the significance of multiple "FNEK Signature" authorization tokens being added to Home-directory encryption keyrings?[/COLOR]**

Over in this "[dead-in-the-water]("http://ubuntuforums.org/showpost.php?p=9918445&postcount=27")" thread, I'm merely attempting to MANUALLY decrypt my home directory, given only the login password of the user (because Gnome, for some reason, catastrophically failed).

So many things are confusing about these FNEK Signature auth tokens! :(

For example, in post #23 of that thread, I managed to [re-generate the original encryption passphrase]("http://ubuntuforums.org/showpost.php?p=9917927&postcount=23"):
```

$ **ecryptfs-unwrap-passphrase /home/.ecryptfs/user/.ecryptfs/wrapped-passphrase**
Passphrase:
**[COLOR=DarkRed]bfb3fc19842eade0b79ca4e7249ebe71[/COLOR]**

```So now I had both the login password and the encryption passphrase. Now all I need is the correct FNEK Signature set.

So, in post #24 of that thread,[ I obtain (one of two) sets of the supposed "FNEK Signature]("http://ubuntuforums.org/showpost.php?p=9918005&postcount=24")":
```

$ **sudo ecryptfs-add-passphrase --fnek**
[sudo] password for user: **foobar**
Passphrase: [B]bfb3fc19842eade0b79ca4e7249ebe71
[/B]Inserted auth tok with sig [**[COLOR=DarkRed]5eaa38e46b503148[/COLOR]**] into the user session keyring
Inserted auth tok with sig [**[COLOR=DarkRed]2a1860e7cb545c30[/COLOR]**] into the user session keyring

```Great. Now I have three necessary items:
- User login password (which is all I needed prior to Gnome giving up on encryption)
- Mount passphrase (which I had to re-generate because Ubuntu created it upon OS installation)
- Filename Encryption Key Signature, FNEK (which was 'inserted' into the "session keyring" (whatever that means).

That SHOULD be enough ... but it's just NOT working! :(

Time and time and time again I try this ... but I must be missing something fundamental ... or more sinister perhaps ... I may be "damaging" my keyring (whatever that is) by constantly "inserting" multiple "auth tok" authorization tokens (whatever they are) into the "user session keyring" (whatever that is).

Can you help me with a few of these basic questions?

**[COLOR=DarkRed]What does it mean to be "inserted into the session keyring" anyway?[/COLOR]**
And, if I do that multiple times with different FNEK signatures ... is something damaged forever?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171120&stc=1&d=1286063094[/IMG]

---

