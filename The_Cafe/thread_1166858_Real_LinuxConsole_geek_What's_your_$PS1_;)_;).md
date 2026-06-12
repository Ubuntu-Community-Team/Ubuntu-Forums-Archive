---
title: "Real Linux/Console geek: What's your $PS1 ;) ;)"
date: 2009-05-22
forum: The Cafe
---

### Post by frenchn00b on 2009-05-22
Linux/Console geek: What's your $PS1 ;)  
and with screenshot please ;)
 
 
Edit:
For those who do not know what is $PS1 variable:
[http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html)

---

### Post by fatality_uk on 2009-05-22
Doesn't seem to work :D

---

### Post by Dr Small on 2009-05-22
Why is a screenshot necessary? It's just ASCII...
```
[drsmall@darkghost ~]$ echo $PS1
[\u@\h \W]\$

```

---

### Post by whitefang5412 on 2009-05-22
It's highly top secret and classified.

---

### Post by Sublime Porte on 2009-05-22
fairly basic:

'\u@\h:\w% '

Which looks somewhat like this:

user@machine:~% ls -la

---

### Post by monsterstack on 2009-05-22
Here you go,

```
PS1="$PR_LIGHT_GREEN%n$PR_GREY@$PR_BLUE%m$PR_GREY:$PR_LIGHT_RED%2c$PR_NO_COLOR%(!.#.$) "
```

See if you can get that to work properly. Oh, it looks like this:

```
[COLOR="Green"]user[/COLOR][COLOR="Gray"]@[/COLOR][COLOR="MediumTurquoise"]host[/COLOR][COLOR="Gray"]:[/COLOR][COLOR="Red"]~[/COLOR][COLOR="White"]$[/COLOR]
```

Looks better against a black background, though.

---

### Post by MaxIBoy on 2009-05-22
Here's mine:
```
~$echo $PS1
\[\033[0;31m\]\w$\[\033[0m\]
~$

```

---

### Post by RiceMonster on 2009-05-22
Just keepin' it simple

PS1='\u@\h:\W\$ '

---

### Post by FuturePilot on 2009-05-22
```
[%{%}%n%{%}@%{%}%U%m%u%{%}:%{%}%2c%{%}]%(!.#.$) 
```

Looks something like
[[COLOR="RoyalBlue"]user[/COLOR]@[COLOR="Lime"]_host_[/COLOR]:[COLOR="Red"]~[/COLOR]]$

ZSH

---

### Post by tomcheng76 on 2009-05-22
Here it is.
[COLOR="Green"][fakeusername@realubuntu ~ 11:44 &#21320;&#24460;]$[/COLOR] echo $PS1
\[\][\u@\h \W \@]$ \[\]
Even you request screenshot, you won't get my username. lol

---

### Post by schauerlich on 2009-05-22
[img]http://grubbn.org/u/edavidburg/ericprompt.png[/img]

---

### Post by baseface on 2009-05-22
```
PS1="[\W]$ "
```
```
[~]$ pwd
/home/lntv
```
 
i loathe colorful terminals.

---

### Post by chriskin on 2009-05-22
user@pc:~$ echo $PS1
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$

what does it even mean though? :P

---

### Post by miggys on 2009-05-22
I made a blog post about my prompt and it would be neat to actually get visitors :)

[smiley prompt]("http://miggysmith.wordpress.com/2009/05/08/cool-bash-prompt-smiley/")

---

### Post by Tibuda on 2009-05-22
```
~$ echo $PS1
\w\$
```

---

### Post by Dougie187 on 2009-05-22
```
\[\e]0;\u@\h: \w\a\]\[\e[31m\]\u\[\e[36m\]@\[\e[33m\]\h \[\e[35m\]\w: \[\e[0m\]
```

---

### Post by CJ Master on 2009-05-22
[img]http://www.blogcdn.com/playstation.joystiq.com/media/2008/05/061030_ps1_hmed_9ahmedium.jpg[/img]

---

### Post by Cl0ud9 on 2009-05-22
```

PS1="$PR_GREEN%U%n%u$PR_RED: %B% $PR_BLUE~%b $PR_BLUE$>$PR_NO_COLOR "

```
Looks something like:
[COLOR="Lime"]_username_[/COLOR][COLOR="Red"]:[/COLOR] [COLOR="RoyalBlue"]~[/COLOR] [COLOR="RoyalBlue"]$>[/COLOR]

---

### Post by Dr Small on 2009-05-22
> **baseface said:**
> ```
PS1="[\W]$ "
```
```
[~]$ pwd
/home/lntv
```
 
i loathe colorful terminals.
I can't stand it, unless there is some sort of color

---

### Post by kk0sse54 on 2009-05-22
Simple and imo elegant :p > ~

---

### Post by RATM_Owns on 2009-05-22
Zsh.

```
&#9484;&#9472;[andy @ vithon]-[16:29:05]
&#9492;&#9472;[~]-[$]> echo $PROMPT
$'%{\e[0;34m%}%B&#9484;&#9472;[%b%{\e[0m%}%{\e[1;32m%}%n%{\e[0m%} @ %{\e[0m%}%{\e[0;36m%}%B%m%{\e[0;34m%}%B]%b%{\e[0m%}-%{\e[0;34m%}%B[%b%{\e[0;34m%}'%B%*%b$'%{\e[0;34m%}%B]%b%{\e[0m%}
%{\e[0;34m%}%B&#9492;&#9472;[%b%{\e[0m%}%~%{\e[0;34m%}%B]%b%{\e[0;34m%}-%B[%{\e[1;35m%}$%{\e[0;34m%}%B]>%{\e[0m%}%b
```

---

### Post by MaxIBoy on 2009-05-22
> **CJ Master said:**
> [IMG]http://www.blogcdn.com/playstation.joystiq.com/media/2008/05/061030_ps1_hmed_9ahmedium.jpg[/IMG][http://ubuntuforums.org/showthread.php?t=1103231#16](http://ubuntuforums.org/showthread.php?t=1103231#16)

---

