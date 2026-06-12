---
title: "tcsh and commands"
date: 2011-02-07
forum: Server Platforms
---

### Post by cormu7 on 2011-02-07
Hello,

I just recently installed Ubuntu for our server, and I had a question about using tcsh.

I'm trying to run a script of commands and the first line of my script is:

> #! /bin/tcsh -fI chmod +x my script, but when I type the name of my script at the command line i get this message:

> myscript: Command not found.  the only way my script will work is if I type:

> tcsh myscriptOnly then, will myscript execute its set of commands.

I would like to be able to type the name of scripts without having to type tcsh at the beginning, each time. Is there a way to do that?

Your help would greatly be appreciated.

Thanks,

Cor

---

### Post by CharlesA on 2011-02-07
The script would have to be in the path.

Instead of running:
```
tcsh myscript
```

You can just run this if you are in the same directory as the script:

```
./myscript
```

---

### Post by cormu7 on 2011-02-07
that is right, i discovered the ./myscript trick just recently. I forgot to mention that in my post.

i am a recent convert to ubuntu.

i have used redhat in the past, and used simiarl shell scripts via tcsh. but i don't recall ever having to always type "./" before the name of myscript to execute it.

should i set up something in my .cshrc file to to get around this? 

thanks,

cor

---

### Post by CharlesA on 2011-02-07
The . just means to look in the current directory.

Unless the place where your scripts are stored is in the $PATH variable, then you have to use the full path to execute them.

---

### Post by cormu7 on 2011-02-07
Charles,

Thanks for the reply. I set up a path in my .cshrc file where I will store my scripts, and that did the trick.

Thanks again,

cor

---

### Post by CharlesA on 2011-02-07
Glad you got it working. Don't forget to mark the thread as solved from thread tools at the top. :)

---

