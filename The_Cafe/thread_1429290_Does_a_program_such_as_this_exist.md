---
title: "Does a program such as this exist?"
date: 2010-03-13
forum: The Cafe
---

### Post by dragos240 on 2010-03-13
Say you have a home partition, and say you want to reinstall your OS, fine you can, and everything is almost exactly as you left it! Except the packages..... Is there a program for any distro that will track user installed applications and reinstall them if a new OS is installed?

---

### Post by fewt on 2010-03-13
> **dragos240 said:**
> Say you have a home partition, and say you want to reinstall your OS, fine you can, and everything is almost exactly as you left it! Except the packages..... Is there a program for any distro that will track user installed applications and reinstall them if a new OS is installed?

before:
```

dpkg --get-selections >my_pkgs.txt

```

Put my_pkgs.txt on your thumb drive unless you aren't overwriting /home.

after:
```

sudo apt-get install $(cat my__pkgs.txt | grep install$ | awk '{printf $1" "}')

```

You may want to take a copy of your /etc/apt/sources.list and sources.list.d/* files so you can pull over any extra repositories.

YMMV, this only works if all of your software is a .DEB.

---

### Post by lisati on 2010-03-13
The nearest I can think of at the moment is [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") but have a hunch that this isn't quite what you're after.

I do remember reading somewhere in the forums of a technique where you could use something like synaptic to produce a list in a text file of what you have installed, which could then be used as an aid to reinstalling stuff when you reinstall your OS. (edit: see the above post, that's the sort of thing I was thinking of....)

---

### Post by pastalavista on 2010-03-13
Synaptic Package Manager has that functionality built-in. You can export and save a list of installed software and import it into a new installation to download all the same packages.

---

### Post by Regenweald on 2010-03-13
> **pastalavista said:**
> Synaptic Package Manager has that functionality built-in. You can export and save a list of installed software and import it into a new installation to download all the same packages.What he said. Know your tools :p

---

### Post by pastalavista on 2010-03-13
> YMMV, this only works if all of your software is a .DEB.

I know what you're saying but I can't figure out "YMMV"

I don't do a lot of IM texting...

---

### Post by empty_spaces on 2010-03-13
YMMV - Your Mileage May Vary

Meaning the results may vary from person to person

---

### Post by pastalavista on 2010-03-13
> **empty_spaces said:**
> YMMV - Your Mileage May Vary

Meaning the results may vary from person to person

ah, thanks for that. I can never understand why people use those kind of acronyms in a place like this with unlimited character space. I guess it's a badge of street/tech-cred or something, lol. no offense to [COLOR="YellowGreen"]fewt[/COLOR] intended, I'm clearly the uncool one here

---

