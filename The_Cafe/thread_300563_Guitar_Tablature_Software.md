---
title: "Guitar Tablature Software?"
date: 2006-11-15
forum: The Cafe
---

### Post by CPtAJ on 2006-11-15
Is there such a beast in the linux world? I need something like guitar pro or powertab that can not only view those formats but also play them. Any ideas?

I tried running guitar pro with wine and it barely worked. I couldnt use it. Is it a configuration problem or does wine simply not support it? Maybe I did something very wrong...](*,)

---

### Post by IYY on 2006-11-15
KGuitar might be what you're looking for. It can edit... Tab, midi, Guitar Pro 3 and 4, and XML.

---

### Post by GarethMB on 2006-11-16
Tux guitar is the best I've found. It needs Java though. They all suck in comparison to GP5.

---

### Post by Gargamella on 2006-11-16
> **GarethMB said:**
> Tux guitar is the best I've found. It needs Java though. **They all suck in comparison to GP5**.

yes they do

---

### Post by GarethMB on 2006-11-16
Someone should write a good one...any volunteers?

---

### Post by TLE on 2006-11-16
How many of these programs allows you to import from midi and support bass also ?

---

### Post by ComplexNumber on 2006-11-16
> **CPtAJ said:**
> Is there such a beast in the linux world? I need something like guitar pro or powertab that can not only view those formats but also play them. Any ideas?

I tried running guitar pro with wine and it barely worked. I couldnt use it. Is it a configuration problem or does wine simply not support it? Maybe I did something very wrong...](*,)
try denemo
[http://denemo.sourceforge.net/](http://denemo.sourceforge.net/)

---

### Post by matthew on 2006-11-16
> **ComplexNumber said:**
> try denemo
[http://denemo.sourceforge.net/](http://denemo.sourceforge.net/)Good news: it's also in the repositories (v0.7.5 is in Edgy) so you can use Synaptic, apt-get, aptitude, etc. to install it. I just installed it and am playing around with it now. Cool little program! Thanks for the referral.

---

### Post by ComplexNumber on 2006-11-16
> **matthew said:**
> Good news: it's also in the repositories (v0.7.5 is in Edgy) so you can use Synaptic, apt-get, aptitude, etc. to install it. I just installed it and am playing around with it now. Cool little program! Thanks for the referral.
no worries :). i've been using it(on and off) for about 6 months now.

---

### Post by CPtAJ on 2006-11-17
Hey guys, thanks for the responses. I'm trying out KGuitar and it looks neat. Cant get it to play any sound though. Sound is working fine in other applications so I have no idea what could be wrong...

denemo looks good as well, but it cant open gp3-4 files so I cant use it.

They're all great, the thing is I dont need them to be particularly fantastic, I just need them to play the tabs so I can learns some songs. No need to compose yet.

Any ideas on getting kguitar working properly?

---

### Post by matthew on 2006-11-17
> **CPtAJ said:**
> Hey guys, thanks for the responses. I'm trying out KGuitar and it looks neat. Cant get it to play any sound though. Sound is working fine in other applications so I have no idea what could be wrong...

denemo looks good as well, but it cant open gp3-4 files so I cant use it.

They're all great, the thing is I dont need them to be particularly fantastic, I just need them to play the tabs so I can learns some songs. No need to compose yet.

Any ideas on getting kguitar working properly?I haven't had much luck with any of the tab programs on linux, but I admit I haven't really tried too hard. I still have a tendency to grab a piece of paper and a pencil.

I have also found "gnometab" and "songwrite" in the repos and played with them just a little bit along with kguitar. I have yet to get any of them to successfully import ASCII tabs (of which I have hundreds going back to the founding of the [OLGA]("http://www.olga.net/") in the early 1990's). If you get that to work, tell us all how you did it. I think any of these would be useful for writing and hearing your own tabs, though.

---

### Post by jem7v on 2006-11-25
It's probably not playing because MIDI playback isn't enabled by default in Ubuntu Linux. If you have a sound card that supports hardware MIDI playback, this should help you:
[http://ubuntuforums.org/showthread.php?t=30963](http://ubuntuforums.org/showthread.php?t=30963)
If not, you could always look at **timidity**.

---

### Post by ComplexNumber on 2006-11-25
> **matthew said:**
> I haven't had much luck with any of the tab programs on linux, but I admit I haven't really tried too hard. I still have a tendency to grab a piece of paper and a pencil.

I have also found "gnometab" and "songwrite" in the repos and played with them just a little bit along with kguitar. I have yet to get any of them to successfully import ASCII tabs (of which I have hundreds going back to the founding of the [OLGA]("http://www.olga.net/") in the early 1990's). If you get that to work, tell us all how you did it. I think any of these would be useful for writing and hearing your own tabs, though.
no luck with denemo then?

as for kguitar, i couln't get any sound out of it either.

---

### Post by matthew on 2006-11-25
> **ComplexNumber said:**
> no luck with denemo then?
To be honest, I've installed it but I haven't had time to test it out other than to look at all the menu options.

---

### Post by wonkycross on 2007-02-08
tuxguitar opens and plays gp3,4, and 5 and powertab files.  i've tested it on several of my tabs and they all play nicely.

---

### Post by CPtAJ on 2007-02-08
Hey, tuxguitar looks great. I just tried it out. Now all I need to do is figure out how to get midi sound working... I've been putting this off for so long.

> It's probably not playing because MIDI playback isn't enabled by default in Ubuntu Linux. If you have a sound card that supports hardware MIDI playback, this should help you:
[http://ubuntuforums.org/showthread.php?t=30963](http://ubuntuforums.org/showthread.php?t=30963)
If not, you could always look at timidity.

Some of the links on that guide are broken. It hasn't been maintained since 2005. I'll try to figure it out for myself later and send some revisions to the author. What soundfont do you guys recommend for guitars?

---

### Post by wonkycross on 2007-02-10
i think this is the guide i used to get timidity set up --> [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo")

as for the soundfont, i use Unison.sf2 thats mentioned in the above howto and i think it sounds pretty nice.

---

