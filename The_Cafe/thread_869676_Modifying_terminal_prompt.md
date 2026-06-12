---
title: "Modifying terminal prompt"
date: 2008-07-25
forum: The Cafe
---

### Post by kvk on 2008-07-25
Where is the syntax for the terminal prompt stored? If I wanted to go play with toys and have the normal user prompt, instead of "user@host:", be instead "Speak to me!" or somesuch, or change the root prompt to something fun like "What is thy bidding, my Master?", is there a file I could modify? Or is that so deep in the kernel it's really untouchable?

---

### Post by Bachstelze on 2008-07-25
export PS1="foo: "

Put in .bash_profile to have it set automatically.

---

### Post by kvk on 2008-07-25
Thanks so much!! :)

What does the "export PS1="foo:" accomplish?

---

### Post by LaRoza on 2008-07-25
foo was just a place holder. The code for it can be a bit confusing.

This is my custom prompt (guess what is looks like...). Using "export PS1=..." will apply it for that session.

```

PS1='\e[01;31m\w\$\e[00m'

```

---

### Post by Bachstelze on 2008-07-25
You really should use zsh, by the way, but this is outside the scope of this thread. I'm really amazed at how many people still use Bash as an interactive shell...

---

### Post by LaRoza on 2008-07-25
> **HymnToLife said:**
> You really should use zsh,
Reasons would help ;)

> 
 by the way, but this is outside the scope of this thread. I'm really amazed at how many people still use Bash as an interactive shell...

Dash also.

---

### Post by Bachstelze on 2008-07-25
> **LaRoza said:**
> 
Dash also.

I don't think anyone does :p As for reasont to use zsh, the completion system is much smarter than Bash's, and it is overall much more customizable.

---

### Post by mali2297 on 2008-07-25
A tutorial:
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

---

### Post by Trail on 2008-07-25
Mine:
```

[${debian_chroot:+($debian_chroot)}\[\[\033[0;37m\]\u\[\033[00m\]]\[\033[1;35m\]\w\[\033[00m\]\$

```

It is like:
[username(in grey)]workingdirectory(in pink)$

And I changet the username color in other hosts so I always know easily where I am when I ssh.

---

### Post by Bachstelze on 2008-07-25
As for me, I just use the green and blue Gentoo prompt (that turns red for root) in every OS I use.

---

### Post by kvk on 2008-07-25
Thanks for the clarification, La Roza! And...um...once I get proficient a bit more with the regular BASH shell, I'll go play with the other toys. :)

---

### Post by ice60 on 2008-07-25
i made my root prompt red too, the file to edit for the root prompt is in a different place, it's here -
```
/etc/bash.bashrc
```

[[IMG]http://img67.imageshack.us/img67/2060/termtq6.th.png[/IMG]](http://img67.imageshack.us/my.php?image=termtq6.png)

this is what i added to the end of /etc/bash.bashrc and ~/.bashrc, it's got loads of colours defined so you can change the colours of the prompt if you want.

```
rgb_restore='\[\033[00m\]'
rgb_black='\[\033[00;30m\]'
rgb_firebrick='\[\033[00;31m\]'
rgb_red='\[\033[01;31m\]'
rgb_forest='\[\033[00;32m\]'
rgb_green='\[\033[01;32m\]'
rgb_brown='\[\033[00;33m\]'
rgb_yellow='\[\033[01;33m\]'
rgb_navy='\[\033[00;34m\]'
rgb_blue='\[\033[01;34m\]'
rgb_purple='\[\033[00;35m\]'
rgb_magenta='\[\033[01;35m\]'
rgb_cadet='\[\033[00;36m\]'
rgb_cyan='\[\033[01;36m\]'
rgb_gray='\[\033[00;37m\]'
rgb_white='\[\033[01;37m\]'

rgb_std="${rgb_white}"

if [ `id -u` -eq 0 ]
then
    rgb_usr="${rgb_red}"
else
    rgb_usr="${rgb_green}"
fi

[ -n "$PS1" ] && PS1="${rgb_usr}`whoami`${rgb_std} \W ${rgb_usr}\\\$${rgb_restore} "

unset   rgb_restore   \
        rgb_black     \
        rgb_firebrick \
        rgb_red       \
        rgb_forest    \
        rgb_green     \
        rgb_brown     \
        rgb_yellow    \
        rgb_navy      \
        rgb_blue      \
        rgb_purple    \
        rgb_magenta   \
        rgb_cadet     \
        rgb_cyan      \
        rgb_gray      \
        rgb_white     \
        rgb_std       \
        rgb_usr
```

---

