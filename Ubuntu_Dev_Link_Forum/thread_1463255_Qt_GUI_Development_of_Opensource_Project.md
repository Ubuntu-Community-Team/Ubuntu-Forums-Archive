---
title: "Qt GUI Development of Opensource Project"
date: 2010-04-26
forum: Ubuntu Dev Link Forum
---

### Post by stefanadelbert on 2010-04-26
I have recently had some experience with Qt (4.6.2) and would like to do some development work on a opensource project that uses Qt. Is there a definitive list of projects that have a Qt frontend somewhere?

---

### Post by Siph0n on 2010-04-26
I just started learning qt4 (with python) this past week. I created a date calculator here : [http://code.google.com/p/date-calculator/](http://code.google.com/p/date-calculator/) . You are welcome to work on that if you like. Or even if you don't, please give me some comments and suggestions, as i'm sure my code could use improvement. Thanks !

---

### Post by Bachstelze on 2010-04-27
Kubuntu is in dire need of contributors, and obviously uses Qt a lot. That would probably be a good place to start.

---

### Post by stefanadelbert on 2010-04-27
> **Siph0n said:**
> I just started learning qt4 (with python) this past week. I created a date calculator here : [http://code.google.com/p/date-calculator/](http://code.google.com/p/date-calculator/) . You are welcome to work on that if you like. Or even if you don't, please give me some comments and suggestions, as i'm sure my code could use improvement. Thanks !

I'm afraid I haven't spent much time with Python, so I'm not going to be much help there re. comments and suggestions. I've had a brief look at your code though. MVC is an extremely powerful concept and you might consider it, i.e. breaking the underlying logic out of the GUI code and putting it into classes.

For example, consider creating MyDate and MyDateSkip classes. MyDateSkip could hold a skipValue (the number of units to skip) and a skipUnit (days, weeks, etc.) and maybe be capable of converting this to a number of days. When calcClicked is triggered, you could create a DateSkip from the values currently in the GUI and pass it to the MyDate.Skip on your own MyDate class. The MyDate class would then extract the number of days from the MyDateSkip class and add them to its current date (underlying datetime) and then return a date which you could display in your GUI.

This way the model (MyDate and MyDaetSkip) is kept separate from the view (and the controller is somewhere in between!). MVC. It rocks.

This way, your GUI has no date arithmetic logic in it, (which is always a bit nasty so best to leave as much of it to existing libraries). I find that the best way to think about this is to forget about the GUI initially. Think in terms of what information needs to go and what information needs to go out of the model part of the code (MyDate MyDateSkip). Jumping in with GUI is always so tempting - I know it always is for me anyway.

Good luck
Stef

---

### Post by stefanadelbert on 2010-04-27
> **Bachstelze said:**
> Kubuntu is in dire need of contributors, and obviously uses Qt a lot. That would probably be a good place to start.

I'll have a look. Thanks.

---

