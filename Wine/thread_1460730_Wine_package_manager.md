---
title: "Wine package manager"
date: 2010-04-23
forum: Wine
---

### Post by afrodeity on 2010-04-23
I'm having trouble getting wine-doors to set-up and wondering if there was any alternative? I know there are quite a few "windows package managers" but none seem tailored to wine like wine-doors.

It is a great pity but appears that the wine-doors project is dormant for at least a year now. Here is bug I am experiencing on karmic

```

Installing Application: autohotkey
Error: Installation failed: Installing Application: autohotkey returned 32256
Installing Application: winegecko
Error: Unable to extract "winegecko"
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/queue.py", line 161, in Execute
    app_pack = ApplicationPack( INSTALL, pack, version, repo )
  File "/usr/share/wine-doors/src/application.py", line 185, in __init__
    self.InstallApplication()
  File "/usr/share/wine-doors/src/application.py", line 314, in InstallApplication
    self.Parse()
  File "/usr/share/wine-doors/src/application.py", line 205, in Parse
    parser.parse( self.app_pack_xml )
  File "/usr/lib/python2.6/xml/sax/expatreader.py", line 102, in parse
    source = saxutils.prepare_input_source(source)
  File "/usr/lib/python2.6/xml/sax/saxutils.py", line 298, in prepare_input_source
    f = urllib.urlopen(source.getSystemId())
  File "/usr/lib/python2.6/urllib.py", line 87, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.6/urllib.py", line 206, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.6/urllib.py", line 468, in open_file
    return self.open_local_file(url)
  File "/usr/lib/python2.6/urllib.py", line 482, in open_local_file
    raise IOError(e.errno, e.strerror, e.filename)
IOError: [Errno 2] No such file or directory: '/home/afrodeity/.wine-doors/apppacks/winegecko-0.9.0/pack.xml'
```

---

### Post by cogadh on 2010-04-23
Its been a while since I messed with Wine-Doors, but I believe that error is caused by not having the cabextract package installed.

As for alternatives to Wine-Doors, the best ones are listed on Wine's website:
[http://wiki.winehq.org/ThirdPartyApplications](http://wiki.winehq.org/ThirdPartyApplications)

---

### Post by afrodeity on 2010-04-24
synaptic says cabextract is installed on my system.

UPDATE: I removed .wine and reinstalled cabextract

Now I get this error:
```
Executing queue
Installing Application: arial
Warning: MD5 sum not found
Installing Application: arial_bold
Warning: MD5 sum not found
Installing Application: comicsans
Warning: MD5 sum not found
Installing Application: courier_new
Warning: MD5 sum not found
Installing Application: times_new_roman
Warning: MD5 sum not found
Installing Application: webdings
Warning: MD5 sum not found
Installing Application: autohotkey
Error: Installation failed: Installing Application: autohotkey returned 32256
Installing Application: winegecko
Error: Unable to download file: http://www.wine-doors.org/repositories/base.repo/winegecko-0.9.0.wdi
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/queue.py", line 162, in Execute
    if app_pack.status:
AttributeError: ApplicationPack instance has no attribute 'status'

```

---

### Post by cogadh on 2010-04-24
If I had to guess, it looks like the Wine-Doors servers are down (again).

---

### Post by afrodeity on 2010-04-25
oh dear. sigh.

---

