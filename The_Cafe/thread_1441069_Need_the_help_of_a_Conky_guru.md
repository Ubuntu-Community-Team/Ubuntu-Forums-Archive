---
title: "Need the help of a Conky guru"
date: 2010-03-28
forum: The Cafe
---

### Post by conb123 on 2010-03-28
Hiya I am in need of an expert to help me fix this conky configuration. I have been using this [http://conky.linux-hardcore.com/?page_id=1412](http://conky.linux-hardcore.com/?page_id=1412) . I have just been making some modifications to it to apply to my system. Here is my current .conkyrc: [http://pastebin.com/LnhJtibr](http://pastebin.com/LnhJtibr) . But I think the problem lies in my .conkyForecast.template: [http://pastebin.com/uMGhKzez](http://pastebin.com/uMGhKzez) . It is probably something blindingly obvious but if you look at this screenshot, monday is being overlapped by something.

[IMG]http://i.imgur.com/kTdcf.png[/IMG]

All help would be greatly appreciated, thanks.

---

### Post by which ones pink on 2010-03-28
On the very last line, your weather section points to another file.  Try that one.  BTW I don't actually use conky, so I'm just guessing. ;)

---

### Post by conb123 on 2010-03-28
Yeah that is the .conkyForecast.template I linked to it [http://pastebin.com/uMGhKzez](http://pastebin.com/uMGhKzez), I suspect that is where the problem lies.

---

### Post by pbpersson on 2010-03-28
I notice that the word "Cloudy" is being cut off at the far right.  Why does the forecast not fit in the window?  How do you know Friday is not wrapping around and getting placed on top of Monday?

---

### Post by pbpersson on 2010-03-28
Okay, I know exactly what that is.  Look on the left hand side - you have two graphics with text below each one.  The text below the wind graphic is telling you something like 5mph WSW and that is getting overlaid with the day of the week.

You need to fool around with that file and somehow get an extra blank line in there or change the vertical offset.

You can't hurt anything by experimenting, if something goes totally wrong just set it back. :)

---

### Post by conb123 on 2010-03-28
You sir, are brilliant! I fixed my script like so [http://pastebin.com/9V88Fw5g](http://pastebin.com/9V88Fw5g) thanks a bunch. "Mostly Cloudy" is still displaying as "Mostly Clo" but I think I can live with that :)

---

