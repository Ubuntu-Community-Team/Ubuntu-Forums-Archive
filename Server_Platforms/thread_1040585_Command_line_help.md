---
title: "Command line help"
date: 2009-01-15
forum: Server Platforms
---

### Post by stonneway on 2009-01-15
Hi chaps. 

I have a whole stack (about 200) of folders whose names are of the format 

ANNNN.AAA

Where N is a numerical number like 80001 through to 99999. 

I need to rename them to this format

ANNNN.BBB.AAA

That is to say to keep the same numerical range, with the same extension, but with a new string inserted between the filename and the extension.

At the moment, I'm doing it by hand which is a chore. Can anyone think of an easy command line which will rename them all at once, or at least rename them in blocks ?

Olly

---

### Post by xplode on 2009-01-15
> **stonneway said:**
> Hi chaps. 

I have a whole stack (about 200) of folders whose names are of the format 

ANNNN.AAA

Where N is a numerical number like 80001 through to 99999. 

I need to rename them to this format

ANNNN.BBB.AAA

That is to say to keep the same numerical range, with the same extension, but with a new string inserted between the filename and the extension.

At the moment, I'm doing it by hand which is a chore. Can anyone think of an easy command line which will rename them all at once, or at least rename them in blocks ?

Olly

for stuff like this i like to write commandlines that produce commandlines, because it gives you a chance to review what you're about to do. so, for your example:

```

ls A?????.AAA | awk -F'.' '{print "mv",$0,$1".BBB."$2}'

```

that will produce some output on your terminal, one line per file. check it and then when you are happy with the output (beware of spaces in filenames for example - but you don't have any) just add a **| /bin/bash** at the end to run it.

```

ls A?????.AAA | awk -F'.' '{print "mv",$0,$1".BBB."$2}' | /bin/bash

```

or run a test of 10 files first

```

ls A?????.AAA | awk -F'.' '{print "mv",$0,$1".BBB."$2}' | head -10 | /bin/bash

```

etc.

another possibly more straightforward solution:

```

ls A?????.AAA | while read f; do mv "$f" "${f/AAA/BBB.AAA}"; done

```

but not as testable - although i guess if you switch **mv** for **echo** you'd get an idea as to what you're about to do.

hope that helps. (btw, not sure if you had 4 digits or 5, i assumed 5 here.)

---

### Post by hyper_ch on 2009-01-16
midnight commander has a mass rename file tool integrated :)

---

### Post by stonneway on 2009-01-16
Wow Xplode. That's certainly a comprehensive answer. Thanks very much :)

---

### Post by gtdaqua on 2009-01-16
[mmv]("http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/mass-rename.html") is another tool for mass renames. It Supports several options/wildcards.

---

