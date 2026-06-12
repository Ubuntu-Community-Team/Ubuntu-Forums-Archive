---
title: "cd into the $DISPLAY directory"
date: 2010-04-13
forum: Server Platforms
---

### Post by sportfreak2020 on 2010-04-13
Hey everybody

i was wondering if we could cd in the directory of the PATH variable

for example, if i type in echo $DISPLAY

it will give me /tmp/launch-3ee4fg/org.x:0

is there any way that i can just take the value '/tmp/launch-3ee4fg/' from the output of $DISPLAY and exclude out the filename to the end of the command

i tried using the read command and the IFS variable..apparently IFS does not recognise / i guess

but any help is greatly appreciated... :P

---

### Post by cdenley on 2010-04-13
How about this?
```

dirname $DISPLAY

```

---

### Post by sportfreak2020 on 2010-04-13
GOT IT!!
You are awesome..thank you sir..

---

