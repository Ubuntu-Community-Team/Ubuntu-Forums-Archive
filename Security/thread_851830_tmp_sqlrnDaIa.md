---
title: "/tmp: sqlrnDaIa"
date: 2008-07-07
forum: Security
---

### Post by cjtjamandra on 2008-07-07
When i opened the file it contains:

show variables like 'datadir'

is this normal or it an attack?

---

### Post by ProbablyX on 2008-07-07
I'd think it's a file made by some program that chooses random names for it's temporary files.
Remember that /tmp is just a place for temporary or "junk" data.

Most likely a program needed to save some data, maybe from the RAM memory. It created a file, as its nothing important - that can be removed when the app stops, it just takes a random name and puts it there.
Then it just remembers that files name if it needs it later. Once the app ends, it expects your system will remove all files in /tmp after reboot.

---

