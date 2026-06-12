---
title: "Password authentication help"
date: 2011-01-26
forum: Security
---

### Post by Thandroo on 2011-01-26
Hi all,

Running Ubuntu 10.10 and I'm getting annoyed by the password authentication each time I want to do something. I find this more annoying than Windows 7 and UAC.

Is there any way of disabling the authentication?

---

### Post by Thandroo on 2011-01-26
Hi,

As the only user of my Ubuntu OS, I want full access to all files and folders (i.e. able to take ownership for read/write/delete/create, etc)

how can I do this? I've tried searching the forums, but can't find anything!

---

### Post by gordintoronto on 2011-01-26
It should only happen when you are exposing your system to danger, such as installing programs. It protects you and your computer.

Email, web browsing, editing video or pictures, watching DVDs, etc, etc, do not require authentication.

---

### Post by teacheredgard on 2011-01-26
I have the same problem how can I do to solve it?

---

### Post by HermanAB on 2011-01-26
Howdy,

Use sudo:

$ sudo nautilus

$ sudo gedit

---

### Post by HermanAB on 2011-01-26
Get used to it.

---

### Post by snowpine on 2011-01-26
Use the "sudo" before a command (or "gksu" for graphical applications) and you can do anything, as the following link illustrates: 

[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by weedeater64 on 2011-01-26
Have you considered getting Debian? The new squeeze should be out any day. None of this sudo business, unless you wish to set it up so.

---

### Post by cariboo on 2011-01-26
Since there were two threads basically asking the same question, I've merged them. To understand how security works, have a look at the [RootSudo]("https://help.ubuntu.com/community/RootSudo") document

All your questions will be answered if you read the whole document.

---

### Post by Thandroo on 2011-01-27
> **HermanAB said:**
> Get used to it.

Not very helpful, but thanks for playing!

---

