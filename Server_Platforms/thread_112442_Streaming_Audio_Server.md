---
title: "Streaming Audio Server"
date: 2006-01-04
forum: Server Platforms
---

### Post by ubuntunooob on 2006-01-04
I've searched the threads here, but they left me confused.  I'm looking for software to stream audio from my sound card line in.

Which would you use?

---

### Post by jesushero on 2008-07-04
Hello... 

I think there's a few different options you can choose from.. All of them involve some basic understanding of linux commands. 

So, the server part first: Icecast is an easy and widely-used option. It will receive a stream from either the same or another machine and will host it for listeners to click and listen.. (using a web interface of its own, easy to customise).

Then you need to have something to send the stream.. If you want to set up a bit thing, I'd suggest two computers. One running Icecast on Ubuntu Server and another one sending the stream.. 

Stream side: The obvious option is to use darkice (which also has a simple gui called darksnow) to do it, using Jack to route the soundcard input to darkice (both darkice and darksnow need to be compiled from source if you want to stream mp3, only ogg is there by default). 

I am making something like this, will be ready soon and I will need some beta-testers.. Let me know if you're interested..

---

