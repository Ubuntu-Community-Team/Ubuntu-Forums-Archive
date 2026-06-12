---
title: "bash script for mount cifs"
date: 2011-07-07
forum: Server Platforms
---

### Post by jlazkano on 2011-07-07
Hello forum, I am trying to config a bash script to copy a file on a remote cif folder. Before to copy, I need to mount, then copy and last umount.

So I want to know if it really mount.

Is possible to check with a "if" if it mount well?

Something like this?

[/CODE]
if [ mount -t cifs $recurso $montaje -o user=$usercifs,pass=$passcifs,domain=$domaincifs ]; then
        cp file $montaje
else
        echo "Error mounting"
fi

if [ !umount.cifs $montaje ]; then
        echo "Error unmounting"
fi
[/CODE]

I try to execute but always I can not mount.

Can you help with this?

Thanks and best regards.

---

### Post by rubylaser on 2011-07-07
First question, are you running this as root (otherwise it won't work)? If you are, then I would probably just mount the share right away rather than including that in the if block.  After it's mounted, I would check that it's mounted with the mount command in an if block (try it a few times).  Here's an [example]("http://www.linuxquestions.org/questions/programming-9/bash-script-to-check-mount-is-ok-520051/#post2589529") for some ideas.  It's not the same thing, but could be adapted as part of your solution.

---

### Post by jlazkano on 2011-07-08
> **rubylaser said:**
> First question, are you running this as root (otherwise it won't work)? If you are, then I would probably just mount the share right away rather than including that in the if block.  After it's mounted, I would check that it's mounted with the mount command in an if block (try it a few times).  Here's an [example]("http://www.linuxquestions.org/questions/programming-9/bash-script-to-check-mount-is-ok-520051/#post2589529") for some ideas.  It's not the same thing, but could be adapted as part of your solution.

Thanks for your help, I got it, this is the code:

```

mount -t cifs $recurso $montaje -o user=$usercifs,pass=$passcifs,domain=$domaincifs
if [ $? -eq 0 ]; then
        echo "OK"
else
        echo "Error"
fi

```

Thanks and best regards.

---

