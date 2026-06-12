---
title: "Why vim uses h, j, k and l to move the cursor?"
date: 2013-06-25
forum: The Cafe
---

### Post by azzamite on 2013-06-25
Anyone knows the mnemonics to remember where each key moves the cursor to?

I can't find the documentation telling why those keys were chosen, I remember it
was something like:

```
          ???
           k
           | North
       /-------\
       |       |
??? h--|  you  |--l ???
  West |       | East
       \-------/
           | South
           j
     (Lake?) Java
             ^
```

Any ideas about the other 3?

---

### Post by papibe on 2013-06-25
Hi azzamite.

Not exactly mnemonics, but the way I learned it was like this:

Since the keys are close together in a row, put your hand over the keyboard and put each finger over a key:
[LIST]
[*]index over the h,
[*]middle over the j,
[*]ring over the k, and
[*]pinky over the l.
[/LIST]
Then it is very easy to understand index (h) as left, and pinky as (l) right.

Just a thought.
Regards.

---

### Post by Old_Grey_Wolf on 2013-06-25
When Bill Joy created the vi text editor he used the ADM-3A terminal which had the arrows on the HJKL keys. The ADM-3A terminal did not have dedicated arrow keys.

---

### Post by TheFu on 2013-06-25
The terminals that I learn on didn't have arrow keys at all.  At work, we didn't get terminals with arrows until 1991.

---

### Post by sanderj on 2013-06-25
> **Old_Grey_Wolf said:**
> When Bill Joy created the vi text editor he used the ADM-3A terminal which had the arrows on the HJKL keys. The ADM-3A terminal did not have dedicated arrow keys.

Ah, cool! ... and here's the proof from [http://rollmops.wordpress.com/2006/05/01/vintage-computer/](http://rollmops.wordpress.com/2006/05/01/vintage-computer/)


[IMG]http://rollmops.files.wordpress.com/2006/04/Lear_Siegler-ADM3A_1805.jpg[/IMG]

---

### Post by sanderj on 2013-06-25
PS:

And we all know that Gmail uses the same J and K keys for Down and Up through your mails ...

---

### Post by azzamite on 2013-06-25
Interesting, thanks everyone!

---

### Post by Old_Grey_Wolf on 2013-06-25
> **sanderj said:**
> Ah, cool! ... and here's the proof from [http://rollmops.wordpress.com/2006/05/01/vintage-computer/](http://rollmops.wordpress.com/2006/05/01/vintage-computer/)

I have to admit I didn't realize the significance of cd ~

 LOL

---

### Post by Erik1984 on 2013-06-25
Wow, this thread is educational! :P Didn't know both things (tilde for home folder and origins of HJKL).

---

### Post by markbl on 2013-06-25
Just as an aside - if I am looking over the shoulders of another software developer and I see him move his fingers over to the arrow keys to navigate around vim then I immediately write him off as a noob .... ;)

---

