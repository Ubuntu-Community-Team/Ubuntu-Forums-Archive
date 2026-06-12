---
title: "wine &amp; quickpar &amp; nautilus"
date: 2009-06-02
forum: Wine
---

### Post by jonndoe45 on 2009-06-02
i am trying to get quickpar working with nautilis using nautilus actions & a shell script

i have sussed out that quickpar won't take the path+filename as a parameter it just doesn't like it 

but if you first change directory to the location of the par2 file it works

ps quickpar works fine with this version haven't tested creating a par set yet but checking, fixing works

here's the script

#!/bin/bash
gnome-terminal -x sh -c "cd $1;wine '/home/me/.wine/drive_c/Program Files/QuickPar/QuickPar.exe' $2;sh"

any help appreciated thanks

ubuntu jaunty
wine 1.1.22
quickpar 0.9.1

---

### Post by iuz on 2010-05-01
```
#!/usr/bin/python
import os;
import sys;

if len(sys.argv) != 2:
  print "Usage: " + sys.argv[0] + " <absolute-path>"
  sys.exit(-1);

os.system("cd \"" + os.path.split(sys.argv[1])[0] + "\"; wine ~/.wine/drive_c/Program\ Files/QuickPar/QuickPar.exe \"" + os.path.split(sys.argv[1])[1] + "\"");

```

This works for me. Save it to e.g ~/bin/quickpar and make it executable (e.g chmod 700), then make nautilus call this quickpar script (assuming ~/bin is in your $PATH of course).

---

### Post by lightenup on 2010-10-29
Perfect! Follow the instructions Iuz posted on creating the script file, for  an easy way to call the script in Nautilus, right click on a .par file, choose `Open With Other Application`, and then choose the quickpar script file.

---

