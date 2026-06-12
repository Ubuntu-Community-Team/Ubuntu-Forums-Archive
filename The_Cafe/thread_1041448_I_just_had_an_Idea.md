---
title: "I just had an Idea"
date: 2009-01-16
forum: The Cafe
---

### Post by days_of_ruin on 2009-01-16
What if there was a website you could entire bash commands to see if 
they are "clean" i.e not malicious.And there could be a firefox
plugin to make it even easier, just select the command text and right
click->"check command" or something like that.Is this feasible?

---

### Post by Sealbhach on 2009-01-16
It's good thinking. However, it would probably not be able to replicate the effect the command would have on your own system if you actually ran the command - due to all the possible different configurations.

It could work as a command vetting system - able to advise whether the command is potentially harmful or not.



.

---

### Post by RATM_Owns on 2009-01-16
```
read -p "$PS1 " COMMAND
if [ "$COMMAND" = "sudo rm -rf /" ] ; then
      echo "Command is not safe."
fi
```

---

### Post by cardinals_fan on 2009-01-16
Well, fakeroot simulates a root environment, so you can test things before running them as root.

---

