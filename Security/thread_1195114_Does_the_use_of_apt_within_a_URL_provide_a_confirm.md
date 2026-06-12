---
title: "Does the use of apt within a URL provide a confirmation?"
date: 2009-06-23
forum: Security
---

### Post by risingsun on 2009-06-23
Hi,

I realise it's a simple question but I don't particuarly want to test how an apt url link functions without knowing what will happen. 

For example [https://help.ubuntu.com/9.04/musicvideophotos/C/music-extract.html](https://help.ubuntu.com/9.04/musicvideophotos/C/music-extract.html) has such a link for gstreamer which I almost clicked on (thinking it would be to a page with info about gstreamer), but I was concerned at the prospect that if I accidently clicked a link and happened to use sudo somewhere in the environment at the time it might be able to simply install (given that synaptic seems to remember the use of sudo for some time.) 

Will Firefox3 (which I'm currently using) always provide a confirmation of some sort and/or will it always require a sudo password regardless of whether I've used it in synaptic or elsewhere in the environment?

Additionaly I assume I'm at least relatively safe in that these sorts of commands can only access files from enabled repositories only?

Many thanks :)

Edit: On further investigation I found the ubuntu help on this topic, but I noted that by default network.protocol-handler.warn-external.apt and network.protocol-handler.warn-external.apt+http are set to the value false where the help says they should be set to true. Would this disable the confirmation prompt or does it relate to something else?

---

### Post by Agent ME on 2009-06-23
I just tested by trying an apt: url to a package I didn't have, and yes, it does ask for confirmation. It even lets you view the package description in the same window.

---

