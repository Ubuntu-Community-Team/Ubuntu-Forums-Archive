---
title: "print multiple files in specified order"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by jlillywh on 2009-05-18
I have successfully printed multiple files by doing lp file1.txt file2.txt ...etc -d PrinterName

from the command line.

Is there a way to specify an order, say alphabetic?

Thank you.

---

### Post by raboofje on 2009-05-18
(deleted)

---

### Post by unutbu on 2009-05-18
If you put the names of the files in a file called files_to_print, then you could use this command:

```
sort files_to_print | while read file; do lp "$file" -d PrinterName; done
```

Example contents of files_to_print:

```
cfile1.txt
bfile2.txt
afile.txt

```

---

### Post by raboofje on 2009-05-18
Unfortunately, as you can see for example [here](http://www.unix.com/unix-advanced-expert-users/12990-lp-order-files-printed.html), the lp print spool is not guaranteed to handle the print jobs in FIFO order: it will commonly print the small jobs first, for example.

Are these txt's really text files? If they are, you could try catting them together into one long text file with form-feed characters in between them:

 for i in file1.txt file2.txt ; do cat $i ; echo -e \\f ; done > all.txt
 lp all.txt

(or in one go: for i in file1.txt file2.txt ; do cat $i ; echo -e \\f ; done | lpr)

---

### Post by jlillywh on 2009-05-18
Thanks! I was showing txt files as an example only. My question is more general. I would like to print batch for pdfs, CAD, docs, etc.

---

### Post by unutbu on 2009-05-18
raboofje, thanks for clarifying the problem -- I completely misunderstood.

---

### Post by unutbu on 2009-05-18
jlillywh, here is a script which issues "lp" commands and monitors "lpq" to see when each file is done printing.

Save this to ~/bin/mylp
[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT
from time import sleep
import sys

lof=sys.args[1:]

for filename in lof:
    print('printing %s'%filename)
    proc=Popen('lp %s -d PrinterName', shell=True, stdout=PIPE, )
    output=proc.communicate()[0]
    done=False
    while not done:
        proc=Popen('lpq', shell=True, stdout=PIPE, )
        output=proc.communicate()[0].split('\n')
        jobs=[]
        for line in output:
            if line.startswith('active'):
                jobs.append(line.split()[3])
        if filename not in jobs:
            done=True
        sleep(1)
[/PHP]
Edit line 10 of the file, changing "-d Printername" to whatever the correct printer name is.

Make it executable:
```

chmod 755 ~/bin/mylp
```

Run it like this:
```

mylp file1.doc file2.pdf file3.txt
```

---

### Post by raboofje on 2009-05-19
Cool approach!

---

