---
title: "Whats happening in SSH?"
date: 2006-10-17
forum: Server Platforms
---

### Post by jordans on 2006-10-17
Ok, i need an answer fast. I have a friend that is working on a server via SSH and I want to be able to see what he is doing while directly on the server. Is this possible.

---

### Post by Iowan on 2006-10-17
SSH is designed to *prevent* eavesdropping...
A lot of his activities may end up in the logs, though.

---

### Post by _AA_ on 2006-10-17
# cat /home/user/.bash_history

---

### Post by az on 2006-10-17
There is a tool to share a command-line session through ssh....

Just like VNC for the command-line...  

Wait...

---

### Post by baastie on 2006-10-17
indeed, you can use 'screen' to share the cli

Cheers,

---

### Post by skymt on 2006-10-17
> **baastie said:**
> indeed, you can use 'screen' to share the cli

Cheers,

But only if each user is using screen. You use the -x option to "listen in".

---

