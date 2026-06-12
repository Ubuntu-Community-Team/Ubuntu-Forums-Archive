---
title: "Conky with 16 CPU"
date: 2009-07-09
forum: The Cafe
---

### Post by lukeiamyourfather on 2009-07-09
The system I'm using has 16 processing cores (four socket Opteron system with quad cores) and I'd like to setup Conky to show all of them. If it try this in the .conkyrc, everything after 10 shows up as zero.

```

TEXT

${cpugraph cpu1}
${cpugraph cpu2}
${cpugraph cpu3}
${cpugraph cpu4}
${cpugraph cpu5}
${cpugraph cpu6}
${cpugraph cpu7}
${cpugraph cpu8}
${cpugraph cpu9}
${cpugraph "cpu10"}
${cpugraph "cpu11"}
${cpugraph "cpu12"}
${cpugraph "cpu13"}
${cpugraph "cpu14"}
${cpugraph "cpu15"}
${cpugraph "cpu16"}

```

Same with anything else that uses the cpuN variable. Am I using this incorrectly or is there a bug in Conky that will only allow 10 CPU to be monitored? Thanks for the help. Cheers!

---

### Post by Cam42 on 2009-07-09
Why are the quotes around the last 7?

---

### Post by lukeiamyourfather on 2009-07-09
> **Cam42 said:**
> Why are the quotes around the last 7?

Oh yeah, forgot about those. With the quotes they all show the exact same information that isn't correct like they are all referencing the first CPU or something else that all returns the same number, and without quotes they show zero.

---

### Post by lukeiamyourfather on 2009-07-09
Maybe this will help to clarify what's going on since its broke either way. Screens and code for each configuration using Conky 1.6.1 on Ubuntu 9.04 (default version of Conky in the repository). First one is the TEXT portion of the .conkyrc with quotes.

```
TEXT

${cpugraph "cpu1" 30,256}
${cpugraph "cpu2" 30,256}
${cpugraph "cpu3" 30,256}
${cpugraph "cpu4" 30,256}
${cpugraph "cpu5" 30,256}
${cpugraph "cpu6" 30,256}
${cpugraph "cpu7" 30,256}
${cpugraph "cpu8" 30,256}
${cpugraph "cpu9" 30,256}
${cpugraph "cpu10" 30,256}
${cpugraph "cpu11" 30,256}
${cpugraph "cpu12" 30,256}
${cpugraph "cpu13" 30,256}
${cpugraph "cpu14" 30,256}
${cpugraph "cpu15" 30,256}
${cpugraph "cpu16" 30,256}
```

Here's the TEXT portion of the .conkyrc without quotes. This seems to break CPU2 as well?

```
TEXT

${cpugraph cpu1 30,256}
${cpugraph cpu2 30,256}
${cpugraph cpu3 30,256}
${cpugraph cpu4 30,256}
${cpugraph cpu5 30,256}
${cpugraph cpu6 30,256}
${cpugraph cpu7 30,256}
${cpugraph cpu8 30,256}
${cpugraph cpu9 30,256}
${cpugraph cpu10 30,256}
${cpugraph cpu11 30,256}
${cpugraph cpu12 30,256}
${cpugraph cpu13 30,256}
${cpugraph cpu14 30,256}
${cpugraph cpu15 30,256}
${cpugraph cpu16 30,256}
```

The screen captures of each are attached, quote or no quote is in the title of the image. Seems like there's something in the code of Conky that breaks with more than 10 CPU. Maybe someone can confirm this or maybe has a workaround, or suggestion? Cheers!

---

### Post by juancarlospaco on 2009-07-09
*Conky Bug ...?*

---

### Post by lukeiamyourfather on 2009-07-09
> **juancarlospaco said:**
> *Conky Bug ...?*

I guess so. :(

Does the syntax look correct for the graph? Right now I'm downloading the source for Conky 1.7.1.1 to compile and see if there's any difference compared to 1.6.1 in Ubuntu.

---

### Post by lukeiamyourfather on 2009-07-13
I sent an email to the Conky mailing list, not a single reply. :-k

---

### Post by Vadi on 2009-07-13
Seems like a bug that it's not allowing double-digits.

---

### Post by JillSwift on 2009-07-13
This may well just be silly, but what if the digits are really in hex?
Try :

```
...
${cpugraph "cpu8" 30,256}
${cpugraph "cpu9" 30,256}
${cpugraph "cpuA" 30,256}
${cpugraph "cpuB" 30,256}
...
```

---

### Post by hanzomon4 on 2009-07-13
What do you use 16 CPUs for?

---

### Post by tom66 on 2009-07-13
Servers?

---

### Post by lukeiamyourfather on 2009-07-13
> **JillSwift said:**
> This may well just be silly, but what if the digits are really in hex?
Try :

```
...
${cpugraph "cpu8" 30,256}
${cpugraph "cpu9" 30,256}
${cpugraph "cpuA" 30,256}
${cpugraph "cpuB" 30,256}
...
```

That was a good idea, but it doesn't seem to work. The values default to "cpu0" which is the average of all processors. I'll submit a bug and hope it gets read? If I knew C I'd dive in myself but all I know right now is Python. Cheers!

---

### Post by lukeiamyourfather on 2009-07-13
> **hanzomon4 said:**
> What do you use 16 CPUs for?

The link in my signature shows some of my work. Mostly fluid simulations for animation and film visual effects. Cheers!

---

### Post by JillSwift on 2009-07-13
> **lukeiamyourfather said:**
> The link in my signature shows some of my work. Mostly fluid simulations for animation and film visual effects. Cheers!
Your 2008 demo reel clip is very cool =^_^=

---

### Post by Kithera on 2012-04-03
I have a suspicion, I think they are just looking at that first character, and doing a blind ASCII to integer conversion. If that's the case, you could try just adding the next character in ASCII to see what happens.

Using the chart here, and noting that  '9' is decimal 57, the character for 58 is ':'. What does "cpu:" do?

---

