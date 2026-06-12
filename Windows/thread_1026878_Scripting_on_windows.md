---
title: "Scripting on windows"
date: 2008-12-31
forum: Windows
---

### Post by lykwydchykyn on 2008-12-31
Anyone know where I can find a good guide to writing cmd scripts on Windows -- something like the BASH beginner's guide only for Windows cmd?

I tried googling for a while, but everything I turned up was useless.

---

### Post by Grant A. on 2009-01-02
BASH doesn't exist on Windows; however, there are a lot of ASH commands on there. You can find some rather intuitive videos on YouTube, but you may want to try the Windows Powershell and its language if you want real scripting.

---

### Post by lykwydchykyn on 2009-01-02
> **Grant A. said:**
> BASH doesn't exist on Windows; however, there are a lot of ASH commands on there. You can find some rather intuitive videos on YouTube, but you may want to try the Windows Powershell and its language if you want real scripting.

Well, there are any number of shells I COULD use, but I need to stick to something built-in.  I'm just searching for a primer/reference for writing .cmd scripts (modern-day batch files, basically), but so far I can't find anything (except a lot of articles and blogs explaining to Windows users the value of scripting/CLI, with a few minimally-explained example scripts).

If I was going to install something extra to run the scripts, I'd just put Python on there and be done with it.  But that defeats the purpose for what I need to do.

---

### Post by cabbiinc on 2009-01-02
Would this [http://commandwindows.com/index.html](http://commandwindows.com/index.html) be of any help?

---

### Post by lykwydchykyn on 2009-01-02
That site's a great start, thanks!
you don't happen to know how I can do string manipulation in a batch/cmd file, do you?  I've seen people do some stuff like:

set variable=%variable.texttoremove=%

..to remove text from a string, but it doesn't work for me.  I can't find a definitive reference of how to do that anywhere.

---

### Post by ghostdog74 on 2009-01-03
> **Grant A. said:**
> BASH doesn't exist on Windows; 
although bash doesn't exist on windows, however, with cygwin, or even the Microsoft Services for Unix, you able to write bash on Windows.
anyway, to the OP, for "scripting" in windows, I would recommend you to learn vbscript instead of the cmd (since you don't want to install platform independent languages like Python). It packs more punches to what batch can offer. Search google for script56.chm. Go to the first link that shows up and download the guide.

---

### Post by cmay on 2009-01-04
try look for old dos scripting tutorials. i used Freedos so i have books about dos and there is lots of information in these but i do not use it that much. i would rather want to use Freebasic than dos shell scripting. maybe there is links to something trough freedos homepage or wikipedia.

---

### Post by cabbiinc on 2009-01-06
[http://www.microsoft.com/technet/scriptcenter/hubs/start.mspx](http://www.microsoft.com/technet/scriptcenter/hubs/start.mspx)

---

