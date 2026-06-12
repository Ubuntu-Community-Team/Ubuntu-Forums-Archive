---
title: "Forbidden characters in id_rsa passphrase?"
date: 2007-04-16
forum: Server Platforms
---

### Post by kag on 2007-04-16
I've got my ~/.ssh/id_rsa filed chmoded to 600. When I ssh to the remote server, it keeps asking me to "Enter passphrase for key '/home/kag/.ssh/id_rsa'"

I've tried to generate another id_rsa file without any password and it worked fine. So it makes me wonder if there are forbidden characters in a passphrase? I've got some "!", "é" and spaces - other than that it's regular characters.

---

### Post by kag on 2007-04-22
Anyone?

---

### Post by gaten on 2007-04-23
The only thing I can think of is possibly the terminal type you are using? If you're not using a local console that might be it, other than that I can't think of anything. According to **man ssh** your passphrase can be:
```
 ...any string of characters you want
```

---

### Post by kag on 2007-04-28
I'm using the local console. I generated another id_rsa with only regular characters ([A-Z]{8}) and it still doesn't work. So far, the only id_rsa that worked was the password-less one. Weird huh?

---

