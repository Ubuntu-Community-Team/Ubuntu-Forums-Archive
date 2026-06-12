---
title: "recover openssh moduli file"
date: 2014-01-20
forum: Server Platforms
---

### Post by n89thanh on 2014-01-20
I was configuring openssh, messed up, decided to delete the etc/ssh directory. I proceeded to reinstall openssh. After following additional guides, I ended up with everything back, albeit in new condition. All except the moduli file, which somehow didn't get created. I followed steps online, and now I have the files moduli-2048.candidates and moduli-2048.

Now my question is, is the moduli file needed for ssh to work properly? If so, how exactly can I restore it because there doesn't seem to be any sort of clear direction on how to do so anywhere, with most places just pointing back to the man page. I was reading about how it's related to encryption algorithm testing but in the end I still don't know if I actually need it or not. Any help is appreciated!

---

### Post by n89thanh on 2014-01-24
Wow, is my problem that unique that all other threads rush pass with a good amount of replies while mine remains empty? Typical, this is what I get for being good at sifting through old forums in solving less difficult problems and leaving the really hard one in the hands of... no one. :-(

---

### Post by steeldriver on 2014-01-24
Did you reinstall the client or the server, or both? A moduli file should have been provided as part of the openssh-client package I think

```

$ dpkg -S /etc/ssh/moduli
openssh-client: /etc/ssh/moduli

```

Since you don't what "steps online" you followed, it's hard to comment about that

---

