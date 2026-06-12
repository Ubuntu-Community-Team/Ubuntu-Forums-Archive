---
title: "Is there any way to limit the memory a process can use?"
date: 2008-05-02
forum: Security
---

### Post by rivasdiaz on 2008-05-02
I need to limit the memory a process can use. I need it 'cause I need to access a web site that only works with IE so I have installed IE under wine, but in some occasions the wineserver takes all my memory and the whole system becomes irresponsible. So I need a way to say that I want wineserver to be under 512MB of RAM, and to get "out of memory" errors after that. I have found ulimit but it seems that it will limit the RAM for all the processes of a user, which I do not want. I want protection from a process, not from a user.

Is there any way I can achieve that? Can I limit "ulimit" work on some processes? Can I do what I need with other command?

Thanks in advance,
Rivas

---

### Post by movieman on 2008-05-02
I believe ulimit limits the usage of the shell and any process it starts. So if you create a shell script like:

#!/bin/bash
ulimit {whatever}
/usr/local/bin/my_program

and use that to start your program, I think it should work.

---

### Post by kung fu buntu on 2008-11-25
I'm really interested in this.

But how can you use it with X applications? Like iceweasel or opera... or worse, how can you do that with java?


I think this is a serious security flaw in Linux. The proof is that this already trashed my system several times... but I only realized the cause now :-|

---

