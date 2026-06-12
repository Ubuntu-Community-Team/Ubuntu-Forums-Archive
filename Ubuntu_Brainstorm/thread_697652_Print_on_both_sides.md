---
title: "Print on both sides"
date: 2008-02-15
forum: Ubuntu Brainstorm
---

### Post by iopo on 2008-02-15
Hi!

Now, at least if you are using KDE, in order to print on both sides it is necessary to:

 -print odd pages

 -reload the printer with the stuff you just printed (being very carefull on the side)

 -print even pages

I think it could be a good idea to simplify the procedure by adding a "print on both sides" option.

Best

[https://blueprints.launchpad.net/ubuntu/+spec/printing-two-sides](https://blueprints.launchpad.net/ubuntu/+spec/printing-two-sides)

---

### Post by smartboyathome on 2008-02-15
Does your printer support printing on both sides?

---

### Post by iopo on 2008-02-15
Hi smartboyathome,
it does not, meaning that if I want to print on both sides I have to follow the steps I described: print the odd pages, reload, print the even pages. 
The "print on both sides" option will print odd pages, the lats page would be a big arrow showing you how to reload the pages you just printed, and after you finish reloading you can just click a "continue printing" button to print the even.
Nothing too fancy but I thought it may be a useful feature.
cheers

---

### Post by steeleyuk on 2008-02-17
> the lats page would be a big arrow showing you how to reload the pages

But not all printers load paper the same way. Some feed from the top (alot of Epson's do this), some feed from below (HP usually do this) and thats not to mention those printers with multiple trays.

It would require work on the driver side to know how your particular printer loads paper (if this isn't already done).

---

### Post by iopo on 2008-02-18
I'm not sure how it is possible to handle printers with multiple trays, but for all the others there could be something like "print test page" for double sided printing: there are at most 4 ways the paper can be reloaded! And instead of a big arrow there could be a on-screen diagram with the instructions.

---

### Post by iopo on 2008-02-19
Finally, the rationale for this is:

- Allow everybody to easily print on two sides, even those user that do not own a printer that supports double sided printing
- Reduce the consumption of paper, therefore saving money and reducing the impact on the environment. 

Anyway, does anybody know how the blueprints process works? After registering it, what do I do? Should I propose it for a meeting?
Cheers!

---

### Post by smartboyathome on 2008-02-19
Like steeleyuk said, it is probably better to go to the drivers for your printer and ask for this. It would be (in my opinion) more of a waste of time to get it so that the user to do it (and also it would be a waste of programming time).

---

### Post by steeleyuk on 2008-02-19
> big arrow showing you how to reload the pages you just printed
> there are at most 4 ways the paper can be reloaded!

This really isn't going to work without the print drivers telling the program how to reload the paper. The drivers need to know **how** the paper loads into the printer.

For example, my HP printer (6940). When the paper is in the tray, the side facing down is the side that gets printed on.
However, my old Epson (R300), the paper side facing up was the side that was printed on.

You'd have to speak to each driver project individually (HPIJS, Gutenprint, etc.) and find out first if a) they already support this and if not b) how would you go about implementing it. Only then could the printing system and/or programs implement the handing of this.

Note: this is how I see it. I could be completely wrong about this and if I am, hopefully someone will correct me. It's a good idea in theory and is something that many Windows drivers for HP, Epson and others handle quite well.

Just had a quick search and seems this has been [requested a few times before]("https://lists.ubuntu.com/archives/desktop-bugs/2006-August/046747.html").

---

### Post by iopo on 2008-02-19
Hi guys!
thanks you for your feedback. To be honest with you, I'm just a end-user that has never coded anything and that does not understand much of how things work inside. For this reason, forgive me if I insist a bit longer.

 Let's say you print some stuff and you want to reload your printer with what you just printed. You can:

-turn the pages or not (what is up as output is ether up or down as input).
-rotate the pages or not (meaning putting what is up down and what is down up or keep everything unchanged).

With one test page you should be able to determine how your printer works. Print the first page, take the paper and put it back without turning it and without rotating it and print the second page. Depending on the outcome you should be able to determine how your printer needs to be reloaded if you want to print on two sides.

Let's say there is a way for you to attach this information to your printer. By checking "print on both sides" the computer would:
-print odd pages
-pause, display how to reload the paper (Information that you have previously saved) and wait for a confirmation
-print even pages 

It seems to me that this would not involve any work on the driver, right?  

Cheers!

---

