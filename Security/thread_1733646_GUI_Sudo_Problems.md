---
title: "GUI Sudo Problems"
date: 2011-04-19
forum: Security
---

### Post by mynameisnotbob on 2011-04-19
Hello all. I try to avoid posting questions on the forums because I know it's probably out there somewhere already but this time I really can't find the answer.

I can only run super user in terminal. I can start the Root Terminal application, but anything else, like user-admin or synaptic, just shows me a authentication screen with no password box that dissapaers after a minute. Please advise. I'm mostly comfortable with terminal, but there's a few things I find hard to do.

It wouldn't even let me sudo until i put the box in recovery mode and fixed the /usr permissions (i had run "chmod 777 /usr -R to edit some game files, BAD IDEA!). I feel like that may have something to do with it.

---

### Post by debd on 2011-04-19
>  just shows me a authentication screen with no password box that dissapaers after a minute.

if that doesn't give you the PW field, try ```
gksudo <application_name>
``` in a terminal or in the blanc-field after pressing Alt+F2

---

### Post by mynameisnotbob on 2011-04-19
Thanks! That solved it! I guess I just wasn't thinking straight.

---

