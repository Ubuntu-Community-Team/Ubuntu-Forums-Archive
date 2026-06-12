---
title: "Print &quot;Trouble&quot; - Two Papers out"
date: 2006-08-14
forum: Server Platforms
---

### Post by DanHober on 2006-08-14
Hi
 Im with a little trouble with my print Epson LX300, Samba shared as Epson Dot Matrix. When a send a print job from a DOS application in a Windows/DOS machine (theses machines are DOS W95/6.22 with LanMan and using LPT1 to \\linux\epson), it print, but another form sheet (a second page exactly) go out in print... 

Lpd is running to print control and my /etc/printcap is:

lp|Epson
      :lp=/dev/lp0
      :sd=/var/spool/lpd/lp
      :af=/var/log/lp-acct
      :lf=/var/log/lp-errs
      : pl#66
      : pw#80
      : pc#150
      :mx#0
      :sh

I try change pl, pw, pc values, but not hapenned :(
I try add px and py, not success too..


:arrow: Sorry my english if I dont know as describle my problem correctily

Edited: put a space :_here_pl

---

### Post by Iowan on 2006-08-14
Is the second page another copy of the first - or is it a blank page?

---

### Post by DanHober on 2006-08-15
A blank page... Thanks Iowan

---

### Post by DanHober on 2006-08-17
Up :(

---

### Post by bergi on 2006-10-28
Hi,

my problem is as follows:
When i try to print a pdf with acrobad reader (edgy - cups - HL-2030) it prints the first page and then a blank one, then it goes with mostly no more blank page printing the rest. At second print job it mostly occurs again (second page white but 'toasted'). Has anyone idea(s)?

[http://www.pcwelt.de/forum/drucker/220636-brother-hl-2030-zieht-ein-blatt-papier-zuviel.html]("http://www.pcwelt.de/forum/drucker/220636-brother-hl-2030-zieht-ein-blatt-papier-zuviel.html") (German)
Here communication problems are mentioned (although its between a thinclient and a printer)

Could CUPS or lpr or any other tool be the problem (or solution)?

---

