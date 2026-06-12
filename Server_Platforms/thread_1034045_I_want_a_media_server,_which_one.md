---
title: "I want a media server, which one????"
date: 2009-01-07
forum: Server Platforms
---

### Post by Lori700698 on 2009-01-07
I just had my last failed attempt with Jinzora2&3/Ices/Icecast.  It just didn't work how I thought it would.  I thought I'd hit the jukebox button and my stuff would stream over my request...not the case.  I want to stream music, movies and see our pictures from any computer in the house, that's windows, Ubuntu, and XUbuntu (the PS3's would be an added bonus) I want a web browser that I can access from work to listen to music via windows media play (I just can't download anything fancy to that computer to make it work) I have seen Mediatomb, Gnump3d, Fuppies all mentioned, is there others and what are the advantages of these?  I would love to see screen shots too!  Gee, I sound demanding~I'm just tired and disappointed that my original idea won't work.  If all else fails Jinzora2 did the best at pulling in my unorganized music along with the stuff that is organized so I will go back to that minus the MPD player.  It did broadcast nicely to Icecast, but I had to log onto Icecast to hear the music which I didn't want bothered with.  My intent is for individual users in the house to listen to what they want, not the stream I'm playing.  By the way I'm using Intrepid as a headless server! 
Thanks soo much!
Lori

---

### Post by Lori700698 on 2009-01-10
Ok, maybe I asked for to much, let me simplify my questions.
1. What do you use?
2. What do you like about it (what's the perks)?
3. What don't you like about it?
4. What have you tried that you didn't like and what was the issue?

---

### Post by Sarastro on 2009-02-15
I am currently exploring media server options.

Some of them:

1.  Remapping of the player programs music source to the directory of a  remote machine on the network.  This technique may require some knowledge of SAMBA.

2.  Using a mt-maapd daemon on the server.  This application is native in Rhythmbox, other players may need a plugin (such as Songbird but plugins are available).

3.  Use MPD

It appears relatively easy to access your home server remotely for the purpose of music playback at the remote location.  Here is an article which describes the required steps to access a Daapd server (option 2 above):

[http://wiki.mt-daapd.org/wiki/SSH_Tunnel](http://wiki.mt-daapd.org/wiki/SSH_Tunnel)

Streaming music (or video) to different points around the home is my objective.  Particularly networking music to a playback location with minimal hardware (doing away with a noisy and bulking entire media pc),  using for instance a [fit-PC]("http://www.fit-pc.com/") (or equivalent), to USB DAC, to amp to speakers.

Another possibility is using [Jinzora]("http://en.jinzora.com/") which might require a bit more setup but is much more powerful

I believe MPD or Jack may be the answer but any input is appreciated.

---

### Post by beatgr on 2009-02-15
I use **FireFly**, *mt-daapd* for my personal media server usage (primarily audio for iTunes).

FireFly Media Server web site
[http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/)

I have installed FireFly on computers running W2K, Debian, Ubuntu and uNSLUng(Linksys NSLU).
[http://www.fireflymediaserver.org/support.php](http://www.fireflymediaserver.org/support.php)

g. beat

---

### Post by inphektion on 2009-02-15
i've used this: [http://xbmc.org/](http://xbmc.org/)

[http://www.howtoforge.com/installing-xbmc-on-ubuntu-8.04](http://www.howtoforge.com/installing-xbmc-on-ubuntu-8.04)
not sure if it does everything you want but I think it does.

---

