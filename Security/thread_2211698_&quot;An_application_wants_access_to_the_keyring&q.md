---
title: "&quot;An application wants access to the keyring&quot;"
date: 2014-03-17
forum: Security
---

### Post by stimpy77 on 2014-03-17
I have Ubuntu 13.10 Desktop installed. I am being prompted with this message: "Title: 'Unlock Keyring' - An application wants access to the keyring 'default', but it is locked. Password? [____]"

This is not an unfamiliar message, similar concepts exist for both Windows and Mac, and the behavior derives from earlier forms of Linux. The idea of a keyring specifically is something I used on the Mac.

I have some beef with this message in Ubuntu's form, however. What application is requesting this? Accessing a keyring with a password is asking for a Master password, one password to rule them all. One cannot, and should not, just hand out this master password to any application. So what application wants access to the keyring??l

This failure to disclose who is asking for the master password is critically bad security. Where can I submit this concern as development feedback?

[IMG]https://pbs.twimg.com/media/Bi8D2dxCQAIg6sk.png[/IMG]

---

### Post by cariboo on 2014-03-17
You can submit a bug to [Launchpad]("https://bugs.launchpad.net/"), if you don't have one. you'll need to create an account, or you can email the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list.

---

### Post by stimpy77 on 2014-03-17
thanks

---

