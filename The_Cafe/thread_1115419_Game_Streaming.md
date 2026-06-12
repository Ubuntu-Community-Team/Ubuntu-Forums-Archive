---
title: "Game Streaming"
date: 2009-04-03
forum: The Cafe
---

### Post by Indian_Guy101 on 2009-04-03
Hello everyone, 

An idea just dawned on me. I was reading the other day about game streaming such as OnLive and StreamMyGame. Basically how they work, is you have a server that is capable of running any game and you install all you're games on it. Then you stream the game to any pc in you're house. However, the problems with OnLive is that it is not out yet, you have to pay a monthly fee of $50, and they control the server, meaning it is nowhere near you. It is in Palo Alta, CA and they stream the games over the Internet. The problem with StreamMyGame is that it only plays a very little amount of games and the software to be installed on the server is only for Windows. Also it requires me to the client and server programs to access the internet, meaning i have to unblock them in my firewall and I don't know why. That was when I was thinking, why can't I do something like that which runs on Linux (superior) servers, that is local, and can be streamed to  any operating system? So I was thinking if my favorite community would have any ideas to share.

---

### Post by wildman4god on 2009-04-03
well those streaming game services use a special compression to go over slower WAN links, I guess it would be possible without compression for over a LAN but the problem is that there isn't really any software out for that yet. That would be something you would have to pioneer your self with some friends.

---

### Post by Indian_Guy101 on 2009-04-04
The thing is I don't know where to start. That is pretty much why I am asking for suggestions

---

### Post by wildman4god on 2009-04-05
let me do some searching on the net and get back to you.

---

### Post by wildman4god on 2009-04-05
Okay did some checking and found this site:

[www.streammygame.com](www.streammygame.com)

It's available for all OS's but people have said its a little complicated for the normal game player to start a game, so you may want to look into making it eaiser to use, also this would require a very powerful server because this meathod mean that the computer is processing that game the same number of times as you have clients running the game, and even with today's powerfull desktops, we normally only run once instance of a game, and some newer games even push desktops to their limits, so this will not be a cheap project. You just can't use some pc for a server you need a very (and I mean very) powerful server.

Hope that helps. Good luck and God speed.

Edit: I forgot, you also need industrial gigabit speed switches, By industrial I mean the type a corporation or small business would use, not something you pick up at staples.

Edit again: My bad, it doesn't run on mac, it runs on windows, linux and PS3.

---

### Post by zekopeko on 2009-04-05
> **wildman4god said:**
> Okay did some checking and found this site:

[www.streammygame.com](www.streammygame.com)

It's available for all OS's but people have said its a little complicated for the normal game player to start a game, so you may want to look into making it eaiser to use, also this would require a very powerful server because this meathod mean that the computer is processing that game the same number of times as you have clients running the game, and even with today's powerfull desktops, we normally only run once instance of a game, and some newer games even push desktops to their limits, so this will not be a cheap project. You just can't use some pc for a server you need a very (and I mean very) powerful server.

Hope that helps. Good luck and God speed.

you are running only one instance of the game and are encoding the video stream then sending it to the client(which is sending only keyboard and mouse clikcs to the server). like watching the movie over the network.

i played fallout3 on a PentiumM 2GHz with a X3100 since i stream the game from the rig in my sig.

so if your main computer (the server) can play the game then the only extra load you have is to encode the stream and send it over the network. that could be handled by a quad core machine since most  games us only 2 cores and the rest are idling so you could give those 2 cores to the video encoder. or you could put a cheap mid-range graphic card in and encode on it with something like CUDA or OpenCL.

EDIT: sorry should have paid more attention when reading. in a multi-client setup you would have to have more instances of games running simultaneously.

---

### Post by artir on 2009-04-05
I think you can do it with VLC over RDP and a fast encoder and some kind of app that send your input back to the server.

---

### Post by pwnst*r on 2009-04-05
> **wildman4god said:**
> Okay did some checking and found this site:

[www.streammygame.com](www.streammygame.com)

