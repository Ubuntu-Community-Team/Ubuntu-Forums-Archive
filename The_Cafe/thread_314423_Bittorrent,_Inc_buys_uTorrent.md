---
title: "Bittorrent, Inc buys uTorrent"
date: 2006-12-07
forum: The Cafe
---

### Post by zachtib on 2006-12-07
I'm sort of surprised that this hasn't been posted already, so I'll kick off the discussion:

Bittorrent, Inc., the company founded by the creator of Bittorrent, just bought out uTorrent. It was announced on uTorrent's forums, here: [http://forum.utorrent.com/viewtopic.php?id=17278](http://forum.utorrent.com/viewtopic.php?id=17278) and is currently being discussed in a Q&A like session on IRC.

So, to recap, in the last several days, we've got Mainline going legit with their 'movie store,' Azureus trying for legitimacy by starting their Zudeo web interface, and then Bittorrent Inc buying out uTorrent.

---

### Post by potrick on 2006-12-07
So, does this mean that the generic bittorrent client is going to be replaced with uTorrent? The generic client has a linux version. Might a utorrent for ubuntu be in the works? Not that running utorrent in wine is very complicated, but it's a thought.
  It's really interesting seeing all the movements, though. I'll have to keep watch over these stories.

---

### Post by potrick on 2006-12-07
And wow, there are a lot of negative responses to the announcement on the forum like you gave there. Stark contrast from what I'd expect from this forum, I'd say.

---

### Post by zachtib on 2006-12-07
I'm not a fan of it.  There's no way that this results in a Linux version of uTorrent, and BT, Inc. has already stated that they won't be open sourcing uTorrent.

<paranoia>
I'm guessing that BT, Inc may be looking for a closed-source torrent implementation for their new 'Movie Store' in case they need to implement any sort of copy protection or other sort of control over it.
</paranoia>

---

### Post by maniacmusician on 2006-12-07
this really f*cking sucks. uTorrent was my favorite client while on windows and I was looking forward to the author releasing a linux version, closed-source though it may be. This is really frustrating. it's also funny to think that BT, Inc, the fathers of BT, are going to be the ones to ruin the BT protocol by leaking DRM-happy commercial interests into the culture. This annoys me a lot. It always happens though. well-intentioned inventions go awry after turning into a corporation-controlled object. *sad*

---

### Post by Rhapsody on 2006-12-08
> Q: How will uTorrent’s technology be integrated with the current BitTorrent client?

A: Although uTorrent is lightweight, it is missing the patented innovations BitTorrent has made at the protocol level. It is also lacking an implementation for Mac and Linux. We will improve uTorrent in these arenas.

What they give with one hand, they take away with another. Mac and Linux versions sound good, but 'patented innovations' sounds like Microsoft-style embrace, extend, and extinguish stuff.

---

### Post by zachtib on 2006-12-08
> **Rhapsody said:**
> What they give with one hand, they take away with another. Mac and Linux versions sound good, but 'patented innovations' sounds like Microsoft-style embrace, extend, and extinguish stuff.

That's exactly what I see happening here.  Any improvements uTorrent has over standard Bittorrent will be incorporated into Mainline, then development for uTorrent will suddenly drop off.

Another scenario, which I think is even _more_ likely is that Bittorrent, Inc. incorporates any of their 'proprietary' features into uTorrent, then Mainline as we know it is killed, and uTorrent essentially becomes the new Mainline.  After all, Mainline's market share seems to be pretty low, I'm rarely on a torrent where Azureus and uTorrent make up less than 90% of the swarm, and given their recent deal with the movie industry, I'm sure the movie studios would love it if Bittorrent, Inc's official client was both: A) Extremely popular and widely used, and B) Closed-source and proprietary.

---

### Post by PriceChild on 2006-12-08
As a side note... has anyone read the comments to that post?

I love ubuntuforums.org - that place just sounds nasty :)

---

### Post by Rhapsody on 2006-12-08
> **zachtib said:**
> Another scenario, which I think is even _more_ likely is that Bittorrent, Inc. incorporates any of their 'proprietary' features into uTorrent, then Mainline as we know it is killed, and uTorrent essentially becomes the new Mainline.  After all, Mainline's market share seems to be pretty low, I'm rarely on a torrent where Azureus and uTorrent make up less than 90% of the swarm, and given their recent deal with the movie industry, I'm sure the movie studios would love it if Bittorrent, Inc's official client was both: A) Extremely popular and widely used, and B) Closed-source and proprietary.

Pretty much what I was thinking. Looking at the torrents I've seen, uTorrent would be among the top 3 in popularity (with Azureus and BitComet being the others). Porting uTorrent to Mac and Linux, then introducing patented changes to uTorrent which would be hard or impossible for others implement due to legal difficulties seems like a good way to kill the others off. Then the undisputed #1 BitTorrent client is owned and controlled by a company which has pledged to the MPAA to 'actively work against piracy'. The 'new' BitTorrent protocol is inaccessible to those the MPAA would rather not see use it, and it is gone to all but the minority that stay with the old protocol.

Unfortunately for BitTorrent Inc, I don't think this is going to work. The reaction on the uTorrent forum was generally violently against any of this, with only a small minority being in favour at all. The more likely probability is that uTorrent will become marginalized as everyone dumps it. Eventually, ludde will decide he's had enough and leave for a new project. uTorrent will become like Winamp. A previously well-loved but proprietary program that had the magic stripped out by corporate interests, serving as an example of the durability of free software.

