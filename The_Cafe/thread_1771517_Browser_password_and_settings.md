---
title: "Browser password and settings"
date: 2011-05-30
forum: The Cafe
---

### Post by Oxwivi on 2011-05-30
Browsers can import password and settings from each other, without any special privileges - what's stopping malware to do the same and send it back home?

---

### Post by NMFTM on 2011-05-30
Don't know. They might be hashed for some added security. But then again, if another browser can import them, the hashes must be readily known and therefore almost as good as nothing. I've never stored passwords so I have no idea what kind of security's employed in keeping them safe.

Devils advocate: keyloggers can record keystrokes. Without stored passwords, what's stopping them from sending them back home? Seems like we're damned if we do and damned if we don't.

EDIT: You've peaked my interest enough that I'm going to read some [related]("http://en.wikipedia.org/wiki/Password_manager") wiki articles.

---

### Post by juancarlospaco on 2011-05-30
It doesnt work like you think...  try to see your own passwords

sudo cat /etc/shadow

---

### Post by Oxwivi on 2011-06-04
> **juancarlospaco said:**
> It doesnt work like you think...  try to see your own passwords

sudo cat /etc/shadow
See NMFTM's point about hashes.

And of the linked wiki article, that's fine if we have seahorse (the manager on Ubuntu) installed, but if it isn't? Regardless, if perchance we installed a browser with malicious code, it might be given permission to the stored passwords anyway.

---

### Post by Lucradia on 2011-06-04
> **Oxwivi said:**
> See NMFTM's point about hashes.

And of the linked wiki article, that's fine if we have seahorse (the manager on Ubuntu) installed, but if it isn't? Regardless, if perchance we installed a browser with malicious code, it might be given permission to the stored passwords anyway.

If the malware can get root easily (IE: Rootkits) You're pretty much fragged anyway. On an unrelated note, Trojans can infect any system. (Linux included)

---

