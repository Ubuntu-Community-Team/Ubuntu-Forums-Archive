---
title: "linux on an old pc"
date: 2006-03-26
forum: The Cafe
---

### Post by mzilhao on 2006-03-26
hey all,

so, i want to get that old pentium II at 200 Mhz working for my kid brother.
what linux distro would you recommend? 
ubuntu is WAY to heavy... the breezy live cd took almost 30 mins to boot, and it jammed the computer...
damn small linux is too minimal...
the computer used to have windows 98 on it and it worked ok, but i can't get the wireless network to work under win 98... 
will xubuntu work ok on a 200 Mhz computer? and what about Debian? 
anybody know a good distro that would work ok? 

thanks in advance
Miguel

---

### Post by GeneralZod on 2006-03-26
How much RAM? That tends to be more of a bottleneck that CPU speed.  Also, you say that DSL was "too minimal" - what extra stuff does your brother need, and are you sure you can't add those things to a DSL install?

Also, try [vectorlinux](http://www.vectorlinux.com/).

---

### Post by Randomskk on 2006-03-26
DSL can be extended very easily - from the pc, click the "MyDSL" icon, or if the pc doesn't have internet access you can download .dsl files on a pc that does, save to a USB/floppy/CD and put it in the DSL pc, open the file manager, find the .dsl and click the "MyDSL" button at the top middle menu on it to install.

What else do you need on it, though? There are DSLs for OOo, Skype, gAIM, all sorts.

---

### Post by mzilhao on 2006-03-26
i think it has 256 MB RAM, but i'm not sure... maybe it's only 128... it does have a decent hard drive (20Gb).
an office suite (like open office), a few games and internet access would be cool. DSL didn't recognise the usb wireless stick...

thanks!

---

### Post by Randomskk on 2006-03-26
Reconising USB wireless sticks always seems to be a bugger :D
I believe you could get ndiswrapper working on DSL, and use that - if not, look around and maybe there's a driver.
Consider using wired internet, too :P

---

### Post by mstlyevil on 2006-03-26
[QUOTE=mzilhao]i think it has 256 MB RAM, but i'm not sure... maybe it's only 128... it does have a decent hard drive (20Gb).
an office suite (like open office), a few games and internet access would be cool. DSL didn't recognise the usb wireless stick...

thanks![/QUOTE]

Xubuntu would be perfect for it if the computer has only 128 megs of RAM. Ubuntu will run fine on a computer with 256 megs of RAM.

---

### Post by mzilhao on 2006-03-26
i did try to use ndiswrapper with DSL, but it didn't work... :-(
i may give Xubuntu and Vector Linux a try...

---

### Post by teet on 2006-03-26
I don't know your "linux skill level" or anything, but you might try doing a server install of ubuntu (just type "server" when you boot off the breezy cd instead of just hitting enter).  I just think that even xubuntu may be too much gui for that computer...maybe I'm wrong.

After it gets done installing, use nano to edit /etc/apt/sources.list and uncomment the extra repos and add in the multiverse repos.  Then just do an:

sudo apt-get install fluxbox rox-filer dillo xdm

You might have to add in some other things (x-window-system-core ?) but this would give you pretty much the minimal install of a gui.  You could then add in things like abiword or firefox if you wanted (although firefox may be a little too heavy).

Alternatively, I use puppy linux on my 200 mhz pentium I (64 mb ram).  It's very windows 95/98 like.  It also uses the older, but faster, 2.4 kernel.  Puppy linux may be the easiest option.  Although, if you didn't like DSL, you probably won't like puppy.

-teet

---

### Post by ssam on 2006-03-26
live cds need far more ram than installs.

i recon an install of xubuntu work run ok.

---

### Post by red_shrike on 2006-03-31
Debian woody, if you can install it. It runs like crazy man

---

### Post by Vulpus on 2006-04-07
[QUOTE=mzilhao]hey all,

so, i want to get that old pentium II at 200 Mhz working for my kid brother.
what linux distro would you recommend? 
ubuntu is WAY to heavy... the breezy live cd took almost 30 mins to boot, and it jammed the computer...
damn small linux is too minimal...
the computer used to have windows 98 on it and it worked ok, but i can't get the wireless network to work under win 98... 
will xubuntu work ok on a 200 Mhz computer? and what about Debian? 
anybody know a good distro that would work ok? 

thanks in advance
Miguel[/QUOTE]

Take a look at Zenwalk!  It runs on very basic hardware but looks like a 'proper' distro.  [www.zenwalk.org](www.zenwalk.org)

---

### Post by freedomforme on 2006-04-07
Well most any liveCD is going to take forever on that.:)

maybe Debian w/xfce or icewm w/nautilus or rox w/firefox and balsa
~~what else ya need~~
:)
Or libranet even though it is getting a bit older and is more than likely dead.

Parsix is a good distro, still a bit heavy but might do! Of course nothing beats dapper! :D

---

### Post by IYY on 2006-04-07
All liveCDs (maybe with the exception of DSL) will work very slowly on such a machine, but I think you could get decent performance with any of the Debians, even Ubuntu, if you use the right software.

For example, ROX for the file/desktop manager, IceWM/Fluxbox as the window manager, dillo for web browsing whenever it's possible.

---

