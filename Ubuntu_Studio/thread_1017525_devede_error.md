---
title: "devede error"
date: 2008-12-21
forum: Ubuntu Studio
---

### Post by shadowfirebird on 2008-12-21
Ubuntu 8.04.

I get the following out on standard error when I click the "forward" or "preview" buttons on devede 3.11b:

```
Traceback (most recent call last):
  File "/usr/lib/devede/devede_newfiles.py", line 943, in on_preview_film_clicked
    converter=devede_convert.create_all(self.gladefile,tmp_structure,self.global
_vars,self.callback)
  File "/usr/lib/devede/devede_convert.py", line 160, in __init__
    self.iso_creator=global_vars["iso_creator"]
KeyError: 'iso_creator'
```

(This is not the Devede from the repositories, BTW, but the latest version.  The one in Synaptic also doesn't work for me, for different reasons.)

Has anyone seen this error?  Any ideas?

---

