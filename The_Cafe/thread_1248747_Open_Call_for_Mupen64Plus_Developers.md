---
title: "Open Call for Mupen64Plus Developers"
date: 2009-08-24
forum: The Cafe
---

### Post by argor on 2009-08-24
[from  Richard42   ]("http://www.emutalk.net/showthread.php?t=49508")
> Developers, users, and fans:

After a great deal of work, late nights, and accompanying marital tension, I have finally finished the initial draft of the Mupen64Plus v2.0 API. It can be viewed on the developers' wiki:

[Mupen64Plus v2.0 Core API v1.0 - EmuWiki](http://www.emuwiki.com/index.php?title=Mupen64Plus_v2.0_Core_API_v1.0)

I'm pretty excited about this, because while the re-architectured emulator won't look a lot different from the user's perspective, there will be a lot of improvements "under the hood". The big high-level changes are in splitting the monolithic Mupen64Plus application into separate Core and GUI/Front-End parts, and going from a single integrated release to a bunch of smaller projects which can be independently developed and released. Some of the benefits of the new architecture are:

- Faster releases, more development
- simpler and less problem-prone installation and configuration on Unix
- inclusion in more Linux distributions
- simplified makefiles on Linux/OSX
- clean, native MSVC build for Win32
- better handling of log/debugging text output
- better error handling
- improved video plugins, based off of newer sources

Mostly I'm optimistic that the resulting Mupen64Plus projects will attract more developers and improve at a faster pace after the 2.0 release. Now comes the fun part, writing the code and implementing all of the changes.

So I would like to request help from anyone interested, willing, and qualified. There's lots of work to be done, and it starts with reviewing the API at the link above. Get on the IRC channel or drop us a line at the Mupen64Plus Google Group to voice your comments. I would particularly like to hear if anyone finds a current feature of the GUIs which can't be implemented with the new API, or any future features that might be added which would require an extension of the API.

While the API is under review, I'll be setting up new source code repositories hosted by Mercurial, a Python-based distributed source code control system. When the API review wraps up, we'll jump into the code. I plan to maintain ownership of the Core library and the new Console front-end and spend most of my time on these projects. I would to hear from developers who are able to contribute their effort on the following tasks:

1. Leadership of the GTK GUI front-end. If someone doesn't step up to fill this role, the GTK GUI may die and we will only have a Qt GUI.
2. Leadership of the plugins. I can manage the smaller plugins myself for a while, but the video plugins are big and complex. Anyone willing to take over development and releases of any plugins should contact me. I can provide SVN or Mercurial source code repositories, or you can host it yourself.
3. Windows developers. I would like to have good Win32 C developers who can help port and maintain the plugins. In particular the video plugins will take some effort to assimilate properly into Windows.
4. Porting plugins to the new architecture.
5. Front-end developers. Anyone willing to help out improving or porting the GTK or Qt Front-ends is welcome.

Anyone who's willing to step up, be a hero, and make a name for yourself in the N64 emulator world, now's your chance. The more developers we have, the quicker we'll get it done, so let's get started!

---

### Post by dragos240 on 2009-08-24
I love Mupen64Plus. But other than java, I don't know anything about programing.

---

### Post by HappinessNow on 2009-08-24
I'm too young when I am 64plus I will contact you. :lolflag:

---

### Post by dragos240 on 2009-08-24
> **&#20170 said:**
> I'm too young when I am 64plus I will contact you. :lolflag:
Are you? I don't see an age limit.

---

