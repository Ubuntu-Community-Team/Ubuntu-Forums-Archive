---
title: "Odd wine directory behavior."
date: 2007-04-19
forum: The Cafe
---

### Post by Patrick K on 2007-04-19
Here is something odd I found. Opening the wine "C" drive then the \Windows\profiles\"Username"\My Documents directory, I found the entire directory tree from my /home directory residing there. Opening the .wine directory in this buried directory I found the above repeated again. That is, in \Windows\profiles\"Username"\My Documents, the entire /home directory tree is there again. I drill down several more layers but never found a bottom. Interestingly, the files are active, at least text and picture files can be opened. 

Anyone else find this most unusual behavior. 

I doubt these files really exist since that would fill the entire partition in short order.

---

### Post by tbroderick on 2007-04-19
Its just a symlink.

---

