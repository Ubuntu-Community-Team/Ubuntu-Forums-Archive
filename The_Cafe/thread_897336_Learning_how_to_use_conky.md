---
title: "Learning how to use conky"
date: 2008-08-22
forum: The Cafe
---

### Post by Oxypunk on 2008-08-22
Hi everyone.  I am fairly new to ubuntu, and am loving it so far.  The only real draw back so far is games, but I can do with out them.

So here is my question.  I was trying to understand how to modify conky.  All the website say to create a conkyrc file into the / folder.  Is this just implying copying the the conky.conf file into the / folder renamed conkyrc?  Also, what is the purpose of creating a conkyrc file?  When conky starts up, how does it know to startup from the conkyrc file instead of where it normally starts?

I hope these are not too many questions, but as I said before I am new to linux.

---

### Post by TheSlipstream on 2008-08-22
```
sudo gedit ~/.conkyrc
```

Will create and open one for you. :)

We have a ton of nice Conkys somewhere, but you'll have to search for it.

You don't need to do anything but put code in there, Conky does the lot of it. No moving the file (which is inside the Home directory, although you should just use the terminal command so nothing gets messed up, just in case.

---

### Post by Mr.Crowley on 2008-08-22
Yes, the conky.conf file is just the example conky configuration file given to you with the program. You can make that your conkyrc file with:
```
sudo mv /path/to/conky.conf ~/.conkyrc
```
However, I don't think the stock config file works, but I don't really remember. The conkyrc file is simply the configuration file conky reads so that the program knows what to display on the screen when it is started.

Read '[HOW TO: A Beginners Guide to Setting up Conky]("http://ubuntuforums.org/showthread.php?t=867076")' and you will get a better understanding of how to use conky.

---

### Post by backupdevice on 2008-08-22
And don't forget to check this topic to get inspired 

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by FuturePilot on 2008-08-22
I've found this very helpful.
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

---

### Post by Oxypunk on 2008-08-23
Thank you for the help.  I have conky working now.

---

### Post by Sealbhach on 2008-08-23
> **Oxypunk said:**
>  Also, what is the purpose of creating a conkyrc file?  When conky starts up, how does it know to startup from the conkyrc file instead of where it normally starts?


As I understand it, the conkyrc file contains a set of instructions telling Conky how to display itself on your desktop.

So any changes you make in the conkyrc file will change to way Conky looks.

There are addtional scripts you can use (which are referred to in the conkyrc file) which can get and format data about weather, RSS news feeds and other stuff.


.

---

