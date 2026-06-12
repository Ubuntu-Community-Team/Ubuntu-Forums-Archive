---
title: "GRAMPS:  How do you show a divorce?"
date: 2010-10-11
forum: The Cafe
---

### Post by Gulfvet91 on 2010-10-11
I've been doing a lot with the GRAMPS genealogy program lately and was just wondering how you are supposed to go about showing a divorce.  That and a string of marriages for one person who had an awful time trying to finally find the right spouse.  Any help would be greatly appreciated!

---

### Post by Old_Grey_Wolf on 2010-10-11
> **Gulfvet91 said:**
> I've been doing a lot with the GRAMPS genealogy program lately and was just wondering how you are supposed to go about showing a divorce.  That and a string of marriages for one person who had an awful time trying to finally find the right spouse.  Any help would be greatly appreciated!

For a divorce, you select one of the people in the marriage. I use the person that is in the direct lineage for my family. Then select Event, then Event type = Divorce. Fill in the information you have.

For additional marriages, select the person, then from the top menu select Edit > Add Partner. Fill in the information you have.

I had one person that got divorced 4 times, and remarried 4 time. The fifth spouse shot them dead. I have always wanted to know the real reason.
:lolflag:

I hope that helps.

---

### Post by Gulfvet91 on 2010-10-12
Wolf, I don't seem to have the Divorce option in my drop-down.

---

### Post by Old_Grey_Wolf on 2010-10-12
> **Gulfvet91 said:**
> Wolf, I don't seem to have the Divorce option in my drop-down.

Try this:

1) On the left had side of the main window, I select People.
2) In the right pain of the main window, I double click on the person for whom I want to enter a divorce event.
3) In the Person: window, I select the Events tab in the middle of the window.
4) In middle of the Events Reference Editor window, select General tab, then select Divorce from the Event Type: menu.

I hope that helps.

Edit: I am using GRAMPS: 3.2.0-1

---

### Post by Gulfvet91 on 2010-10-12
I don't have a General tab in that location and I don't have Divorce as an event type.  Which version of GRAMPS are you running?

---

### Post by Old_Grey_Wolf on 2010-10-12
> **gulfvet91 said:**
> i don't have a general tab in that location and i don't have divorce as an event type.  Which version of gramps are you running?

3.2.0-1 from the Ubuntu 10.04 repository

I forgot that on the step

> 3) In the Person: window, I select the Events tab in the middle of the window.

you need to click on the green (+) icon below the Events tab in order to get to the Events Reference Editor window

then you will see the Events Reference Editor window with the General tab

------

It would be nice if I knew how to use a CLI for GRAMPS; however, I don't know if it exists. It would solve instruction error like that :)

---

### Post by boxcorner on 2011-06-08
I am using Gramps 3.2.3-1
Say, for example X marries Y. 
They divorce, and then X marries Z.
If you create People entries for X, Y and Z.
Then create Events: 2 marriages and 1 divorce for X, 1 marriage and 1 divorce for Y, and 1 marriage for Z. 
Then create Families for X+Y and X+Z. 
Viewing X in Relationships displays marriages with both Y and Z.
If both marriages produced children then they can be added.
However, if you run Reports > Web Pages > Web Calendar, it also displays anniversaries for both marriages.
Z might want to be reminded of X's marriage to Y!
So instead, I create People entries, including all marriage and divorce Events for X, Y and Z, but create Families only for Z.
Relationships for X only displays the marriage with Z, and hence only one marriage anniversary appears on the Web Calendar.
Not an ideal solution, but I hope this helps ...

---

