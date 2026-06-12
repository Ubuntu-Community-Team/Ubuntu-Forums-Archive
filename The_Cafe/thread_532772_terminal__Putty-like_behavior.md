---
title: "terminal : Putty-like behavior?"
date: 2007-08-23
forum: The Cafe
---

### Post by justleen on 2007-08-23
Hey all

I know i dont NEED putty, i can just use the command shell to ssh.

however for my work i need to connect to quite a few servers... and im starting ease of use of putty now..

I need to open a new shell evertime (i have shortcuts. but still) and i dont know how to set the title so when it opens, i can actually see what system im on (quite a few Tru64 machines, so the default prompt is just a #...)


does any one know a tool or this, or has a guide on how to change my terminal behavior at startup?

---

### Post by Tuna-Fish on 2007-08-23
using xfce4-terminal, my default dynamically set title is 
"tuna@tunamasiina: /home/tuna"
If that is something you are after, perhaps you should just swap your terminal emulator into one that does it.

---

### Post by justleen on 2007-08-23
Does your title change, when you ssh to another system?

---

### Post by saulgoode on 2007-08-23
Most xterms will permit you to change the window title by echo'ing escape sequences. Try the following command:

echo '**^[**]0;Window Title**^[**\'
 
The **^[** is the ESCAPE character and should be typed in using CTL-v then hitting the ESC key.

EDIT: Oops. You would seem to want to know how to set the command line prompt, not the terminal's title. I would suggest viewing your shell's 'man' page for the appropriate method. For BASH (Bourne Again SHell), do a "man bash" and  look under the PROMPTING section for environment variables PS1, PS2, ...

---

### Post by vexorian on 2007-08-23
```

sudo atp-get install putty

```

:)

---

### Post by justleen on 2007-08-24
Thnx for the replies guys, but thats not what im looking for, im afraid.

For now, i just use a profile for each server i connect to, with the terminal/tab title set to the hostname.
That way i can see what system im on. 
Dynamic setting would be nicer, but i cant get that to work what so ever...

---

