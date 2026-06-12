---
title: "if you dont use bash what do you use?"
date: 2008-11-20
forum: The Cafe
---

### Post by jimi_hendrix on 2008-11-20
the name says it alll

please post why you use what you use

---

### Post by nandasunu on 2008-11-20
whatever is there by default, otherwise no idea :confused:

---

### Post by jimi_hendrix on 2008-11-20
thats bash

---

### Post by snova on 2008-11-20
I prefer Zsh. I don't actually have a practical reason for it, but it has more features than Bash. :p

My prompt:

```
PS1="%n@%M[%D{%I:%M}]:%~%(!.#.$)"
```

I also have 250 lines of aliases, functions, and various other odds and ends.

Oh yes, I like all the options it has. Better completion in addition.

---

### Post by jimi_hendrix on 2008-11-20
please explain that prompt

---

### Post by snova on 2008-11-20
It looks like this:

```
snova@snova-laptop[06:55]:~/.zsh$
```

The % directives are replaced with other things. You can do all sorts of neat things with it.

Still haven't figured out colors, though. :(

---

### Post by bobbocanfly on 2008-11-28
I just switched from Bash to zsh and loving it. Here are my prompts:

```
export PS1="%{$fg[red]%}%n%{$reset_color%}@%{$fg[blue]%}%m%{$reset_color%}% > "
export RPROMPT="%{$fg[blue]%} $(pwd) %{$fg[red]%}$VCS%{$reset_color%}"
```

ends up with:

```
bobbo@tiger>  [....] /home/bobbo
OR (in a VCS enabled directory)
bobbo@tiger>  [....]  /home/bobbo/Code/gwibber bzr:gwibber@rev150
bobbo@tiger>  [....]  /home/bobbo/Code/random  git:random@rev15
```

---

### Post by Th3Professor on 2008-11-28
ksh was one of the earliest shells i was exposed to, so i feel 'at home' with it, though i still use others, like zsh, bash, each for their own advantages.

---

### Post by snova on 2008-11-28
> **bobbocanfly said:**
> I just switched from Bash to zsh and loving it. Here are my prompts:

```
export PS1="%{$fg[red]%}%n%{$reset_color%}@%{$fg[blue]%}%m%{$reset_color%}% > "
export RPROMPT="%{$fg[blue]%} $(pwd) %{$fg[red]%}$VCS%{$reset_color%}"
```

ends up with:

```
bobbo@tiger>  [....] /home/bobbo
OR (in a VCS enabled directory)
bobbo@tiger>  [....]  /home/bobbo/Code/gwibber bzr:gwibber@rev150
bobbo@tiger>  [....]  /home/bobbo/Code/random  git:random@rev15
```

Is there an option that has to be set for this to work? Because it doesn't work for me, and I really want a color prompt...

---

### Post by smartboyathome on 2008-11-28
I use ZSH, and even have [made a thread]("http://ubuntuforums.org/showthread.php?t=532957") for people to post their .zshrc files.

---

### Post by blithen on 2008-11-28
Can someone post a screenshot of what can be possible with ZSH? It seems a lot cleaner then the normal Bash. But show me something that it can do that bash can't.

---

### Post by ::: on 2008-11-28
fish

---

### Post by smartboyathome on 2008-11-29
> **blithen said:**
> Can someone post a screenshot of what can be possible with ZSH? It seems a lot cleaner then the normal Bash. But show me something that it can do that bash can't.

It can do easier tab complete:
```
(aabbott@arch: ~)$ gimp screenshot-080524-112308.png
file
screenshot-080524-112308.png  screenshot-115358-112608.png
screenshot-080556-112308.png 
```

It can do corrections:
```
(aabbott@arch: ~)$ odprobe                          
zsh: correct 'odprobe' to 'modprobe' [nyae]? 
```

Thats really all I can think of right now, but there are also many zstyles in my .zshrc which I load.

---

### Post by ibutho on 2008-11-29
I use zsh on my desktop system because I really like the way they implemented tab completion.

---

