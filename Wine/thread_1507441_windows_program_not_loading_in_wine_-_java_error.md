---
title: "windows program not loading in wine - java error?"
date: 2010-06-11
forum: Wine
---

### Post by mikeprosceo on 2010-06-11
Re: loading java in wine?
This is the error I get when trying to load a windows based program in wine. It seems to be a java error but it also says to see problematic frame for where to report the bug. Anyone have any ideas, please??

The crash happened outside the Java Virtual Machine in native code.

# See problematic frame for where to report the bug.

#
I am having trouble loading a windows based work problem into ubuntu 10.0.4 via wine.  I have re installed java (needed to load the exe file) into wine to make sure java wasn't downloaded improperly. Attached is the full error message I get the following error message.  I have no idea how to proceed from here, other than putting windows back on my computer. ugh.  Please anyone, help.





A fatal error has been detected by the Java Runtime Environment:

#

# Internal Error (0x80000101), pid=39, tid=54

#

# JRE version: 6.0_20-b02

# Java VM: Java HotSpot(TM) Client VM (16.3-b01 mixed mode windows-x86 )

# Problematic frame:

# C 0xf77e2425

---

### Post by asdfoo on 2010-06-13
you haven't told us which version of Wine you are using...

wine-1.2-rc3 is the most recent

---

### Post by mikeprosceo on 2010-06-13
Sorry, yes I am using the newest release of wine 1.2-rc3

---

### Post by asdfoo on 2010-06-13
The only thing I can suggest is to try installing an earlier version of java to see if it makes a difference.  I see you have Java 1.6, but within 1.6 sun has released many updates (you appear to have the most recent), so you could try an earlier one.

---

