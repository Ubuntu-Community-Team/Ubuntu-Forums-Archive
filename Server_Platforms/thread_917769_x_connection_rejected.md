---
title: "x connection rejected"
date: 2008-09-12
forum: Server Platforms
---

### Post by bohrstein on 2008-09-12
I'm writing to get some advice about how to sort out a network problem i'm having.
I'm working 'ssh-ing' on my laptop from home. Now the problem i have is that when i'm trying to open some text files using gedit, kate etc i get nothing but this message:

only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
DCOPServer self-test failed

If i try to run root i get a message similar to:
X connection to localhost:12.0 broken (explicit kill or server shutdown).

How do i sort out this problem? Please!!! I'm using ubuntu and when i try to open any text files offline (with gedit, emacs) its okay.

Thank you

---

### Post by cdenley on 2008-09-12
> **bohrstein said:**
> I'm writing to get some advice about how to sort out a network problem i'm having.
I'm working 'ssh-ing' on my laptop from home. Now the problem i have is that when i'm trying to open some text files using gedit, kate etc i get nothing but this message:

only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
DCOPServer self-test failed

If i try to run root i get a message similar to:
X connection to localhost:12.0 broken (explicit kill or server shutdown).

How do i sort out this problem? Please!!! I'm using ubuntu and when i try to open any text files offline (with gedit, emacs) its okay.

Thank you

So you have a mounted ssh partition through gnome?
```

ls -1 ~/.gvfs

```
Then how exactly do you attempt to open the file?

---

### Post by bohrstein on 2008-09-14
Yes i have a mounted ssh partition through gnome. This is the out i get after ls -l ~/.gvfs  :
total 0.
Normally if one has say a .cc file simply typing gedit file.cc should display the text but what i get is the error shown above.
What should i do?

---

### Post by cdenley on 2008-09-14
> **bohrstein said:**
> Yes i have a mounted ssh partition through gnome. This is the out i get after ls -l ~/.gvfs  :
total 0.
Normally if one has say a .cc file simply typing gedit file.cc should display the text but what i get is the error shown above.
What should i do?

Well, apparently you do not have it mounted through gnome. When gnome mounts network servers it creates mount points in ~/.gvfs. Since the output you posted shows .gvfs is empty, there are no servers mounted through gnome.

---

### Post by bohrstein on 2008-09-15
yeah, thanks. i kind of noticed this after i sent the reply.
cheers and thanks again

---

