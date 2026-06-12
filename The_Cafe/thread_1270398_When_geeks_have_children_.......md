---
title: "When geeks have children ......"
date: 2009-09-19
forum: The Cafe
---

### Post by renzokuken on 2009-09-19
When geeks have children ...... they do this

[http://www.youtube.com/watch?v=bYcF_xX2DE8](http://www.youtube.com/watch?v=bYcF_xX2DE8)

brilliant

---

### Post by scragar on 2009-09-19
What a grossly inefficient solution. Any simple motor could produce a cleaner rocking motion without the horrible jerk that the CD tray produces and without the horrible wait, and as for ```
while [ 1 = 1]
``` All I can say is I'm ashamed.

---

### Post by querent on 2009-09-19
Hey!  be nice.  Maybe they didn't have any motors on hand.

I'm sure there are better ways, but it works.

---

### Post by Hosmion on 2009-09-19
Can you seriously program it to open and close like that?

---

### Post by PurposeOfReason on 2009-09-19
> **Hosmion said:**
> Can you seriously program it to open and close like that?
Yup, but I would just use ```
while true
```

It's hardly geeky, it's a bash script with four lines.

---

### Post by JordyD on 2009-09-19
> **Hosmion said:**
> Can you seriously program it to open and close like that?

Yeah, why not? He actually shows you the code for it in the beginning of the video.

---

### Post by Tipped OuT on 2009-09-19
Geeks have babies? Well this is news to me. :lolflag:

---

### Post by scragar on 2009-09-19
> **PurposeOfReason said:**
> Yup, but I would just use ```
while true
```

It's hardly geeky, it's a bash script with four lines.

```
while true; do
  eject -T /dev/cdrom
done
```Please, the code is so much easier and shorter than what he wrote, I don't understand that large thing when this version works perfectly.

---

### Post by hoppipolla on 2009-09-19
Haha that's great! Quite possibly the most random thing I've seen all day, but great! lol :)

---

### Post by lisati on 2009-09-19
> **scragar said:**
> What a grossly inefficient solution. Any simple motor could produce a cleaner rocking motion without the horrible jerk that the CD tray produces and without the horrible wait, and as for ```
while [ 1 = 1]
``` All I can say is I'm ashamed.

How sloppy! Using **goto** would be more elegant than **while 1=1**

---

### Post by PurposeOfReason on 2009-09-19
> **scragar said:**
> ```
while true; do
  eject -T /dev/cdrom
done
```Please, the code is so much easier and shorter than what he wrote, I don't understand that large thing when this version works perfectly.
I wasn't sure if there was a switch to eject and close the tray and was too lazy to look it up. You should sent that to him fr the lols.

---

### Post by hoppipolla on 2009-09-19
I don't think the exact code is the point here though.. lol

It's just funny ^_^

---

### Post by MikeTheC on 2009-09-19
> **When geeks have children ......**
It's through artificial insemination?

---

### Post by scragar on 2009-09-19
> **lisati said:**
> How sloppy! Using **goto** would be more elegant than **while 1=1**

... :frown:

Please tell you you aren't trying to promote a goto.

---

### Post by ctrlmd on 2009-09-19
lol its funny video 
creative idea

---

### Post by MikeTheC on 2009-09-19
> **scragar said:**
> ... :frown:

Please tell you you aren't trying to promote a goto.

Why? What's wrong with GOTO? I used to use it all the time back in high school when I futzed around in GW-BASIC.

---

### Post by scragar on 2009-09-19
> **MikeTheC said:**
> Why? What's wrong with GOTO? I used to use it all the time back in high school when I futzed around in GW-BASIC.

/me doesn't want to hear it.

---

### Post by PurposeOfReason on 2009-09-19
> **MikeTheC said:**
> Why? What's wrong with GOTO? I used to use it all the time back in high school when I futzed around in GW-BASIC.
Because if that one line gets moved then everything is messed up. Goto and any command the references a line is horrible practice.

---

### Post by MikeTheC on 2009-09-19
> **PurposeOfReason said:**
> Because if that one line gets moved then everything is messed up. Goto and any command the references a line is horrible practice.

Hmm... Well, I'm not quite sure what other options one would have in GW-BASIC, although I will also readily admit I have never, ever been even remotely close to a knowledgeable person (let alone a power user) of GW-BASIC.

Apart from line numbers, how do more commonly-used programming languages differ? And, for that matter, just strictly on the basis of curiosity, what other options besides GOTO does one have in modern languages?

---

### Post by scragar on 2009-09-19
functions and loops.

---

### Post by MikeTheC on 2009-09-19
> **scragar said:**
> functions and loops.

Which means *what*, exactly?

---

### Post by Namtabmai on 2009-09-19
GOTO is seen as bad as it generally lead to [Spaghetti code](http://en.wikipedia.org/wiki/Spaghetti_code).

On small programs it may seem fine, but once it gets bigger have to track where all the code jump are and go to can lead to code that is very difficult to manage.

Ideally you should be breaking you code down in to manageable chunks/functional and calling them where needed, and of course for/while loops where appropriate.

I've been programming for about 10 years now and I've yet to encounter a problem where I'd use GOTO. That said [Donald Knuth](http://en.wikipedia.org/wiki/Donald_Knuth) is a man I respect and he states that GOTO can be more efficient in some circumstances.

---

### Post by Muppeteer on 2009-09-19
Jeez, it's getting all geeky in here...Just laugh and forget all the technical crap :popcorn:

---

