---
title: "Streamlining Ubuntu Server (APT repos)"
date: 2014-03-03
forum: Server Platforms
---

### Post by head-desk on 2014-03-03
Hello

This is a quick question for those server bods. Trying to make a streamlined minimal install (other than just the minimal installer) and I noticed that when do minimal install that the universe and multiverse repos are enabled by default. Is it possible to remove these repos from APT without any negative impact?

Or is there something with the default minimal install that depends on these repos? The aim is to only have repo's that are supported by ubuntu enabled and have community repos disabled until they are really needed.

H-D

---

### Post by head-desk on 2014-03-03
Finally found what I was looking for. If anyone else was interested you can disable non-official repos

> [COLOR=#333333][FONT=Ubuntu]By default, the [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*Universe*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] and [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*Multiverse*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] repositories are enabled but if you would like to disable them edit [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/apt/sources.list[/FONT][/COLOR]

[https://help.ubuntu.com/12.04/serverguide/configuration.html](https://help.ubuntu.com/12.04/serverguide/configuration.html)

---

