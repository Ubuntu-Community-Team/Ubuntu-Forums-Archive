---
title: "Streaming Video to Another Computer?"
date: 2008-12-27
forum: Ubuntu Studio
---

### Post by bgugi on 2008-12-27
okay, so here's the scoop. i have several videos on my hdd, and i want to stream them to a friend while watching. i was thinking about using vlc (for upstream and downstream). it didn't work.

i'm running ubuntu 8.10, he is running xp sp2or3. we both have vlc and an internet connection. we can both ping each other, and have a pretty decent ping (~35ms iirc).

i went to open file > streaming (drop down next to play). i checked play locally, and (in different trials) checked http, rtp, and prefer udp over rtp, on each i tried inputting his ip, and no ip. he tried connecting each time, to each protocol, to my ip.

so, what am i doing wrong? i don't think its a router issue, because i can't stream between vlc windows by entering 127.0.0.1...

---

### Post by seventyeights on 2008-12-28
I've used vlc for streaming *locally* with great success.

Both of you should double check your ip's.
Consider temporarily setting up dmz.
Use a lo-res (320x240) source while testing.

However, if I recall correctly,  I think you'd want to know that you can't watch the streamed video on the server side. Perhaps you and your friend can connect as clients to a third machine set up as a server? (not something I ever tried)

---

### Post by Jose Catre-Vandis on 2008-12-28
If your friend is not on the same subnet as you (LAN) then the problem is most likely to be an IP adressing issue. If he is trying to connect from over the internet then you / your router / PC has either a fixed or static IP address that is known/accesible to the world, probably protected and locked down by your NAT/firewall etc. VLC uses a broadcast IP for internal LANs, something odd like 224.0.1.2. You will need to get your serving PC accessible to the internet and then forward the ports required for your friend to access the stream.

Suggest you google:
```
vlc stream video to the internet
```

to find your required solution, there is lots of help out there

---

### Post by bgugi on 2008-12-28
i'm pretty sure its not the connection, because i can't stream between windows on the loopback (127.0.0.1)

---

### Post by seventyeights on 2008-12-28
ooh ooh the new vlc is sooo nice!   Forget what I said before about playing streamed files locally, I see there is a "play locally" checkbox now.

It didn't work for me at first. But here is what I did:

1. Start two instances of vlc, for the client and server.

In the client instance:
2. Select "open network" from the media menu.
3. On the network tab, select protocol RTP, 127.0.0.1, Port 1234
4. Click "play", it will start when you get the server ready.

In the server instance:
5. Select "streaming" from the media menu.
6. Select a file to stream. *Make sure your choice pops into the "File Names" box below.*
7. Click "Stream" 
8. Check "RTP" , 127.0.0.1 port 1234
9. Below that, don't pick an encapsulation. Pick a profile instead. I chose "H264" *mpeg2 also worked*
10. Click stream. You should see the client start up.

---

### Post by bgugi on 2008-12-29
okay, so now how does this translate over the internet?

which ip do i need to enter on the server side, and what ip does he need to enter for the client?

i.e, does one person need localhost, or their lan ip, or their [http://whatismyip.com/](http://whatismyip.com/) ip?

either way, loopback worked, so that's one less thing i'm doing wrong :D

---

### Post by bgugi on 2009-01-02
why is it that only two profiles will actually stream from window to window?

just a note: still trying to figure out how to setup all the fun networkyness... i've set my router to allow all traffic on port 9005 (chosen at random) originating from either the wan or my computer to pass to the other 

also: h264 reports that it can't find aac, and mpeg2 reports that it couldn't encode the video... how can i make vlc able to encode these?

---

