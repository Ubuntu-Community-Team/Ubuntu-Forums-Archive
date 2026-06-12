---
title: "Apache log unreadable after rotate"
date: 2010-11-07
forum: Server Platforms
---

### Post by mistypotato on 2010-11-07
Hi,

Odd problem with ONE of my Apache logs.

After rotating, the log is there and growing...but I cannot open it with gedit like I can all the others.  The backed up copy still opens just fine...just not the current new one that is being appended to with each web access of the site in question.

Gedit says something about it cannot read the character encoding.

When I ran the command **file myfile** it says 
"ASCII text with very long lines"

All the other logs that were rotated are fine and open normally.

I opened the log in question with gvim and it appears normal....meaning the contents look the same as the files that are opening as expected.

I tried opening the file with gvim, then saving it back with a new name but the new file has the same problem.

Been working on this for a day or two now and decided it was time to seek assistance.
[B]
Any idea why Gedit cannot open this file?[/B]

Thx for yours :KS

---

### Post by mistypotato on 2010-12-04
The solution was that there WAS no solution.

Noone at this or any other forum where I posted this problem could offer an answer.

I ended up rotating out the log and recreating it.

So far, no problems with the new copy.

---

### Post by Ryan Dwyer on 2010-12-04
It happens when a character in the file is outside the standard ASCII range or something like that. It could be a weird character it someone's user agent or requested URL. gEdit then fails to detect that it's a plain text file and refuses to open it. It's lame like that.

---

