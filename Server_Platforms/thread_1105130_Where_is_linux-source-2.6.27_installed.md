---
title: "Where is linux-source-2.6.27 installed?"
date: 2009-03-24
forum: Server Platforms
---

### Post by supercell on 2009-03-24
I just performed an apt-get install linux-source-2.6.27 (intrepid [8.10 server]) and it successfully installed the source. When performing a "find" nothing is found other than /usr/share/doc/linux-source-2.6.27. Do I have to reboot? If that is not the solution, where are the source files installed?

Thank you in advance,

supercell

---

### Post by Bachstelze on 2009-03-24
As you can see for example [here]("http://packages.ubuntu.com/intrepid/all/linux-source-2.6.27/filelist"), the [font="monospace"]linux-source-*[/font] packages only install a tarball of the sources in [font="monospace"]/usr/src[/font]. To actually use the sources, you must decompress them:

```
cd /usr/src
sudo tar xjvf linux-source-2.6.27.tar.bz2

```

---

### Post by supercell on 2009-03-24
Thank you!

---

