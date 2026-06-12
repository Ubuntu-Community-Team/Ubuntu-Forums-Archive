---
title: "Problem with UNR 10.4/Chrome not playing wmv files"
date: 2010-04-27
forum: Ubuntu Moblin Remix
---

### Post by JimTaverna on 2010-04-27
Hello all! Can't wait till the 29th.

As the title states, I'm running Ubuntu Netbook Remix 10.4 LTS RC. Love it and hope to trash Windows as soon as I can get some things straightened out.

The main issue for me currently is the inability to run wmv files instream with Google Chrome. I've tried both the Beta and Dev versions of Chrome with the same results: the movie doesn't play and all I'm presented with is a black screen and the GStreamer 0.10.28 controls. The only way to play it is to right click and select "Movie Player", which opens another window.

When I first ran a wmv file in Chrome, I got the usual missing components message and the system did its thing, searching and installing, then mildly complaining that not all components were installed. What they are is anyone's guess.

I've loaded the W32codecs and all the GStreamer packages (the good, the bad, and the ugly), in addition to mplayer, to no avail. Chrome is using the Mozilla GStreamer lib and is in fact pointing to it. Firefox has no problem with the wmv file.

One enterprising gent thought that the problem was the VLC player and went through some interesting moves to get it to work. Nada for me. Frankly, I still don't see how VLC could be involved.

My question therefore is twofold: has anyone else had this problem and, if so, what was the resolution?

Any help would be gratefully appreciated.

HP Mini 110-1100 CTO
Atheros wireless and lan
Broadcom Crystal HD card 
Intel 945GM Express chipset
The ubiquitous Atom n270 processor

For what it's worth, with the exception of the Broadcom card, everything worked  worked straight out of the box.

---

### Post by JimTaverna on 2010-04-28
Looks like I'll have to go this one alone. Friggin' CODECS...

BTW, for those using Chrome who want to free up some of the 2.4tbs of memory it consumes, try adding "--purge-memory-button", quotes excluded, to the command line. Then periodically hit shift+esc to bring up the task manager. Hit the purge button and enjoy life in the fast lane...at least until you open another YouBoob tab.

Note to Google Dev staff: add an option to automatically purge memory at a pre-determined rate (time, memory used, number of tabs open) or at the very least throw it on the menu bar. No thanks necessary...

---

### Post by cariboo on 2010-04-29
Have you tried [this]("https://chrome.google.com/extensions/detail/bamkbfdmckphehgiafpenehgebjgdlli?hl=en")? I don't have any wmv files, so there isn't any sense in me installing the extension.

---

### Post by JimTaverna on 2010-05-01
Yes. No go.

Installed gnome-mplayer and gecko-mediaplayer and it works well enough.

---

