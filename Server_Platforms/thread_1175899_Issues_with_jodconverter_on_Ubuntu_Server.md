---
title: "Issues with jodconverter on Ubuntu Server"
date: 2009-06-01
forum: Server Platforms
---

### Post by jahservant on 2009-06-01
Greetings,
I have been beating my head against the wall trying to figure this out, and it's driving me nuts.

What I am trying to do:
I am trying to set up the jodconverter ([http://www.artofsolving.com/opensource/jodconverter](http://www.artofsolving.com/opensource/jodconverter)) to run on an Ubuntu Server box (i.e. run with the openoffice.org-headless package) so I can convert .odt and .doc documents to .pdf files.

The problem:
I tried downloading the jodconverter and running it, but I keep getting this:
```

me@myserver:~/$ java -jar jodconverter-2.2.2/lib/jodconverter-cli-2.2.2.jar -f pdf test.doc
Jun 1, 2009 11:21:51 AM com.artofsolving.jodconverter.openoffice.connection.AbstractOpenOfficeConnection connect
INFO: connected
Jun 1, 2009 11:21:52 AM com.artofsolving.jodconverter.openoffice.connection.AbstractOpenOfficeConnection disposing
INFO: disconnected
Exception in thread "main" com.artofsolving.jodconverter.openoffice.connection.OpenOfficeException: conversion failed: could not load input document
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadAndExport(OpenOfficeDocumentConverter.java:131)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.convertInternal(OpenOfficeDocumentConverter.java:120)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:104)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:74)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:70)
        at com.artofsolving.jodconverter.cli.ConvertDocument.convertOne(ConvertDocument.java:154)
        at com.artofsolving.jodconverter.cli.ConvertDocument.main(ConvertDocument.java:139)
Caused by: com.sun.star.lang.IllegalArgumentException: URL seems to be an unsupported one.
        at com.sun.star.lib.uno.environments.remote.Job.remoteUnoRequestRaisedException(Job.java:182)
        at com.sun.star.lib.uno.environments.remote.Job.execute(Job.java:148)
        at com.sun.star.lib.uno.environments.remote.JobQueue.enter(JobQueue.java:344)
        at com.sun.star.lib.uno.environments.remote.JobQueue.enter(JobQueue.java:313)
        at com.sun.star.lib.uno.environments.remote.JavaThreadPool.enter(JavaThreadPool.java:101)
        at com.sun.star.lib.uno.bridges.java_remote.java_remote_bridge.sendRequest(java_remote_bridge.java:652)
        at com.sun.star.lib.uno.bridges.java_remote.ProxyFactory$Handler.request(ProxyFactory.java:154)
        at com.sun.star.lib.uno.bridges.java_remote.ProxyFactory$Handler.invoke(ProxyFactory.java:136)
        at $Proxy5.loadComponentFromURL(Unknown Source)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadDocument(OpenOfficeDocumentConverter.java:150)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadAndExport(OpenOfficeDocumentConverter.java:127)
        ... 6 more

```

I can get the soffice service running just fine:
```

me@myserver~$ /usr/bin/soffice -headless -nologo -nofirststartwizard -accept="socket,host=127.0.0.1,port=8100;urp" & > /dev/null
...
...
me@myserver~$ netstat -nap | grep office
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               LISTEN      26044/soffice.bin
...

```


I've also tried using the PyODConverter ([http://www.artofsolving.com/opensource/pyodconverter](http://www.artofsolving.com/opensource/pyodconverter)) but it just gives me this:
```

me@myserver:~$ python DocumentConverter.py test.doc test.pdf
Traceback (most recent call last):
  File "DocumentConverter.py", line 143, in <module>
    converter.convert(argv[1], argv[2])
  File "DocumentConverter.py", line 75, in convert
    document = self.desktop.loadComponentFromURL(inputUrl, "_blank", 0, self._toProperties(Hidden=True))
__main__.IllegalArgumentException: URL seems to be an unsupported one.

```


I've also tried "unoconv" ([http://dag.wieers.com/home-made/unoconv/](http://dag.wieers.com/home-made/unoconv/)) which just gives me this:
```

me@myserver:~$ unoconv -v -f pdf test.doc
Input file: test.doc
unoconv: UnoException during conversion: URL seems to be an unsupported one.
The provided document cannot be converted to the desired format.

```


I apologize for the long post, but I just can't seem to figure out what's been going on.
I've updated *everything*: openofice.org, java, python, unoconv, even the OS (ubuntu server 8.x) -- everything to no avail.  I've browsed the web, and can't seem to find anything.
There are a couple of threads on this site, and I've tried everything on them but, again, to no avail:
[http://ubuntuforums.org/showthread.php?t=1151819&highlight=jodconverter](http://ubuntuforums.org/showthread.php?t=1151819&highlight=jodconverter)
[http://ubuntuforums.org/showthread.php?t=977327&highlight=jodconverter](http://ubuntuforums.org/showthread.php?t=977327&highlight=jodconverter)

Any ideas? Your help is greatly appreciated....

---

### Post by jahservant on 2009-06-02
*bump*

... anybody?

---

### Post by jahservant on 2009-06-02
I figured it out! 
I killed the soffice process, then start it again. 

Apparantly OOo started soffice twice and I was just never smart enough 
to try killing and restarting it....

---

### Post by michielu on 2010-10-19
I ran into the same problem as noted above. It turned out I had to install the openoffice-writer package.

---

### Post by mukherjee.siddhartha on 2011-04-07
its solved by

sudo apt-get install openoffice.org-writer

---

### Post by mukherjee.siddhartha on 2011-04-13
Also be sure to install latest openoffice..

---