I've started to wonder whether ludde planned on this from the start. The other big projects he's started or made major contributions to (ScummVM, OpenTTD) are both free software, but uTorrent was always proprietary. Did he always plan to be making a living from uTorrent some day? If so, I think he'll be about as popular as Novell soon enough...

---

### Post by maniacmusician on 2006-12-08
whatever the original plan was, the whole thing smells of corporate reek now. uTorrent used to be the toy of the people and now it won't be. Just today, I was introducing someone I knew to torrent downloads. Normally, I would steer them towards uTorrent, but in light of all this, I've advised them to go the route of Azureus instead. 

Just as a little background info, this guy is a counselor at my school. I've started him off with torrents and open source, and I've got him thinking about Linux already. The impression I got from him was that if he can get the hang of torrents and stuff, and if he likes open source alternatives, he's going to risk the jump to Linux. He was also pretty impressed when I told him he could just set up a dual-boot (with detailed instructions from me, of course :)) 

(sorry for getting off track a little. the point being, I'm not even advising people to use uTorrent anymore. This reeks; I was looking forward to a linux version from ludde. I won't consider one from BT, Inc.)

---

### Post by Brunellus on 2006-12-08
Educate an ignorant reader:  isn't the bittorrent protocol a GPL'd bit of Free Software?

If any uTorrent code or features make it onto a new Bittorrent client...that makes those features GPL'd as well.

---

### Post by haxer on 2006-12-08
Didnt the united states of america "usa" buy the uttorent to owerview all souces to stop filesharing trough .torrent?:-k

---

### Post by Brunellus on 2006-12-08
> **haxer said:**
> Didnt the united states of america "usa" buy the uttorent to owerview all souces to stop filesharing trough .torrent?:-k
I don't even understand this post.

---

### Post by ciscosurfer on 2006-12-08
> **haxer said:**
> Didnt the united states of america "usa" buy the uttorent to owerview all souces to stop filesharing trough .torrent?:-k

> **Brunellus said:**
> I don't even understand this post.ROTFL :lol:

---

### Post by maniacmusician on 2006-12-08
I think he's saying that the US gov't obtained uTorrent code to monitor filesharing and watch for piracy. 
1. they don't need uTorrent code to do this
2. That's a totally incorrect statement.

@Brunellus: If the BT protocol is truly GPL'd then I don't see how this will work out. BT, inc has stated that they have no plans to open source uTorrent. Anyways, if your theory were true, then uTorrent would already have been GPL'd because it's already using the BT protocol (obviously, that's its only function). So no, I don't think it's going to be open-source, and even if it was OS'ed, I wouldn't use it. It's going to be used to spread DRM'd content from media manufacturers.

---

### Post by TMM on 2006-12-08
Ah, I'm not too worried. We all know what happens in the torrent world... one good thing goes down, and 20 new ones pop up to replace it (e.g. suprnova.org anyone?). I'm sure another good client will come along :). Until then, there really isn't anything wrong with the latest utorrent. It just works, so i don't see any reason to need to update to some backdoored version in the future :-k

---

### Post by BWF89 on 2006-12-08
I switched BitTorrent clients. My downstairs PC (Linux) from the official BitTorrent Client to Shadow's Client (aka BitTornado) and my upstairs iMac to TomatoTorrent. I'm not going to use any software that has affiliations or is owned by a company that has affiliations with the MPAA.

---

### Post by christhemonkey on 2006-12-08
Maybe something like Deluge will pop nicely in place? ;)

---

### Post by KoRnholio on 2006-12-08
Yeah, now's a perfect time for a Windows port of Deluge.

---

### Post by ciscosurfer on 2006-12-08
> **KoRnholio said:**
> Yeah, now's a perfect time for a Windows port of Deluge.Coming soon: [http://www.deluge-torrent.org/index.php/2006/12/07/deluge-on-win32/](http://www.deluge-torrent.org/index.php/2006/12/07/deluge-on-win32/)

---

### Post by zachtib on 2006-12-08
> **christhemonkey said:**
> Maybe something like Deluge will pop nicely in place? ;)

> **KoRnholio said:**
> Yeah, now's a perfect time for a Windows port of Deluge.

> **ciscosurfer said:**
> Coming soon: [http://www.deluge-torrent.org/index.php/2006/12/07/deluge-on-win32/](http://www.deluge-torrent.org/index.php/2006/12/07/deluge-on-win32/)

Wow, I don't even have to shamelessly plug my own project anymore :D

---

### Post by banjobacon on 2006-12-08
> **Brunellus said:**
> Educate an ignorant reader:  isn't the bittorrent protocol a GPL'd bit of Free Software?

If any uTorrent code or features make it onto a new Bittorrent client...that makes those features GPL'd as well.

Bittorrent, the software, is not GPL'd. It's released under the BitTorrent Open Source License. 

Either way, don't the authors of the code have the right to relicense the code? And does the protocol fall under any license?

---

### Post by zachtib on 2006-12-08
well, the good news is that Bittorrent, Inc can't exactly kill the protocol, because they'd have to change something and implement some proprietary feature, and if all the other clients just stay put, they will keep working.

---

### Post by graigsmith on 2006-12-09
does the regular? mainline version of bittorrent come preinstalled with ubuntu?   or is that an open source version.  im not talking about the gui bittorent that works in gnome. but the text version in the console.

---

### Post by zachtib on 2006-12-09
> **graigsmith said:**
> does the regular? mainline version of bittorrent come preinstalled with ubuntu?   or is that an open source version.  im not talking about the gui bittorent that works in gnome. but the text version in the console.

it's probably based off of the 3.x series, when bittorrent was truly "free"

---

