---
title: "No Snappy Unity or nothing with 64bitA1.iso"
date: 2012-06-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-11
Just reporting in that the 64bit install of qq alpha 1 went really good with alternate install .iso (even has correctly detected Ati Graphics card), wirless is engaged , however, the GUI is really sluggish.  This is an Acer Extensa 4420 AMD64 Athlonx2 and worked very zippy with i386 Precise .

  It almost behaves like WinXP or Vista. ff has also  got molasses on it's feet so I think it is a global sugglishness .. but system Monitor reports using very low resources as far as processor speed  but a littl high memory (555MB with onlly ff and terminal)

---

### Post by balloons on 2012-06-11
> **ventrical said:**
> Just reporting in that the 64bit install of qq alpha 1 went really good with alternate install .iso (even has correctly detected Ati Graphics card), wirless is engaged , however, the GUI is really sluggish.  This is an Acer Extensa 4420 AMD64 Athlonx2 and worked very zippy with i386 Precise .

  It almost behaves like WinXP or Vista. ff has also  got molasses on it's feet so I think it is a global sugglishness .. but system Monitor reports using very low resources as far as processor speed  but a littl high memory (555MB with onlly ff and terminal)

ventrical, I know your going to report this result to the isotracker right? :guitar: 

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases)

Slot it in under however you did the install. THANKS!

On the sluggishness front, I haven't experienced that yet, but I am definitely finding some bugs. The good news is that the upgrade bug I found (no gtk theme, borked appearance) already got fixed. +1 for reporting. Now I'm trying to track down some python and other weird rendering bugs that are causing things like vlc to just never draw it's window.

---

### Post by mc4man on 2012-06-11
> **guitara said:**
> . Now I'm trying to track down some python and other weird rendering bugs that are causing things like vlc to just never draw it's window.

For the most part vlc works fine here unless you try to open certain vlc windows like 'Open Media', Tools > Preferences when it's set to advanced or from simple clicking on the 'all' radio button. (maybe be some other vlc windows involved 

In that case it's a return of or some element of a 11.10 dev bug, new report on (hopefully this time if new qt4 packages don't resolve it won't drag on as long as previously
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1005677](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1005677)

---

### Post by fjgaude on 2012-06-11
We can talk about snappy but here's the test data from my 64K Intel box staring with 12.10 first:

```
frank@cutie:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   22742 MB in  2.00 seconds = **11383.27** MB/sec
 Timing buffered disk reads: 1292 MB in  3.00 seconds = **430.01** MB/sec
```
---
GtkPerf 0.40 - Starting testing: Mon Jun 11 10:16:39 2012

```
GtkEntry - time:  0.02
GtkComboBox - time:  0.59
GtkComboBoxEntry - time:  0.29
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.07
GtkToggleButton - time:  0.22
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.08
GtkTextView - Add text - time:  0.40
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.66
GtkDrawingArea - Circles - time:  1.20
GtkDrawingArea - Text - time:  2.34
GtkDrawingArea - Pixbufs - time:  0.20
 --- 
Total time:  **6.20**
```
===

Now for 12.04 LTS:

```
frank@cutie:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   23710 MB in  2.00 seconds = **11868.59** MB/sec
 Timing buffered disk reads: 1288 MB in  3.00 seconds = **429.12** MB/sec
```
===

GtkPerf 0.40 - Starting testing: Mon Jun 11 10:22:00 2012

```
GtkEntry - time:  0.02
GtkComboBox - time:  0.53
GtkComboBoxEntry - time:  0.30
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.05
GtkToggleButton - time:  0.39
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.10
GtkTextView - Add text - time:  0.49
GtkTextView - Scroll - time:  0.08
GtkDrawingArea - Lines - time:  0.63
GtkDrawingArea - Circles - time:  1.26
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.08
 --- 
Total time:  **4.41**
```
===

gtkperf of 6.60 versus 4.41 is much slower for graphics. And 
11383.27 versus 11868.59 is telling. Enough said, as for my main box.

---

### Post by jerrylamos on 2012-06-11
From your results, looks like the biggest difference was
on 12.10
GtkDrawingArea - Text - time:  2.34
vs, on 12.04
GtkDrawingArea - Text - time:  0.37

From the outside looking at the "black box" the Gtk routine(s) for Text are way way different....any way to put the 12.04 code back into 12.10?

I haven't done those tests for a while, but that difference would be almost visible.

Jerry

---

### Post by ventrical on 2012-06-11
> **guitara said:**
> ventrical, I know your going to report this result to the isotracker right? :guitar: 

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases)

Slot it in under however you did the install. THANKS!

On the sluggishness front, I haven't experienced that yet, but I am definitely finding some bugs. The good news is that the upgrade bug I found (no gtk theme, borked appearance) already got fixed. +1 for reporting. Now I'm trying to track down some python and other weird rendering bugs that are causing things like vlc to just never draw it's window.

 I did report it:

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases/18/results](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds/17167/testcases/18/results)

