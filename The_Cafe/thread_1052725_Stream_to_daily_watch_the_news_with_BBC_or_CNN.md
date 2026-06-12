---
title: "Stream to daily watch the news with BBC or CNN?"
date: 2009-01-28
forum: The Cafe
---

### Post by frenchn00b on 2009-01-28
Hi,

Is there somehow a working stream to daily watch the news with BBC or CNN, with mplayer ?
thanks

---

### Post by pt123 on 2009-01-28
> **frenchn00b said:**
> Hi,

Is there somehow a working stream to daily watch the news with BBC or CNN, with mplayer ?
thanks

maybe using gsopcast

---

### Post by smartboyathome on 2009-01-28
> **frenchn00b said:**
> Hi,

Is there somehow a working stream to daily watch the news with BBC or CNN, with mplayer ?
thanks

I have it on livestation. You could check into that. :)

---

### Post by calvinps on 2009-01-28
Surely someone would have managed to get BBC iPlayer to work on Ubuntu? :-?

---

### Post by Johnsie on 2009-01-28
The BBC  IPlayer works in Ubuntu but you need to be in the UK to use it. UK taxpayers fund the BBC so it would be unfair for foreigners to get it for free. You can get alot of Channels on TVU  for Windows. Internet TV is one of the main reasons I keep windows on my machines. Linux doesn't have an equivalent to TVU or PPStream.

A few years ago I wrote a program called STV Linux which had a number of TV channels but I'm too busy to maintain it.

---

### Post by Sunflower1970 on 2009-01-28
> **Johnsie said:**
> The BBC  IPlayer works in Ubuntu but you need to be in the UK to use it. UK taxpayers fund the BBC so it would be unfair for foreigners to get it for free. 

I wish they'd set something up so if someone from a different country wanted to watch something on the BBC in iPlayer we could just pay a per monthly fee for it. I know it would be something I'd be interested in...

---

### Post by Johnsie on 2009-01-29
I think the license payers who have funded the organisation should get to vote on that. I'm sure there are are alot of people who would like their license fee subsidised by foriegners. However if the the BBC was targeting people outside the UK then it might lose it's Britishness in order to appease the tastes of foriegners. This could be the slippery slope de-Britification of the BBC.

---

### Post by wmcbrine on 2009-01-29
As far as CNN, I have URLs for four live streams, not all of which are necessarily on at any given time:

[http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)

(and change the "1" to "2", "3" or "4" for the other streams). These streams are dedicated webcasts and don't correspond to any of their regular channels.

---

### Post by bruce89 on 2009-01-29
> **Sunflower1970 said:**
> I wish they'd set something up so if someone from a different country wanted to watch something on the BBC in iPlayer we could just pay a per monthly fee for it. I know it would be something I'd be interested in...

Based on what the British Government is saying, we may even have to pay extra for iPlayer.

> **Johnsie said:**
> However if the the BBC was targeting people outside the UK then it might lose it's Britishness in order to appease the tastes of foriegners. This could be the slippery slope de-Britification of the BBC.

It's already not very relevent in order to not be London-centric.

---

### Post by Johnsie on 2009-01-29
Maybe they should put adverts in for foreigners. That would get them a bit of revenue and help them improve programming. All this reality TV stuff id because they are being cheapskates. How many years has the weakest link been on every day?? :-)

---

### Post by bruce89 on 2009-01-29
> **Johnsie said:**
> Maybe they should put adverts in for foreigners. That would get them a bit of revenue and help them improve programming.

There already is something like this, it's called BBC America.

---

### Post by t0p on 2009-01-29
> **bruce89 said:**
> Based on what the British Government is saying, we may even have to pay extra for iPlayer.


?? What's the government got to do with it??

---

### Post by bruce89 on 2009-01-29
> **t0p said:**
> ?? What's the government got to do with it??

The Govenment allocate the funding for the BBC.

---

### Post by PartisanEntity on 2009-01-29
> **smartboyathome said:**
> I have it on livestation. You could check into that. :)

+1 for Livestation, great app, runs on Linux, Mac and Windows. Allows you to watch live streaming TV many stations around the world.

Currently the selection is heavy on news channels.

I am currently also beta testing it on the iPhone :)

---

### Post by kitts on 2009-02-28
i dled the file 'livestation-2.5.0.run' from livestation. I don't know how to install the file on Ubuntu 8.10-intrepid.

---

### Post by PartisanEntity on 2009-02-28
1. Navigate to the directory of the .run file. For example, if on the desktop you would type in "cd ~/Desktop" and press enter.
2. Type "chmod +x livestation-2.5.0.run" (press enter).
3. Now type "./livestation-2.5.0.run", press enter, and the installer will run.

---

### Post by frenchn00b on 2010-01-19
I found one for World news, stream, BBC , but well it is a sort of hack of bbc, but free and working
```
mplayer "http://scfire-mtc-aa06.stream.aol.com:80/stream/1047"
```

on the other hand it is not like the real bbc radio

---

### Post by frenchn00b on 2010-01-19
there is a link here: 
```
http://www.bbc.co.uk/worldservice/audioconsole/?stream=live
```

but could it be possible to do netstat -plane or wireshark from it, to know the stream if possible?

---

### Post by frenchn00b on 2010-01-19
OK

I think that I found how : 

```
mplayer -noframedrop -dumpfile bbcworldnews.flv -dumpstream  "http://www.bbc.co.uk/worldservice/audioconsole/?stream=live"  & 

sleep 20s ; mencoder -ovc lavc -lavcopts none -oac mp3lame -o bbcworldnews.flv & 

sleep 40s ; mplayer  bbcworldnews.mp3 
```

what do you think ? 
***FLV => Mencoder FLV2MP3 => Mplayer***


**CLIVE** is not working either

---

### Post by frenchn00b on 2010-01-19
**OK, here is the solution , console based, no browser needed. **
```
get_iplayer --pid radio:bbc_radio_one --amode=flashaac --stdout --nowrite | mplayer -cache 128 -
```

---

### Post by frenchn00b on 2010-01-20
[http://bbcstreams.com/](http://bbcstreams.com/)

use ```
apt-get install vlc-nox 
```
then :

```
 cvlc "http://www.bbc.co.uk/worldservice/meta/tx/nb/live_ennws_au_nb.asx"
```
and you get news into console

---

