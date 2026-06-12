---
title: "Disassemblers/editors for linux"
date: 2008-08-15
forum: Security
---

### Post by Intangir on 2008-08-15
im looking for any good disassemblers for linux
i know objdump can make a big dumped file disassembly, but what i want is one that will link jumps/calls, figure where functions start/end by rets

possibly generate some sort of graphical hierachy of calling structures

i found alot of REALLLY OOOOLD stuff/scripts that did these things before supposedly, but none of them appear to be working anymore.

id love one that will allow you to EDIT the assembly in real time, i heard of a program named ht that supposedly allowed that but i had no luck getting it to work or run in X in any useful way.. i got it to open files for hex editing if i ran it outside of X (so the hotkeys could work) but thats just inpractical and extremely dated..

i saw a program named dissy which looked very promising from the screenshots, but i havent gotten it to work AT ALL, its even in the repositories, anything i try to open.. i tried over a dozen things .. nothing happens, nothing loads. sometimes i get errors in terminal window about nm: no symbols, but anything your going to want to disassemble will likely have no symbols.. so i hope its not relying on that to even run

i found a useful hex editor named bless which seems to work
gdb works
and objdump..

theres gotta be something better than these extremely basic, extremely low level, command line operated tools. something integrated.. something that serves more than 1 basic rudimentary function perhaps..

---

### Post by gatorbait on 2008-08-18
The IDA Pro Freeware works well in Wine: ([http://www.hex-rays.com/idapro/idadownfreeware.htm](http://www.hex-rays.com/idapro/idadownfreeware.htm))

---

### Post by The Tronyx on 2008-08-19
I guess my first question would be, what is it you want to do?

Crack software?  Find vulnerabilities?  Simply edit on the fly?

---

