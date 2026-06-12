---
title: "MS Office 2007 crashes with large files"
date: 2010-07-28
forum: Wine
---

### Post by marquee moon on 2010-07-28
I've succesfully installed MS office in WINE using the instructions [here](http://www.programmerfish.com/roffice-2007-in-linux/). No problem installing. In excel & word, I tested the new install by creating a file & saving, closing down, then opening them again. That works. 

Then I tried using my documents. I have a 90 page word document with frequent images inbedded, and quite a few excel files that often run to 15,000 rows of data, each with twenty or more collumns. 

At this point, my Ubuntu 10.04 desktop grey'd up. When I close office by right clicking the panel, I'm told the program is not responding, and I "end task" 
 
The documents work on Open Office on the same PC, and also work on MS office in Windows (at work). 

I've opened a medium size data file in excel- a few hundred data points with a simple line graph, and this works. Its just the *really* big files that appear to be the problem. 

Can this be resolved easily? 
I've wondered whether its my RAM (1Gb, which has been plenty for ubuntu previously, even when using these large office files).

---

### Post by asdfoo on 2010-07-29
> **marquee moon said:**
> I've succesfully installed MS office in WINE using the instructions [here](http://www.programmerfish.com/roffice-2007-in-linux/). No problem installing. In excel & word, I tested the new install by creating a file & saving, closing down, then opening them again. That works. 

Then I tried using my documents. I have a 90 page word document with frequent images inbedded, and quite a few excel files that often run to 15,000 rows of data, each with twenty or more collumns. 

At this point, my Ubuntu 10.04 desktop grey'd up. When I close office by right clicking the panel, I'm told the program is not responding, and I "end task" 
 
The documents work on Open Office on the same PC, and also work on MS office in Windows (at work). 

I've opened a medium size data file in excel- a few hundred data points with a simple line graph, and this works. Its just the *really* big files that appear to be the problem. 

Can this be resolved easily? 
I've wondered whether its my RAM (1Gb, which has been plenty for ubuntu previously, even when using these large office files).

are you using the most recent version of Wine? open a terminal and type `wine --version`

it should print 1.2

---

