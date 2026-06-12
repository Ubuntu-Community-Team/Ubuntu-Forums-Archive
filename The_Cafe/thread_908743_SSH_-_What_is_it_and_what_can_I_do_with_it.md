---
title: "SSH - What is it and what can I do with it?"
date: 2008-09-02
forum: The Cafe
---

### Post by uraliss on 2008-09-02
Hi Folks,
Can somebody please explain what SSH is and whats so good about it?

How do you use it and what do you use it for?

Thanks

---

### Post by LaRoza on 2008-09-02
[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

Basically, in simplist terms, it allows you to securely remotely control another computer.

For example, I have several computers. If I have two on a network, I can log on to another computer with ssh, and control it (in terminal). It is often used for controlling servers, but I used it for many things (I use a lot of terminal apps, so that is not an inconvenience) and I use it to do things on my desktop from my laptop from other parts of the house.

---

### Post by Heinzelotto on 2008-09-02
i use it to get a remote **S**ecure **Sh**ell on my desktop-computer from my laptop and to encrypt file-transfers over a network.

---

### Post by Kingsley on 2008-09-02
It could be used to fork bomb part of your university's web server. :-\"

---

### Post by jimi_hendrix on 2008-09-02
> **kingsley said:**
> it could be used to fork bomb part of your university's web server. :-\"

rofl [-X

---

### Post by Trail on 2008-09-03
You can log-in remotely to a machine and administer it. You can also tunnel X through SSH, which means you can launch graphical applications remotely as well. Then you can do random hackish stuff, like tunnel specific ports to act like a proxy, write a cdrom remotely in real-time, pretty much anything.

Also of use to me is to launch graphical application from the same machine as another user (without launching a new session). Usage is "ssh -X {user}@localhost {command}".

You can also chain SSH connections.

---

### Post by graabein on 2008-09-03
I have a media fileserver without screen and keyboard at home. With SSH I can access it to run programs etc from anywhere using [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") or the terminal.

Here is a [useful tutorial]("http://www.suso.org/docs/shell/ssh.sdf").

---

