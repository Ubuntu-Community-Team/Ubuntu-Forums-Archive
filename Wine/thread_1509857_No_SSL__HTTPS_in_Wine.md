---
title: "No SSL / HTTPS in Wine"
date: 2010-06-14
forum: Wine
---

### Post by standards on 2010-06-14
Hi, I've looked everywhere and although I've read numerous hints about solving this problem they're all from years ago and now seem to be "fixed", except I still can't get it to work. 

Ubuntu 10.4 x86_64
Wine 1.2 rc3

My ultimate goal is to use a 3rd party program that logs into a financial institution via SSL, but as a guinea pig I'm using IE7. 

I can download and run IE7 via winetricks just fine, but any and all HTTPS sites (banks particularly- something like gmail or ebay works fine) just time out or are completely inaccessible. Is there some sort of higher level SSL dependency I'm missing?

I also have downloaded all the wine dependencies and have built it from scratch via the package and it still doesn't work. Again, everything else about wine as far as I can tell works beautifully.

Thanks in advance

---

### Post by cogadh on 2010-06-14
I think the problem is IE7, it doesn't actually work in Wine. You might be better off using Firefox in Wine.

---

### Post by standards on 2010-06-15
I don't really care if IE works, I want my other software to work. IE is just easier to demonstrate the problem.

edit: oh wait i get what you're saying. I'll test with FF.

---

