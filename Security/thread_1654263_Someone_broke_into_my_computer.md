---
title: "Someone broke into my computer?"
date: 2010-12-28
forum: Security
---

### Post by espenbe on 2010-12-28
This morning mpg123 suddenly started playing a police siren occationly. I checked the process once I heard it, and root was the process owner. How could this happen? Have someone broke into my computer? If so - how could I verify an attack?

I run Ubuntu 9.10.

---

### Post by HermanAB on 2010-12-28
Let me guess:  Some time ago, you played with VNC and forgot all about it and you are using a super kool 4 character password?

If so, backup your data and re-install.  Then in future, use SSH and 9 character passwords.

---

### Post by EifleMan on 2010-12-28
Espenbe is right. The only way someone could have "broken" into your system is if you somehow gave them access. You could try killing the process and changing your root password using the command "sudo passwd", but if the process starts again with root ownership, you will have to reinstall your system, and choose a strong root password. When choosing any password, it should:

- Consist of at least nine characters
- Contain two or more numerical characters, and upper and lower case characters.
- Not consist of any pattern or sequence, such as "123", or "EFG", etc
- Not consist of any familiar dates or phrases
- Contain two or more words that are completely unrelated.

---

