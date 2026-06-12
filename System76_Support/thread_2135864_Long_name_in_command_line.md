---
title: "Long name in command line"
date: 2013-04-15
forum: System76 Support
---

### Post by TomConnolly on 2013-04-15
In my terminal I am "thomas@thomas-Gazelle-Professional:~/

I just want it to be home/

How do I change it?

---

### Post by iponeverything on 2013-04-15
[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

---

### Post by TomConnolly on 2013-04-16
> **iponeverything said:**
> [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

Thank you. It didn't make a difference in my case, because I guess the link to "debian_chroot" is what controls the long bash name. I'll try to figure out how to edit that file.

---

### Post by TomConnolly on 2013-04-16
This isn't going to be as easy as I thought. Somehow the "@thomas-Gazelle-Professional" was added to my user id. I don't know where to make that change!

---

### Post by cool110 on 2013-04-16
You need to remove \h from the prompt. Remember that \u is your username \h is your hostname and \w is the current working directory.

---

### Post by Lars Noodén on 2013-04-16
To see what all those shortcuts mean, check the manual page for [bash](http://manpages.ubuntu.com/manpages/quantal/en/man1/bash.1.html) and scroll down to "PROMPTING"

```

man bash

```

Knowing what they do will help you edit the PS1 lines.

---

### Post by TomConnolly on 2013-04-25
> **Lars Noodén said:**
> To see what all those shortcuts mean, check the manual page for [bash]("http://manpages.ubuntu.com/manpages/quantal/en/man1/bash.1.html") and scroll down to "PROMPTING"

```

man bash

```

Knowing what they do will help you edit the PS1 lines.


Thanks, but that didn't help. I think I need to actually find my username and change it. Here's the appropriate line from my bashrc:

else
    #PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    PS1="[ ${debian_chroot:+($debian_chroot)} \u: \w ]\\$ "
    PS2="&gt; "

and here is my command line:

thomas@thomas-Gazelle-Professional:~$

I want it to be :

thomas:~$

---

### Post by Lars Noodén on 2013-04-26
Wouldn't that be something like this?  It leaves out the host name.

```

PS1='\u: \w \$ '

```

If you want to make the changes permanent then you'll have to edit .bashrc.  Be sure to make a backup copy first, before you start editing.

---

### Post by isantop on 2013-04-26
Specifically, you can make that change permanent by running:

```
PS1='\u: \w \$ '
cp ~/.bashrc ./bash-bak
echo "PS1='\u: \w \$ '" | tee -a ~/.bashrc
```

What you're trying to eliminate is the Hostname, which needs to be set to something. Changing the prompt is a much better way to do it.

---

