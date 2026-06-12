---
title: "I made my very first program!"
date: 2008-03-25
forum: The Cafe
---

### Post by hhhhhx on 2008-03-25
from 3:00 to 4:00 clock last night i started learning python, and this is what i came up with a super simple program that calculates download time...


what do you think?

```
$  python 1.py
```(this is my first time programing, so im still new lol)

---

### Post by LaRoza on 2008-03-25
It is bigger than my first program :-)

There are a few things you should do differently:

[php]
#! /usr/bin/python

print " Welcome to the bittorent downoad time calculation program"
print "-----------------------"
print
print

print "What is the unit of meashure?"
print "  1 -- kb"
print "  2 -- mb"
print "  3 -- gb"
mes = raw_input(">:  ")

if mes == '1':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = size/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."

elif mes == '2':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = (size*1024)/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."

elif mes == '3':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = (size*1024*1024)/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."
else:
   print "Unknown option"
[/php]

The changes:
[list]
[*] Added a shebang.
[*] Change all input() to raw_input()
[*] Change the input to a numeric datatype because raw_input() returns strings
[*] Add a catch so an unknown option is not ignored.
[/list]

---

### Post by fedex1993 on 2008-03-25
where did you learn from i tried to learbn but my ADD becomes a conflict

---

### Post by hhhhhx on 2008-03-25
> **LaRoza said:**
> It is bigger than my first program :-)

There are a few things you should do differently:

[php]
#! /usr/bin/python

print " Welcome to the bittorent downoad time calculation program"
print "-----------------------"
print
print

print "What is the unit of meashure?"
print "  1 -- kb"
print "  2 -- mb"
print "  3 -- gb"
mes = raw_input(">:  ")

if mes == '1':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = size/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."

elif mes == '2':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = (size*1024)/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."

elif mes == '3':
   size = float(raw_input("What is the file size? >:"))
   rate = float(raw_input("What is the rate? (kb/s) >:"))
   time = (size*1024*1024)/rate
   print
   print
   print "Your download will be finished in", time,"seconds or", time/60, "minuts."
else:
   print "Unknown option"
[/php]
Whoa!, what is the difference between float(raw_input()) and input() , sorry i dont yet know what strings are, ive only had about an hr of learning

---

### Post by hhhhhx on 2008-03-25
> **fedex1993 said:**
> where did you learn from i tried to learbn but my ADD becomes a conflict
from links in LaRosa's sig,

---

### Post by LaRoza on 2008-03-25
> **xhhux said:**
> Whoa!, what is the difference between float(raw_input()) and input() ?

also i got the link to the guides from your sig :)

On the Python page in my wiki, there is a link to an article named "saving users from themselves" : [http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

The problem with input() is that it takes a python expression and runs it. In your program, it takes a number, which is what you want, but that doesn't stop anyone from putting other things in it.

raw_input() works similiarly, but it just takes a string. Because it takes a string (character data) you can't perform math on it, so float() is used to change the content to a number. Now this is unsafe, as if the input isn't able to be converted, it will through and exception. My advice is to not worry about exceptions at the moment.

Thanks for using my wiki, hope it continues to be useful.

---

### Post by Mr. Picklesworth on 2008-03-25
Hey, that's not bad. Just proves how easy Python is!

(Although you are indenting with spaces. I'm a tabs person. Grr...)

One issue *I*I see here is that you have 3 different If statements, all for a very similar operation. As a rule of thumb, if you are repeating a notable ammount of code in different places, there is a better solution. (Creating custom functions, or using variables).
It is bad practise to duplicate code since it makes it difficult to maintain if, for example, you decide down the line to change the text displayed by your program or need to fix a bug. As a convenient example, you have a typo saying "minuts" instead of "minutes". Now you have to fix that in three different places!

In your case, one simple way to fix this repetition would be to have your program set a new variable for the unit of measure based on "mes". Indeed, that means the same "if mes == 1:" deal you already have, but the important part is not having anything other than, for example, "size_kb  = 1024" in those new If blocks.

Thus, you only need one copy of that code you *currently* have in the three Ifs (the inputs for size, and the time calculation), which would make your program shorter, easier to understand and easier to maintain!

---

### Post by LaRoza on 2008-03-25
> **Mr. Picklesworth said:**
> Hey, that's not bad. Just proves how easy Python is!

(Although you are indenting with spaces. I'm a tabs person. Grr...)


Worse, they are three spaces, not four spaces like Python is normally coded in.

@OP You are free to use whatever you want, but most of the time, Python is coded using four space indents.

---

### Post by fissionmailed on 2008-03-25
My first program printed "Hello, world!" and that was about it.   I love learning new computer languages.  I know some C, C++, Python and Perl, which I just started.  Not that I'm any good but I enjoy it. :)

---

### Post by Mr. Picklesworth on 2008-03-25
> @OP You are free to use whatever you want, but most of the time, Python is coded using four space indents.

	Oh, no you don't! Crazy lunatics, trying to pollute innocent minds, sheesh.
    Do not allow these tempters to twist your thoughts. There is still chance for forgiveness; ```
use tabs or you will go 
                        straight to indentation-    	  	   	          	!!!!
```             ...The worst place imaginable for the indentation-concerned!

  As you may guessed, there is much controversy in that topic. The good thing is it really doesn't matter; just go with whatever works for you. People must adapt between different styles of indenting all the time, because everyone has a different idea for what an indentation is but they can't be changed afterward without creating a really horrific patch... Sane developers generally sigh grumpily the first time they see a project using indentation styles other than their own and then move on with it.

---

### Post by hhhhhx on 2008-03-25
Thank you all for your input, i made some changes based on what you said. also, LaRosa, i got better results using float(raw_input()) rather than the input() :)

@MR. Picklesworth, i dont think that i quite understand what you mean, or how to do it, sorry i am very new to this.

---

### Post by LaRoza on 2008-03-25
> **Mr. Picklesworth said:**
> Oh no you don't! Trying to pollute innocent minds, sheesh. Tabs all the way!

As you may guessed, there is much controversy in that topic. The good thing is it really doesn't matter; just go with whatever works for you. People must adapt between different styles of indenting all the time, because everyone has a different idea for what an indentation is but they can't be changed afterward without creating a really horrific patch...

Here are my religious beliefs in programming (just for disclosure):

[list]
[*] Vim
[*] Four space indents
[*] Aligning braces
[/list]

---

### Post by fissionmailed on 2008-03-25
> **LaRoza said:**
> Here are my religious beliefs in programming (just for disclosure):

[list]
[*] Vim
[*] Four space indents
[*] Aligning braces
[/list]

That's how I learned it from my C++ prof, except he used gedit for the class(some of them where complete computer noobs), but I later picked up Vim on my own.

---

### Post by fedex1993 on 2008-03-25
i like bluefish but i am adapting to vim finally  :)is vim only terminal or is there a graphical envirment  for it?

---

### Post by LaRoza on 2008-03-25
> **fedex1993 said:**
> i like bluefish but i am adapting to vim finally  :)is vim only terminal or is there a graphical envirment  for it?

