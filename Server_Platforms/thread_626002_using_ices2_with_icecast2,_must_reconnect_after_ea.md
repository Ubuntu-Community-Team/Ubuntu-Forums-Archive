---
title: "using ices2 with icecast2, must reconnect after each song"
date: 2007-11-28
forum: Server Platforms
---

### Post by davidshere on 2007-11-28
I read and followed this awesome tutorial:

[http://www.howtoforge.com/linux_webradio_with_icecast2_ices2_p2](http://www.howtoforge.com/linux_webradio_with_icecast2_ices2_p2)

and now have my own internet radio station!!!

[http://lancer.davidshere.com:8000/](http://lancer.davidshere.com:8000/)

One small problem.  When listening, a song plays, and when it ends, the stream goes silent.  I'm still connected, but no music.  I have to disconnect and reconnect (stop/play) in order to get the music back.

In the ices2 log, I get this:

```
[2007-11-28  16:22:48] INFO playlist-builtin/playlist_read Currently playing "/home/david/Desktop/music/Soundtracks/Beverly_Hills_Cop/03. Junior - Do_You_Really__Want_My_Love__.ogg"
[2007-11-28  16:22:48] DBUG encode/encode_clear Clearing encoder engine
[2007-11-28  16:22:48] DBUG reencode/reencode_page Reinitialising reencoder for new logical stream
[2007-11-28  16:22:48] INFO encode/encode_initialise Encoder initialising in VBR mode: 2 channels, 44100 Hz, nominal 64000
[2007-11-28  16:26:32] INFO playlist-builtin/playlist_read Currently playing "/home/david/Desktop/music/Pop/Dance_Naked/05. John_Mellencamp - L.U.V..ogg"
[2007-11-28  16:26:32] DBUG encode/encode_clear Clearing encoder engine
[2007-11-28  16:26:32] DBUG reencode/reencode_page Reinitialising reencoder for new logical stream
[2007-11-28  16:26:32] INFO encode/encode_initialise Encoder initialising in VBR mode: 2 channels, 44100 Hz, nominal 64000
[2007-11-28  16:29:33] INFO playlist-builtin/playlist_read Currently playing "/home/david/Desktop/music/Soundtracks/Beverly_Hills_Cop_III/10. The_Supremes - Come_See_About_Me.ogg"
[2007-11-28  16:29:33] DBUG encode/encode_clear Clearing encoder engine
[2007-11-28  16:29:33] DBUG reencode/reencode_page Reinitialising reencoder for new logical stream
[2007-11-28  16:29:33] INFO encode/encode_initialise Encoder initialising in VBR mode: 2 channels, 44100 Hz, nominal 64000

```

any help will be greatly appreciated.  Eternally grateful, firstborn children, all that...

I suppose I might mention that this is running on a development box running Hardy Heron, if that matters.

---

