---
title: "VLC Web Interface via command line"
date: 2011-07-17
forum: Server Platforms
---

### Post by ptmuldoon on 2011-07-17
I'm using headless Ubuntu Server as a file server, and I'm trying to see if I can some video's to stream to my android device.

I learned I can use a VLC app for the phone, but it needs VLC on a home machine with the Web Interace enabled.

Is this something I can seup on my Ubuntu Server?  I installed VLC on the server, but I can't seem to figure out how to set/start a Web Interface.

Can you do this via a terminal?

EDIT...

I've been googling and searching best I can, and came across this here, but yet attempts to access the server at port 9090 still fail.  

Any help would be greatly appreciated

[http://wiki.videolan.org/How_to_DBox](http://wiki.videolan.org/How_to_DBox)

---

### Post by ptmuldoon on 2011-07-20
Well, I'm on my 3rd day of trying to figure this out.    I've found the VLC wiki and how to's, yet still can not quite figure out how to get a headless Ubuntu server to stream VLC.

Here's the other info I found

[http://www.videolan.org/doc/play-howto/en/ch04.html](http://www.videolan.org/doc/play-howto/en/ch04.html)

and I've tried all sorts of vlc and cvlc commands, but can't seem to access anything via a web browser.

I wonder.. Do you need to have a video card, etc in your server for this to work?

Again, any and all help is much appreciated.

---

### Post by Wayne_V on 2011-07-20
try the example here under 'http streaming':  [http://www.videolan.org/doc/streaming-howto/en/ch04.html](http://www.videolan.org/doc/streaming-howto/en/ch04.html)

---

### Post by smurphy_it on 2011-07-20
A quick google search turned this up:

[http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/](http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/)

---

### Post by Wayne_V on 2011-07-20
this works for me:

server$ unset DISPLAY ; vlc -vvv movie.mp4 --sout '#standard{access=http,mux=asf,dst=0.0.0.0:8080}'

client$ vlc http://<server>:8080/

---

### Post by ptmuldoon on 2011-07-20
I've seen both those tutorials as well already as well, but still haven't had success.  Every time I try to hit my server, my browser tells me it could not connect.

The server has both apache and tomcat installed on it as well.  Thus first I can't use port 8080 for vlc as tomcat is using it.

And if i hit my server at 192.168.xx.xx  it will find the apache webserver.  and if visit 192.168.xx.xx:8080 it finds the tomcat server.

I've been trying to use vlc on port 9090.  yet every time I try, the browser doesn't find it.

Wayne.  That's a new command for me to try, but same thing, I can't get a browser to open up vlc.

---

### Post by ptmuldoon on 2011-07-20
I read somewhere (forget where) that using a port above 8080 may not work.

I just tried on port 7000, and it appears to have connected.

I'm off to do some testing and see how it goes.

---

