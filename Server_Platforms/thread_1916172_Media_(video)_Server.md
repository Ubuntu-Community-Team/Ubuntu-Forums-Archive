---
title: "Media (video) Server"
date: 2012-01-27
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-27
Hello Everyone,
I just built a system to serve video files (movies) to all the computers on my LAN network. I was wondering if anyone could tell me how to set that up. What folders should I be putting these video files in? I was going to use VLC on the client computers to view the movies.
 
Can I set this up for the computers on the network just see the server in "my computer" as a network drive? That way they can just view what movies on in the folders and then double-click on the one they want to watch?
 
:popcorn:
 
Thanks in Advance!
 
 
For those who are wondering, the system is running with a intel i5, 6GB of ram, and 8 TB (Terabytes) of storage :)

---

### Post by TFroehlich3 on 2012-01-27
Also, would it be possible for me to serve the movies over the internet to my family?

---

### Post by Cheesemill on 2012-01-27
If you have Windows machines on your network then you need to use Samba. 
[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

> **TFroehlich3 said:**
> Also, would it be possible for me to serve the movies over the internet to my family?
Possible, yes.
Illegal, probably.

You would also need a very good upload speed on your internet connection.

---

### Post by TFroehlich3 on 2012-01-27
> **Cheesemill said:**
> If you have Windows machines on your network then you need to use Samba. 
[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)
 
 
Possible, yes.
Illegal, probably.
 
You would also need a very good upload speed on your internet connection.
 
Thank you for the info, I will look into it! 
And these video's are home made from students in my class at a film academy and they want me to host their video's, and allow my and my family (who edit them) to view them as well.

---

### Post by TheFu on 2012-01-29
There are many different ways to share video files on a LAN. The easiest and the way that I do it is with samba, as suggested by [Cheesemill]("http://ubuntuforums.org/member.php?u=559258").  Samba is useful for LAN file sharing, not internet file sharing.  

There are also protocols specific ally designed for video streaming like DLNA.  A few DLNA servers are available for Linux and many people are happy with them.  I tried a few and dropped back to samba.   
MiniDLNA and MediaTomb are DLNA server options.

For sharing videos over the internet, the best option is probably to upload the videos to something like youtube or vimeo and let them handle the transcoding and streaming for you.  Streaming video files uses lots of bandwidth.

However, if you really want to make these video files available to the internet, the you probably need a web server for simple download the video capabilities.  If you need to stream the video files, then you need a video streaming server ... VLC will let you do this and there are other more scalable solutions as well.  Oddly, Apple has released a video streaming server that is free to use for Linux. 

Thread on a similar topic: [http://ubuntuforums.org/showthread.php?t=1847193](http://ubuntuforums.org/showthread.php?t=1847193)

[http://flowplayer.org/tutorials/introduction-to-streaming-servers.html](http://flowplayer.org/tutorials/introduction-to-streaming-servers.html)

Some older articles where found
* 2007 -  [http://www.howtoforge.com/video_streaming_lighttpd_flowplayer](http://www.howtoforge.com/video_streaming_lighttpd_flowplayer)
* 2003 - [http://www.linuxjournal.com/article/6720](http://www.linuxjournal.com/article/6720)

For a problem so easily described, the solutions appear to be more complex than I'd thought.

---

### Post by Markg55 on 2012-02-11
This guide should be of some use. Nicely put together.
[http://www.havetheknowhow.com/](http://www.havetheknowhow.com/)

---

### Post by ptmuldoon on 2012-02-11
> **TFroehlich3 said:**
> Hello Everyone,
I just built a system to serve video files (movies) to all the computers on my LAN network. I was wondering if anyone could tell me how to set that up. What folders should I be putting these video files in? I was going to use VLC on the client computers to view the movies.
 
Can I set this up for the computers on the network just see the server in "my computer" as a network drive? That way they can just view what movies on in the folders and then double-click on the one they want to watch?

You are doing almost exactly what I am doing, but with more storage space :)

Like mentioned above.  Set up a samba file sharing on the ubuntu server.  But for you front ends, forget about VLC.   Go with a solid full fledged Media Front End.  In my opinion XBMC is the best.

As far as serving movies over the internet to family.   Not sure on the legal aspects, but unless you have some serious upload speed, forget about it.  It will never stream fast enough.

---

### Post by TFroehlich3 on 2012-02-11
> **ptmuldoon said:**
> You are doing almost exactly what I am doing, but with more storage space :)

Like mentioned above.  Set up a samba file sharing on the ubuntu server.  But for you front ends, forget about VLC.   Go with a solid full fledged Media Front End.  In my opinion XBMC is the best.

As far as serving movies over the internet to family.   Not sure on the legal aspects, but unless you have some serious upload speed, forget about it.  It will never stream fast enough.

Alright thanks for the info!  And my internet speeds are rolling 77 megs down, and 10 megs up :)

---

### Post by SeijiSensei on 2012-02-12
I don't think you need any complicated setup on the server to distribute the videos.  What matters is the codecs used to encode them and the container format in which the movies are stored.  The easiest format to support is XviD in the AVI container.  Most players support this format natively.  So you could just put the videos in a directory visible over the web, and let people play them directly.

Still I'd second the idea of putting the files on YouTube. Create a YouTube "[channel]("http://support.google.com/youtube/bin/static.py?hl=en&guide=1734705&topic=1735163&page=guide.cs")" for your class.  They might have fun designing what it will look like as well.

---

