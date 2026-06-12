---
title: "Check Whether an Application is Debian Package/Flatpak/Snap"
date: 2020-05-03
forum: Ubuntu Application Development
---

### Post by ChrisOfBristol on 2020-05-03
My program runs a function of an application. The command for the Snap doesn't work for the Debian Package and vice-versa. I could just try each in turn and ignore the command which fails, but that seem a bit crude to me. Is there a command I could use or a variable I could check to see whether the user has installed the application from a Debian application, a Flatpak or a Snap?

The only way I can think of is to use a command like snap info {program} > filename.txt then read and edit the text file to find whether it indicates success or not. That's very long-winded.

---

### Post by Frogs Hair on 2020-05-03
I don't know of a single command, but there could be one.Process of elimination is not an elegant solution and some applications listed in the output are default and  not user installed.    
```
snap list
```  ```
flatpak list
```

---

### Post by ChrisOfBristol on 2020-05-03
I have found 3 useful commands on a post elsewhere:[INDENT]command -v {application name}                        (Posix compliant systems only)
hash {application name}
type {application name}
[/INDENT]

If I call **type** from Python, it  produces the most useful result - a zero if it has found the application and something else if not. Since the Debian package and the Snap have different names, I can try both and see which comes up with a zero.

---

