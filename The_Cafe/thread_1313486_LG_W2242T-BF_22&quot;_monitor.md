---
title: "LG W2242T-BF 22&quot; monitor"
date: 2009-11-03
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-11-03
According to a Newegg reviewer of the [LG W2242T-BF]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824005132") 22" LCD monitor:
[QUOTE=""]WILL NOT WORK ON LINUX 100% of the time right out of the box. This monitor comes with a cd with drivers for it, but in linux you cant install them. This monitor worked at first when plugged in but afterwards it kept getting stuck in "Power Saving Mode" every time I booted up.

It wasn't a video card problem or PSU problem as some ppl might suggest its simply a communication problem between the LG monitor and the video card. This problem persisted even when switching from VGA to DVI. I opted to buy a DVI cable and seek a solution for that.

After much searching I found a solution that worked for me on Ubuntu 9.04:
edit xorg.conf file and add these two "options" to the device section (for your video card, eventhough I added it to the monitor section and it worked just as well):
Option "UseDisplayDevice" "DFP-1"
Option "ConnectedMonitor" "dfp"

In the monitor section add:
Horizsync 30-83
Vertrefres[/QUOTE]
Can anyone verify that this actually works?

Also, do most monitors have problems like this when trying to get them to work with Linux? Or are display problems the exception rather than the rule?

---

### Post by blueshiftoverwatch on 2009-11-29
Update: I decided to just take the risk and buy the monitor. I tested this monitor out with both VGA and DVI cables, on two different graphics cards, and with Ubuntu 9.04 and 9.10. But was **unable** to recreate the power save mode bug that poster complained about with any of the above mentioned combinations.

Just figured I'd post this in case any Linux user was thinking about buying the monitor but was put off after reading that comment. Maybe this thread will come up during a web search and help someone out.

---

### Post by Exodist on 2009-11-29
It must have a really strange refresh (Hz and Vt sync).
But who would really want a LG 22" at that price when you could buy one larger with a better picture and more dependable. 

I am getting TWO of these come spring [http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H](http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H)

---

### Post by Skripka on 2009-11-29
> **Exodist said:**
> It must have a really strange refresh (Hz and Vt sync).
But who would really want a LG 22" at that price when you could buy one larger with a better picture and more dependable. 

I am getting TWO of these come spring [http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H](http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H)

IME, ASUS monitors have great price points...but lack in accurate color rendering.  My VW222 sucks at rendering shades of red.

---

### Post by blueshiftoverwatch on 2009-11-29
> **Exodist said:**
> But who would really want a LG 22" at that price when you could buy one larger with a better picture and more dependable.

I am getting TWO of these come spring [http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H](http://www.newegg.com/Product/Product.aspx?Item=N82E16824236049&Tpk=ASUS%20VW246H)
People who aren't concerned with having a perfect 1080p capable display and would rather save $50?

Your monitor might be better. But I got this monitor after using a 19" CRT with VGA cable hookup. So compared to the graphics on my old one, this monitor blew me away. The biggest difference I've noticed is with text, theirs actually a sharp distinction between text and the background. Wheras on my old CRT the letters were kind of fuzzy around the edges. Makes reading stuff less straining on the eyes.

When I first glanced over the specs I was amazed that a monitor that's 2" bigger and had a response time 3ms faster than mine only cost $50 extra. But than I saw that the response time was rated in GTG, not the standard black to white that most monitors are. In reality your monitor is probably around 5ms like mine is. I hate it when companies come up with their own standards to try and deceive customers. Just like the whole thing with rating contrast ratios in ACM which is a completely different standard than the generally accepted standard so that people will see the bigger number and think that it's better.

---

