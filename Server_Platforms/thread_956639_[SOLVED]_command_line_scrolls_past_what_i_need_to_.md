---
title: "[SOLVED] command line scrolls past what i need to read"
date: 2008-10-23
forum: Server Platforms
---

### Post by adept_king on 2008-10-23
Im using Ubuntu Server.

There is only a command line, of course, but sometimes the screen shoots by without a pause.  is there a way to make the screen pause at every full screen of text?  a toggle for this?

lets say i do ls --help and want to read the full entry instead of just the end.

by the way,
Ubuntu Server is beating the utter crap out of me.

---

### Post by Krupski on 2008-10-23
> **adept_king said:**
> Im using Ubuntu Server.

There is only a command line, of course, but sometimes the screen shoots by without a pause.  is there a way to make the screen pause at every full screen of text?  a toggle for this?

lets say i do ls --help and want to read the full entry instead of just the end.

by the way,
Ubuntu Server is beating the utter crap out of me.

Use the "more" command. You can take the output of anything and pipe it through "more" - it will display one page at a time.

Examples:

```

ls -laF /home/big-directory | more

cat huge-document | more

command --help | more

```


Hope this helps.

-- Roger

---

### Post by sisco311 on 2008-10-23
sometimes less is more ;)

```
ls --help | less
```

---

### Post by koenn on 2008-10-23
+1 for less
it allows you to scroll up and down the text

---

### Post by adept_king on 2008-10-23
thanks folks!

now to the next mystery...

---

### Post by sisco311 on 2008-10-23
You're welcome!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by lykwydchykyn on 2008-10-23
Sometimes, you need the most:
```

sudo aptitude install most
ls --help |most

```

---

### Post by Krupski on 2008-10-23
> **lykwydchykyn said:**
> Sometimes, you need the most:
```

sudo aptitude install most
ls --help |most

```

More... less... most...least...


How about "ls | maybe"?

:)

---

### Post by lykwydchykyn on 2008-10-24
> **Krupski said:**
> More... less... most...least...


How about "ls | maybe"?

:)

Heh... here you go.  Just pop this into a file called "maybe", make it executable, and drop it into /usr/local/bin:

```

#!/bin/bash

DOIT=$(($RANDOM%2))
read input
if [ 0  -eq $DOIT ] ; then
echo $input
else
   echo "meh, not this time..."
fi

```

---

### Post by DGortze380 on 2008-10-24
> **lykwydchykyn said:**
> Heh... here you go.  Just pop this into a file called "maybe", make it executable, and drop it into /usr/local/bin:

```

#!/bin/bash

DOIT=$(($RANDOM%2))
read input
if [ 0  -eq $DOIT ] ; then
echo $input
else
   echo "meh, not this time..."
fi

```

:lolflag:

---

### Post by hyper_ch on 2008-10-24
you could also

(a) output the text into a file
```

COMMAND > output.txt

```

or

(b) run a "screen" sessions and scroll back with ctrl-a + ESC

---

