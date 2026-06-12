---
title: "Print server for about 250 people, tracking usage including account codes."
date: 2018-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by garycarrollhome on 2018-08-06
I need to set up a solution for a university print shop that wants to 
[LIST]
[*]accept print jobs from 200 to 300 people,
[*]allow the people to input around five fields of information in the print dialog box, and
[*]record those fields plus other basic information such as job name, time, number of pages, media and finishing (staple or not, duplex or not, etc) requested.
[/LIST]
That there are over 200 users implies the list is constantly changing. We don’t want to have to install software on the user computers. The vast majority of the users will be Windows, but there will be Macs in the mix too.

I’m thinking we use a Linux box as a font-end / print server for the printer. We define a PS printer queue with a PPD. On the server we use tea4cups to send a copy of the PS to a program that parses it and extracts the required data for accounting.
 
This is high level conceptualizing, but I don’t really have an idea HOW to do this, or if it’s the best way, or a good way, or even whether it will really work as I imagine.
 
Before I start trying to figure this out, am I on the right track?

---

### Post by wildmanne39 on 2018-08-06
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by wyliecoyoteuk on 2018-08-07
PyKota sounds like what you need, as it is the parent of tea4cups.
However, it hasn't been updated in over 10 years.

---

### Post by garycarrollhome on 2018-08-07
> **wyliecoyoteuk said:**
> PyKota sounds like what you need, as it is the parent of tea4cups.
However, it hasn't been updated in over 10 years.

Do you know if that means "still works, and is stable as bedrock" or "not longer works with anything in this universe"?  
Thanks, by the way.

---

### Post by wyliecoyoteuk on 2018-08-07
Sorry, no idea, I work for a Printer dealership.
In terms of software, we support PapercutMF, which inexpensive compared to most other offerings and runs on Linux, Windows and Macs.
It can also manage copying and scanning on MFDs, and best of all it is nice and easy to use.
[https://www.papercut.com/](https://www.papercut.com/)

---

