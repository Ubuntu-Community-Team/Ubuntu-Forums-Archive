---
title: "Best distro for remote desktop server?"
date: 2008-09-22
forum: Server Platforms
---

### Post by Oliver Acevedo on 2008-09-22
What would you guys say would be the best distro to use as a remote desktop server? I have Ubuntu Hardy and would like to set up an old computer in my house to be connected to the internet at all times, holding all my music and movies so that I can easily connect to it and view or download more music while I'm away from home. 

I'd like to find a distro that's easy to configure for remote desktop and also low on resources (power consumption). So far I've tried xubuntu, puppy linux, and ubuntu. What would you guys recommenced other than these?

---

### Post by baudday on 2008-09-22
I use Ubuntu Server. Doesn't have a gui, so if you're good with unix that's a plus. Otherwise you can install one for it. I use it for pretty much the same thing you're talking about, but I also have some other things I do with it. Runs 24/7 with no problems so far...(Knock on wood)

---

### Post by cariboo on 2008-09-22
This will probably get into one of those why dont' you just answer the question thread again. To answer your question there is no best distribution for remote desktops, Linux was designed from the ground up to be networkable, so any desktop you choose will work well. However if you install the server version, all you have to do is install the gui programs you need then use X forwarding to run them. So install openssh-server on the server, the ssh client comes installed by default on most distributions then in a terminal type:

```
ssh -X user@server
```

Once you have connected, it is simply a matter of running the program you want in the terminal and it will be forwarded to the computer you are working from. eg:

```
sudo synaptics
```

will run synaptic package manager on your desktop, but all the installation will be down on the server.

My choice for a lightweight desktop would be window maker.

Jim

---

### Post by Oliver Acevedo on 2008-09-22
So I run the programs from my laptop but they'll actually be running on the server? I would definitely need a GUI, I'm not that familiar with Unix. I'll give it a try and let you know how it goes. Thanks!

---

