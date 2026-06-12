---
title: "Alpine Mail - Alias Problem"
date: 2010-05-16
forum: Software
---

### Post by pmorton on 2010-05-16
I've been trying to get Bogofilter working with Alpine, so far without much success. One of my problems is with aliases. I want to be able to pipe a message to the command 'bogofilter -s' which will mark the message as spam and update the spam database. That can be done from the Inbox using the pipe command '|' and sending the raw message to the above command. Only I want to shorten that to the alias 'spam'. I've set up the alias as follows:

~/.bashrc contains the lines:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

and file ~/.bash_aliases contains the line:

```
alias spam="bogofilter -s "
```

Alias 'spam' works ok at the terminal. Only Alpine gives the error message:

> bash: spam: command not found

I've tried aliasing other, simpler commands like 'cat', and while 'cat' itself works, the alias does not. I get either the above error, or the message 'broken pipe'.

Anyone out there familiar with Alpine (or the workings of aliases) can tell me what I've got wrong?

---

