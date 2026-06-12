---
title: "Why current hash and symbolic link has changed for a file?"
date: 2017-02-09
forum: Security
---

### Post by martemarziano on 2017-02-09
What follows is one of the warnings I get after running Rkhunter:
> [COLOR=#000000][I]Current hash: 2531d65f43f6ed32b8d1f8c9d61075301aee23a43dd635ec55 feff72a44ccc0a
[/I][/COLOR][COLOR=#000000][I]Stored hash : 91c3e9551264fc2b8a46a104715d51c13d717460f460e5d0d9 7295c69196ed1c
Current symbolic link target: '/usr/bin/awk' -> '/usr/bin/gawk'
Stored symbolic link target : '/usr/bin/awk' -> '/usr/bin/mawk'
Warning: The file '/usr/bin/gawk' exists on the system, but it is not present in the 'rkhunter.dat' file.[/I][/COLOR]
I wonder why the current hash and symbolic link differ from what is being stored?
I really appreciate if someone can tell me what this is about.

---

