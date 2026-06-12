---
title: "Software accelerated AIGLX/Compiz?"
date: 2006-09-07
forum: The Cafe
---

### Post by Mathiasdm on 2006-09-07
If I understood correctly, we can have those fancy effects because the processing is off-loaded to the GPU.

Would there be any way to simulate this using the CPU?

I'm mainly asking because I have an SiS 760 on my laptop, and I'm 99% sure it'll never get 3D acceleration on Linux.

I think it would be a nice idea to activate such effects when no processor-intensive tasks are running, and de-activate it when it's needed (for a laptop: when using the battery).

I would like to give this a try, but I don't know if it's possible.

---

### Post by jdong on 2006-09-07
well, if it's possible, it'll likely be horrendously slow.... That probably explains why nobody's bothered to implement it yet.

---

### Post by Mathiasdm on 2006-09-07
Well, that's what I'm curious about.

Most computers have a huge amount of processing power, but are much slower at processing graphics than the graphics card (sounds logical :-P ).

However, if things like Compiz are possible, even on reasonably 'light' graphics cards, wouldn't it work on the CPU as well?

---

### Post by chaosgeisterchen on 2006-09-07
You confuse sth. Graphic cards are built for showing graphical effects. They bring their performance natively.

CPUs must imitiate every little bit of the GPU to give you AIGLX on a software emphasis. I do not know the factor but the processor needs several times the performance of a graphic chip to imitiate its performance.

---

