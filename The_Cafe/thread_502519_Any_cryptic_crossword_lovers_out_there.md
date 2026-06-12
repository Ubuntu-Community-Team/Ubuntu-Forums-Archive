---
title: "Any cryptic crossword lovers out there?"
date: 2007-07-16
forum: The Cafe
---

### Post by jkblacker on 2007-07-16
Just wondering how many of us are out there. I'm not terribly good, but I can usually manage most of the Observer's Everyman puzzle. Used to take all week; now I can get it mostly (if not all) finished on the day. Favourite clue ever (or at least, most memorable) was this: Rubicon is ace (5,2,2,6)

---

### Post by ynnhoj on 2007-07-16
i can't figure out cryptic crosswords -- whenever i look at them in my saturday or sunday papers i get confused :o  i'll stick to the number puzzles (sudoku and kakuro), thank you!

---

### Post by jkblacker on 2007-07-16
Ah, the unconverted. I was like that once... Really, all you have to do is learn the language the setter's speaking. Easier said than done, of course!

---

### Post by ynnhoj on 2007-07-16
i definitely would like to figure these puzzles out, but as you say: easier said than done!  i was just reading the wikipedia entry on cryptic crosswords, and the explanations of different types of clues seem relatively simple; however, i'm not so sure it will seem simple at all, the next time i look at a real puzzle.

---

### Post by jkblacker on 2007-07-17
I'd suggest looking at the Observer's Everyman, but that would require an online subscription for you as you're in America... Have a look at 
[the Private Eye crossword]("http://www.private-eye.co.uk/sections.php?section_link=crossword&"), which has some very rude clues and answers (be warned) but also some easy ones. 1across on the current crossword should be solvable.

---

### Post by Rorke on 2008-06-24
Hee Hee! I'd just closed this forum and did a cryptic crossword search, and bang, back here again.
I'm keen on, but not expert at, cryptic crossword puzzels.
Do you know of a good source of them? I usually buy a puzzel magazine, but it only has a couple of good ones in!

---

### Post by zbiblo on 2008-09-02
River of no return!!!  Ha Ha Ha, Just love the wit and humour.

I used to be able to do the Daily Telegraph in a couple of hours. But that was over thirty years ago. Now, I'm often unable to solve any clues.

---

### Post by smoker on 2008-09-02
thought it might be 'point of no return'?

anyway, sometimes do the glasgow herald crossword, though hardly ever finish it. you can also do it online if you've java installed: [http://www.theherald.co.uk/crosswords/](http://www.theherald.co.uk/crosswords/)
:-)

---

### Post by clanky on 2008-09-02
I normally do the Times crossword, results vary between finished in 20 minutes and only 75% fininshed after 24 hours.

---

### Post by CK1 on 2008-11-28
When I try to use the Observer everyman crossword or the Guardian crossword online, the grids do not come up. The message at the bottom of the browser says "Start: applet not initialized".  I am using Ubuntu 8.04 64 bit and Firefox 3.0.4. Link to crossword: [http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html]("http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html")

Any ideas how to get this working ?  I have icedtea java plugin and OpenJDK Java runtime installed.

---

### Post by jamesstansell on 2008-11-30
> **CK1 said:**
> When I try to use the Observer everyman crossword or the Guardian crossword online, the grids do not come up. The message at the bottom of the browser says "Start: applet not initialized".  I am using Ubuntu 8.04 64 bit and Firefox 3.0.4. Link to crossword: [http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html]("http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html")

Any ideas how to get this working ?  I have icedtea java plugin and OpenJDK Java runtime installed.

There's a thread in the 64-bit forums for installing Java and getting applets to run.  In short your current options are either

 * upgrade to 8.10 where the icedtea6-plugin package has liveconnect support, or
 * install a 32-bit browser and use the sun-java6-plugin package

Hope that helps,

-james.

---

### Post by leafpaul on 2008-11-30
* upgrade to 8.10 where the icedtea6-plugin package has liveconnect support

I have the above installed and it still doesn't work.  The Java plugin works on other websites but not for the Guardian crossword, anyone got any ideas?

Could it be to do with this:

"The LiveConnect feature of Java is not in OpenJDK. Some sites will not work with OpenJDK because of this missing feature."

---

### Post by MickS on 2008-11-30
Works for me Kubuntu 8.10...   After I remembered to allow it in NoScript:lolflag:


Mick

---

### Post by jamesstansell on 2008-11-30
> **leafpaul said:**
> * upgrade to 8.10 where the icedtea6-plugin package has liveconnect support

I have the above installed and it still doesn't work.  The Java plugin works on other websites but not for the Guardian crossword, anyone got any ideas?

Could it be to do with this:

"The LiveConnect feature of Java is not in OpenJDK. Some sites will not work with OpenJDK because of this missing feature."

That quote has to do with older version of OpenJDK.  Liveconnect was added to the version that ships with 8.10 - specifically the icedtea6-plugin package.

Of course there have been some bugs fixed since then; some but not all of the fixes are included in the jaunty packages.  Eventually they should show up in the intrepid-updates and intrepid-proposed archives.

Of course, sometimes the site itself needs to make some fixes - generally due to having made invalid assumptions.

I suggest you open a bug report and describe how to reproduce the problem.  Then the qa team and devs can figure out if it's something they can address.

-james.

---

### Post by leafpaul on 2008-12-06
This is not ideal and a bit bizarre but if you retrieve the solution ie the completed grid into the java applet from either the latest solutions or the "Crossword Archive Search".  This shows the grid and the answers within the grid in the Java applet. 

Now click "Clear" under the java panel then the grid appears with the answers removed and you can complete it as normal.

ie the Java applet appears to work OK with Ubuntu 64 with the exception that the initial load fails for some reason unless you load it with the answers.

---

### Post by CK1 on 2008-12-08
> **leafpaul said:**
> This is not ideal and a bit bizarre but if you retrieve the solution ie the completed grid into the java applet from either the latest solutions or the "Crossword Archive Search".  This shows the grid and the answers within the grid in the Java applet. 

Now click "Clear" under the java panel then the grid appears with the answers removed and you can complete it as normal.

ie the Java applet appears to work OK with Ubuntu 64 with the exception that the initial load fails for some reason unless you load it with the answers.

What version of Ubuntu are you using? I tried this with 8.04. The completed solution comes up with the grid, but the clear button does not work.

---

### Post by leafpaul on 2008-12-08
Intrepid 8.10

Although thinking about it the following is more likely to be relevant:

Firefox 3.0.4 with the icedtea plugin

Openjdk 6

---

### Post by Baklanov on 2009-08-18
> **CK1 said:**
> When I try to use the Observer everyman crossword or the Guardian crossword online, the grids do not come up. The message at the bottom of the browser says "Start: applet not initialized".  I am using Ubuntu 8.04 64 bit and Firefox 3.0.4. Link to crossword: [http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html](http://www.guardian.co.uk/crossword/java/new/0,,-23702,00.html)

Any ideas how to get this working ?  I have icedtea java plugin and OpenJDK Java runtime installed.

I had exactly this problem, and fixed it by getting rid of IcedTea and installing sun-java6-plugin instead. The Guardian's crosswords now work nicely here. I'm using Firefox 3.0.13 on Ubuntu 8.04, but I'm told this fix works on Jaunty Jackalope as well.

As MickS mentioned, you need to allow the site in Noscript, too, if you use that.

HTH

---

