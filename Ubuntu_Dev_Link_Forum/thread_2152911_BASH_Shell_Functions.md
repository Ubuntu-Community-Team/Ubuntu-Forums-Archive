---
title: "BASH Shell Functions"
date: 2013-06-09
forum: Ubuntu Dev Link Forum
---

### Post by CosmicFlux on 2013-06-09
Hi,

Is it possible to create a BASH shell function that accepts arguments at the prompt?  I want to create a function that allows the user to carry out a long complex command string by entering a single command, but the command string takes an argument that may change depending on user preference. 

_For example:_
I've created the function bg which will carry out **[FONT=Courier New]gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/background_color "USER_HEX_ENTRY"[/FONT]**
but is it possible to let the user follow the bg command with the USER_HEX_ENTRY value and have the function supply the argument at the end of the command string?


Cosmic

---

### Post by Cheesemill on 2013-06-09
```
function bg() {
    gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/background_color "$1"
}
```

$1 is substituted for the first argument you provide after the bg command.

---

### Post by CosmicFlux on 2013-06-09
Thanks!

So can I use $2 $3 $3...etc to accept multiple arguments?


Cosmic

---

### Post by Cheesemill on 2013-06-09
Yes you can :)

---

