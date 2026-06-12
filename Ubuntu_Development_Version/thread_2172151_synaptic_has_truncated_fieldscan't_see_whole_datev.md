---
title: "synaptic has truncated fields/can't see whole date/ver#"
date: 2013-09-03
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-09-03
Synaptic has truncated fields. Not sure if it is gnome, unity or other.

(can't post screenshot - upload failed)

---

### Post by mc4man on 2013-09-03
> **ventrical said:**
> Synaptic has truncated fields. Not sure if it is gnome, unity or other.

(can't post screenshot - upload failed)

Could be this bug i filed a ways back, no action on

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571)

As far as screenshots here, thought it was just me, thread says multiple though it's with any number inc. 1, just keep trying
(usually on the 3rd or 4th attempt it finally goes thru

[http://ubuntuforums.org/showthread.php?t=2170444](http://ubuntuforums.org/showthread.php?t=2170444)

---

### Post by ventrical on 2013-09-03
> **mc4man said:**
> Could be this bug i filed a ways back, no action on

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571)

As far as screenshots here, thought it was just me, thread says multiple though it's with any number inc. 1, just keep trying
(usually on the 3rd or 4th attempt it finally goes thru

[http://ubuntuforums.org/showthread.php?t=2170444](http://ubuntuforums.org/showthread.php?t=2170444)


Thanks . I just started a new thread in Forums Help.

edit :

ahhh .. yes I see . thanks..
[http://ubuntuforums.org/showthread.php?t=2172154](http://ubuntuforums.org/showthread.php?t=2172154)

---

### Post by mc4man on 2013-09-03
is this what you see (2nd attempt to add screen...
(which worked this time..

---

### Post by ventrical on 2013-09-03
> **mc4man said:**
> is this what you see (2nd attempt to add screen...
(which worked this time..


Will try again.

This is with a fully upgraded saucy install i386.

Ok.. had to try three times.

here it is.

Usually it appends .. but you can see the number 8 half cut off. I even tried to expand it and it will not append normally.

---

### Post by mc4man on 2013-09-03
> **ventrical said:**
> Will try again.

This is with a fully upgraded saucy install i386.

Ok.. had to try three times.

here it is.

Usually it appends .. but you can see the number 8 half cut off. I even tried to expand it and it will not append normally.

That's something different than what I mentioned  which was no hort. scrollbar which affects the ability to read last column, by default description.

As far as cutting off, not that much different than before, all columns except the last one have a predetermined size. I guess now it just fills that column to the max rather than filling to the max with some ... when the text can't fit.
screens show what I mean, using one of my pp's because almost all will not fit in 
screen 1 removed description, size is last with wasted space
 screen 2 removed descriptions & size, set latest version to last  so it could expand

Forum has switched order of screens, another issue

---

### Post by ventrical on 2013-09-03
Perhaps I just didn't notice until now. In fact I think I may have even brought this topic up in a previous cycle.

Thanks again.

---

### Post by mc4man on 2013-09-03
Ot - to note
This forum now orders screens by name/date/time, whatever, **Not the order you add them in**
Known issue but not yet addressed, so if wishing screens in a particular order one sometimes needs to adjust the names

---

### Post by mc4man on 2013-09-03
> **ventrical said:**
> Perhaps I just didn't notice until now. In fact I think I may have even brought this topic up in a previous cycle.

Thanks again.

It may have occured when synaptic moved to gtk3 in a less than optimum way, (though columns will truncate anyway.
Another gtk3 'issue' is 
open synaptic, go to File > History 
The Date box is so narrow nothing of use can be read, one has to expand each time synaptic is opened

---

### Post by xc3RnbFO8P on 2013-09-03
> **mc4man said:**
> Ot - to note
This forum now orders screens by name/date/time, whatever, **Not the order you add them in**
Known issue but not yet addressed, so if wishing screens in a particular order one sometimes needs to adjust the names

or drag them to order

---

### Post by cariboo on 2013-09-03
> **Ringi said:**
> or drag them to order

I'm not totally sure, but that only works if you are using the enhanced attachment utility.

As for the synaptic problem, I just expand the column to view the complete information, and personally I would rather not have a horizontal scroll bar.

---

### Post by mc4man on 2013-09-03
> **cariboo907 said:**
> I'm not totally sure, but that only works if you are using the enhanced attachment utility.

As for the synaptic problem, I just expand the column to view the complete information, and personally I would rather not have a horizontal scroll bar.
checking with enhanced I see I can reorder as needed, even thru an edit.

Never noticed that one can resize columns in synaptic or if I previously tried didn't hit the spot I guess.

---

### Post by xc3RnbFO8P on 2013-09-04
> **cariboo907 said:**
> I'm not totally sure, but that only works if you are using the enhanced attachment utility.

As for the synaptic problem, I just expand the column to view the complete information, and personally I would rather not have a horizontal scroll bar.

like this

---

### Post by VinDSL on 2013-09-08
> **ventrical said:**
> Synaptic has truncated fields. Not sure if it is gnome, unity or other.

> **mc4man said:**
> Could be this bug i filed a ways back, no action on

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1203571)
Rolling Synaptic Package Manager back to version 0.75.13 took care of the problem, for me. ;)

Now, let's try an attachment...  

[INDENT][ATTACH=CONFIG]246096[/ATTACH][/INDENT]

---

### Post by VinDSL on 2013-09-08
Added a 'me too' to the bug...

---

### Post by ventrical on 2013-09-08
> **VinDSL said:**
> Rolling Synaptic Package Manager back to version 0.75.13 took care of the problem, for me. ;)

Now, let's try an attachment...  
[INDENT][ATTACH=CONFIG]246096[/ATTACH][/INDENT]



Everytime I see one of your amazing screeshots I actually think I have been teleported right into the middle of a rock concert .. :) lol  or something ! :)

---

### Post by ventrical on 2013-09-08
> **VinDSL said:**
> Added a 'me too' to the bug...

Actually I was working on anothe problem and I needed to see the version number of a file and when I used synaptic I got this truncated thingy.. even tried to maximize.. etc.. but to no avail..

---

### Post by ventrical on 2013-09-08
> **cariboo907 said:**
> I'm not totally sure, but that only works if you are using the enhanced attachment utility.

As for the synaptic problem, I just expand the column to view the complete information, and personally I would rather not have a horizontal scroll bar.


Can't expand the 'Latest Version' or "Installed Version' columns. (fields)

How to?

---

### Post by cariboo on 2013-09-08
Epanding the columns work fine with the version of synpatic I'm using.

---

### Post by VinDSL on 2013-09-08
> **cariboo907 said:**
> Epanding the columns work fine with the version of synpatic I'm using.
You're still missing the horizontal scrollbar, cariboo.

Hrm...

Maybe we're talking apples n' oranges...

---

### Post by VinDSL on 2013-09-08
> **ventrical said:**
> Actually I was working on anothe problem and I needed to see the version number of a file and when I used synaptic I got this truncated thingy.. even tried to maximize.. etc.. but to no avail..
Okay, let's make sure we're all on the same page...

Initially,  I didn't understand what your title meant.  I thought you were talking about how there is no horizontal scrolling on the fields window -- only vertical scrolling, e.g. there is a vertical scrollbar on the fields window, but no horizontal scrollbar.

This long-standing bug comes n' goes in Synaptic.

Seems like the regression occurred after version 0.75.13.

Personally, I have ALL fields check-boxed in Synaptic, so horizontal scrolling is paramount.

When I read mc4man's bug link, it pointed to this regression, so I posted a workaround.

Sooo, are we talking about the same problem -- or two different problems?  :)

---

### Post by VinDSL on 2013-09-08
Sometimes a pic is worth 1000 words.  Here is 0.75.13:


Gnome3 Staging (now) PPA chosen / all fields check-boxed / horizontal scrollbar present

[INDENT][ATTACH=CONFIG]246103[/ATTACH][/INDENT]


Versions (truncated by default) aligned to left edge using the horizontal scrollbar

[INDENT][ATTACH=CONFIG]246104[/ATTACH][/INDENT]


Versions fields now expanded by dragging the frames with the mouse

[INDENT][ATTACH=CONFIG]246105[/ATTACH][/INDENT]


How does that compare to 0.80.2 ?

You be the judge...   ;)

---

### Post by ventrical on 2013-09-08
Vin, Vin , Vin ....:)  lol ... I blew up the image a bit . Look at the numbers '8' in the two different fields, Installed Version and Latest Version. What am I doing wrong? Do ya see where it is truncated??

---

### Post by ventrical on 2013-09-08
> **cariboo907 said:**
> Epanding the columns work fine with the version of synpatic I'm using.

Ok.. finally got that feature to work on one system install but it is forzen up on other installs. The dual arrow comes up but the field border will not budge.

Thanks for your interest.

---

### Post by ventrical on 2013-09-08
> **VinDSL said:**
> Okay, let's make sure we're all on the same page...

Initially,  I didn't understand what your title meant.  I thought you were talking about how there is no horizontal scrolling on the fields window -- only vertical scrolling, e.g. there is a vertical scrollbar on the fields window, but no horizontal scrollbar.

This long-standing bug comes n' goes in Synaptic.

Seems like the regression occurred after version 0.75.13.

Personally, I have ALL fields check-boxed in Synaptic, so horizontal scrolling is paramount.

When I read mc4man's bug link, it pointed to this regression, so I posted a workaround.

Sooo, are we talking about the same problem -- or two different problems?  :)'


Ok.. I go it to work fianlly on one system. It must be a bug or I have to update my systems.

Thanks for your time. Apologies if I was not clear on this.

regards..

---

