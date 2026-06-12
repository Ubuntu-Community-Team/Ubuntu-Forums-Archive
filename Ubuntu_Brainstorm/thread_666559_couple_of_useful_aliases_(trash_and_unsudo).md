---
title: "couple of useful aliases (trash and unsudo)"
date: 2008-01-13
forum: Ubuntu Brainstorm
---

### Post by dak-AD on 2008-01-13
just 2 aliased commands i use quite often:


alias trash='mv -t ~/.Trash/'
alias unsudo='sudo -k'

trash acts like rm, but with the benifit of storing a backup copy of the directory/file in /home/username/.Trash (i.e., the trash can), whilst unsudo manually revokes the sudo-without-password privelage that CLIs usually keep for 5 mins after a succesful sudo usage. for some reason, i can never remember 'sudo -k'

---

### Post by smartboyathome on 2008-01-13
I don't ever use these, and trash would be even less useful since not many people actually use the command line for that stuff.

---

### Post by insane_alien on 2008-01-14
you can set up your .bashrc to not remember the sudo password at all except for the command it is running at the time. i'm not entirely sure where it is in my .bashrc as it is heavily customized and getting ridiculous, i might remove some of the quoted out bits.

i actually have the exact same trash alias as well. i give this +1 although people most likely to use them will have already got them.

---

### Post by dak-AD on 2008-01-15
helloooooo! small intarwebz, eh? :)

> **insane_alien said:**
> you can set up your .bashrc to not remember the sudo password at all except for the command it is running at the time. 

yeah i know, but wouldn't that just be iritating if you want to run more than one sudo thing in a row, e.g.:

sudo apt-get update
sudo apt-get upgrade

---

### Post by insane_alien on 2008-01-15
so use 'su'.

the thing is, your setting up sudo for added security, typing in your password for stuff like that everytime is more secure than having to remember to exit.

---

