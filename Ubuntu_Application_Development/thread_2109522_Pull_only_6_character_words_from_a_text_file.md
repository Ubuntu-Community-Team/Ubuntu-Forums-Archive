---
title: "Pull only 6 character words from a text file"
date: 2013-01-27
forum: Ubuntu Application Development
---

### Post by takuie on 2013-01-27
I cant seem to find much on the internet for this, hopefully you guys can help.  I have a large list of names in a text file and I want to **only** extract the names with 6 characters and ignore anything greater or less than 6 characters in that word.  

would be nice to drop these results in a separate text file.
Any suggestions?

---

### Post by steeldriver on 2013-01-27
How about 'grep' ?

```
$ cat names
fred
albert
boris
wendy
george
michael
$
$ grep -Ew '[[:alpha:]]{6}' names
albert
george

```

---

### Post by takuie on 2013-01-27
That worked! 

1 more question,  is there a way to capture that info and write into a separate text file?

Forgive my noobness, only recently gave windows the finger and switch over to the ubuntu/linux world.

---

### Post by takuie on 2013-01-27
nvm, >> filename ftw!

---

### Post by slickymaster on 2013-01-27
```
 grep -Ew '[[:alpha:]]{6}' names > textfile.txt
```

Keep in mind that the &#8220;>&#8221; redirection operator always rewrittes files from the beginning. So if you don't want to rewrite a file, use the &#8220;>>&#8221; redirection operator, which will append the output to the end of the file without overwriting it.

---

### Post by steeldriver on 2013-01-27
^^^

Also I forgot to mention if the names aren't one-per-line you may want to use the '-o' option e.g.

```
$ cat names2
fred albert boris 
wendy george 
michael 

```results in```
$ grep -Ew '[[:alpha:]]{6}' names2
fred albert boris 
wendy george 
```(probably not what you want) but

```
$ grep -Ew[COLOR=Red]**o**[/COLOR] '[[:alpha:]]{6}' names2
albert
george

```You can do

```
man grep
```to get a complete overview - have fun

---

### Post by takuie on 2013-01-27
Thank you all for your input.  It has all been useful.  Thats what I love about the ubuntu community, instead of giving me a fish, you teach me how to fish!

---

