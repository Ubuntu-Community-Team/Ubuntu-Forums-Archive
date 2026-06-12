---
title: "How long until the ubuntu servers are back at full speed?"
date: 2005-10-15
forum: The Cafe
---

### Post by xequence on 2005-10-15
I decided to give KDE another chance, but the ubuntu repositories were very slow. 3800 bytes per second, it said it would take 7 hours to download 120 MB.

I am guessing this is from people not using bittorent to download breezy, but my question is... How long until it is back at full speed? I heard you can get speeds of 500KBPS from it, and my max is 300 KBPS or so.

---

### Post by BWF89 on 2005-10-15
If slow speeds mean tons of people downloading Ubuntu hopefully never :) .

---

### Post by xequence on 2005-10-15
I just thought of this... I used the debian repos to download the w32codecs, could I use them to get KDE?

I just wish everyone would use the wonderfull thing that is bittorent to download the wonderfull thing that is ubuntu.

---

### Post by poofyhairguy on 2005-10-15
[QUOTE=xequence]I just thought of this... I used the debian repos to download the w32codecs, could I use them to get KDE?
[/QUOTE]

No. Using debian repos for anything other than the w32codecs can lead to breakage. You should take that line out of the sources.list now.

EVERYONE should take that line out of there sources.list now. It can break things if you install updates with it activated.

---

### Post by pmj on 2005-10-15
You could always try mirrors in another country. The Swedish mirror seems a bit slow too compared to normal, but at least I got a couple of hundred KB/s last time I updated.

---

### Post by xequence on 2005-10-15
> No. Using debian repos for anything other than the w32codecs can lead to breakage. You should take that line out of the sources.list now.

EVERYONE should take that line out of there sources.list now. It can break things if you install updates with it activated.

Ok, thanks :) I was wondering why my breezy installation, downloaded and installed 2 days before final, had 200 MB of updates on the final release day.

> You could always try mirrors in another country. The Swedish mirror seems a bit slow too compared to normal, but at least I got a couple of hundred KB/s last time I updated.

How do I change apt to use different mirrors? I thought it was just automatic.

---

### Post by pmj on 2005-10-15
[QUOTE=xequence]Ok, thanks :) How do I change apt to use different mirrors? I thought it was just automatic.[/QUOTE]
You can change this in the file /etc/apt/sources.list

Just add "se", or some other country prefix, in front of archive.ubuntu.com. For me it looks like this: "deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted", and so on. Since Sweden is on the other side of the planet from where you are, though, you might get better speed from somewhere else.

And remember to make a backup of the sources.list file or of the lines you edit. :)

---

### Post by UbuWu on 2005-10-15
[QUOTE=pmj]
Just add "se", or some other country prefix, in front of archive.ubuntu.com. For me it looks like this: "deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted", and so on. Since Sweden is on the other side of the planet from where you are, though, you might get better speed from somewhere else.
[/QUOTE]

Most mirrors actually still point to the main site (they are just there for future compatibility). Se is one of the few that is real, can't remember the others...

---

