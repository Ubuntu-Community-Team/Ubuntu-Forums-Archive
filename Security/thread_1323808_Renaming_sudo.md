---
title: "Renaming sudo"
date: 2009-11-12
forum: Security
---

### Post by Dead Die Jazz on 2009-11-12
I just had an intriguing idea, and I'd be interested to know if the verdict on it is that it's an indicating that the men in white coats should be coming to take me away, if it's just far too advanced for someone like me who hopes to never do a manual install,, or if it just means I should be beaten for suggesting the utilisation of obscurity.

So in anycase, I was wondering if it was possible to change the sudo command to something like isay or simonsaid or something else, so that should a malicious script or hacker take an interest in my computer, the normal commands would do nothing. And while I'm sure it would be trivial for a sufficiently advanced script or competent hacker to find that my admin command was odus, I'm sure it wouldn't be too hard to tell aide to release the hounds the minute someone or something attempted to use the command sudo. Or would I just make life difficult for myself?

---

### Post by jollysnowman on 2009-11-12
Well, everything has to be written in a program somehow, and *nix is open source, so there's gotta be a line somewhere that's like:

String super_command = "sudo";

[/tongueincheek]

---

### Post by cdenley on 2009-11-12
You can probably just move the sudo executable, but I wouldn't recommend it. There may be init/cron scripts which use the sudo command. For all I know, it might break sudo. If you installed an update which replaces sudo, you would have the new sudo command AND your renamed original sudo command.

---

### Post by Keith Hedger on 2009-11-12
Renaming sudo probably not a good idea as lots of scripts use it, if you are worried about security make sure you have a properly configured firewall and a strong password and you should be ok.

---

### Post by mukyboy on 2009-12-04
I had this idea a while ago, too. I wanted to rename it "please." All I've tried so far is ```
cp sudo please
``` but that didn't work. I knew it couldn't be that easy.

---

### Post by cariboo on 2009-12-04
You'd have to find every script system wide that has sudo in it and change it to please.

---

### Post by cdenley on 2009-12-04
> **mukyboy said:**
> I had this idea a while ago, too. I wanted to rename it "please." All I've tried so far is ```
cp sudo please
``` but that didn't work. I knew it couldn't be that easy.

This wouldn't rename sudo, but basically create an alias. This wouldn't have any security benefits, which was what the original poster had intended. It wouldn't break anything, since the original "sudo" command will still work. There are three ways it can be done.
```

sudo cp /usr/bin/sudo /usr/bin/please
sudo chmod u+s /usr/bin/please

```

```

sudo ln -s /usr/bin/sudo /usr/bin/please

```

```

echo alias please=sudo>>~/.bashrc

```

The last one only creates the alias for the user that runs the command. It will not work on shells started before the alias was created.

---

### Post by teward on 2009-12-04
well, here's one way without messing with all your files or all the system files.

I did this to make commands execute by typing something different.

go into the terminal, do this:
```
sudo cp ~/.bashrc ~/.bashrc.factoryDefaults
sudo gedit ~/.bashrc
``` This will make a duplicate of the original bashrc file in case you mess it up and you need to restore it.  In the .bashrc file, there will be lines that contain this (or similar):
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

```If you add to the end of this group of aliases ```
# Alias to make sudo execute when something else is typed in
alias **newSudoCommand**='sudo'
```you can use whatever you put in for **newSudoCommand** in replacement of sudo.

I did something like this so that I type ```
internet
``` and it executes w3m (terminal's web browser) and takes me to whatever site I specify.

And the best part is that it won't mess with your system files too much, and you can recover from mistakes if you have to.


***EDIT: 2 things.  One, sorry for the long post.  Two, this only applies to the user who you ran the first commands for.  To duplicate these commands over, and use the cp command, like this (where ~ is your user directory, and targetUserDir is the user you're copying these settings to):
```
sudo cp ~/.bashrc /home/targetUserDir/.bashrc
```

However, if you're thinking of copying these settings to the user root, just don't do it.  Trust me. ***

---

### Post by cdenley on 2009-12-04
That is the same as my third method, just more complicated.

---

### Post by teward on 2009-12-04
eh, can't be pressured into reading every post :P  Nevertheless, you only modify one file and it works.  never has to rename any system files at all.

---

### Post by ciandro on 2009-12-05
Hahahahah that would be funny...:D

You could rename it to something like billgateswouldntlike... but I guess it's too long! :guitar:

Good luck with that!

---

