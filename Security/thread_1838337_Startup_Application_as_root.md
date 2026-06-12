---
title: "Startup Application as root"
date: 2011-09-03
forum: Security
---

### Post by QwUo173Hy on 2011-09-03
I've set up a headless box (Ubuntu 11.04) with a webcam attached to act as a security camera. The problem is, that I need to run "sudo motion" to run the application from the command line.

Since I want the set up headless (no monitor), how can I add it to the startup applications in gnome so that I don't have to type in a password?

Many thanks,
Jarlath

---

### Post by QwUo173Hy on 2011-09-03
I found a way here: [http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)

This works because the application does not have a gui - however I'm still interested in the original question for a gui app if anyone has an answer.

---

### Post by Lars Noodén on 2011-09-04
Add a special line for that program in sudo's /etc/sudoers using the NOPASSWD option.

---

### Post by fdrake on 2011-09-04
> **jarlath said:**
> I found a way here: [http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)

This works because the application does not have a gui - however I'm still interested in the original question for a gui app if anyone has an answer.

using symbolic links with update-rc.d did it worked on 10.10, too or not?

---

### Post by QwUo173Hy on 2011-09-04
> **fdrake said:**
> using symbolic links with update-rc.d did it worked on 10.10, too or not?Im using 11.04. It worked.

---

### Post by QwUo173Hy on 2011-09-04
> **Lars Noodén said:**
> Add a special line for that program in sudo's /etc/sudoers using the NOPASSWD option.

Lars, 
Thats great, thank you.! I couldnt even find that with google.

Jarlath

---

