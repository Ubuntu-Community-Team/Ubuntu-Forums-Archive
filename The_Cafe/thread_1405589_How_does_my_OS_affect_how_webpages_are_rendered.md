---
title: "How does my OS affect how webpages are rendered?"
date: 2010-02-12
forum: The Cafe
---

### Post by dyingsun on 2010-02-12
Hi all

I just spent a couple of days working on a new site for somebody, and there is one particular page giving me trouble. I was building it on my Ubuntu box, as always, using Firefox for testing, but when I went to test on a Windows machine, it displays wrong, the divs won't play nicely.

I know about fixing the CSS for IE, etc, but it doesnt seem to be related just to IE - all the browsers on my windows box display it the same - the only config that works is when I view the page on Firefox 3.0.17 on this Jaunty 64 bit install. Konqueror doesn't work either.

So, what kind of factors can make a page display differently in the same browsers on different OS's? I'm not at liberty to post code, but the CSS properties that are directly applied to the offending divs are width, border,padding and float. 

I know it's not much to go on, the owner is very protective and wont let me share the code :)  But if anyone has some general ideas about where to start looking, I'd be really grateful.

TIA!

---

### Post by sxmaxchine on 2010-02-12
as far as i was aware the OS didnt affect page loading it was your browser, it could be a problem with the program you developed it on try copying the code and make it with a different program. sorry i cant be more help, but i also would like to know if an OS affects a webpage.

---

### Post by diesch on 2010-02-12
Not all fonts are available on all platforms and the available fonts may have different metrics.

Maybe you could create a minimal example that demonstrates the problem but isn't related to the real files.

---

### Post by Sam on 2010-02-12
Do you have any screenshot that show the difference between Ubuntu and Windows ?

---

### Post by dyingsun on 2010-02-14
Hi, thanks for your responses everyone - it does appear to be font metrics as you suggested, Diesch. I've switched to using ems for font sizing, and it's working fine now. Going to investigate a little deeper so as to understand the "why" a bit better.

Thanks!
Damien

---

