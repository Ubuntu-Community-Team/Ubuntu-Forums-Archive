---
title: "Where is it? equivalent for Linux (cataloguing cds etc.)"
date: 2006-01-23
forum: The Cafe
---

### Post by xequence on 2006-01-23
[QUOTE=prizrak]Nah I'd consider it a poor choice ;) 
I'd just write a Java program that has a nice interface and connects to a MySQL database ;) (or if I don't feel like dealing with a server to a local OO Base file).
In fact I have been working on one on and off for some time now ;)[/QUOTE]

Not everyone can program java =P

---

### Post by dolny on 2006-01-23
Is there a good application that will allow me to catalogue my music cds, movies  and books, and will allow me to mark the things I borrowed to somebody etc. ? 

Something like "Where is it?" for Windows.

Thanks in advance guys.

---

### Post by BSDFreak on 2006-01-23
[quote=dolny]Is there a good application that will allow me to catalogue my music cds, movies  and books, and will allow me to mark the things I borrowed to somebody etc. ? 

Something like "Where is it?" for Windows.

Thanks in advance guys.[/quote]

I would probably just make a database in MySQL but most people would consider that overkill. :D

[Kat seems to do what you want though]("http://linux.softpedia.com/get/Desktop-Environment/Tools/Kat-Desktop-Search-Engine-for-Linux-2138.shtml")

From the above link:

> Kat is an application for KDE designed to index files. Meta information, fulltext and thumbnails are extracted from documents, images, mp3 and other media allowing quick and accurate information retrieval.

Similar to the Windows application WhereIsIt, but also similar to Google Desktop Search, Kat is completely written in C++, using Qt3, KDE and KIO libraries.

---

### Post by prizrak on 2006-01-23
[QUOTE=BSDFreak]I would probably just make a database in MySQL but most people would consider that overkill. :D

[Kat seems to do what you want though]("http://linux.softpedia.com/get/Desktop-Environment/Tools/Kat-Desktop-Search-Engine-for-Linux-2138.shtml")

From the above link:[/QUOTE]
Nah I'd consider it a poor choice ;) 
I'd just write a Java program that has a nice interface and connects to a MySQL database ;) (or if I don't feel like dealing with a server to a local OO Base file).
In fact I have been working on one on and off for some time now ;)

---

### Post by 23meg on 2006-01-23
Just to let you know: "Where Is It?" works fine under Ubuntu with Wine.

---

### Post by maruchan on 2006-01-23
You might also be interested in this very long list of Linux cataloging software (somebody has been doing their homework at Linuxlinks!): 

[http://www.linuxlinks.com/Software/Home_and_Education/Cataloging/index.shtml](http://www.linuxlinks.com/Software/Home_and_Education/Cataloging/index.shtml)

---

### Post by 23meg on 2006-01-24
[Here]("http://www.gnomefiles.org/subcategory.php?sub_cat_id=140") is another list.

---

### Post by dolny on 2006-01-24
[http://www.mcatalog.net/](http://www.mcatalog.net/) - this looks cool, and Where is it gives me too much problems under Wine. Can somebody tell me how to compile mcatalog? I installed the XML Parser but it gives me an error with Mono.

```

<...>
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking pkg-config is at least version 0.9.0... yes
checking for MONO... configure: error: Package requirements (mono >= 1.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the MONO_CFLAGS and MONO_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

Sorry, I'm n00bish ;)
I have Mono installed.

---

### Post by dolny on 2006-01-24
*bump* :roll:

---

### Post by dolny on 2006-01-25
Em, help? :(

I would also be grateful for a deb package: [http://showdb.sourceforge.net/](http://showdb.sourceforge.net/) - I downloaded the cvs version but couldn't install it. Bah!

---

### Post by adamkane on 2006-03-23
I was able to install mcatalog in Breezy, but it wouldn't run. mcatalog needs the latest version of gecko-sharp2, which I installed from source. gecko-sharp2 probably will only be functional in Dapper.

---

