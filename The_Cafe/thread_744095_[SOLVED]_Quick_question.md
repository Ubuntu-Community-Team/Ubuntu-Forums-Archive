---
title: "[SOLVED] Quick question"
date: 2008-04-03
forum: The Cafe
---

### Post by blithen on 2008-04-03
How would you go about making a GUI for a program like FFMPEG. It's one POWERFUL program. Just there is a lot of options most people won't use. And I want to streamline it using a GUI. Could you use python for this? Or what?

---

### Post by bobbocanfly on 2008-04-03
You could probably do it quite easily in python using PyGTK, Glade and os.system(). Use the GUI to let users select input and output filenames + the encoding options, then use the Submit buttons function to error check and pass the arguments to ffmpeg in os.system().

TBH the hardest bit to make should be the GUI but then again i have no experience using ffmpeg so i dont know if any commands clash or dont work together etc.

---

### Post by blithen on 2008-04-03
OKay well that solves that I will get working on it and it will be done eventually(meaning in 5 or 6 years)

---

