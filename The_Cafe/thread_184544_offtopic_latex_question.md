---
title: "offtopic: latex question"
date: 2006-05-30
forum: The Cafe
---

### Post by phen on 2006-05-30
hello all,
maybe one of you is able to help me with this offtopic-problem:
I work with latex for my studies, and i have to write the same equations very very often. I wonder if it is possible to save often used expressions in some kind of a variable?

for example, i have to write \frac{c1}{M d 3} in nearly every equation. i could save it in a variable like %fraction_1% or something...

thank you for your help!

---

### Post by GeneralZod on 2006-06-01
Look into the \newcommand ... command :)  Something along the lines of:

```

\newcommand{\phenfrac}{\ensuremath{\frac{c1}{M d 3} i}}

```

You can now replace this string of symbols with "\phenfrac".  The \newcommand call should be made near the beginning of your document - many people have a separate "definitions.tex" file containing all their custom macros/ commands/ environments, which they then \include into the main document.

It is highly recommended that you make use of this as much as is possible, and not just to save your typing fingers - if you ever need to change the notation for something, you'll only need to change it in one place.  Plus, separating semantics (the meaning of the string of symbols "\frac{c1}{M d 3} i" which I assume stands for something special [I've called this "something" "phenfrac"; you'll doubtless have a more descriptive name for it!]) from the actual presentation (the string of symbols representing the concept of phenphrac; i.e. the string "\frac{c1}{M d 3} i") is generally good practice in all fields.  You can use arguments/ parameters with \newcommand, too, in case "frac{c1}{M d 3} i" is a template that you wish to put specific values into at different times.

---

### Post by curuxz on 2006-06-01
call me stupid...but from the title i expected this thread to be about something else entirely...

---

### Post by Rikostan on 2006-06-01
[QUOTE=curuxz]call me stupid...but from the title i expected this thread to be about something else entirely...[/QUOTE]

Ahahaha I was *hoping* it was about something else. :)

---

### Post by sherlock-holmes on 2006-06-01
[QUOTE=Rikostan]Ahahaha I was *hoping* it was about something else. :)[/QUOTE]


yup... the 'x' at the end....:cool:

---

### Post by phen on 2006-06-07
hehe, what did you expect? :)

thank you, generalzod! that's exactly what i was looking for!

---

