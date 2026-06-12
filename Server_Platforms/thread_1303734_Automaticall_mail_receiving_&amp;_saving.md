---
title: "Automaticall mail receiving &amp; saving"
date: 2009-10-28
forum: Server Platforms
---

### Post by alkamid on 2009-10-28
What I need:

1. A mail client (preferably console app) that checks and downloads my mail every x seconds
2. A script (or a built-in function) that will save every mail in a specified folder in a .txt format.

Is it possible?

---

### Post by elvinatom on 2009-10-28
yes

---

### Post by alkamid on 2009-10-29
Could you give me any advice on how to achieve it? If the answer is yes, please do so.

---

### Post by elvinatom on 2009-10-29
I was afraid you were going to say that.  If I had the answer I would have written it in my last post already.  Here is the general idea:
find a cli email client; one that works like this:

```
you@yourbox$cliemailclient

from: abc@a.com
subject: hi there
body:
this is just a demo

you@yourbox$
```
you can then redirect the output to a textfile like this:
```
you@yourbox$cliemailclient > /home/you/Desktop/email.txt
you@yourbox$
```

once that works you write a bash script that adds the time stamp to the file:

```
#!/bin/bash
timestamp=`date -d now "+%Y.%m.%d"`
emailfile="/home/you/Desktop/email_$timestamp"
cliemailclient > $emailfile
```
When that script works you put it into '/usr/scripts' or wherever else you might want it to reside and add it to cron at 10min intervals.

That's basically what I would try.

---

