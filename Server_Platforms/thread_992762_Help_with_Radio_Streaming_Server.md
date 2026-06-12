---
title: "Help with Radio Streaming Server"
date: 2008-11-25
forum: Server Platforms
---

### Post by nqlblq on 2008-11-25
Alright guys, uber-noob here. I picked up Linux in August and want to make the switch from Fedora to Ubuntu. I hear the Ubuntu server is legit.

The reason I'm here is I have an idea for a live-streaming audio server but I don't know if it will work. 

I own a sports website and I'm going to be broadcasting some (high school and small college) basketball games soon. What I'd like it the ability to put my laptop down, anywhere in the world, and stream live audio from it.

Basically pull the audio signal from my board and plug it into the laptop and stream it live.

Is that possible? And how would I do that? I have the Ubuntu sever edition, but I haven't installed it yet because I'm not sure how to proceed.

Any help would be awesome and very much appreciated.

---

### Post by thelinuxer on 2008-11-25
> **nqlblq said:**
> Alright guys, uber-noob here. I picked up Linux in August and want to make the switch from Fedora to Ubuntu. I hear the Ubuntu server is legit.

The reason I'm here is I have an idea for a live-streaming audio server but I don't know if it will work. 

I own a sports website and I'm going to be broadcasting some (high school and small college) basketball games soon. What I'd like it the ability to put my laptop down, anywhere in the world, and stream live audio from it.

Basically pull the audio signal from my board and plug it into the laptop and stream it live.

Is that possible? And how would I do that? I have the Ubuntu sever edition, but I haven't installed it yet because I'm not sure how to proceed.

Any help would be awesome and very much appreciated.

I understand what you mean by "my board" is some kind of mixer, am I right ? So you gonna input a signal into your PC and need to stream it live. That's an easy thing to do. All you need is a streaming server running icecast and darkice which is a live audio streamer. You should install darkice on your laptop and darkice will send the audio given in the mic input to icecast which should be installed somewhere else, like your VPS or something.

If you're interested and need to know more check this

[http://www.gnuware.com/icecast/](http://www.gnuware.com/icecast/)

It contains all the information you need 
Good luck

---

### Post by nqlblq on 2008-11-25
Awesome. I'll give it a try. I'll probably be back with more questions though. Thanks a bunch.

---

### Post by Thirtysixway on 2008-11-25
You could also look at Shoutcast.  It's not open source, but it is popular and does work on Ubuntu.  My school uses it to broadcast our radio station online.

---

### Post by nqlblq on 2008-11-28
So, when making a server what is my ip addy? Can I designate it, or is it somewhere that I need to find.

Thanks and sorry, again, uber noob.

---

