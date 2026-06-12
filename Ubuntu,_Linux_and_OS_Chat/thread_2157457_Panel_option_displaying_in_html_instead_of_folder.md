---
title: "Panel option displaying in html instead of folder"
date: 2013-06-25
forum: Ubuntu, Linux and OS Chat
---

### Post by ndex477 on 2013-06-25
Any help would be greatly appreciated. When i select Places/Home Folder from my top panel it use to display the folders in my Home Folder, now it displays them in a html list. How can i change it back to the original format? Thank you very much in advance.

---

### Post by gordintoronto on 2013-06-25
What version of Ubuntu? I don't understand what you mean by "a html list". Does it open in Firefox?

---

### Post by ndex477 on 2013-07-17
I used to go to Places on my panel and  then select a folder (Home, Documents etc.) and it would show folders. Now it list them on a page titlored Index of file:///root/Documents. By the way, sorry for taking so long to respond. Thanks for your consideration.

---

### Post by Copper Bezel on 2013-07-18
1. Which desktop are you running? That is, the default Unity desktop, Gnome, Xfce, etc.

2. Run [FONT=courier new]xdg-open ~ [/FONT]to see what the default handler is for locations. Most likely, you'll get that browser window again, but let's check to be sure.

I've seen this when I was running a standalone window manager instead of a full desktop environment, as a result of xdg-open getting confused, but not on a full desktop.

---

