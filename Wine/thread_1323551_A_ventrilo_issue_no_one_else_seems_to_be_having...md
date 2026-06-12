---
title: "A ventrilo issue no one else seems to be having.."
date: 2009-11-11
forum: Wine
---

### Post by m0rbidpercepti0ns on 2009-11-11
Ok so..ive installed WoW on several makes of Ubuntu,currently on 8.10,since ive had the best results with it.Aside from a bit of pre work to be done,my only issue up until this point was 1-5FPS consistently,that i couldent raise. However,suddenly my vent has stopped working. Ive googled ALL OVER the place,and searched several different forum sites. Im using Wine 1.1.31 and Ventrilo 3.0.5. Vent has ALWAYS worked for me,straight out of the box,all the way back to Feisty,ive never had to change or alter or work around anything to make it function. Ive been able to find threads on all kinds of mic issues and stream and codec issues,the only problem i have is that i cant hear anyone.I dont use my mic..i just want to be able to hear my guild,and i cant,nor can i find why,or anyone else with this same problem. Every post ive found says "I can hear everyone fine,but...." Im not getting errors...just no sound. Nothings muted,and as far as i can tell..my configuration shouldent have changed since it worked a few days ago.At first i thought it was an issue with Wines audio,since im using Pulseaudio,but I turned sound on in WoW to find that it worked..so it likely isnt Wine. Thank in advance to anyone who can help,im extremely frustrated with this..as ive put in 10+ hours in the past day or two trying to figure this out,and i cant.I copied the msgsm.acm file to the correct place,and added the correct line to system.ini,and ive checked it for typos.

---

### Post by ekilfoil on 2009-11-12
As I said in the other thread.  I'll repost here for the people searching.

You're using Ubuntu 8.x, which has horrible PulseAudio support.  You should at least be on Ubuntu 9.04.

Install the PPA version of WINE with PulseAudio support from: [https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)

Use Mangler ([http://www.mangler.org](http://www.mangler.org)) instead of Ventrilo in WINE.

The problem is WINE.  Once you install WINE with PulseAudio (or compile yourself at [http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)), everything works fine.

[http://www.mangler.org/wp-content/uploads/2009/11/PulseWowAudacityManglerRB.png](http://www.mangler.org/wp-content/uploads/2009/11/PulseWowAudacityManglerRB.png)

---

