---
title: "Can someone please help me understand Muekow?"
date: 2007-02-22
forum: Server Platforms
---

### Post by namelessone on 2007-02-22
I am having trouble understanding how ltsp and muekow work. When I boot up one of my thin clients, I can type in my username and password from the server and use fluxbox just like the server is using.

I chrooted into the /opt/ltsp/i386 directory and added a user student in group students, but I can't log in with that username, which should log me into a raw x session (if i understand everything right), nothing happens. The screen refreshes and I get back to the log in screen.

Obviously, I don't know what I'm doing. I don't understand the point of the /opt/ltsp/i386 directory. Can someone please explain this to me?

---

### Post by elst on 2007-02-22
The system in /opt/ltsp/i386/ is what actually runs on the client - in the default configuration it has enough software to boot the machine and connect to the LTSP server. All software and user accounts are held on the main system, and you don't need to manually tinker with /opt/ltsp/ - just use the ltsp-* tools to maintain the client.

The best documentation that I've seen is probably the LTSP v. 4 guide. This focuses on the internals rather than how to use LTSP, and is worth reading once you've been using LTSP for a bit.

---

### Post by namelessone on 2007-02-22
> All software and user accounts are held on the main system, and you don't need to manually tinker with /opt/ltsp/ - just use the ltsp-* tools to maintain the client.

So what's with the whole muekow thing then? I was reading about it, and it appeared that the whole point was that you chrooted into the /opt/ltsp/i386 and then used apt-get to install stuff. If  all users and files are from the server, why would you want to install anything in /opt/ltsp/i386?

---

### Post by hscottyh on 2007-02-22
It frees up the LSTP guys not to have to maintain a mini distribution and allows them to focus on innovation. In the future it will allow one to run some apps locally, for instance a media player, while everything else is still running on the server. The local app will be the same package as the host distribution uses.

I hope that made sense. 

By the way LTSP is great stuff, worth learning about. For a $20 x86 fan less thin client I got off ebay, my daughter can now do all the computing see wants in her room, except for high res video (low res flash works fine) and 3D gaming, which see cares nothing about.:)

---

### Post by namelessone on 2007-02-23
I think I understand.

And I have to admit, ltsp is pretty sweet. My server is a PIII running on 256 MB of RAM and it can boot at least two machines--both of which work at a usable speed.

---

### Post by yldouright on 2007-02-23
I'm glad you said that. I am about to try setting up an Edubuntu network around a Dual P3-500 1GB RAM SCSI system. I'll need 6 clients (all Macintosh hardware). All the Macs have video boards with at least 2MB of VRAM and 40MB of RAM. The old P5 PCs had 512K video and less RAM so I threw those out and kept the Macs instead. Was this a tactical error? Can the video processing run on the local hardware? How well will my six clients run in this configuration assuming Open Office, Firefox, Thunderbird and GAIM?

---

### Post by namelessone on 2007-02-24
well, you probably would have been able to pull it off with the old P5s, but the macs will work fine. Using Open Office might be pushing it, though. They are memory vampires. Try using lightweight things like Abiword.

It should be noted that my server is using fluxbox for its window manager, which is why I can actually get two clients on it.

Since you have a gig of ram and a dual core PIII, you might be able to pull it off, though.

---

