---
title: "how to automatically launch a script when a new file is placed in a folder"
date: 2010-01-31
forum: Server Platforms
---

### Post by alikthename on 2010-01-31
I want to run a setfacl command automatically when a new file is placed in a certain directory (to set a certain acl for this file).  the aim is to have same acl's for all the files in this directory.
I think it sould be possible, but I do not know the techniques of scripting very well and so I do not know to which event I could attach this run action.

If somebody could point me towards a right way I'd be very thankfull.

---

### Post by falconindy on 2010-01-31
inotifywait is well suited to this job. Something like...

```
#!/bin/sh

watchdir=/path/to/watch

inotifywait -qm -e CREATE --format %f | while read file; do
  # run setfacl here. you'll need to reference
  # the full path of the file as "$watchdir/$file".
done
```

---

### Post by koenn on 2010-01-31
there are some tools that could help you do this. They're mentioned here : [http://aplawrence.com/Unixart/watchdir.html](http://aplawrence.com/Unixart/watchdir.html)

but probably you should set the acl of the directory so that new files in it inherit an appropriate acl from it.

---

### Post by alikthename on 2010-01-31
Thank you guys very much. Tomorrow I'll try to implement that.

> **koenn said:**
> 

but probably you should set the acl of the directory so that new files in it inherit an appropriate acl from it.

Yes, setting a default acl's on a folder makes all new files created in this directory inherit those acl's. But when the file is copied from another place acl's of a destination folder are not applied to the file.

---

