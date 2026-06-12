---
title: "Seahorse plugin abnormal CPU usage?"
date: 2016-01-03
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-01-03
Hello,
I post here because I'm using Xenial, but I got the same problem in 15.10 and (if I remember correctly) in 15.04.

When I try to decrypt a gpg-encrypted file, the seahorse plugin open a window asking for the password. In this moment the seahorse-plugin CPU usage jumps to 25%.
The CPU usage is not due to the decryption process, but only to the window which asks for the password. Is it normal?

Below you can see the CPU graph.

[ATTACH=CONFIG]266515[/ATTACH]
Normal CPU usage (beginning) -> Seahorse CPU usage (middle of the graph)-> Normal CPU Usage (end of the graph)

---

### Post by sudodus on 2016-01-03
It does not look normal. I used to run seahorse, but nowadays I have learned some standard command lines with ***gpg***, and made a couple of aliases, which makes it quite convenient.

I use these aliases (with the file name as parameter)

```
alias sign-by-sudodus='gpg --clearsign  -u sudodus'

alias encode-for-sudodus='gpg -er sudodus'
```

but for decoding, it is enough to run gpg without any options (with the file name as parameter)

```
gpg filename.gpg
```

See ```
man gpg
``` for more details

---

### Post by enricobe on 2016-01-03
> **sudodus said:**
> It does not look normal. I used to run seahorse, but nowadays I have learned some standard command lines with ***gpg***, and made a couple of aliases, which makes it quite convenient.

I use these aliases (with the file name as parameter)

```
alias sign-by-sudodus='gpg --clearsign  -u sudodus'

alias encode-for-sudodus='gpg -er sudodus'
```

but for decoding, it is enough to run gpg without any options (with the file name as parameter)

```
gpg filename.gpg
```

See ```
man gpg
``` for more details

Thank you. Seahorse works fine and I use it everytime I need to encrypt/decrypt. The only strange thing is this abnormal CPU usage that I'll report as a bug if other users have the same issue

---

