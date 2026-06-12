---
title: "What's the Difference Between #!/bin/bash and #/bin/bash ???"
date: 2006-10-13
forum: The Cafe
---

### Post by user1397 on 2006-10-13
does that exclamation point have to be there?

---

### Post by iovar on 2006-10-13
The # is just for commenting. When you add the ! you have a [shebang line]("http://en.wikipedia.org/wiki/Shebang_(Unix)")
which generally means, that if the file is made into an executable, 
that line will be executed first.

---

### Post by prizrak on 2006-10-13
The ! is scarier ;) But yeah what the dude above me said :)

---

### Post by user1397 on 2006-10-13
> **iovar said:**
> The # is just for commenting. When you add the ! you have a [shebang line]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29")
which generally means, that if the file is made into an executable, 
that line will be executed first.so if you dont have the !, what happens?

---

### Post by mostwanted on 2006-10-13
> **erik1397 said:**
> so if you dont have the !, what happens?

Nothing, it's just a comment.

---

### Post by skymt on 2006-10-13
> **mostwanted said:**
> Nothing, it's just a comment.

No, it isn't. The system needs a shebang line (#!/bin/bash) in order to know how to run the file. Without it, it wouldn't know whether it's Perl, Python, or Awk. It doesn't work without the #, either. And not just because of Bash, either. The system needs the #.

You don't need the shebang line if you run it as "bash myscript", but you need it if you want to just type "myscript".

EDIT: I just did a rather cool demo of this. Make a file, and put this in it:```
#!/usr/bin/gedit
This file will open in gEdit.
```Make it executable (chmod +x filename) and run it (./filename). It will open in gEdit.

---

### Post by mostwanted on 2006-10-13
> **skymt said:**
> No, it isn't. The system needs a shebang line (#!/bin/bash) in order to know how to run the file. Without it, it wouldn't know whether it's Perl, Python, or Awk. It doesn't work without the #, either. And not just because of Bash, either. The system needs the #.

He was asking whether something would happen if the ! was missing to which I would replied "nothing happens" because then it would just be a comment and not an execution path. I don't really know where you're going at with this long reply...

---

### Post by user1397 on 2006-10-13
i see...then how come aysiu's songbird script does not include it?

[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

---

### Post by meng on 2006-10-13
Hey that's a real good question! From what I *thought* I knew, that shouldn't work, unless one specifically runs
sh songbird.sh
but maybe someone can confirm if it runs as-is?

---

### Post by skymt on 2006-10-13
> **mostwanted said:**
> He was asking whether something would happen if the ! was missing to which I would replied "nothing happens" because then it would just be a comment and not an execution path. I don't really know where you're going at with this long reply...

I misunderstood his post. I thought he was asking what would happen if you left out the whole ! line. I was trying to clarify. Sorry. :oops: 

But you have to admit, the gEdit thing is kind of cool. ;)

---

### Post by givré on 2006-10-13
It's an error.
#/bin/bash will be take as a comment, and you can put #/bin/what_the_hell or what you want it will change nothing.
If the script is executed, it's because you launch it from an interactive shell, and so the script will be executed as a shell script.
Removing it will also have the same effect. 
But if you execute it from an external program, it will not work. That's why you need to shebang to #!/bin/sh or #!/bin/bash at the beginning of a shell script.
#/bin/bash means nothing.

---

### Post by asimon on 2006-10-13
> **meng said:**
> Hey that's a real good question! From what I *thought* I knew, that shouldn't work, unless one specifically runs
sh songbird.sh
but maybe someone can confirm if it runs as-is?
Yes, it works without the shebang too.
From bash's manual:
> 
When a normal program is executed, the shell runs the program, passing the arguments and the environment to the program.  If the program is not a normal executable file (i.e., if it does not begin with the "magic number" whose ASCII representation is "#!", so execve(2) returns ENOEXEC then) the shell will interpret the program in a subshell.
Thus bash will interpret the songbird.sh without a shebang a bash script. Other shells may do other things.

---

### Post by meng on 2006-10-13
Thanks for clarifying! This is what I love about the community.

---

### Post by user1397 on 2006-10-13
why go thru that trouble? (well its not rally trouble, but..)
i mean, why would you ever want to write #/bin/bash instead of #!/bin/bash?  does not having the ! really have a purpose at all?

---

### Post by givré on 2006-10-14
It's just a mistake, #/bin/bash don't have a purpose at all.

---

### Post by user1397 on 2006-10-14
> **givré said:**
> It's just a mistake, #/bin/bash don't have a purpose at all.ah, ok, thanks for all the knowledge

---

