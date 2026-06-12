---
title: "How safe is it to use hdparm to generate entropy?"
date: 2006-05-02
forum: Server Platforms
---

### Post by auroraborealis on 2006-05-02
For a project, I needed a way to increase the entropy pool without typing keys or moving the mouse. I don't know much about how Linux increases its entropy pool, but I did read somewhere that disk I/O would cause this increase. So I came up with a simple way to accomplish my task:

hdparm -t /dev/hda1

But I'm thinking that this could be deterministic somehow. I haven't been able to find out any more information on this issue. Does any have experience with entropy generation?

---

### Post by Ocxic on 2006-05-02
what is an etropy???, I have no idea what your talking about, but it sounds interesting.

---

### Post by auroraborealis on 2006-05-02
Entropy is randomness.

---

### Post by jazzmuzik on 2006-05-02
From what I understand, generating true randomness on a computer is difficult if not impossible. You should ask your question on the programming forum.

---

