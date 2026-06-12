---
title: "Home Server Questions (Media and File Backup)"
date: 2009-12-23
forum: Server Platforms
---

### Post by linux4life88 on 2009-12-23
I was looking at the cost to purchase the parts for a new home server setup that I could use for media streaming/dvr functions (I was considering mythTV) and also for file storage and backup. I have never set up a server before and I had a few questions about this undertaking:

1) Does the frontend do the video ripping/encoding or does the backend server do it? I know both probably could do it but which is recommended to it. If I'm going to have the server doing the ripping/encoding would I need a decent graphics card for the server? I'm assuming that the frontend would need somewhat decent graphics to simply be able to play HD video, let alone if it rips/encodes video.

2) Do I need to have the TV tuner card in the server or do I need to have the tuner in the fronend that is hooked up to the TV.

3) Sort of relates to question 2, but if the server backend has a TV tuner card then can I remotely watch TV, lets say, on my laptop?

4) I was hoping to have this server both quite and as energy efficient as possible. When looking at power supplies would an 80 plus gold rated power supply really save me that much money in the long run over running an 80 plus or 80 plus bronze rated power supply? I've never had a power supply that I can remember over an 80 plus bronze rating.

5) Now for the fun part, what is a example configuration that you would recommend. The part I'm most interested in is CPU and what I will most likely need there. It would be awesome if I could run this off of an Intel Atom 330 processor because of how little power they use, but I'm afraid I will need a lot more power than that.

I know I have asked a lot of questions that are very varied in nature, but as I said I'm new to the server arena and I was wanting a home server to do a couple of different things. Thanks for any help/advice/tips in advance.

---

### Post by garfonzo on 2009-12-23
> **linux4life88 said:**
> I was looking at the cost to purchase the parts for a new home server setup that I could use for media streaming/dvr functions (I was considering mythTV) and also for file storage and backup. I have never set up a server before and I had a few questions about this undertaking:

1) Does the frontend do the video ripping/encoding or does the backend server do it? I know both probably could do it but which is recommended to it. If I'm going to have the server doing the ripping/encoding would I need a decent graphics card for the server? I'm assuming that the frontend would need somewhat decent graphics to simply be able to play HD video, let alone if it rips/encodes video.

2) Do I need to have the TV tuner card in the server or do I need to have the tuner in the fronend that is hooked up to the TV.

3) Sort of relates to question 2, but if the server backend has a TV tuner card then can I remotely watch TV, lets say, on my laptop?

4) I was hoping to have this server both quite and as energy efficient as possible. When looking at power supplies would an 80 plus gold rated power supply really save me that much money in the long run over running an 80 plus or 80 plus bronze rated power supply? I've never had a power supply that I can remember over an 80 plus bronze rating.

5) Now for the fun part, what is a example configuration that you would recommend. The part I'm most interested in is CPU and what I will most likely need there. It would be awesome if I could run this off of an Intel Atom 330 processor because of how little power they use, but I'm afraid I will need a lot more power than that.

I know I have asked a lot of questions that are very varied in nature, but as I said I'm new to the server arena and I was wanting a home server to do a couple of different things. Thanks for any help/advice/tips in advance.

Some good questions, some of which I might shed some light on. For what its worth, I have something similar to what I think you're trying to accomplish. Let me explain my setup and it might help you figure out how to do your setup, or just give you some new ideas. 

- I have a home server running Ubuntu Server Edition sitting in my garage and has a tonne of space for all our home files from all our computers. It has Samba running so everyone plays nice.

- I have a Vista machine (my main workstation) that has the server's hard drives mapped to it (dealt with via Samba on the server). This computer has a TV tuner card and uses Windows Media Center to record TV shows. On this machine I installed a free piece of software called "Media Buddy" which monitors for newly recorded content shows, converts it to a compressed format, and sends the file to my home server while deleting the original (no files left on my main workstation). 

- I have a third computer hooked up to my movie projector/TV via an HDMI cable and also has the server's hard drives mapped to it. This computer runs WinXP. To watch a TV show or any content, I simply navigate to the server's hard drives, and open the show I want to watch. 

So, I think the above may have answered some of your questions, if not, here's my thoughts on your questions:

Q1) The only way to get cable TV into any computer is through a capture card (a TV tuner card). You would want to get a card the does the ripping itself instead of offloading some of the work onto the CPU. This way, the card does all the hard work and the computer can sit back and just store the file. Having never used MythTV (too much work for my liking) I'm not sure which computer should do this chore, but my thought would be the backend.

Q2) See Q1

Q3) Interesting idea. I know that VLC Player can do something like this, but I have never tried. 

Q4) I have no clue on that stuff. 

Q5) I would say that this comes back to how your overall network is setup and which computer is doing the TV recording. As outlined in my setup above, my server doesn't do any of the hard work. My main computer does the recording and converting and just ships the file over to the server. When watching a show, the computer hooked up to the projector has to do the hard work of translating the file into a movie (I use VLC to watch all videos) and again, the server just provides the file. 

With my setup, my server does nothing but serve files. This is true for my music too - all the client computers get files from the server to listen to, the server doesn't stream the music. 


I'm not sure if I've muddied the waters or helped here. If I'm off on any of this, I would hope my fellow Ubuntu users would point out my error. In any event, I hope I've provided something useful. 

Good luck with the server! It's a lot of fun!

---

### Post by linux4life88 on 2009-12-24
Thank you very much for sharing your setup and answering the questions that you could. My main computer that I use is my laptop, that is why I was wondering if it would be possible to put the TV tuner in the server. The TV tuner card that I was looking at was a Hauppauge HVR-1600 tuner card and saw that it does hardware encoding. I was also looking at a Nvidia graphics card that handles VDPAU. By having these two in the server I thought I could significantly diminish the load on the processor, therefore I might possibly be able to use an Intel Atom 330 processor in the server. I know it might sound ludicrous to use an atom processor in a server but my reasoning behind it is that the server is going to be on 24/7 and the atoms use almost no power at all. This would help make the electrical bill a lot more affordable. If not the atom I was looking at a Celeron dual core or a Pentium dual core. This was just my thoughts as I said though I'm new to the server and thanks again garfonzo for the help.

---

