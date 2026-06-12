---
title: "Cannot execute binary file?"
date: 2017-01-08
forum: Ubuntu Application Development
---

### Post by littlepebble on 2017-01-08
I written a program successfully in code blocks and even ran it by clicking compile and run. I then went into compiling it with gcc. Again successful. Then when I went to run it in the terminal it said,  "cannot execute binary file." At first I thought I had a bug in my program that I did not show up in Code Blocks. 
.
Then I got the bright idea to try my other programs that I knew ran because I ran them before. To my surprise it said the exact same thing for all of them even "Hello world."           

```
 bash: .: hello: cannot execute binary file 
```

Here is the exact code
```

#include <stdio.h>
int main()
{
    printf("Hello world \n");
    return (0);
}

```

---

### Post by steeldriver on 2017-01-08
How exactly are you trying to run them? don't explicitly use `bash` to run **binary **executables, just call them by name and path e.g.

```

./hello

```

Based on the error, it looks like you're trying to use `bash hello`

---

### Post by littlepebble on 2017-01-08
Oh I had my forward slash and backslash mixed up.:shock: 

Thanks I really appreciate it

---

