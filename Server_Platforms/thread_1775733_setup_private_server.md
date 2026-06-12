---
title: "setup private server"
date: 2011-06-05
forum: Server Platforms
---

### Post by Michaël-D on 2011-06-05
Hello all,

first of all...this is my very first post on the ubuntu forum, plz tell me if i posted in wrong category etc...

I'd like to set up a small private server at my home.
It has to be protected with some kind of password/username (no public thing...average use: few hours per week)
The goal would be that i can stream a movie/slideshow on it (live) and the people that are logged in can watch it.
Is this possible-> How do i do this/could you point me to the right tutorial?

thx,

M.

---

### Post by frankplummer on 2011-06-05
Hi,

The only issue you would be facing is that Ubuntu Server does not come with a GUI; it's purely command line-based out of the box. You could install a minimal X server within it for your purpose, but really it could be a lot of hastle for someone who hasn't touched Ubuntu Server before.

A question however - when you say stream a movie/slideshow on it and a user would watch it, do you mean the user would watch it on another device on the network - say another computer - or on that Ubuntu machine? Reason I ask if you've asked about a server, so I'm a little confused :D

---

### Post by Michaël-D on 2011-06-05
hey,

thx for the fast reply, i know ubuntu server is puer command line but if you want to you can install the server apps in ubuntu desktop as well (i would start out that way).

It would be for people to watch outside the network (so i suppose it must be ssh or somth.)

M.

ps: how do i quote part of what you said in my reply?

---

### Post by frankplummer on 2011-06-05
> **Michaël-D said:**
> hey,

thx for the fast reply, i know ubuntu server is puer command line but if you want to you can install the server apps in ubuntu desktop as well (i would start out that way).

I was going to suggest this would be the best method - Ubuntu Desktop makes a very effective home server in itself, even if it does have a fully-fledged GUI.

> **Michaël-D said:**
> 
It would be for people to watch outside the network (so i suppose it must be ssh or somth.)

Okay this makes it slightly more complex.. If you want to stream video over the web you would have to look into it. I've done a quick Google and linked the relevant (I think!) articles below for you to have a look at.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) - Complete Streaming, Multimedia & Video How-To
[http://www.linuxquestions.org/questions/ubuntu-63/streaming-video-from-a-ubuntu-machine-526132/](http://www.linuxquestions.org/questions/ubuntu-63/streaming-video-from-a-ubuntu-machine-526132/) - Streaming video from a Ubuntu machine
[http://ubuntuforums.org/showthread.php?t=909412](http://ubuntuforums.org/showthread.php?t=909412) - build a streaming server

You will need to read up on port-forwarding on your router as well. As for having login credentials I am not so sure - maybe an Apache setup could work wonders for this. Whereby you have a webserver running with a protected directory (requiring login) and you could host files there with which they can stream from your Ubuntu box..

> **Michaël-D said:**
> 
ps: how do i quote part of what you said in my reply?
You click "Quote" at the bottom-right of my post. :)

---

### Post by Lars Noodén on 2011-06-05
[Icecast](http://icecast.org/), [VLC](http://wiki.videolan.org/), or [FFmpeg](http://ffmpeg.org/) can stream video.

---

### Post by Michaël-D on 2011-06-05
ok...i'm getting closer...

so...apache server (i know about port forwarding...)
but still 1 thing about the streaming: i should be able to load a file on the server and play it so people (private) can watch it while it is playing, it should not be permanently accesible => when i don't play anything => nobody is able to see somthing, that's the idea :-)

thx

M.

---

### Post by frankplummer on 2011-06-05
> **Michaël-D said:**
> ok...i'm getting closer...

so...apache server (i know about port forwarding...)
but still 1 thing about the streaming: i should be able to load a file on the server and play it so people (private) can watch it while it is playing, it should not be permanently accesible => when i don't play anything => nobody is able to see somthing, that's the idea :-)

thx

M.
That sounds more like streaming then.

What you could do however is combine both the Apache server method with what Lars has said above and have a protected directory within Apache that hosts the streaming file in it. That way you could achieve the effect you want.

---

### Post by SeijiSensei on 2011-06-05
The only way to accomplish that is to remove the file when you don't want it to be viewed.

Is it important that people watch the video simultaneously, or can they just download it and view it on their own schedule?

Remember that however you send them the file, they'll be able to make a local copy if they're at all savvy.

---

### Post by Michaël-D on 2011-06-05
> **frankplummer said:**
> 
What you could do however is combine both the Apache server method with what Lars has said above and have a protected directory within Apache that hosts the streaming file in it. That way you could achieve the effect you want.

was thinking somthing like that as well...

> Is it important that people watch the video simultaneouslythat's the idea

---

### Post by Michaël-D on 2011-06-05
Could someone point me to a basic (but good) :p tutorial on how to setup an apache server, do i install the whole lamp pack or don't i need all that?

---

### Post by Lars Noodén on 2011-06-05
> **Michaël-D said:**
> Could someone point me to a basic (but good) :p tutorial on how to setup an apache server, do i install the whole lamp pack or don't i need all that?

You don't need the other stuff (mysql or perl/php/python).  If you are just into streaming then you don't even need Apache and can do fine with FFmpeg, VLC or Icecast.  I'd look at Icecast first.

---

### Post by Michaël-D on 2011-06-07
I can get around quite well with VLC but how can i protect my stream with a password? I suppose that was why i was advised the apache server...:)

---