It's available for all OS's but people have said its a little complicated for the normal game player to start a game, so you may want to look into making it eaiser to use, also this would require a very powerful server because this meathod mean that the computer is processing that game the same number of times as you have clients running the game, and even with today's powerfull desktops, we normally only run once instance of a game, and some newer games even push desktops to their limits, so this will not be a cheap project. You just can't use some pc for a server you need a very (and I mean very) powerful server.

Hope that helps. Good luck and God speed.

Edit: I forgot, you also need industrial gigabit speed switches, By industrial I mean the type a corporation or small business would use, not something you pick up at staples.

Edit again: My bad, it doesn't run on mac, it runs on windows, linux and PS3.

lol, read the first post.

---

### Post by Indian_Guy101 on 2009-04-05
> **wildman4god said:**
> Okay did some checking and found this site:

[www.streammygame.com](www.streammygame.com)

It's available for all OS's but people have said its a little complicated for the normal game player to start a game, so you may want to look into making it eaiser to use, also this would require a very powerful server because this meathod mean that the computer is processing that game the same number of times as you have clients running the game, and even with today's powerfull desktops, we normally only run once instance of a game, and some newer games even push desktops to their limits, so this will not be a cheap project. You just can't use some pc for a server you need a very (and I mean very) powerful server.

Hope that helps. Good luck and God speed.

Edit: I forgot, you also need industrial gigabit speed switches, By industrial I mean the type a corporation or small business would use, not something you pick up at staples.

Edit again: My bad, it doesn't run on mac, it runs on windows, linux and PS3.

Only the client software runs on linux and ps3. The server software runs only on Windows, that is my main problem because I have a linux server. Also the server is processing the game the number of times that I have clients running the games **at the same time** right? 

If some one would like to work with me on this let me know, and if you would like to lead I am open.

---

### Post by wildman4god on 2009-04-05
> **Indian_Guy101 said:**
> Only the client software runs on linux and ps3. The server software runs only on Windows, that is my main problem because I have a linux server. Also the server is processing the game the number of times that I have clients running the games **at the same time** right? 

If some one would like to work with me on this let me know, and if you would like to lead I am open.

well it would make sense to run windows games on a windows server, if you could run windows games on a Linux server then we could also run them on a Linux desktop, but are we talking about running open source games and streaming them?

---

### Post by Indian_Guy101 on 2009-04-05
Wel I will be running both open source and closed source games. I have the windows games installed via WINE on the linux server. They run fine.

---

### Post by wildman4god on 2009-04-06
Well then I don't know of any software that would do what you want, you could try having people remote desktop into the server to run the games. Also talk to people on the Red Hat and Suse forums since they deal with enterprise desktops, one of the things and enterprise will do is essentially stream the desktop to thin clients. I hear about it all the time on the windows side, but I have only heard about it once with the Linux desktop, so Suse and Red Hat are the guys to ask, if you can stream desktops and apps you should be able to stream games.

---

### Post by Indian_Guy101 on 2009-04-06
Can u only stream to thin clients? because my clients are'nt thin. Also could you give me a sample specs of the server I would need. My friend told me a few things and what he said was absolutely astonishing.

---

### Post by wildman4god on 2009-04-06
No you can use any computer, I only metioned thin clients because 1. Thats what they normally use and 2. being that thin clients are underpowered I hope that would give you an idea about what kind of desktops you could get away with. 

Also let it be known that while i do know some networking I am no expert in the subject of game streaming. I am only letting you know what I know, like I said, talk to some one from redhat or suse as they'll probably know more than me.

And about the server, I imagine it would have to be pretty powerful, depending on how many clients you plan on connecting. But it sounds like your friend knows more than me, my suggestion is take a laptop and remote desktop in to a desktop pc that runs your games well and try and monitor the cpu and ram usage to get an idea about how much more you'll need, also I would suggest dual graphics cards of the highest end.

Also remember, this is a completely new area, no one until recently has managed to stream games over any kind of network, so right now there are no protocols or software so you are pioneering new technology, it won't be easy.

