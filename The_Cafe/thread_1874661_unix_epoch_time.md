---
title: "unix epoch time"
date: 2011-11-03
forum: The Cafe
---

### Post by cybo on 2011-11-03
i'm not new to *nix but this issue started to bug me. we all know that there exists unix epoch time, which is number of seconds since 00:00:00 Jan 1 1970. here is the question. why do we need it? what is its purpose? why do we keep track of this time? is there anybody out there who used this time? what did you use it for? and why? 

any answers are welcomed.

---

### Post by dcstar on 2011-11-04
> **cybo said:**
> i'm not new to *nix but this issue started to bug me. we all know that there exists unix epoch time, which is number of seconds since 00:00:00 Jan 1 1970. here is the question. why do we need it? what is its purpose? why do we keep track of this time? is there anybody out there who used this time? what did you use it for? and why? 

any answers are welcomed.

It makes Linux work.

---

### Post by prodigy_ on 2011-11-04
> **cybo said:**
> this issue
Please, explain why you think this is an issue.

---

### Post by alco75 on 2011-11-04
You have to store times somehow. Most modern databases support their own datetime datatype, but storing times as integers is a reasonable database-independent solution. Arithmetic operations on integers are fast; determining the time between two timestamps is just a subtraction operation.

Once you've decided to store times as integers, you obviously then need a zero-time. The number of seconds since the birth of the baby Jesus wouldn't be terribly practical, so something arbitrary, but sensible, was chosen: number of seconds since January 1, 1970.

---

### Post by cybo on 2011-11-07
@alco75

thanks for the explanation it makes sense.

---

### Post by cybo on 2011-11-07
> **prodigy_ said:**
> Please, explain why you think this is an issue.

can you please point out what issue specifically you are talking about?

if you are asking about why i'm asking this question then i simply wanted to know why we use this strange epoch time. these days every computer has an real-time-clock circuit, which can keep track of time in standard format, HH-MM-SS etc. but as far as i know when engineers design something, and especially with *nix systems, they have something in mind. i just needed to know what was the reason for using epoch time. explanation provided by alco75 made sense.

---

### Post by Vaphell on 2011-11-07
i think he simply quoted 'issue' from your post: i'm not new to *nix but this **issue**... :) 'issue' suggests that there is some problem and he dismissed such a notion.

when the standard was being put in place memory was a luxury. You had to come up with tricks to compress the data. Going with full year/month/day/hour/minute/second would be way to generous and bloated. Integer <-> date translation is straightforward so it was a good solution.
Sure, now few bytes more don't mean much today but then you have that thing called 'backward compatibility'. Every day we depend on systems that depend on that format. Redesigning would be a huge task, work done to alleviate y2k bug is peanuts in comparison.

---

### Post by philinux on 2011-11-07
Moved to Cafe forum.

---

### Post by cybo on 2011-11-07
thanks everyone for explanation. it did make things a lot clearer. and thanks to philinux for moving this thread into the right location.

---

### Post by Paqman on 2011-11-07
Technically there is an "issue" with the system, in that you can only go as far as 2038 with a 32-bit integer. So any 32-bit or less Unixy systems still around on 19 January 2038 are liable to get very confused.

---

### Post by Thewhistlingwind on 2011-11-07
> **Paqman said:**
> Technically there is an "issue" with the system, in that you can only go as far as 2038 with a 32-bit integer. So any 32-bit or less Unixy systems still around on 19 January 2038 are liable to get very confused.

Actually, if you've ever tried to boot a system that has a time earlier then the date it's root directory was created, you'd know it just fails.

I wouldn't want to be on the roads come January 19th 2038.

---

### Post by Paqman on 2011-11-07
> **Thewhistlingwind said:**
> 
I wouldn't want to be on the roads come January 19th 2038.

Sorta what they said about December 31 1999. Critical systems will be upgraded if necessary, I'm sure.

---

### Post by Thewhistlingwind on 2011-11-07
> **Paqman said:**
> Sorta what they said about December 31 1999. Critical systems will be upgraded if necessary, I'm sure.

Windows wasn't (And still isn't (And hopefully never will be)) the standard for embedded electronics.

2038 will make Y2K look like what it was, peanuts.

EDIT: After consulting with people who claim to know the subject better than me, it is unlikely that any critical systems in a car use Unix-like OS's. They are not suitable.

---

