---
title: "If Netflix Isn't Avalible To Linux, How is it possible..."
date: 2011-03-23
forum: Wine
---

### Post by sylar petrelli on 2011-03-23
Sorry if this is the wrong forum, but how is possible that Netflix is available for TiVo, Wii, PS3, and Roku, which are all Linux based systems, but not available to your regular desktop system.

I am thinking that if those embedded systems are able to implement the Playready DRM Stack, there must be a way to do it on Ubuntu.

---

### Post by dino99 on 2011-03-23
maybe this can help:

[https://launchpad.net/ubuntu/+ppas?name_filter=netflix](https://launchpad.net/ubuntu/+ppas?name_filter=netflix)

but:

[http://how-to.wikia.com/wiki/How_to_watch_Netflix_%28Watch_Instantly%29_in_Linux](http://how-to.wikia.com/wiki/How_to_watch_Netflix_%28Watch_Instantly%29_in_Linux)

---

### Post by cogadh on 2011-03-23
More to the point, as explained in one of those links, Netflix streaming on PCs uses Microsoft Silverlight and its DRM stack to deliver and protect the movies. Obviously that won't work on Linux. In the case of systems like the Roku that are Linux based, they are not using the same streaming method as is used on PCs and there is no Silverlight involvement. The closed nature of those devices is sufficient protection (in most cases).

---

### Post by tgm4883 on 2011-03-23
The linux based devices decode the stream via a hardware chip

---

### Post by Clessy on 2011-03-23
I dont get it. Mac OSX has silver light and mac osx is just a unix based system. Why cant there be silver light on ubuntu based off the mac osx port?

---

### Post by tgm4883 on 2011-03-23
> **Clessy said:**
> I dont get it. Mac OSX has silver light and mac osx is just a unix based system. Why cant there be silver light on ubuntu based off the mac osx port?

Closed source system which allows DRM vs open source system where DRM is impossible?

---

### Post by Simian Man on 2011-03-23
> **sylar petrelli said:**
> Sorry if this is the wrong forum, but how is possible that Netflix is available for TiVo, Wii, PS3, and Roku, which are all Linux based systems, but not available to your regular desktop system.

First off, Wii and PS3 are not Linux based systems.  Secondly, the reason NetFlix doesn't support Linux is that hardly anybody uses it, and there is a lot of work to port the streaming service both technologically and legally.  Of course it isn't impossible, just not worth it.

---

### Post by cogadh on 2011-03-23
> **Simian Man said:**
> First off, Wii and PS3 are not Linux based systems. 
The PS3 definitely is... sort of. The CellOS of the PS3 is FreeBSD based, so it's not really Linux, but it is a *nix system. I don't know for certain what the Wii uses for an OS.

It actually wouldn't take much work to "port" Netflix streaming to Linux, all it would take is Microsoft allowing the Mono project access to the Silverlight DRM stack so that it could be ported to Moonlight. Netflix doesn't actually have to do anything. Alternatively, it would be just as easy for Netflix to go back to the Flash-based streaming they used to use, which is already compatible with Linux.

---

