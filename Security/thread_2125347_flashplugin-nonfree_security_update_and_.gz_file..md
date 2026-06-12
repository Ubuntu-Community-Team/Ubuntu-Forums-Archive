---
title: "flashplugin-nonfree security update and *.gz file."
date: 2013-03-13
forum: Security
---

### Post by kleenex on 2013-03-13
Hi, today during flashplugin security update, I've noticed that at the very end of the updating process, flash was installed from a "strange" local file.

```
(...)
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.275.orig.tar.gz
**Installing from local file /tmp/tmpHwGR0I.gz**
Flash Plugin installed.
```

Generaly I wonder why there is [COLOR=#008000]/tmp/tmpHwGR0I.gz[/COLOR] file. I don't remember, if flash was always installed from such file. Can anyone confirm this? For me, it is a pretty strange, because I never put my attention on this.

---

### Post by Bashing-om on 2013-03-13
kleenex; Hi !

I am not at all sure as to what is going on presently with flashplugin. I get this:
> Failed to fetch [URL="http://ftp.utexas.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.275ubuntu0.12.04.1_amd64.deb"]http://ftp.utexas.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-

installer_11.2.202.275ubuntu0.12.04.1_amd64.deb[/URL]  404  Not Found
maybe a temporary problem with the file upload to the mirror ?

I am going to wait and see what develops, as I can find no fault in my sources.list file.[INDENT=3]my thoughts on the matter

[/INDENT]

---

### Post by cariboo on 2013-03-14
The Canonical server hosting the flash plugin package seems to be having a few problems of late, installing the plugin has been hit or miss for several people. The plugin, has always been in tar.gz format, even when it was hosted by Adobe.

---

### Post by vasa1 on 2013-03-14
> **cariboo907 said:**
> The Canonical server hosting the flash plugin package seems to be having a few problems of late, installing the plugin has been hit or miss for several people. The plugin, has always been in tar.gz format, even when it was hosted by Adobe.

Yes, there was this thread at the time of the last update: [http://ubuntuforums.org/showthread.php?t=2120625&p=12534637#post12534637](http://ubuntuforums.org/showthread.php?t=2120625&p=12534637#post12534637)

Anyway, I got mine uneventfully:

---

### Post by Soul-Sing on 2013-03-14
Perfectly normal in tar gz, extremely slow download. 5 minutes...

---

### Post by kleenex on 2013-03-14
Hi all. So, [COLOR=#008000]/tmp/tmpHwGR0I.gz[/COLOR] file is absolutely normal and everything is fine?

---

### Post by Soul-Sing on 2013-03-14
yes the source is/was ok
no, it took a very long time to download/install
yes/no the destination is somewhat 'strange' imo.

---

### Post by Bashing-om on 2013-03-14
All; 
I just updated flash-installer. No problems this time. 12.04 ubuntu AMD64 //

---

