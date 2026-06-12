---
title: "how do i use time as a variable in bash?"
date: 2009-07-15
forum: The Cafe
---

### Post by chriskin on 2009-07-15
variable might not be the right way to call it, anyway let's say what i "need" to do

i want a script to add the current hours with the minutes and use the last digit of the number that comes out of it to choose one of the options coming later on in the script.

can you help me?

---

### Post by Tibuda on 2009-07-15
Start with this:
```
H=`date +%H`
M=`date +%M`
expr $H + $M
```

---

### Post by Barrucadu on 2009-07-15
```
hours=`date +%H`
minutes=`date +%M`
sum=$[$hours + $minutes]
digit=`echo $sum | sed -e 's/\(^.*\)\(.$\)/\2/'`
```

That last line isn't particularly nice&#8230; In zsh it would just be digit=$sum[-1]

---

### Post by Tibuda on 2009-07-15
I have to learn how to use awk, it's so powerful. Right now, I have done it using grep.

```
D=$(expr `date +%H` + `date +%M` | grep [0-9]$ -o)
echo $D

```

---

### Post by monsterstack on 2009-07-15
Edit: oh balls, didn't see the "last digit" part of your post. Well, others have already told you how to get that. Hope the rest of this helps!

Sure thing. First, grab the time variables:
		
```
minute=$( date +%M )	
```	

Then just make your options:

```
if   [[ $minute == 01 ]]; then
    echo option one;
elif [[ $minute == 02 ]]; then
    echo option two;
    echo etc; fi

```

Or, if you don't want to have to make sixty different options, use ranges:

```
if   [[ $minute -ge 0 && $minute -lt 20 ]]; then
    echo between 0 and 20 minutes
    echo code goes here
elif [[ $minute -ge 20 && $minute -lt 40 ]]; then
    echo between 20 and 40 minutes
    echo code goes here
else
    echo anything else; fi
```

Shout if you need more help.

---

### Post by chriskin on 2009-07-15
*can you tell me how i would put the $H + $M into a variable so i can use it later on?* <--i found it on one of the answers
thanks for the answers

---

### Post by chriskin on 2009-07-15
i might be too stupid for bash's tutorials

how do i use if to choose between possible choices?
i mean

if sum is lower than 25, do that
if sum is between 25 and 60 , do that
if sum is between 60 and 84 , do that
and then end the if command 

that would be the last question, i promise :)

---

### Post by monsterstack on 2009-07-15
> **chriskin said:**
> i might be too stupid for bash's tutorials

how do i use if to choose between possible choices?
i mean

if sum is lower than 25, do that
if sum is between 25 and 60 , do that
if sum is between 60 and 84 , do that
and then end the if command 

that would be the last question, i promise :)

I gave the answer in my last (off-topic) post. It now becomes relevant at last! Say you named your variable "poop", do this:

```
if [[ $poop -ge  0 && $poop -lt 25 ]]; then **echo code goes here**; fi
if [[ $poop -ge 25 && $poop -lt 60 ]]; then **echo code goes here**; fi
if [[ $poop -ge 60 && $poop -lt 84 ]]; then **echo code goes here**; fi
```

Which in English means,

[INDENT]If poop is **greater than or equal to** (-ge) 0, **and** **less than** (-lt) 25, **then** stuff happens.[/INDENT]

And so on.

---

### Post by chriskin on 2009-07-15
i saw your post above but my knowledge of bash is so little that i didn't even understand it :P

i just started with this script

thanks again, will try to check it now :)

edit : yep, it works
thanks :)
:popcorn:

---

### Post by koleoptero on 2009-07-15
> **monsterstack said:**
> 
Which in English means,

[INDENT]If *poop* is **greater than or equal to** (-ge) 0, **and** **less than** (-lt) 25, **then** **stuff happens**.[/INDENT]

And so on.

:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

