---
title: "Even with rekonq %U set as default browser in KDE 4, RSS feeds opened w/ winebrowser?"
date: 2010-10-01
forum: Wine
---

### Post by murderslastcrow on 2010-10-01
Okay, this is weird. So, I hadn't used Wine for a long time, and I've had the feed reading applications running just fine- I click a link and it takes me into rekonq. However, when I installed Wine again, my RSS readers, Krunner, and all applications opening web links tried to open in winebrowser (which results in nothing but an endless slew of winebrowsers trying to open until I kill wineserver).

So, I go to Default Applications and set the browser manually to rekonq %U, and everything is working great- except for the feed-readers. Apparently xdg-open is somehow involved, and I don't know how I'm supposed to restrict the feed readers from thinking winebrowser is my primary web browser.

Does anyone know a fix or a simple way to resolve this? (command line counts as simple for me) I'd really rather keep my Wine applications handy if I could- thanks for your input. I know this isn't a support forum, but I don't know a better place to mention this.

---

### Post by murderslastcrow on 2010-10-02
*subtle bump*

---

### Post by pyrforos on 2010-11-04
i have the same problem...

EDIT: I found a solution here [http://www.webupd8.org/2010/03/how-to-make-wine-open-links-in-your.html](http://www.webupd8.org/2010/03/how-to-make-wine-open-links-in-your.html)
going to try it out


EDIT2 :didn't work for me so i found the problem .Seems that wine associated all applications and protocols that have to do with internet , like .html , .xml ecc. to open with winebrowser.

So if you right clik a html file and change the application you want to open with you are ok!
Works fine

---

