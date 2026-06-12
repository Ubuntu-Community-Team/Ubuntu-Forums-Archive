---
title: "show conky only when needed"
date: 2009-05-10
forum: The Cafe
---

### Post by americano70e10 on 2009-05-10
I made a conky script to use with rhythmbox, but I'd like for it to show up only when rhythbox is running. So far I was able to make it open with rhythmbox but don't know how to close them together, only rhythmbox closes.
Does anyone know how to make conky close along with rhythmbox?

Another solution is to have conky running since startup but only becoming visible when rhythmbox starts, and after it closes it would go to invisible mode again. But I don't know how to do either of those steps.

Anyone got any ideas??

---

### Post by MaxIBoy on 2009-05-10
In your home directory, there is a file called .bashrc. Edit it to include the following line:
```
alias rhythmbox_and_conky="conky & rhythmbox; killall conky"
```Now whenever you run the command rhythmbox_and_conky, it will start conky and background it, then run rhythmbox, and when rhythmbox exits, conky will be killed. This is called an "alias," because your "alias" is automatically substituted for the actual command you want to run, whenever you run the alias.

Then, run the command "source .bashrc" to reload it and apply your new alias.



Finally, go to system > preferences > main menu, and find the item for rhythmbox. Right click it, go to "properties," and in the "command" field, replace "rhythmbox" with "rhythmbox_and_conky," so it'll run the alias instead. Edit any other launchers to rhythmbox if you have them (desktop shortcuts, launchers on your panels, etc.)


If I recall correctly, running conky twice at once is harmless.




If it doesn't work, post here, but I think it ought to work.

---

### Post by americano70e10 on 2009-05-10
I inserted the line with a little modification because I'm running another conky:

```
alias rhythmbox_and_conky="conky -c .conkyrc2 & rhythmbox; killall conky && conky"
```

and when I run the command "rhythmbox_and_conky" on the terminal it works but when I put it in the lauchers it says that there is no file or folder with that name.

---

### Post by MaxIBoy on 2009-05-10
If you're running another conky display, killing all instances of conky and then starting it again seems like kind of an ugly solution.

Try this alias instead: ```
alias rhythmbox_and_conky="conky -c ~/.conkyrc2 & rhythmbox; kill -9 $!"
```

If the launchers still refuse to work after making these changes, try doing away with the alias altogether and copy/pasting "conky -c ~/.conkyrc2 & rhythmbox; kill -9 $!" into the "command" field straight up.

---

### Post by americano70e10 on 2009-05-10
The changes didn't work. The launchers still couldn't load and after rhytmbox closed conky kept running...

---

### Post by MaxIBoy on 2009-05-10
Okay, final measure, and if this doesn't work I give up: 
```
alias rhythmbox_and_conky="bash 'conky -c ~/.conkyrc2 & rhythmbox; kill -9 $!' "
``` Pretty bad, but hopefully it'll work.

If the kill -9 $! thing doesn't work, that's very odd ($! is the PID of the process most recently forked off.)

---

### Post by MadCow108 on 2009-05-10
this should work:
add folling to a text file:
#!/bin/bash
rhythmbox &
PID=$!
conky &
CONKYPID=$!
wait $PID
kill $CONKYPID

then make the file executable
chmod u+x filename

and now direct the launcher at the file

actually the most simple solution from MaxIBoy should work too if you add the line to an executable file instead of the alias
#!/bin/bash
conky & rythmbox; killall conky

---

### Post by americano70e10 on 2009-05-10
This one worked...

```

#!/bin/bash
rhythmbox &
PID=$!
conky &
CONKYPID=$!
wait $PID
kill $CONKYPID

```

The others didn't... And thanks for your help guys!!!

---

