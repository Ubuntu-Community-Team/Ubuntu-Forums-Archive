---
title: "Edit a config using bash...."
date: 2011-06-15
forum: Server Platforms
---

### Post by phillips321 on 2011-06-15
Hi guys,

I would like to quickly replace a few lines in a config file(/etc/bash.bashrc) using a script.

I would like to replace:
```
# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
```
With:
```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

I know sed -i s/[origional]/[new]/g /etc/bash.bashrc is roughly what i'm looknig for but i cannot properly escape all the special characters such as # [ ] / &&

Any help would be greatly appreciated.

---

### Post by DaithiF on 2011-06-15
Hi, so you just want to uncomment those lines then, rather than make other changes to them?

if so, tell sed to do something on a range of lines, starting when it matches the # enable bash...etc line, and ending 3 lines after.

slight complication is that we don't then want to uncomment the first of those lines:
```
$ sed -i '/# enable bash completion in/,+3{/enable bash completion/!s/^#//}'
```

---

### Post by phillips321 on 2011-06-15
And there is the beauty of bash. There's more than one way to skin a cat.... i was trying to skin it with a club, where's you are skinning it with a knife. Cheers for this

P.s. Just noticed your avatar.... a cat :P

---

### Post by DaithiF on 2011-06-15
> **phillips321 said:**
> There's more than one way to skin a cat.... 
I'd never thought about it before, but what a strange idiom that is ... what are these several ways, and why do we need to skin cats anyway? :)

---

### Post by koenn on 2011-06-15
it's usually a good idea to skin an animal before you're going to cook and eat it ...

---

