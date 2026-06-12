---
title: "Changing the home folder disables colours in ssh session"
date: 2010-09-28
forum: Server Platforms
---

### Post by silark on 2010-09-28
This is a weird one. If I change my home folder to anything other than the default home folder I no longer get the different colors in my SSH session. The color I am talking about are the ones that signify directory/file etc... everything is just black and white. Any explanation for this weird behavior or a way to get around it? I changed the home folder in using the usermod -d /home/thisfolder/thatfolder/ chris and the change is present in the ssh_config file.

---

### Post by CharlesA on 2010-09-28
Check yer aliases.

Here's what mine looks like:

```
charles@atlantis:~$ alias
[COLOR="Red"]alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'[/COLOR]
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
[COLOR="Red"]alias ls='ls --color=auto'[/COLOR]
```

---

### Post by silark on 2010-09-28
Does this look right?

darcy@albert:~$ alias
alias ls='ls --color=force'

---

### Post by CharlesA on 2010-09-28
Should be color=auto, or at least that's how mine is.

It's set in .bash-rc.

---

### Post by silark on 2010-09-28
ok so I changed the line first and then update the home folder and I have the same issue. Here is what the lines look like in .bashrc

```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi
```

---

### Post by CharlesA on 2010-09-28
It looks like this for me:

```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

```

What version are you using?

---

### Post by silark on 2010-09-29
darcy@albert:~$ cat /etc/issue
Ubuntu 8.04.4 LTS \n \l

---

### Post by CharlesA on 2010-09-29
Hrm. I'm using 10.04.1 atm, but the aliases should be the same.

Is it still doing the same thing if you create the alias manually?

---

### Post by SeijiSensei on 2010-09-30
I think the colors are going to depend on how the *remote* machine is configured, not the one running the ssh client.

---

### Post by silark on 2010-09-30
I'm still fairly new to this how do I create an alias manually?

---

### Post by Tony Flury on 2010-09-30
> **silark said:**
> I'm still fairly new to this how do I create an alias manually?

Use exactly the same commands as in the .bashrc file i.e

```

    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'

```

---

### Post by silark on 2010-09-30
Ok so right now my home folder is set to /home/darcys/this/that i.e. not the original home folder and I have no color. I'm not sure I did this right but typed each command as displayed in Tony Flury's post and but this had no effect on the .bashrc file. So I went in an manually changed them to what is below and I still get no color when I log in.


if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

---

### Post by SeijiSensei on 2010-09-30
As I suggested, what does .bashrc in the account you're logging into on the remote machine look like?

---

### Post by silark on 2010-09-30
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

---

### Post by Tony Flury on 2010-09-30
> **silark said:**
> Ok so right now my home folder is set to /home/darcys/this/that i.e. not the original home folder and I have no color. I'm not sure I did this right but typed each command as displayed in Tony Flury's post and but this had no effect on the .bashrc file. 

None of the commands i gave you will effect the .bashrc file itself - what they will do is set up an alias for that terminal only - if you open another window - or terminal shell, those aliases wont be there.

As other have said because you are doing a remote shell you might have other issues.

---

