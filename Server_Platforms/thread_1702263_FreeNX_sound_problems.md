---
title: "FreeNX sound problems"
date: 2011-03-07
forum: Server Platforms
---

### Post by Herazio on 2011-03-07
Dear members

I've been having some trouble with figuring out how to get sound to work in FreeNX. After a couple of google searches I'm still stumped to as how I'm supposed to get it to work. 

The first thing that I'm wondering is: is it possible for a server system **without **a sound card to actually stream audio towards a client with the NoMachine NX Client (**multimedia enabled**) ?

If so then the problem gets a bit more complex. I've installed the ESD Sound Server and PulseAudio. But how am I supposed to do this configuration ? Whenever I go to **gstreamer-properties **I get the choice for **ESD **which I choose for my output and **ALSA **for my input. Still no sound. The configurationfile has been changed so that the libraries for ESD get loaded in **/etc/nxserver/node.conf **but also still nothing.

Does anyone have any ideas what to do next ? Because the only thing I see in my soundmixer is a dummy output and that's it. I'm quite stumped and any help would be greatly appreciated !

Many thanks

Herazio

---

### Post by amgadf on 2011-03-24
[COLOR=black][FONT=Verdana]Hi [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am facing the same problem and can't seem to find a solution to this, after extensive searching on Google and the nomachines knowledge base. I still can’t see any clear instructions on how to get this to work!![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have read a few posts that people have got it working and the problem they where having is that is doesn’t play sound from an internet browser. But how to actually get it to work in the first place???[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am case if someone can help with this that would be great. Below are the links to the most “useful” information I found.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any help would be much appreciated with this!! [/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]- [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://www.nomachine.com/ar/view.php?ar_id=AR11E00491[/SIZE][/FONT]]("http://www.nomachine.com/ar/view.php?ar_id=AR11E00491")
[FONT=Times New Roman][SIZE=3]- [/SIZE][/FONT][COLOR=black][FONT=Verdana][http://www.nomachine.com/fr/view.php?id=FR07E01796](http://www.nomachine.com/fr/view.php?id=FR07E01796)

[/FONT][/COLOR]

---

