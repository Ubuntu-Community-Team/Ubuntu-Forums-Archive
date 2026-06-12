---
title: "i now no longer use awk/gawk"
date: 2019-02-23
forum: The Cafe
---

### Post by Skaperen on 2019-02-23
i now no longer use awk/gawk for manipulation of data streams in shell pipelines.  i have created a small tool that makes it easy to use Python for such things.  below is the 3 line Python script to do it:

```
#!/usr/bin/env python3
import os,sys
if len(sys.argv)>1:os.execvp('/usr/bin/env',['env','python3','-c','\n'.join(sys.argv[1:])])
```

the big difficulty was that when using the -c option to put Python code in command line arguments, it was necessary to enter a raw newline character.  that is what so much of the interpreter logic expects to detect line boundaries.  this scripts takes multiple arguments and puts a newline character between them all and passes that on to Python3 as a single argument.  i call this "px" on my computer and have put it in /usr/local/bin/px.  don't forget to indent when entering Python code this way.

---

