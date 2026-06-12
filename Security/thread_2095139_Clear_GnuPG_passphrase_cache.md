---
title: "Clear GnuPG passphrase cache?"
date: 2012-12-16
forum: Security
---

### Post by PDA1 on 2012-12-16
How do I clear my gnupg cache which "remembers" my key/passphrase? 

I right-click on an encrypted file and it automatically decrypts the file. Not very good if someone steals my computer (even though login is passworded, of course).

gpg-agent -SIGHUP doesn't clear it

No, there's no option to clear the cache (or have an key icon on taskbar) in Seahorse 3.4.1 like there was in Ubuntu 10.04

I'm running Ubuntu 12.04

---

### Post by chadk5utc on 2012-12-17
I wasnt sure about this so I googled and though not 100% sure but looks like you can add a config file with a couple lines for max-cache-ttl to resolve it have a look here and scroll down a bit:
[http://www.enigmail.net/forum/viewtopic.php?f=3&t=831](http://www.enigmail.net/forum/viewtopic.php?f=3&t=831)

---

### Post by PDA1 on 2012-12-17
Thank you for the effort but what they mentioned doesn't seem resolved.

Also, they're speaking to a certain amount about enigmail and it's relationship to gpg.

I emailed the gpg users list but haven't heard anything back from them.

This seems to be a very large problem as once you have access to someone's computer you can then decrypt any file they have that has been encrypted via gpg.  

Forget the techno talk- this problem needs fixing!

---

### Post by kevdog on 2012-12-18
What program are you using to envoke GnuPG?  The command line directly are through some other program?

---

### Post by PDA1 on 2012-12-18
I don't know.

Since I don't use command line much it must be through some other program.

---