But I think I borked the results because it is now finishing the updates.

 I'll be on it as soon as I can.

---

### Post by ventrical on 2012-06-11
Also after the update, very snappy now, the memoryUsage has dropped to 439 from 555MB.

---

### Post by ventrical on 2012-06-11
> **fjgaude said:**
> We can talk about snappy but here's the test data from my 64K Intel box staring with 12.10 first:

```
frank@cutie:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   22742 MB in  2.00 seconds = **11383.27** MB/sec
 Timing buffered disk reads: 1292 MB in  3.00 seconds = **430.01** MB/sec
```---
GtkPerf 0.40 - Starting testing: Mon Jun 11 10:16:39 2012

```
GtkEntry - time:  0.02
GtkComboBox - time:  0.59
GtkComboBoxEntry - time:  0.29
GtkSpinButton - time:  0.05
GtkProgressBar - time:  0.07
GtkToggleButton - time:  0.22
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.08
GtkTextView - Add text - time:  0.40
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.66
GtkDrawingArea - Circles - time:  1.20
GtkDrawingArea - Text - time:  2.34
GtkDrawingArea - Pixbufs - time:  0.20
 --- 
Total time:  **6.20**
```===

Now for 12.04 LTS:

```
frank@cutie:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   23710 MB in  2.00 seconds = **11868.59** MB/sec
 Timing buffered disk reads: 1288 MB in  3.00 seconds = **429.12** MB/sec
```===

GtkPerf 0.40 - Starting testing: Mon Jun 11 10:22:00 2012

```
GtkEntry - time:  0.02
GtkComboBox - time:  0.53
GtkComboBoxEntry - time:  0.30
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.05
GtkToggleButton - time:  0.39
GtkCheckButton - time:  0.06
GtkRadioButton - time:  0.10
GtkTextView - Add text - time:  0.49
GtkTextView - Scroll - time:  0.08
GtkDrawingArea - Lines - time:  0.63
GtkDrawingArea - Circles - time:  1.26
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.08
 --- 
Total time:  **4.41**
```===

gtkperf of 6.60 versus 4.41 is much slower for graphics. And 
11383.27 versus 11868.59 is telling. Enough said, as for my main box.

Perhaps you could share with us how to aquire 'hdparam' because I tried the code in terminal and it don't work. I also tried to install it .. not found.

---

### Post by fjgaude on 2012-06-11
Pray, it comes automatically when I installed 12.10, and of course, 12.04.

---

### Post by ventrical on 2012-06-12
> **fjgaude said:**
> Pray, it comes automa

tically when I installed 12.10, and of course, 12.04.

I mispelled of course:)


/dev/sda:
 Timing cached reads:   1626 MB in  2.00 seconds = 812.86 MB/sec
 Timing buffered disk reads: 220 MB in  3.00 seconds =  73.27 MB/sec


Gee..  didn't think my disk was that slow. I'll try that code on another OS.

---

### Post by sgage on 2012-06-12
> **ventrical said:**
> I mispelled of course:)


/dev/sda:
 Timing cached reads:   1626 MB in  2.00 seconds = 812.86 MB/sec
 Timing buffered disk reads: 220 MB in  3.00 seconds =  73.27 MB/sec


Gee..  didn't think my disk was that slow. I'll try that code on another OS.

Similar to mine:

/dev/sda:
 Timing cached reads:   2418 MB in  2.00 seconds = 1209.41 MB/sec
 Timing buffered disk reads: 260 MB in  3.00 seconds =  86.63 MB/sec

---

### Post by fjgaude on 2012-06-12
> **ventrical said:**
> I mispelled of course:)


/dev/sda:
 Timing cached reads:   1626 MB in  2.00 seconds = 812.86 MB/sec
 Timing buffered disk reads: 220 MB in  3.00 seconds =  73.27 MB/sec


Gee..  didn't think my disk was that slow. I'll try that code on another OS.

What I showed was one of my SSDs, Marvell controlled Plextor. Your drive is old generation HDD, not untypical. Your cached reads points to slow memory and CPU. All this is good.

---

### Post by fjgaude on 2012-06-12
> **jerrylamos said:**
> From your results, looks like the biggest difference was
on 12.10
GtkDrawingArea - Text - time:  2.34
vs, on 12.04
GtkDrawingArea - Text - time:  0.37

From the outside looking at the "black box" the Gtk routine(s) for Text are way way different....any way to put the 12.04 code back into 12.10?

I haven't done those tests for a while, but that difference would be almost visible.

Jerry

I can't say but I feel the Text readings will change for the better as 12.10 gets more mature. I can hope, anyway.

---

### Post by ventrical on 2012-06-12
> **sgage said:**
> Similar to mine:

/dev/sda:
 Timing cached reads:   2418 MB in  2.00 seconds = 1209.41 MB/sec
 Timing buffered disk reads: 260 MB in  3.00 seconds =  86.63 MB/sec


@ sage , fjgaude

Thanks you guys.

---

