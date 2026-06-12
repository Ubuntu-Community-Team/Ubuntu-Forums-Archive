---
title: "a little help with a script please"
date: 2005-10-07
forum: Server Platforms
---

### Post by joepotter on 2005-10-07
How would you write a shell script to add a list of users (say 150) to the audio group or the plugdev group in Ubuntu?

I thought; 
adduser `cat list-of-users` pludev
would work but I an told that sending more than two user names to adduser is not allowed.

Anyone with a hint?

Thanks.

---

### Post by bdamon on 2005-10-07
[QUOTE=joepotter]How would you write a shell script to add a list of users (say 150) to the audio group or the plugdev group in Ubuntu?

I thought; 
adduser `cat list-of-users` pludev
would work but I an told that sending more than two user names to adduser is not allowed.

Anyone with a hint?

Thanks.[/QUOTE]

You could try something like 

#!/bin/bash
               for i in `cat list-of-users` ; do
                  adduser $i pludev
               done

---

### Post by joepotter on 2005-10-07
[QUOTE=bdamon]You could try something like 

#!/bin/bash
               for i in `cat list-of-users` ; do
                  adduser $i pludev
               done[/QUOTE]
Thanks, it has been a long time since I used the shell scripting. I am reading a book as as a refresher.

---

### Post by LordHunter317 on 2005-10-09
That's bad form.  You should never, ever use backticks on a potentially unbounded expression, as it risks environment overflows and crashes.  If you need to read from a text file and run commands, use an expression of this form:```
cat file | while read line ; do 
    # Commands, the line is in $line
done
```

---