You can use gVim, but I never do.

---

### Post by fedex1993 on 2008-03-25
ahh okay thanks laroza i miss your red name it was easyer to find in the user groups LOL

---

### Post by Mr. Picklesworth on 2008-03-25
> **xhhux said:**
> @MR. Picklesworth, i dont think that i quite understand what you mean, or how to do it, sorry i am very new to this.

No problem. Here is an example so you can see what I mean:
```
print " Welcome to the downoad time calculation program"
print "-----------------------"
print
print

print "What is the unit of meashure?"
print "  1 -- kb"
print "  2 -- mb"
print "  3 -- gb"
mes = input(">:  ")

if mes == 1:
   unit_kb = 1 #Units are in kilobytes

if mes == 2:
   unit_kb = 1024 #Units are megabytes (1024 kilobytes)

if mes == 3:
   unit_kb = 1024*1024 #Units are gigabytes (1024*1024 kilobytes)

size = input("What is the file size? >:")
rate = input("What is the rate? (kb/s) >:")
time = (size*unit_kb)/rate
print
print
print "Your download will be finished in", time,"seconds or", time/60, "minuts." #FIXME: This typo. Now we only need to fix it in one place!
```

---

### Post by hhhhhx on 2008-03-25
> **Mr. Picklesworth said:**
> No problem. Here is an example so you can see what I mean:
```
print " Welcome to the downoad time calculation program"
print "-----------------------"
print
print

print "What is the unit of meashure?"
print "  1 -- kb"
print "  2 -- mb"
print "  3 -- gb"
mes = input(">:  ")

if mes == 1:
   unit_kb = 1 #Units are in kilobytes

if mes == 2:
   unit_kb = 1024 #Units are megabytes (1024 kilobytes)

if mes == 3:
   unit_kb = 1024*1024 #Units are gigabytes (1024*1024 kilobytes)

size = input("What is the file size? >:")
rate = input("What is the rate? (kb/s) >:")
time = (size*unit_kb)/rate
print
print
print "Your download will be finished in", time,"seconds or", time/60, "minuts." #FIXME: This typo. Now we only need to fix it in one place!
```
thanks   :)

---

### Post by iSplicer on 2008-03-25
Nice job, my first program was

print "hello world!"

---

### Post by DeadSuperHero on 2008-03-26
> **Mr. Picklesworth said:**
> Oh, no you don't! Crazy lunatics, trying to pollute innocent minds, sheesh.



Best. Post. Ever. :lolflag:

---

### Post by hhhhhx on 2008-03-26
i shnazzed it up a little bit, thanks a lot LaRosa and Mr. Picklesworth :)

```
#! /usr/bin/python


print "welcometo the program..."
print 
print

print "Please select a unit of measure:"
print " 1 -- kb"
print " 2 -- mb"
print " 3 -- gb"
print " 4 -- tb"
print
mes = float(raw_input(">:  "))

print
print "--------------------------------------"
print "Please select a rate of download:"
print " 1 -- kb/s"
print " 2 -- mb/s"
print " 3 -- gb/s"
print " 4 -- tb/s"
print
rat = float(raw_input(">:  "))

if mes == 1:
    unit_mes = 1
if mes == 2:
    unit_mes = 1024
if mes == 3:
    unit_mes = 1024*1024
if mes == 4:
    unit_mes = 1024*1024*1024

if rat == 1:
    unit_rat = 1
if rat == 2:
    unit_rat = 1024
if rat == 3:
    unit_rat = 1024*1024
if rat == 4:
    unit_rat = 1024*1024*1024
print
print "--------------------------------------"
size = float(raw_input("What is the size of the file? >:  "))
print
print "--------------------------------------"
rate = float(raw_input("What is the download rate? >:  "))
time = (size*unit_mes)/(rate*unit_rat)
print
print "--------------------------------------"
print
print "Your download will be finished in", time,"seconds or", time/60, "minuts."#yes, i know that it is still there 
```

---

