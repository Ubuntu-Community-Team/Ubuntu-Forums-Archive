---
title: "Ubuntuone-preferences python error"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by Neds Moar Salt on 2010-05-03
ubuntuone-preferences hangs just seconds after I open it due to this error:
```
Exception in thread Thread-4:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/ubuntuone-preferences", line 162, in do_rest_request
    callback(result)
  File "/usr/bin/ubuntuone-preferences", line 348, in parse_devices
    self.error(error)
  File "/usr/bin/ubuntuone-preferences", line 304, in error
    gtk.DIALOG_DESTROY_WITH_PARENT | gtk.MODAL,
AttributeError: 'module' object has no attribute 'MODAL'
```

I was just working earlier....

---

### Post by ABE3K on 2010-05-03
I'm having the same problem here

---

### Post by joshuahoover on 2010-05-03
> **Neds Moar Salt said:**
> ubuntuone-preferences hangs just seconds after I open it due to this error:
```
Exception in thread Thread-4:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/ubuntuone-preferences", line 162, in do_rest_request
    callback(result)
  File "/usr/bin/ubuntuone-preferences", line 348, in parse_devices
    self.error(error)
  File "/usr/bin/ubuntuone-preferences", line 304, in error
    gtk.DIALOG_DESTROY_WITH_PARENT | gtk.MODAL,
AttributeError: 'module' object has no attribute 'MODAL'
```I was just working earlier....

Sorry about this error. The good news is that you should see an update if you run Update Manager and check for new updates. This update should fix the problem. You may need to run the following command after installing the update (Applications->Accessories->Terminal): killall ubuntuone-login ubuntuone-syncdaemon ubuntuone-preferences

Thank you,

Joshua

---

