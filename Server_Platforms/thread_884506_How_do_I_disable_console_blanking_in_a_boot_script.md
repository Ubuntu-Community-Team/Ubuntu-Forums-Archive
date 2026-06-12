---
title: "How do I disable console blanking in a boot script?"
date: 2008-08-09
forum: Server Platforms
---

### Post by alecm3 on 2008-08-09
I am running Hardy Heron (no X).
I need to have something on boot that disables console blanking.

Including 

setterm -blank 0 -powerdown 0 -powersave off
or 
setterm -blank 0 -powerdown 0 -powersave off > /dev/console
or
setterm -blank 0 -powerdown 0 -powersave off < /dev/console > /dev/console

in /etc/rc.local does not help: monitor still blanks out after 10 minutes.

Editing /etc/console-tools/config 
BLANK_TIME=0

does not help either.

Executing setterm -blank 0 -powerdown 0 -powersave off on the console does help, it stays on.

---

### Post by DraakUSA on 2008-09-29
If you place the commands in rc.local you probably need the following:

[INDENT][FONT="Courier New"]for index in $(seq 1 6)
do
[INDENT]setterm -blank 0 -powerdown 0 -powersave off > /dev/tty${index}[/INDENT]
done[/FONT][/INDENT]

There are actually 6 virtual consoles by default (accessed via Alt-F1 through Alt-F6).

---

