---
title: "Squid version in Repository too old (2.6.1 -&gt; need 2.6.9)... help?"
date: 2007-02-22
forum: Server Platforms
---

### Post by evilspoons on 2007-02-22
Hello everyone. I've got an Ubuntu Server box up and running as my home network router and Squid caching proxy server. The only problem is I'm running into Squid Bug #1650: transparent interception "Unable to forward this request at this time", which was fixed back in 2.6.2 (which was released July 31 2006). They're currently up to version 2.6.9!

Does anyone know of an alternate source with a repository that has a newer version of Squid, or simply a .deb file somewhere? I suppose the next alternative is compiling Squid from source, but I'm worried that this will make a disaster out of my system with all sorts of files being thrown everywhere that cannot be easily removed if I decide I no longer need Squid or if I'm upgrading it.

Thanks in advance for any help.

---

### Post by jtc on 2007-02-22
Well, I'm not sure about the deb-files, but I can give you a little advice when it comes to compiling.

If you add the "--prefix=" flag towards ./configure you can tell make where to install its files. That way you can have everything in one specific directory, which you then easily can remove.

```
./configure --prefix=/usr/local/squid-2.6.9
```

Usually there are a whole bunch of options you can pass along.

```
./configure --help
```

---

