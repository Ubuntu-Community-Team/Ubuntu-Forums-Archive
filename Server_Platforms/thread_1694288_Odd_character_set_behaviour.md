---
title: "Odd character set behaviour"
date: 2011-02-24
forum: Server Platforms
---

### Post by FidoLDido on 2011-02-24
Hi all,
 
HELP! Forgive me if I have not posted this in the correct place. Also please bear with me, I am a UNIX novice.
 
I have a strange character encoding problem that I am struggling to fix and really need some help.
 
I'm running Ubuntu Server 10.04. I run a perl script from the command line to pull a text field from a mysql database which contains some UK pound symbols (£), and it displays the result fine.
 
I have created a web page that pulls the same information from the database and prints the result to a log file. Instead of UK pound symbols I get \ax3. This is causing me a lot of grief and am unsure of how to go about fixing it.
 
Any advice greatly appreciated!
 
Phil.

---

### Post by zenwalker on 2011-02-24
I am not good at web stuffs, but i guess your web server knows what culture it is dealing with or some ting similar?

---

### Post by pizzafarmer on 2011-03-02
Phil, are you sure it displayed \ax3 and not something like \xa3? Hex a3 is the ascii value for the UK pound symbol and hex values are usually preceded by something like 0x or x', maybe \x. Values above hex 7f are outside the usual range for printable characters, so maybe that's why it displays what it does. If that's the case, I don't know how to fix it, but maybe there's something you can do with the formatting to straighten it out.

---

