---
title: "Man Page, How-To, Ad Nauseum"
date: 2006-11-02
forum: Ubuntu System Panel
---

### Post by stalker145 on 2006-11-02
Greetings, 
First off, thank you, chanders and Malac for the excellent utility that you have, obviously, worked so hard to create. 
I was wondering if there was a man page (since I can't seem to find it) or if a noble user has posted a how-to somewhere that I might be able to leech off of. I've been tinkering with the configuration editor and USPconfig finding most of what I've been wondering, but a few things still escape me. ](*,) 
The first of which tells me I'm a tad bit of a twit... when I installed, everything ran horizontally. I don't recall making any drastic changes, but the durn thing is now running vertically and I can't get it back. 
That's the big one for now... the rest shouldn't be too terribly difficult, I guess. 
Thanks in advance for pointing me in the right direction.

---

### Post by Malac on 2006-11-03
Can I just say kudos too chanders and team, as USP is all down to them not me and I don't want to usurp, in any way, their deserved praise for it.

As USP and USPconfig are beta apps at present a man page isn't on the cards at the moment as far as I know.
As for a how-to most of the instructions are on the "New Release" or "Plugin Development" threads.
If I understand vertically/horizontally question correctly.
Then you need to insert a "newpane" in the list every time you want USP to add the next plugin to the side of the last one instead of below it. i.e.

USPuser
USPterm
newpane
places

will give you the user plugin then the terminal below that then places will be next to user plugin starting a new column.

Some of the GConf Keys are not in USPconfig as they were going to get depreciated or I couldn't figure out what they did :) so didn't include them. 

Hope this helps.

---

### Post by stalker145 on 2006-11-03
> **Malac said:**
> you need to insert a "newpane" in the list every time you want USP to add the next plugin to the side of the last one instead of below it. i.e.

USPuser
USPterm
newpane
places

will give you the user plugin then the terminal below that then places will be next to user plugin starting a new column.

Hope this helps.

Ahhhh, so that's where I screwed it up. Thank you very much for the reply, it worked perfectly :cool:

I think I'm with everyone else on this forum when I say that I look forward to the next instance of USP and *hopefully* I can contribute.

---

