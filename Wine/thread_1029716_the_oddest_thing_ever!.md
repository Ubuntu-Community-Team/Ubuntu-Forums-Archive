---
title: "the oddest thing ever!"
date: 2009-01-03
forum: Wine
---

### Post by nubix on 2009-01-03
im using ubuntu 8.10, i asume im using the latest version of wine.

im sure the title says it all. thanks in advance. please help!
it gets to the splash screen but doesn't seem to progress past that. it does not hang however it just disapears.

---

### Post by sirdilznik on 2009-01-03
The title does not say it all.  In fact the title doesn't really say anything.  What program are you trying to run through wine?  Have you run it from a terminal?  If so what was the output?

Edit:  Ok, I see cnc as a tag.  Were you running command and conquer perhaps?  Anyway whatever the program, run it from a terminal and paste any output.

---

### Post by nubix on 2009-01-03
sorry, i was simply reposting the body of another thread. the game is called command and conquer 3 tibierium wars. it seems to run fine according to winehq. but i cant seem to launch it past the splash screen. i have not tryed to run it through the terminal because i don't know how, i have however heard of trying that before. please help me! thanks...

---

### Post by sirdilznik on 2009-01-03
You need to open a terminal and change directory to the directory where the executable for the game is located.  Most browsers have an option to either open a terminal window from a given directory or have a terminal built in to the browser itself.  So you can just move the browser to the folder where the game executable is located, probably something along the lines of '~/.wine/drive_c/Program Files/<name of game company>/<name of game>'.  Once in a terminal in the proper directory it would simply be ```
wine <executable.exe>
```Probably something like ```
wine Command3.exe
```

---

### Post by nubix on 2009-01-03
cody@ubuntu:~$ /home/cody/.wine/dosdevices/c:/Program Files/Electronic Arts/Command & Conquer 3/cnc3.exe
[1] 10754
bash: /home/cody/.wine/dosdevices/c:/Program: No such file or directory
bash: Conquer: command not found
[1]+  Exit 127                /home/cody/.wine/dosdevices/c:/Program Files/Electronic Arts/Command
cody@ubuntu:~$ 



im doing something wrong

---

### Post by sirdilznik on 2009-01-03
> **nubix said:**
> cody@ubuntu:~$ /home/cody/.wine/dosdevices/c:/Program Files/Electronic Arts/Command & Conquer 3/cnc3.exe
[1] 10754
bash: /home/cody/.wine/dosdevices/c:/Program: No such file or directory
bash: Conquer: command not found
[1]+  Exit 127                /home/cody/.wine/dosdevices/c:/Program Files/Electronic Arts/Command
cody@ubuntu:~$ 



im doing something wrong

The problem is the spaces in file/directory names.  Windows has no problems with spaces in file names, but Linux (or any *nix type system) does not recognize spaces the same way.  The way to remedy this is to put quotes (single or double, there is technically a difference but either will work in this case I believe) around the file name which tells bash (the shell you're in when in a terminal) to ignore special characters and take the filename exactly how it is written.  You don't have to change directory to a specific directory if you give the complete path to a file so with that in mind (and since I can see from your post the file you are trying to run, try this and post the output:```
wine '/home/cody/.wine/dosdevices/c:/Program Files/Electronic Arts/Command & Conquer 3/cnc3.exe'
```

---

### Post by nubix on 2009-01-03
it says i have 10 to many images for some reason, so i posted this txt file instead, its the output

---

### Post by sirdilznik on 2009-01-03
Ok I looked at the output and this is probably where my level of expertise starts to be exceeded, but I looked at the winehq appdb entry for the game and there is a bug filed with a description matching your own (crashes after splash screen) and a very similar terminal output.  Here it is:

[http://bugs.winehq.org/show_bug.cgi?id=16016](http://bugs.winehq.org/show_bug.cgi?id=16016)

There is a mention of using a cracked cnc3game.dat, though I'm not sure of how appropriate discussing cracks is on the forums (though if you own the game then it's not warez I guess).  Anyway, before replacing any files make sure you make a backup copy of the original file if that's what you decide to do.

---

### Post by nubix on 2009-01-03
well thank you for your help! i will try to make due with the info youve given me =P

---

