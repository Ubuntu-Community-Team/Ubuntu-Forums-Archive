---
title: "Overriding sudo through an alias"
date: 2009-02-14
forum: Security
---

### Post by LAugust on 2009-02-14
Sat organising my aliases in my .bashrc file the other day. Got curious to see what would happen if I defined an alias such as:

alias sudo='echo whoops!'

It surprised me that it was allowed as it's totally unnecessary and potentially a security vulnerability. Spent some more time experimenting with it and the following day I had control over all my workmates' systems. 

Alright, you do have to force the victim to run malicious code, but that can be done pretty easily especially with newbies. 

Can anyone think of a reason why 'sudo' shouldn't be disallowed as an alias?

---

### Post by kerry_s on 2009-02-14
thats a good idea, i think i'll change my sudo to something else, maybe:

**alias sudo='echo ALERT! YOU HAVE BEEN LOGGED!'**

:lolflag:

direct access to the computer will always be a security problem.

---

### Post by LAugust on 2009-02-14
True, but direct access shouldn't make it this simple to gain access of the sudo password:

Embed a code in something trustworthy that 
1. Adds the alias sudo='sud'
2. Writes the code of "sud" to a file (see below)
3. Compiles it and makes it executable
4. Removes itself and the source for sud
5. Reloads .bashrc

Next time the user does a sudo the binary for "sud" is executed, asking for a password as sudo normally would. You can't (i think) pass the password in as an argument to sudo, so display the normal "Sorry, try again" message, post the ip, username and password to yourself and remove the alias to let the victim use sudo as normal. Make the code remove itself and sed away the alias in .bashrc. Now there are no visible traces left of the attack, but you have all you need to log on his system.

I personally think it's bad to allow this. If people disagree, then at least it's a fun prank to play on friends!

---

### Post by kerry_s on 2009-02-14
i personally think it's more of poor training, the computers should be locked when the person using it walks away. i doubt they were locked if you futzed with them, unless they watched you do it. :lolflag:

any user worth 2cents at least looks at any script before they execute it, if not again poor training.

i do like the idea of aliasing sudo for the command line at least it will throw a quick curve and give them a "oh s**t" moment.

i've put this for my bashrc:

```

alias sudo='watch -- echo ALERT! TRACING! LOGGING!'
alias !='/usr/bin/sudo'
alias x='exit'
alias ch='clear;history -c'
alias u='/usr/bin/sudo pacman -Syu'
alias s='search'
alias i='/usr/bin/sudo pacman -S'
alias r='/usr/bin/sudo pacman -Rsn'
alias ?='installed'
alias c='/usr/bin/sudo pacman -Sc --noconfirm'
alias unp='extract'
alias faster='/usr/bin/sudo pacman-optimize && sync'

```

---

### Post by bodhi.zazen on 2009-02-15
Thread closed.

.bashrc has been discussed before and in terms of this thread :

You have mis characterized the problem(s). When you analyze the "problem" it breaks down into :

1. Social engineering (ie getting someone to run your malignant script).

2. Escalation of privileges.

The first is best addressed with education, do not run scripts, programs, or executable programs from untrusted sources. Do not run commands if you do not understand what they do.

The second is addressed by a combination of permissions and/or selinux / apparmor .

Please see : [http://ubuntuforums.org/showthread.php?t=1070309](http://ubuntuforums.org/showthread.php?t=1070309)

---

