---
title: "What are repositories?"
date: 2004-10-31
forum: Repositories &amp; Backports
---

### Post by moon2js on 2004-10-31
Can anyone point me in the direction on some materials Ubuntu/Debian repositories for packages?

I'm a relative newbie to Linux and a "this weekend" newbie to Debian, so I'm not particularly familiar with the differences between repositories in sources.list. For example, what's the difference between universe and multiverse? Main and restricted? How can I use sources (deb-src) in this process? Can I mix repositories/packages from warty with hoary or even real Debian?

That sort of thing. I'm sorry if this has been asked to death or is clearly explained somewhere because I can't quite find the answers.

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=moon2js]Can anyone point me in the direction on some materials Ubuntu/Debian repositories for packages?

I'm a relative newbie to Linux and a "this weekend" newbie to Debian, so I'm not particularly familiar with the differences between repositories in sources.list. For example, what's the difference between universe and multiverse? Main and restricted? How can I use sources (deb-src) in this process? Can I mix repositories/packages from warty with hoary or even real Debian?

That sort of thing. I'm sorry if this has been asked to death or is clearly explained somewhere because I can't quite find the answers.[/QUOTE]


Repo's or Repositories are simply *dumps* for Ubuntu's packages.  Its a huge storage system for Ubuntu's packages that programs goto to retrieve files being asked for.  

EX: apt-get / synaptic

---

### Post by kamstrup on 2004-11-01
You can read more about this on the Ubuntu homepage: [http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

You can enable the multiverse from within the Synaptics package manager.

If you are a Linux noob, I would wait a few months before enabling the Hoary repository ;P

---

### Post by moon2js on 2004-11-01
Thanks for that link. That's the document I was looking for.

So, what's multiverse exactly and how does it differ from universe?

---

### Post by Faramirtook on 2004-11-01
[QUOTE=moon2js]Thanks for that link. That's the document I was looking for.

So, what's multiverse exactly and how does it differ from universe?[/QUOTE]
 [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.1228090247](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.1228090247)

---

### Post by jdong on 2004-11-01
[QUOTE=moon2js]Thanks for that link. That's the document I was looking for.

So, what's multiverse exactly and how does it differ from universe?[/QUOTE]
 Universe are packages that were robot-built and largely untested for Ubuntu (i.e. no strict security updates, no guarantee that things work out-of-the-box, etc)

Multiverse is universe, plus their licenses are restrictive in some way (non-"free")

Restricted are restrictively-licensed packages but with Ubuntu support. Examples include Nvidia 3d drivers.

---

### Post by Vlammend on 2004-12-07
The question now however is:
How to get the multiverse repositories. Universe was easy, even I could do it, but for multiverse I do not have a clue.

please help!

okay already got it: :-)
Choose "new" in the package manager of Synaptic. Copy URL, distribution from the universe repository and type multiverse in the last line.

still no flashplugin-nonfree though :S

---

### Post by poofyhairguy on 2004-12-08
[QUOTE=Vlammend]The question now however is:
How to get the multiverse repositories. Universe was easy, even I could do it, but for multiverse I do not have a clue.

please help!

okay already got it: :-)
Choose "new" in the package manager of Synaptic. Copy URL, distribution from the universe repository and type multiverse in the last line.

still no flashplugin-nonfree though :S[/QUOTE]

[http://ubuntuguide.org](http://ubuntuguide.org) 

Use this guide to add 3rd party repos to get things like that.

---

