---
title: "Question about GPL"
date: 2010-11-19
forum: The Cafe
---

### Post by nolag on 2010-11-19
Can someone make a closed source application that calls something that is under GPL?  Example: say someone makes a new kernel, and it is closed source (and proprietrary).  They make it x window system compatible and port gnome (or kde) to their os.  They include gnome as the window system, and include the (possibly modified) source code in the disk (or make it avalible).  Is this ok?  Or say someone makes app1 (closed source), that uses app2 (by API call or system call wondering for both).  app2 is under GPL and they put it on a disk with app1 and make the source for app2 avalible.
 
Are either of these ok with GPL or LGPL?

---

### Post by limestone on 2010-11-19
The part you use from open-source need to remain open.
But you can close the code you write if it's not a remake and/or compilation of a GLP open-source code.

All open-source softwares often comes with a "hack" file that explains details about redistributing.

---

### Post by kernelhaxor on 2010-11-19
I believe you're right.  
You might also have to let users be able to modify and compile app2 and use app1 with the modified app2.

Isn't this what Apple does with Mac OSX?

---

### Post by LowSky on 2010-11-19
short answer: yes its fine

> **kernelhaxor said:**
> 

Isn't this what Apple does with Mac OSX?

Yup

---

### Post by 3Miro on 2010-11-19
If you are actually going to do something like this, ask a lawyer. All that you can find here are a bunch of geeks with limited understanding of GPL.

Here is my rudimentary understanding. Evince is distributed under GPL and it has a windows version. You can have GPL apps running on proprietary windows environment. The issue may come up, if the environment tries to restrict the way the application is running.

There is work on a windows version of KDE, however, I am not sure if KDE is distributed under GPL.

---

### Post by limestone on 2010-11-19
> **3Miro said:**
> If you are actually going to do something like this, ask a lawyer. All that you can find here are a bunch of geeks with limited understanding of GPL.

[http://www.gnu.org/licenses/gpl-3.0.txt](http://www.gnu.org/licenses/gpl-3.0.txt)
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/)

---

### Post by nolag on 2010-11-19
Thank you all for your replies, I assumed that was how it all worked but wanted to make sure I understood :P.
 
> **pont.andersson said:**
> [http://www.gnu.org/licenses/gpl-3.0.txt](http://www.gnu.org/licenses/gpl-3.0.txt)
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/)
 
These are too long and legal-like for me to understand that was why I asked here
 
If I do plan to do something like that I would ask a lawyer 1st, or at least ask the company that has the patent on the GPL product.

---

### Post by 3Miro on 2010-11-19
> **pont.andersson said:**
> [http://www.gnu.org/licenses/gpl-3.0.txt](http://www.gnu.org/licenses/gpl-3.0.txt)
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/)

There is a difference between reading a document and understanding a document. I wouldn't expect a non-mathematician to understand any of my papers even if they were to read it. I don't expect to fully understand a legal document. If I have a company and I want to make proprietary software that interfaces with GPL, I will consult with a layer and not an on-line forum.

---

### Post by conundrumx on 2010-11-19
Don't forget, the version of the GPL is important.  There's a reason the Linux kernel is still under GPL 2.

---

### Post by nolag on 2010-11-22
> **conundrumx said:**
> Don't forget, the version of the GPL is important. There's a reason the Linux kernel is still under GPL 2.
 
 
I thought that is was because they never said "and greater" and GPL 2 and 3 are not compatible?  I think GPL 3 protects users from more things than 2 does :).

---

### Post by nolag on 2010-11-22
> **conundrumx said:**
> Don't forget, the version of the GPL is important. There's a reason the Linux kernel is still under GPL 2.
 
 
I thought that is was because they never said "and greater" and GPL 2 and 3 are not compatible? I think GPL 3 protects users from more things than 2 does :).

---

### Post by forrestcupp on 2010-11-22
> **nolag said:**
> Can someone make a closed source application that calls something that is under GPL?  Example: say someone makes a new kernel, and it is closed source (and proprietrary).  They make it x window system compatible and port gnome (or kde) to their os.  They include gnome as the window system, and include the (possibly modified) source code in the disk (or make it avalible).  Is this ok?  Or say someone makes app1 (closed source), that uses app2 (by API call or system call wondering for both).  app2 is under GPL and they put it on a disk with app1 and make the source for app2 avalible.
 
Are either of these ok with GPL or LGPL?

What you're talking about is what LGPL is for.  You can't do that with straight GPL.  And even with LGPL, you have to link dynamically instead of compiling it statically with your code.

It's possible to get around the straight GPL thing using what's called a shim.  A shim is basically a middle man between the GPL code and the proprietary code that's used to load the proprietary code.  That's how proprietary video drivers are allowed to work with the GPLed Linux kernel.

---

