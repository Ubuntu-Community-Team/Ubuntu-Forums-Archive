---
title: "KLove streaming"
date: 2007-02-07
forum: Ubuntu Christian Edition
---

### Post by sbennettgso on 2007-02-07
Anyone had any luck getting K-Love's streaming audio feed working?  I can get many others working from ShoutCast using StreamTuner and XMMS.  But K-Love doesn't seem to work for me.  I've tried using RealPlayer, Totem, and MPlayer, but nothing seems to work.

I'm using straight Ubuntu 6.1 on one computer and Ubuntu CE 2.0 on another, but I get the same results.  I get an error message that looks like this when I use Totem to emulate Windows Media Player:

[INDENT]Totem could not play 'mmsh://a181.l3072828068.c30728.g.lm.akamaistream.net/D/181/30728/v0001/reflector:28068?proto=http=caEbma6a_bwcobfctbtcVafclabc2dcc5aO-bfYObf-kJa-ynGCGxp=0002&MSWMExt=.asf'.

Could not open location; You may not have permission to open the file.
[/INDENT]

When I try to use RealPlayer, nothing at all seems to happen.  And I haven't figured out how to get MPlayer to emulate either Windows Media Player or RealPlayer yet.

Any help would be appreciated.

Thanks,
Scott

---

### Post by yoyoned on 2007-02-10
I installed Realplayer using automatix, and it works fine with Klove.  I've never been able to get totem working well with anything.

---

### Post by eric_n_va on 2007-02-14
Hey not sure if you were able to get Klove working, but I was getting an error with RealPlayer (I installed through Synaptics).  It would test okay, but then when streaming the actual music would give a "general error" popup.  I disabled dansguardian temporarily and it works now.

---

### Post by fred.warren on 2008-03-23
You need to use a program  that will accept an .asx playlist. Which means gxine, mplayer, or vlc but not Amarok. The URL is ```
http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx
```

For gxine or vlc just specify the url

```
gxine http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx
```

Or in the case of mplayer you will need to specify that it is a playlist and set the caching to something small so you don't have to wait 5 minutes for it to start.

```
mplayer -cache 64 -playlist http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx
```

The nice thing about using mplayer is running it in the background. 
[LIST=1]
[*]Open a terminal
[*]Run screen
[*]Run mplayer -cache 64 -playlist ]http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx
[/LIST]

With mplayer running under screen, you can even log out and it will keep playing. If you leave the console window open you can hit the space bar to pause play. Other cool tricks. You can close the window or hit Ctrl-a d to put the player in the background. You can reopen the window by typing screen -r to reatach to mplayer.

---

### Post by jgraves on 2010-02-20
With KLOVE's new streaming method, you need flvstreamer:

[http://download.savannah.gnu.org/releases-noredirect/flvstreamer/linux/](http://download.savannah.gnu.org/releases-noredirect/flvstreamer/linux/)

Then just run:

flvstreamer -r rtmp://emf.fl.miisolutions.net/klove-live01/klove/klove_high | mplayer -

---

### Post by highlandsun on 2010-04-07
mplayer can play rtmp streams directly, no need for flvstreamer.

mplayer rtmp://emf.fl.miisolutions.net/klove-live01/klove/klove_high

---

### Post by towerboy on 2010-05-25
I have it working in RhythmBox. You can use anyone of the following urls...
```
mms://wm-live.world.mii-streaming.net/live/klove/low_01
mms://wm-live.world.mii-streaming.net/live/klove/dialup_01
mms://wm-live.world.mii-streaming.net/live/klove/high_01
```
The first two urls are 5Kbs and 20Kbs bandwidth respectively. I am not sure what the third url bandwidth is for sure but when I measured it, it was roughly 150Kbs...

---

### Post by piston9 on 2010-05-29
Awesome - works perfectly!

---

### Post by 886343 on 2010-11-02
Can someone give me a link to play KLOVE in windows media player as the above don't seem to work anymore?
Have KLOVE changed something recently?
Any help would be appreciated.

---

### Post by 480silverton on 2010-12-11
> **886343 said:**
> Can someone give me a link to play KLOVE in windows media player as the above don't seem to work anymore?
Have KLOVE changed something recently?
Any help would be appreciated.

Can you not go into the website? That should work.

---

### Post by 886343 on 2011-01-06
I can't access the k-love website from work, however i have media player and some url's work. I just need to find one that will work for k-love.
Anyone....?

---

### Post by 886343 on 2011-01-06
> **480silverton said:**
> Can you not go into the website? That should work.
 
I can't access the k-love website from work, however i have media player and some url's work. I just need to find one that will work for k-love.
Anyone....?

---

### Post by Kross on 2011-06-19
Try any in your media player

[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_newmedia_low](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_newmedia_low)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_high-01](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_high-01)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_high-02](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_high-02)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_low-01](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_low-01)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_low-02](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_low-02)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_newmedia_high](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_newmedia_high)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_newmedia_low](http://mp3.eap.lee.miisolutions.streamguys.us:80/air1_newmedia_low)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_high-01](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_high-01)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_high-02](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_high-02)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_low-01](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_low-01)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_low-02](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_low-02)
[http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_newmedia_high](http://mp3.eap.lee.miisolutions.streamguys.us:80/klove_newmedia_high)[LIST=1]
[/LIST]

---

### Post by nhavens on 2011-06-23
Thanks for the links. I know it may not help Ubuntu users, but I successfully used [http://mp3.eap.lee.miisolutions.streamguys.us/klove_high-01](http://mp3.eap.lee.miisolutions.streamguys.us/klove_high-01) in exaile on fedora 15.

---

### Post by psycardis on 2011-09-13
These links work perfectly in Banshee, they even shows the currently playing track and artist

K-Love
[http://mp3.eap.lee.miisolutions.streamguys.us/klove_high-01]("http://mp3.eap.lee.miisolutions.streamguys.us/klove_high-01")

Air1
[http://mp3.eap.lee.miisolutions.streamguys.us/air1_high-01]("http://mp3.eap.lee.miisolutions.streamguys.us/air1_high-01")

Hope this helps,
Psycardis

---

### Post by tellapu on 2012-07-19
Thanks psycardis! This works for me in rhythmbox 2.97.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by stlsaint on 2012-07-24
Thread closed and used for reference only.

---

