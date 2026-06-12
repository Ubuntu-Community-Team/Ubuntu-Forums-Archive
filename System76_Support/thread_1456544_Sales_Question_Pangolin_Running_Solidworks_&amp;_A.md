---
title: "Sales Question: Pangolin Running Solidworks &amp; Autocad in Virtualbox"
date: 2010-04-17
forum: System76 Support
---

### Post by Groucho Marxist on 2010-04-17
My mother needs a new computer after years of frustrated dealings with a major vendor which shall not be named. As I have been more than pleased with System76 and their Pangolin Performance laptop (which I am currently using to compose this message), I have recommend that she use System76 computers from now on. 

She does not wish to use Windows Vista or 7 and wants to use Ubuntu Linux for everyday tasks (i.e. checking e-mail, listening to music, etc). However, being a mechanical engineer, my mother needs to run Windows XP in order to use the following programs:

[LIST=1]
[*]Solidworks
[*]Autocad
[/LIST]
Does anyone know if the aforementioned programs will run smoothly within Virtualbox on the following System76 laptop configuration?

**Pangolin Performance**
Core i7-620M Processor ( 32nm, 4MB L3 Cache, 2.66GHz )
8 GB – DDR3 1066 MHZ 2 DIMMs
320 GB 7200 RPM SATA II

I will post more questions if they come up; until then, my thanks in advance to anyone who can help answer this question!

---

### Post by Groucho Marxist on 2010-04-18
Riddle me this, riddle me thy
I hope that this BUMP
Will prompt a reply

---

### Post by gamerchick02 on 2010-04-18
That configuration should be great for a VM.

I've run a VM on my PanP5 with only 4 gb ram and it was a hair slow, but everything worked.

The hardware looks like it can support it, and it looks like you're getting plenty of ram for her to use.

Amy

---

### Post by Groucho Marxist on 2010-04-18
> **gamerchick02 said:**
> That configuration should be great for a VM.

I've run a VM on my PanP5 with only 4 gb ram and it was a hair slow, but everything worked.

The hardware looks like it can support it, and it looks like you're getting plenty of ram for her to use.

Amy

Thanks for the reply! :) 

I know that my PanP5 can run hot while using VM for Adobe or Civ III gaming. Would running, say, Solidworks in a VM be a problem in terms of cooling the laptop?

---

### Post by gamerchick02 on 2010-04-18
My laptop runs warm when playing video games under Win7.

I'd suggest a cooling mat thingy if you're worried about heat buildup.

I haven't run Solidworks in a long time and when I did it was on an old Dell workhorse.  I didn't notice heat issues then, but I'm not sure how it'll translate to the Pangolian.  Sorry I can't be of more help.

Amy

---

### Post by thomasaaron on 2010-04-19
As long as no XP drivers are needed to run XP in Virtualbox, you should be fine. I don't *think* any are necessary, but maybe some customers can chime in with that.

I know that Guest Editions takes care of networking and screen resolution. Not sure about the rest of it.

We can't get XP drivers for any of the laptops in our new line-up.

---

### Post by samalex on 2010-04-20
I haven't tried Solidworks or AutoCad, but I do run VirtualBox 3.1.6 with Windows XP Pro and it runs great on my PanP5 (4 Gigs/Ram).  I use Visual Studio 2008/2010, SQL Server 2008, and a slew of other apps with zero problems.  I even watch Netflix and Appdev videos which use Windows-only DRM video codecs, and they work great.

So I say this setup would be ideal, and even more so on a PanP7 with the newer processor.  

Take care --

Sam

---

### Post by revlimiter on 2010-04-20
I run ArcGIS desktop on my Panp6 in Virtualbox. It runs like a champ. Not so much 3D rendering, but it does really put a machine through the paces. My panp6/vbox setup runs faster than my dedicated XP system at work.... 

2.8ghz core2duo, 4 gigs of ram.

---

### Post by PabloH on 2010-04-26
I would check the 3D rendering requirements of auto-cad.

I/O is always a bit slow in a VM. Maybe a dual boot would be better? If you had a separate Windoze partition, you could use VMWare to mount in as a VM as well (not sure about VirtualBox).

---

