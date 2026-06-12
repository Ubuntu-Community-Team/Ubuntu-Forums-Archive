---
title: "Can AppArmor protect devices?"
date: 2010-11-09
forum: Security
---

### Post by TheAlien on 2010-11-09
This might sound really stupid, so you'll all have to excuse my lacking knowledge. :P

I read that USB attacks get more and more common, like putting in an USB stick with a malicious autorun script on it, and it's game over.

Can AppArmor protect devices and limit their access to the file system?

---

### Post by OpSecShellshock on 2010-11-09
AppArmor isn't really the right tool to use, but it's also entirely unnecessary to use any tool at all in this case. Files on removable storage media simply do not run at mount on Linux systems (well, I suppose the administrator could configure something so that it would, but I'm not sure why anyone would do so).

---

### Post by alphaamanitin on 2010-11-09
I am know security expert but it seems to me that some one could make a malicious program that would some how run on mount if mounting required input of the sudo password.  Any one else think this is possible?

AlphaA

---

### Post by OpSecShellshock on 2010-11-09
> **alphaamanitin said:**
> I am know security expert but it seems to me that some one could make a malicious program that would some how run on mount if mounting required input of the sudo password.  Any one else think this is possible?

AlphaA

I doubt it, if only because configuring the drives in such a way would also necessitate manually entering whatever the next command would be in order to run it.

---

### Post by bodhi.zazen on 2010-11-09
> **alphaamanitin said:**
> I am know security expert but it seems to me that some one could make a malicious program that would some how run on mount if mounting required input of the sudo password.  Any one else think this is possible?

AlphaA

If you are writing a script the possibilities are almost infinite.

---

### Post by alphaamanitin on 2010-11-09
So, is that a yes it is possible bodhi?  Not to worry about me, I don't think I could write the program with detailed instructions on how to do it, unless it was simply copy this program.  Anyway, regardless of OpSecShellshock's opinion I still think it is possible, maybe hard, but completely possible, not just theoretically possible.

AlphaA

---

