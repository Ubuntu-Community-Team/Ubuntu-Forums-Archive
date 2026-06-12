---
title: "ubuntu software"
date: 2007-08-05
forum: The Cafe
---

### Post by bribaetz on 2007-08-05
i need software for ubuntu to develop compilers for CPP python basic 
can some one direct me to a um catolog site

---

### Post by v8YKxgHe on 2007-08-05
System->Admin->Synaptic

Search for what ever you need =)

---

### Post by bribaetz on 2007-08-05
um i could nbot find it

---

### Post by Nekiruhs on 2007-08-05
... Python doesn't compile. Python is an interpreted language. The closest it gets to compilation is bytecode. And thats optional.

---

### Post by bribaetz on 2007-08-05
ooh then its useless to me i need a compiler for the other stuff

---

### Post by Hex_Mandos on 2007-08-05
What "other stuff" do you need to compile? Python is an interpreted language. 

If by CPP you mean C++, you need gcc. copy and paste the following command into your terminal:

> sudo aptitude install build-essential

As for BASIC, I've no idea. You can try GAMBAS, which is quite similar to MS Visual Basic 6:

> sudo aptitude install gambas

But keep in mind that your Gambas GUIs will use QT, so you'll have to release your software under the GPL (unless you have a license from Trolltech for proprietary software development)

---

### Post by Incense on 2007-08-05
Why not give real basic a shot. It's free (beer) on Linux. From what I can tell it looks a lot like MS Visual Basic. 

[http://www.realsoftware.com/]("http://www.realsoftware.com/")

---

