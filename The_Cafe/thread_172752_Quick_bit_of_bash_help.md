---
title: "Quick bit of bash help"
date: 2006-05-09
forum: The Cafe
---

### Post by paul.maddox on 2006-05-09
I'm trying to write a quick bash script to delete all files in a directory under a certain filesize (say for example 1MB).

Has anyone got any good ways of getting that list of files?

I've checked the list of bash test operators and can't find anything about filesizes apart from one to check if it's bigger than 0bytes.

So far the best I can think of is looping through all files in the directory, then running ls -s on them to get the filesize, parse that and then compare to see if it's bigger/smaller than 1MB.

Is there a much nicer way of doing it? There must be!

---

### Post by Engnome on 2006-05-09
I dont know any bash scripting, but I in most programming languages doing what you describe would turn out to be something like:

for(every file in folder)
   {
    sizeof(file)
    if(size > 1mb) {
    delete
   }

:cool:  You should google for some bash guides.

---

### Post by mostwanted on 2006-05-09
There's a programming forum.

---

### Post by kabus on 2006-05-09
'find' can test for size.

---

### Post by paul.maddox on 2006-05-09
[QUOTE=mostwanted]There's a programming forum.[/QUOTE]
Sorry, my mistake I did not see it.


[QUOTE=kabus]'find' can test for size.[/QUOTE]
Thanks! Looking at find's manpage it looks like I can do:
```
find /downloads/music/ripped/*mp3 -size -1500k -delete
```


Cheers!

---

