---
title: "I need some kind of word counting tool"
date: 2005-03-29
forum: The Cafe
---

### Post by primeirocrime on 2005-03-29
Hello fellow [COLOR=Red]Ubunters[/COLOR]

[COLOR=DarkRed]I've[/COLOR] been searching in the babylonic temples for a word counting tool/app/script but with no luck.
To be specific I need something that counts the number of words, how many times do they apear. Frequency, most repeated words and stuff ackin to statistics.

[COLOR=DarkRed]Is[/COLOR] there any Floss tool liike that? I'm using grep in the terminal window but it's not very fast to do what I am planning to do.
I want to analise several different books for a arts project. Any help will be  immeasurable*[Y] splendid 

*one of the words that repeats over and over in The Lotus Sutra

Cheers to all out there.

---

### Post by negatory on 2005-03-29
Have you tried word count console program?What are you trying to count?A text document?

Pedro Carrico

---

### Post by primeirocrime on 2005-03-29
[QUOTE=negatory]Have you tried word count console program?What are you trying to count?A text document?

Pedro Carrico[/QUOTE]
 several text documents. actually it's entire books. I trying to find some patterns in words used in religious books [western and eastern] so I'll need a specific tool to do this task. Something that scans the document a retrieves  a listing like this:

a -17685954304
be- 34792387490
repeat - 32672 
burried - 23
christ - 15
golgota - 2

and also frequency analysis that would be nice.


but I want to do this to something like 15 classical texts maybe more. an I need to have a visual output of the process. 
I know that compression tools do this in order to compress text so there must be a kind of  tool to do this. wc only gives me total words,

---

### Post by jdodson on 2005-03-29
[QUOTE=primeirocrime]several text documents. actually it's entire books. I trying to find some patterns in words used in religious books [western and eastern] so I'll need a specific tool to do this task. Something that scans the document a retrieves  a listing like this:

a -17685954304
be- 34792387490
repeat - 32672 
burried - 23
christ - 15
golgota - 2

and also frequency analysis that would be nice.


but I want to do this to something like 15 classical texts maybe more. an I need to have a visual output of the process. 
I know that compression tools do this in order to compress text so there must be a kind of  tool to do this. wc only gives me total words,[/QUOTE]

run this from the console:

```
man wc
``` 

if that isnt what you are looking for i wrote a python script to do what you want, i could send it to you.

---

### Post by primeirocrime on 2005-03-29
[http://www.niederlandistik.fu-berlin.de/textstat/software-en.html](http://www.niederlandistik.fu-berlin.de/textstat/software-en.html) 

check that one out !

I think it's this what I was looking for. :)

but I can still try out you python script. Man I love the web. I have an idea and 5 hours latter there is a way to put it into practice. eh eh eh

thanks negatory and jdodson :)

yay to ubunters

---

### Post by az on 2005-03-29
There is probably a Perl one-liner out there to do what you need.

---

