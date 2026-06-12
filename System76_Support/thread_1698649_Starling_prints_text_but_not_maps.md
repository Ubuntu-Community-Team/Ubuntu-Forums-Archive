---
title: "Starling prints text but not maps"
date: 2011-03-02
forum: System76 Support
---

### Post by tc101 on 2011-03-02
I have a Brother HL-2170W Wprinter plugged into my starling.  It will print text but not google maps.  I plugged it into another PC and it printed google maps just fine, so the problem is not the printer.

When I try to print the blue light on the printer flashes but nothing happens.  I go to System/Printers/Print Quene and it shows the job as processing but nothing happens.

---

### Post by isantop on 2011-03-02
Will it print other web pages just fine, or are those not working either?

---

### Post by tc101 on 2011-03-02
A utility came up and took me through  a series of steps to debug the printer.  I got to the point in the screen shot below.  I printed the test page but not the map.  The next step said there is no obvious solution.  The 4508 Lake Ivanhoe job is the google maps job.  I can give you more screenshots or more details if that would help.

---

### Post by tc101 on 2011-03-02
It does the same thing with yahoo maps, but it prints graphics just fine.

---

### Post by Flyers2391 on 2011-03-02
> **tc101 said:**
> It does the same thing with yahoo maps, but it prints graphics just fine.

How about trying this ... when you hit print and can select a printer, choose "print to file" then select the PDF radio button and an easy location, such as Desktop.  Now, you should have the maps page printed to a PDF on your desktop.  Confirm that PDF is displaying properly and print the PDF.  

If it prints correctly, then is may be a setting with your browser.

---

### Post by tc101 on 2011-03-02
> Will it print other web pages just fine, or are those not working either?

I have not had a problem with other web pages, although I don't do much printing of web pages so have not tried many.

---

### Post by tc101 on 2011-03-02
> How about trying this ... when you hit print and can select a printer, choose "print to file" then select the PDF radio button and an easy location, such as Desktop. Now, you should have the maps page printed to a PDF on your desktop. Confirm that PDF is displaying properly and print the PDF.

If it prints correctly, then is may be a setting with your browser.

That worked.  How do I track down the browser problem?

---

### Post by Flyers2391 on 2011-03-03
> **tc101 said:**
> That worked.  How do I track down the browser problem?

Cool!  At least you have a work-around now if you need it.  If you have another browser installed, you can try from that, if not chromium is an easy install away from the software center.  

I believe from a past thread you were asking about NoScript ... are you using firefox with it when you try to print?  It is possible that the page rendering the images is being blocked when you go to print, maybe a separate domain is generating them (just a guess).  

If you are using NoScript, you can "allow scripts globally" to test and then turn if back on or "temporarily allow all this page".  Just make sure if you do the "temporarily allow all this page" that more pages don't show as being blocked.

---

