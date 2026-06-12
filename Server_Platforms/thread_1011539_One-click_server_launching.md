---
title: "One-click server launching"
date: 2008-12-14
forum: Server Platforms
---

### Post by Curlydave on 2008-12-14
I'm trying to create a desktop shortcut to my Ventrilo and TF2 server programs. I'll use Ventrilo as an example.

To run it, I have to type in console:
```
cd ventsrv
./ventrilo_srv
```

Nothing else will work. No doubleclicking on the program, no dragging the file into a terminal, no sh ventrilo_srv. I have to use those commands one after the other, as far as I've discovered.

I tried making a .bat file with those commands in it like above and running it, but nothing happens. How would I create a shortcut to run a server?

---

### Post by hictio on 2008-12-14
Sorry, but I don't follow... A .bat file? Are you on a Windows box? And you want to start that program for the Windows box?

If you want to create the equivalent of a .bat file on Linux, do this:

Create a text file like this, let's call it 'my.ventrilo.launcher.sh':
```

#!/bin/sh

cd /ADD/THE/FULL/PATH/HERE/ventsrv
./ventrilo_srv

# EoF #

```

And then make that file executable:

```

chmod +x my.ventrilo.launcher.sh (ENTER)

```

And then, you execute it like this:

```

sh /path/to/my.ventrilo.launcher.sh (ENTER)

```

Then you can add a launcher on your Desktop to the file 'my.ventrilo.launcher.sh', so double clicking would start it.

This shell script does not take into account if you need to pass an option to 'ventrilo_srv', like for instance, 'start', 'stop', etc, etc.

---

### Post by Curlydave on 2008-12-14
Thank you very much, that worked for both programs. The TF2 server does require a number of command line parameters, but they do work.

---

