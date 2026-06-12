---
title: "Media Server"
date: 2009-10-02
forum: Server Platforms
---

### Post by Buntubailey on 2009-10-02
Hello,

I have used an old computer to run ubuntu server 9.10, and installed torrentflux on it, i connect to the server from my laptop and download various media. I also have a network media streamer which connects to the server and lets me browse the torrent folder. However, the media streamer is a no name brand from china and I have found out that it comes up a lot with format not supported for certain popular formats. I was wondering if there is something that I can install on ubuntu server so it will always play a format that I can read from my network media player. I thought I read somewhere that I could install VLC server edition that may help my network media player read these files, is this correct?

---

### Post by openfly on 2009-10-02
most xmpp style media servers can use FFMPEG to do transcoding for streaming.  

however, this can at times be a phenomenal amount of cpu intensive work.  you are generally better off using the proper decoder rather than running your files through a decoder / encoder server side then decoding again on the streaming box.

---

### Post by Buntubailey on 2009-10-02
Thanks for your response, sorry I'm a bit of a newbie when it comes to this, would you be able to point me in the direction of a howto so I could get this up and running?

---

### Post by HDave on 2009-10-02
I've been having good luck with Jinzora.  Set up wasn't too bad and it'll stream many different music or video formats.  And it has a cool web based GUI.  

I put Jinorza/Apache on an Ubuntu server box and stream the media I have on another box.

---

### Post by Buntubailey on 2009-10-02
Jinzora looks pretty cool but my media streamer has no web browser so that is out of the question, I just need something that can do the decoder bit at the server end before it gets to my box so when I play Xvid it doesn't come up with format not supported

---

