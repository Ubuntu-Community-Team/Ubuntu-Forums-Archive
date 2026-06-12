---
title: "Making a &quot;Jailed&quot; HTTP Server"
date: 2005-09-29
forum: Server Platforms
---

### Post by Kyral on 2005-09-29
I apologize if this has been asked before, but is there a way to make a "jailed" HTTP server?

Let me expand on what I mean. I want to run a HTTP server off my desktop machine, but I want to isolate it completely from the rest of the computer, ie, so its not aware that it exists and thusly most hack attempts wouldn't spread out to the rest of my system. I don't know a lot about setting up HTTP servers ( let alone any other server ), so any help would be appreciated

---

### Post by Glut on 2005-09-29
Your best bet would be running a virtual machine such as Xen or VMware.

*Edit*
An afterthought... I think I will explain my reasoning.

I assume that you're wanting to setup a chroot jail. Possible, but it can be nasty to configure and bite you. You said that you don't know a great deal about setting up a server, so I went straight to a virtual machine, where you 'simply' setup another system. I think that it's easier than administering a chroot jail (Or gaol for English speakers.)

Having said that, you are probably wanting to play around with jailing to see how it works, I suggest you follow this guide: [http://www.linux.com/article.pl?sid=04/05/24/1450203](http://www.linux.com/article.pl?sid=04/05/24/1450203)
With a few caveats. The standard Debain (and therefore, ubuntu) apache install uses a modification to the apache httpd.conf file, which you will need to understand before implementation. Also, the default directory for web pages is different, so you will need to setup the configuration. Finally, notice that some of the daemons and other files being referred to will also be in different locations.

Good Luck!

---

