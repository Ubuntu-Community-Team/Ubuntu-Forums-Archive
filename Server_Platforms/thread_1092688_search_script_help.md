---
title: "search script help"
date: 2009-03-10
forum: Server Platforms
---

### Post by komputes on 2009-03-10
I would like to get some help writing a search script, or more carefully said, a very carefully structured command or set of commands to accomplish the goal of searching within a folder for file which contain a word. The goal is to facilitate searching logs, transcript and such. If anyone who has more experience with grep and scripting thinks this would be a useful shell alias to have, I'd appreciate the help.

grep would be at the base of the script, as it is powerful enough, but not always simple enough to use. when you have a desktop you have a series of tools to help you search, but I am not that familiar for searching the command line except for grep. I'm trying to make a command that will be the command line equivalent of the 'searchmonkey' package for the server platform. If something like this already exists please let me know.

The command :
```
$ search outloud
```The back end :
```
#!
IN=outloud
grep -i $IN ./*


```The output:
```
./chatlog47312:<somedude_> so i says to him, i says outloud
Binary file ./movie_01_01.mpg matches
```[I][B]My questions:
[/B][/I] 
  - How do I direct the input (the word) "outloud" to the middle of the command? I now have "IN=outloud" as a placeholder but since I don't want to have to edit the script every time i want to use the command, that would be counter-productive. 

   - I would still like the user to be able to use the -r -R recurive option, would this still be possible?

   - What needs to be done to change the search parameter to accept a sentence or a sequence of words?

:-k

---

### Post by bluefrog on 2009-03-11
I am afraid that what you are trying to do will be very counter productive as per your fear.

You'd better use grep as is and eventually use aliases (alias grep='grep -i')

otherwise:
#!/bin/bash
grep -i "$@" 

would take anything given to your search command as argument

---

### Post by hyper_ch on 2009-03-11
or run this script from a directory where you want to search:

```

#!/bin/bash
find . -exec grep $1 '{}' \; -print

```

and run it like

```

./script.sh KEYWORD

```

---

