---
title: "common spelling errors for bash commands"
date: 2008-09-05
forum: Ubuntu Brainstorm
---

### Post by u-slayer on 2008-09-05
wouldn't it be cool if bash corrected some of the more common spelling errors.

example: rsync and rysnc:)

I do that one all the time. This could be easily added to with a list of symbolic links.

---

### Post by jacksaff on 2008-09-05
Use tab for auto-completion.
Given what you can do with a wrong command, having bash guess at what you really mean is a truly awful idea.

---

### Post by amo-ej1 on 2008-09-05
The ideal thing is tab completion yes, but another suggestion might be to use an alias. E.g. if you know from yourself that you are unable to type a certain word correct you can create a construct as follows:

```

edb@lapedb:~$ pint 10.0.0.1
bash: pint: command not found
edb@lapedb:~$ alias pint=ping
edb@lapedb:~$ pint 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


```

and add the alias command to your ~/.bashrc

---

### Post by mujambee on 2008-09-05
> **u-slayer said:**
> 
example: rsync and rysnc:)


What if I write a program and call it rysnc? :(

---

### Post by signifer123 on 2008-09-05
> **mujambee said:**
> What if I write a program and call it rysnc? :(

I'd hope it would be a link, so you just overwrite it?

---

### Post by smartboyathome on 2008-09-05
This is actually already available in ZSH (the Z Shell). Ubuntu doesn't even use bash, it uses dash (a minimal bash prompt), so I don't think it will be possible to use this. :(

---

### Post by cdenley on 2008-09-05
> **smartboyathome said:**
> This is actually already available in ZSH (the Z Shell). Ubuntu doesn't even use bash, it uses dash (a minimal bash prompt), so I don't think it will be possible to use this. :(

The default shell in ubuntu is /bin/bash. However, scripts tend to use /bin/sh. Ubuntu replaced /bin/sh with a link to dash, since it is faster. Scripts don't need the features of bash or zsh. You can set your shell to whatever you want in ubuntu, including zsh.
```

sudo apt-get install zsh
sudo usermod -s /bin/zsh cdenley

```

---

