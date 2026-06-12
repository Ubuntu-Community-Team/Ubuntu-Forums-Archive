---
title: "LV2 instruments not working, host suggestions?"
date: 2010-11-02
forum: Ubuntu Studio
---

### Post by Dangerouge on 2010-11-02
Howdy y'all, I have good news for you, I'm working on some synths right now, and some goodies on making them easily. However, I've encountered a pitfall: I can't test my synths, since I have no working LV2 host. I'm running 10.10 DT, which is updated from Lucid, so I lost my build of Ingen there (in which the LV2 didn't work in the first place), I've tried Zynjacku, but to no prevail, it just throws python errors at me:

```
Cannot lock down memory area (Cannot allocate memory)
Not sending deprecated LASH_Client_Name event
Loading LV2 plugin cache from "/home/jussi/.cache/zynjacku/plugins"
LV2_PATH not set, defaulting to ['/home/jussi/.lv2', '/usr/local/lib/lv2', '/usr/lib/lv2']
Traceback (most recent call last):
  File "/usr/bin/zynjacku", line 371, in <module>
    main()
  File "/usr/bin/zynjacku", line 362, in main
    host = ZynjackuHostMulti(program_data, client_name, sys.argv[1:], lash_client)
  File "/usr/bin/zynjacku", line 69, in __init__
    ZynjackuHost.__init__(self, client_name, "zynjacku", "synth stack", lash_client)
  File "/usr/bin/zynjacku", line 64, in __init__
    zynhost.host.__init__(self, zynjacku_c.Engine(), client_name, preset_extension, preset_name, lash_client)
  File "/usr/lib/pymodules/python2.6/zynworld/host.py", line 2209, in __init__
    self.lv2db = lv2.LV2DB(lv2sources)
  File "/usr/lib/pymodules/python2.6/zynworld/lv2.py", line 316, in __init__
    self.initManifests()
  File "/usr/lib/pymodules/python2.6/zynworld/lv2.py", line 359, in initManifests
    parseTTL(fn, file(fn).read(), self.manifests, self.debug)
  File "/usr/lib/pymodules/python2.6/zynworld/lv2.py", line 231, in parseTTL
    model.addTriple(spo[0], spo[1], spo[2], uri)
  File "/usr/lib/pymodules/python2.6/zynworld/lv2.py", line 143, in addTriple
    self.object_sources[o] = set((source,))
SyntaxError: Syntax error

```

Not being that much into python, that just looks like a whole lotta stuff I can't really do anything about, but if you have any suggestions, I'm open. (And no, that's not dirty talk)

So basically, are there any other lv2 hosts that I can easily (that's an optional, but preferable parameter) connect my midi keyboard to? Thank you.

Help me and I'll probably help you with some nice synths later on! ;) Meanwhile, if you have Firefox 4, you can check out my quick experiment on Mozilla Audio, [http://niiden.com/websynth/](http://niiden.com/websynth/) oh yeah, and that's kind of a secret, it's still a WIP.

---

### Post by genmi on 2011-05-26
Hey, you just need to set your LV2_PATH environment variable to point to where ever your LV2 Plugins are stored. For example, when I installed lv2core-4.0 the default path was created at usr/local/lib/lv2 so I did this:
```
export LV2_PATH=usr/local/lib/lv2
```
and it worked fine. Hope this helps!

---