---

### Post by Indian_Guy101 on 2009-04-06
Well I don't know if my friend knows more than you considering he is 14 (I am 12) Well what he said was I need at least 32 gb of RAM, A Xenon processor, two 1.5 gig Graphic cards... Yeah pretty expensive stuff.

---

### Post by wildman4god on 2009-04-07
Yeah that sounds about right, you'd probably be better off just hosting LAN parties. I know open arena, wormux and assault cube can run on a 32 mb graphics card and a netbook processor, they're plenty of ways to have fun with your friends on the cheap. Most other Linux games will also run on a netbook hardware and the higher end games like nexuiz, warsow, etc will run with a 64 mb graphics card. If I can be of any further help, let me know.

---

### Post by Indian_Guy101 on 2009-04-07
Well those aren't the only games. I am a die hard Assassin's Creed and Prince of Persia fan. Not to mention all the Valve games I love (Half-life series, Counter-Strike 1.6), but 32 gigs of RAM that can't be right. Because think about it. That means that the OnLive people are going to need one server with specifications similar to what I described for each registered user!

---

### Post by wildman4god on 2009-04-07
> **Indian_Guy101 said:**
> Well those aren't the only games. I am a die hard Assassin's Creed and Prince of Persia fan. Not to mention all the Valve games I love (Half-life series, Counter-Strike 1.6), but 32 gigs of RAM that can't be right. Because think about it. That means that the OnLive people are going to need one server with specifications similar to what I described for each registered user!

Onlive has a server farm to handle all the request, the specs I gave was to handle 10 or so clients not just one, I don't know if you'll specifically need 32gb of system ram, games need more graphics processing power than anything else, and normal servers don't have gpu's they do graphics processing on their cpu's. to find out what you need take the system requirements from your most powerful game and multiply it by the number of clients you want and give it an extra 25% for unexpected overhead. Like I said before this is the first time servers have had to process for high end games, so this is uncharted territory. I should also add that I am very conservative in my estimates you might be able to get away with less, but this is what I would run. Also I still don't know if this will work, you will need some very fast networking equipment to do this, remote desktop protocols usually turn of fancy stuff like the clients themes, wallpaper, etc. to save on bandwidth.

---

### Post by Indian_Guy101 on 2009-05-25
I have done some research and it seems that OnLive claims that they are able to do this because of a special proprietary compression format. I checked the SUSE forums, they take forever to respond. **I was wondering if anyone wanted to work on this with me. If we are able to figure this out we have made a discovery that will change the way that pc gaming is done. _If you want to join me, please send me a private message_.** I have also signed up for the open beta so I can get a better view of how this will work. Thank you and I hope that people will want to work with me on this.

---

### Post by monsterstack on 2009-05-25
The idea is not bad. Offload all of the intense game logic processing to the mighty servers in the sky, and let your computer deal with the working it. 

But by God I can imagine this would be *horrible* for lag. Even no more than a few milliseconds would be enough to throw my keyboard out the window in rage. You can get away with lag on normal multiplayer games because the lag is not always apparent when you're playing, even if it's quite a lot. But you'd notice it if your game was streaming to you: lag between every keystroke and twitch of the mouse? Arrgh.

Still, I don't know. Is this a legitimate problem or have they worked out some fancy way to get around this problem? If they have it would be pretty hot.

---

### Post by pwnst*r on 2009-05-25
from what i've read, lag is not an issue.  that's what i kept bringing up too is the lag.  lag, or lack-there-of, can win or lose a match.

---

### Post by Indian_Guy101 on 2009-05-26
As an FPS gamer I understand that lag=crap. I would really like it if someone would work on this with me.

---

### Post by badrra on 2009-06-08
I have done something to this end. Inspired by problems related to the iCafe business here in the Philippines. Please visit my site [here]("http://badrra.wordpress.com"). I was able to stream games not only to a PC (regardless of OS) but also to a PSP. Check the link [here]("http://badrra.wordpress.com").

---

