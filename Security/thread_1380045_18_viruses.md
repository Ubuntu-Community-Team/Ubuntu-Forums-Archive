---
title: "18 viruses??"
date: 2010-01-13
forum: Security
---

### Post by mdquince on 2010-01-13
I just ran clam av and it says I have 18 viruses. The name of the problem or virus found was call encrypted.zip all the file names start with /usr/lib.......
when I try to quarantine the problem or viruses this is what it says. does anyone have any idea what to do??

There was a problem quarantining /usr/lib/erlang/erts-5.7.2/bin/beam. Check your diskspace, the permissions on your quarantine location and whether a file with the same name already exists in the quarantine.

There was a problem quarantining /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam. Check your diskspace, the permissions on your quarantine location and whether a file with the same name already exists in the quarantine. 

There was a problem quarantining /usr/lib/libclamav.so.6.0.5. Check your diskspace, the permissions on your quarantine location and whether a file with the same name already exists in the quarantine.

---

### Post by bootdoc on 2010-01-13
I would try in terminal
sudo rm -r /usr/lib/erlang/erts-5.7.2/bin/beam
sudo rm -r /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam

be careful with the -r flag.  it removes everything in the target folder so don't hit the enter button until the path is complete.

The question how did a zip file end up there?

---

### Post by mdquince on 2010-01-13
I have not idea what they are.  I'm new to linux so you tell me.  I think has hacked into my computer again and planted that stuff there.  I have unknown files on my external hard drive as well

---

### Post by Perfect Storm on 2010-01-13
I wouldn't start deleting them. ClamAV is pretty known for false positives (as it scans for windows virus) and start deleting libs on your system, you'll bork it pretty nifty.

---

### Post by John Bean on 2010-01-13
The files are part of the erlang programming language which I guess you must have installed. The AV alerts are almost certainly false positives.

---

### Post by KarlIvan on 2010-01-13
i agree, having a zip file in your bin library seems a little odd...you should remove it

sudo rm -rf /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam

the r stands for recursive, which means it will recursively delete all files under that location. the f is for force, which means whether the os likes it or not, its gonna get deleted.

---

### Post by FuturePilot on 2010-01-13
> **KarlIvan said:**
> i agree, having a zip file in your bin library seems a little odd...you should remove it

sudo rm -rf /usr/lib/erlang/lib/erts-5.7.2/ebin/prim_zip.beam

the r stands for recursive, which means it will recursively delete all files under that location. the f is for force, which means whether the os likes it or not, its gonna get deleted.

That is not a zip file. It's a binary file that is part of a package. In fact, all of the files mentioned are part of packages. This is most definitely a false positive. Removing any of those will most likely bork your system.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=contents&keywords=prim_zip.beam]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=contents&keywords=prim_zip.beam")

---

### Post by KarlIvan on 2010-01-13
oo, i missed the .beam part, thought it was a zip file...sorry!

---

