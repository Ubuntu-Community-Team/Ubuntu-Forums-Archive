---
title: "command line shell: running quick python code"
date: 2019-03-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-03-13
i previously used awk as a tool to do some programmatic logic in a command line pipeline such as counting the number of times "foo" appears on a line and putting that count on the front of the line.  now, with the help of the python script below, i can use the python language in my command lines.  i named this command "px" to avoid issues mixing it up with python.  for example, i already use "py" as a short alias for python itself.  i will use the name "px" in this description.

"px" make each argument given to "px" act like one line of a python script by adding a newline at the end of each..  using the -c option of the python command expects each line to end with a raw newline character.  "px" adds those in so you don't have to (press ctrl-v ctrl-j at the end of each line).  "px" also supports configuring an option prefix file and suffix file to be included each time "px" is run.  the names fot these files is derived from to actual command name typed in so you can configure different aliases differently.  take the typed in command name and append it to ".".  then append "-pre.py" or "-suf.py" to come up with the name of the prefix file or suffix file for that command.  so, if you make an alias named "ep-ex" it will like for files named ".ep-ex-pre.py" and ".ep-ex-suf.py" and include them if they exist.  if they don't exist, built-in default strings are used, instead.  this makes it easy to import modules you regularly use, for example. 

px.py:```
#!/usr/bin/env python3
import os,sys
a='~/.'+(sys.argv[0].rsplit('/',1)[1])
n='\n'
try:
 f=open(os.path.expanduser(a+'-pre.py'))
 p=[x[:-1] for x in f]
 f.close()
except:
 p="""
import os
from subprocess import call,DEVNULL,PIPE,Popen,run
from sys import stderr,stdin,stdout,version_info
from time import sleep,time as secs
""".split(n)
try:
 f=open(os.path.expanduser(a+'-suf.py'))
 s=[x[:-1] for x in f]
 f.close()
except:
 s="""
print('DONE')
""".split(n)
c=n.join(p+sys.argv[1:]+s)
if len(sys.argv)>1:os.execvp('/usr/bin/env',['env','python3','-c',c])
```

---

