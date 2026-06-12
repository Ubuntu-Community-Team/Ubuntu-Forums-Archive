---
title: "How-To: Broadcast Shoutcast from Ubuntu"
date: 2009-01-25
forum: Tutorials
---

### Post by Naiki Muliaina on 2009-01-25
This aticle is a 3 part article on running broadcasting Shoutcast music from a Linux desktop to a Shoutcast server. It is aimed at newbies to walls of text and those that just cannot find a good shoutcast guide for Linux. Its also aimed at those, like me, that need Shoutcast on Second Life in Linux. ^^

Ok, so, Shoutcast on Linux kinda sucked for me. I have got it working now, but through none of the normally suggested programs. If you do not want to use what i suggest, try googling VLC, IDJC, DrakIce (and Darksnow) or Amarok.

My way of using Shoutcast is through their own &#8216;looks like a lot of complicated stuff&#8217; way. Its actually however quite easy. Infact if you always broadcast to the same server, you only ever have to make play lists and change the name of the play list in the .conf file once your set up. However, on first viewing this looks complicated to the new to Linux folk, or even just those that dont use terminal and stuff much. My partner uses Mandriva and Mint so never has to touch terminal or config files so was mortified on seeing a wall of text config file when she downloaded Shoutcast. If you know your stuff with linux or know your way about config files, you might want to skip this article. Its aimed at newbies to walls of text and those that just cannot find a good shoutcast guide for Linux. ^^

To download Shoutcast, click the following link:

**[Click here to download Shoutcast]("http://yp.shoutcast.com/downloads/sc_trans_posix_040.tgz")**

Extrat the file to wherever you want. You will have a folder called sc_trans_40 with a couple of files in. The only ones we need are sc_trans.conf and sc_trans_linux. For the sake of this article we are also going to use example.lst as well. The freebsd and macosx can be deleted if you like nice clean folders. ^^

Open up the sc_trans.conf file and you are presented with a wall of text. Below is the list of lines you may have to edit.

PlaylistFile=[COLOR="Red"]example.lst
[/COLOR]
ServerIP=[COLOR="Red"]myserver.com[/COLOR]
ServerPort=[COLOR="Red"]8000[/COLOR]

Password=yourpassword

StreamTitle=[COLOR="Red"]My Gay Son[/COLOR]
StreamURL=[COLOR="Red"]http://mygayson.com[/COLOR]
Genre=[COLOR="Red"]genres go here[/COLOR]

LogFile=[COLOR="Red"]sc_trans.log
[/COLOR]
Shuffle=[COLOR="Red"]1[/COLOR]

Bitrate=[COLOR="Red"]80000[/COLOR]
SampleRate=[COLOR="Red"]44100[/COLOR]
Channels=[COLOR="Red"]1[/COLOR]

Quality=[COLOR="Red"]1[/COLOR]

CrossfadeMode=[COLOR="Red"]1[/COLOR]
CrossfadeLength=[COLOR="Red"]8000[/COLOR]

UseID3=[COLOR="Red"]0[/COLOR]

Public=[COLOR="Red"]1[/COLOR]

AIM=[COLOR="Red"]AIMHandle[/COLOR]
ICQ=[COLOR="Red"]ICQnumber[/COLOR]
IRC=[COLOR="Red"]shoutcast[/COLOR]

That wall of text is suddenly a lot less scary eh? ^^ My partner certainly thought so.

---------------------------------------------------------------------------

In this part I am going to cover what you do with the sc_trans.conf file. If you are only ever going to stream to one server all you ever need to change past the first time is the PlaylistFile entry. For a simple list of what may need editing, have a quick look at Part 1 of this guide.  The bits in red are all you need to change. So lets get editing this file. ^^

For this you will need the following details of the shoutcast server you are broadcasting too.

Server IP
Server Port
Password
Stream Url

Got them? Ok lets roll. ^^ First off, the self explanatory bits.

PlaylistFile=[COLOR="Red"]example.lst
[/COLOR]
Change this to whatever the name of the playlist you want to play is called. Well cover playlists in Part 3 of this guide. For now well just leave it at example.lst.

ServerIP=[COLOR="Red"]myserver.com[/COLOR]
ServerPort=[COLOR="Red"]8000[/COLOR]
Password=[COLOR="Red"]yourpassword
[/COLOR]
All the details you should have for the server your broadcasting to. Replace what ive highlighted in red with your details.

StreamTitle=[COLOR="Red"]My Gay Son[/COLOR]
StreamURL=[COLOR="Red"]http://mygayson.com[/COLOR]
Genre=[COLOR="Red"]genres go here[/COLOR]

Stream Title is whatever you want. Mine is DJ Naiki. Stream Url is as above a detail you should have for your shoutcast server. In Second Life its the club i work fors Land Url. For Genre that is again whatever you want it to be. Mines Urban Chill.

LogFile=[COLOR="Red"]sc_trans.log
[/COLOR]
When broadcasting Shoutcast will save a log into your sc_trans_40 file. This is just the name of it. If you want it to have a different name, edit this. I always just leave it as is.

Shuffle=[COLOR="Red"]1[/COLOR]

Shuffle on or off. 1 is for Shuffle on, 0 is for shuffle off. I cant stand shuffle, i like my playlist to be played as is. You can just delete the 1 and leave it blank and shuffle turns off.

Bitrate=[COLOR="Red"]80000[/COLOR]
SampleRate=[COLOR="Red"]44100[/COLOR]
Channels=[COLOR="Red"]1[/COLOR]

The quailty of the audio that your listeners hear depends directly on the the bit rate of your audio stream. The basic rule is that the higher the bit rate, the higher the quailty of the audio. 96,000 is the most common. The club i work at have 128,000.

Quality=[COLOR="Red"]1[/COLOR]

Quality is self explanatoy. Enter a number 1 to 10. 1 is the best quality, 10 s the worst quality.

CrossfadeMode=[COLOR="Red"]1[/COLOR]
CrossfadeLength=[COLOR="Red"]8000[/COLOR]

Crossfade blends the beggining and ends of songs. Crossfade mode set to 1 is crossfade on, set to 0 is off. Again you can just delete the 1 and leave it blank and this turns it off. Crossfade length is of course the length of the crossfade. Edit as desired.

UseID3=[COLOR="Red"]0[/COLOR]

Allows you to broadcast ID3 tags. Set it to 1 to turn it on, 0 is off.

Public=[COLOR="Red"]1[/COLOR]

Public is wether or not you to have your station on the public listings or not. Again 1 is on, 0 or blank is off.

AIM=[COLOR="Red"]AIMHandle[/COLOR]
ICQ=[COLOR="Red"]ICQnumber[/COLOR]
IRC=[COLOR="Red"]shoutcast[/COLOR]

Edit as desired. They just let people know your handles.  I delete them all and leave them all blank.

Part 3 will be about the Playlist file.

---------------------------------------------------------------------------

Last part of my guide, the play lists. You can call the play lists whatever you like, for this we are going to the example.lst. Personally I have 30+ play lists ready for whenever I need them. Whenever you want to play a different play list, open the conf file, and change the name of the play list. For example:

```
PlaylistFile=example.lst
PlaylistFile=chillout.lst
PlaylistFile=ministry_vs_hedkandi.lst
```

Ok, so on to making a play list. Open example.lst. When you run Shoutcast it will play what ever is in this file in order of this file. If you do not have shuffle turned on it will play in order of The 2 lines are just examples. Delete them both (and the rest of the text if you like, its not needed) and enter the paths to the songs you want to play. An example is below for a four song play list.

```
/home/nai/Shoutcast/sc_trans_040/3 minutes.mp3
/home/nai/Music/Aaliyah/Aaliyah/15 - Try Again.mp3
/home/nai/Music/Chill Carrier - Awakening/01 - Beautiful Flow.mp3
/home/nai/Music/Darude/Sandstorm/01 - Sandstorm (radio edit).mp3
```

In Ubuntu, you can browse for the files in Nautilus, right click and copy them, then paste them into the text file. That will just paste the path into the file. Makes life a little easier if you like using the file manager.

Some things to bear in mind. Now for some odd reason, it has always played from the 2nd track for me. So put your first song into the 2nd line.

Also, the play list keeps repeating itself when done. This can be a pain in the bum if you want a nice smooth ending to your play list. So to counter this, bearing in mind the first time your play list skips the first track, I have a 3 minute long silent track at the start of the play list. This gives me a nice long silence where I can kill Shoutcast. I Kill the process to stop it playing. You can do this through terminal with the KILL command. Personally I keep Ubuntu&#8217;s process monitor open in a small window in the bottom of my screen. Once the play list is done, I right click it and kill it.

Now thats it. Once you have finished your play list make sure the play lists name is in your .conf file correctly. Now start the sc_trans_linux program and it will begin playing your play list.

That&#8217;s it! Your now broadcasting Shoutcast from Linux. Good luck with your DJ&#8217;ing! Hope to hear you soon! ^^


--------------------------------------------------------------------------------------------


New guide for broadcasting with IDJC and Jack posted todays. Linkage here : [http://ubuntuforums.org/showthread.php?t=1434555]("http://ubuntuforums.org/showthread.php?t=1434555")

---

### Post by marseille on 2009-02-11
:guitar: thx!

---

### Post by SoundSquare on 2010-01-26
very interesting post and how to, i'm tired of shoutcasting from a windows box, i'll certainly try what you suggest soon. 

thanks !

---

### Post by MZ250Supa5 on 2010-02-17
Good attempt, but still 'blinded by science' too much info is almost as bad as too little, and I'm still very confused as how to this.  When showing people how to do things I do it in a series of logical steps, using specific example so that people can actually 'do' it.  Keep it *very* simple, and use a 'step -by-step' approach.  I am far from stupid, but I first need to have a 'way in' in order to understand *exactly* how to make this work, including how to create playlists.

---

### Post by MZ250Supa5 on 2010-02-17
Actually I now have to take back my above comments, and say with much egg on face that it is indeed simple to set up.

HOWEVER, there is one vital flaw.  How exactly does one get the sc_trans_linux file to run?  A newbie would not have a clue, which is my predicament.

This is not aimed at this tutorial in specific, but it would be helpful if all guides for 'newbies' were perused before publication to make sure that every step to successful completion is included - so often I see otherwise good tutorial rendered useless by the omission of one vital step - forgivabel in a guide for intermediate, or advanced users, but not in guides for newbies - we all have to start somewhere.

---

### Post by nevaeh.aaric on 2010-02-18
Thanks for the guide and updating us. We are still very confused as how to this but your guideline is very helpful for us. Again thank you.

---

### Post by Qwertinsky on 2010-03-15
Has anyone come up with a linux shoutcast solution that streams LIVE audio? 

SC_Trans only does play lists or trans-codes streams coming from a Windows box running Winamp with the shoutcast plug-in.

I run a live police scanner streaming site and right now I am using two computers. A Windows box (running Winamp with the shoutcast plug-in.) to encode the live audio and a linux box running sc_serv to serve the streams.

The linux box also hosts the website with Apache. 

Has anyone tried running Winamp with the shoutcast plug-in under Wine? Winamp seems to run and play back MP3's but my poor little linux box seems to choke on the shoutcast plug-in.

---

### Post by mjtunes on 2010-07-22
hi ive got it all workin great i just got 1 prob on the radio i dj on ppl like to request and i like put on shuffle i was wonderin if there way to choose wot song to play

---

### Post by MZ250Supa5 on 2010-08-29
I have been using this method for some months now, and most of the time it has worked well, but recently I've been having no end of problems running the app - I make sure that all the settings are correct, and still I get a load of error warnings telling me that the sample rate is wrong, despite the fact that I've made doubly sure that it's all set up correctly.  I'm now tearing my hair out!  I had a look at the updated sc_trans, and the instructions for use are just gibberish to me.  

This is an example of the output I get when I run the app:

<08/29/10@11:19:36> [TRANSCast] DNAS/posix v0.400-LAME (Mar  4 2003) starting up...
<08/29/10@11:19:36> [MAIN] PID: 7511
<08/29/10@11:19:36> [MAIN] Loaded config from sc_trans.conf
<08/29/10@11:19:36> [MAIN] Loading playlist (Music)
<08/29/10@11:19:36> [MAIN] Found (38) entries in playlist
<08/29/10@11:19:36> [MAIN] Playlist decoder thread starting
<08/29/10@11:19:36> [MAIN] Streaming thread starting
<08/29/10@11:19:36> [DECODE] Opened 01 - Allsortz - La Bamba - Radio Edit.mp3
<08/29/10@11:19:36> [CONFIG] WARNING: No InputSamplerate defined, assuming 44100!
<08/29/10@11:19:36> [CONFIG] WARNING: No InputChannels defined, assuming 2!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> [STREAM] Creating stream socket
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338 Hz, must be 44100!
<08/29/10@11:19:36> [DECODE] Opened 01 - Morcheeba - The Sea.mp3
<08/29/10@11:19:36> [STREAM] Connected to host server
<08/29/10@11:19:36> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:19:39> [MAIN] Title Updated
<08/29/10@11:19:43> [MAIN] SIGHUP; Flushing Log File
<08/29/10@11:19:43> [MAIN] SIGHUP handled. lost terminal
<08/29/10@11:19:46> [STREAM] Creating stream socket
<08/29/10@11:19:46> [STREAM] Creating stream socket
<08/29/10@11:19:46> [STREAM] Connected to host server
<08/29/10@11:19:47> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:19:57> [STREAM] Creating stream socket
<08/29/10@11:19:57> [STREAM] Connected to host server
<08/29/10@11:19:57> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:20:07> [STREAM] Creating stream socket
<08/29/10@11:20:10> [STREAM] Connected to host server
<08/29/10@11:20:10> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:20:20> [STREAM] Creating stream socket
<08/29/10@11:20:20> [STREAM] Connected to host server
<08/29/10@11:20:20> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:20:30> [STREAM] Creating stream socket
<08/29/10@11:20:31> [STREAM] Connected to host server
<08/29/10@11:20:31> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:20:41> [STREAM] Creating stream socket
<08/29/10@11:20:41> [STREAM] Connected to host server
<08/29/10@11:20:41> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:20:51> [STREAM] Creating stream socket
<08/29/10@11:20:51> [STREAM] Connected to host server
<08/29/10@11:20:51> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:01> [STREAM] Creating stream socket
<08/29/10@11:21:01> [STREAM] Connected to host server
<08/29/10@11:21:01> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:12> [STREAM] Creating stream socket
<08/29/10@11:21:12> [STREAM] Connected to host server
<08/29/10@11:21:12> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:22> [STREAM] Creating stream socket
<08/29/10@11:21:22> [STREAM] Connected to host server
<08/29/10@11:21:22> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:32> [STREAM] Creating stream socket
<08/29/10@11:21:32> [STREAM] Connected to host server
<08/29/10@11:21:32> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:42> [STREAM] Creating stream socket
<08/29/10@11:21:42> [STREAM] Connected to host server
<08/29/10@11:21:43> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:21:53> [STREAM] Creating stream socket
<08/29/10@11:21:53> [STREAM] Connected to host server
<08/29/10@11:21:53> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:22:03> [STREAM] Creating stream socket
<08/29/10@11:22:03> [STREAM] Connected to host server
<08/29/10@11:22:03> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:22:13> [STREAM] Creating stream socket
<08/29/10@11:22:13> [STREAM] Connected to host server
<08/29/10@11:22:13> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:22:23> [STREAM] Creating stream socket
<08/29/10@11:22:24> [STREAM] Connected to host server
<08/29/10@11:22:24> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:22:34> [STREAM] Creating stream socket
<08/29/10@11:22:34> [STREAM] Connected to host server
<08/29/10@11:22:34> [STREAM] Disconnecting from stream host [waiting 10s]
<08/29/10@11:22:44> [STREAM] Creating stream socket
<08/29/10@11:22:44> [TRANSCast] DNAS/posix v0.400-LAME (Mar  4 2003) starting up...
<08/29/10@11:22:44> [MAIN] PID: 7575
<08/29/10@11:22:44> [MAIN] Loaded config from sc_trans.conf
<08/29/10@11:22:44> [MAIN] Loading playlist (Music)
<08/29/10@11:22:44> [MAIN] Found (38) entries in playlist
<08/29/10@11:22:44> [MAIN] Playlist decoder thread starting
<08/29/10@11:22:44> [MAIN] Streaming thread starting
<08/29/10@11:22:44> [DECODE] Opened 01 - Allsortz - La Bamba - Radio Edit.mp3
<08/29/10@11:22:44> [STREAM] Connected to host server
<08/29/10@11:22:44> [STREAM] Creating stream socket
<08/29/10@11:22:44> [CONFIG] WARNING: No InputSamplerate defined, assuming 44100!
<08/29/10@11:22:44> [CONFIG] WARNING: No InputChannels defined, assuming 2!
<08/29/10@11:22:44> Warning: input file samplerate is -1216760138 

Any constructive help would really be appreciated.

(no, I didn't put the smileys in, they appeared when I Cut & Pasted it here!)

---

### Post by nathanpc on 2010-12-07
> **MZ250Supa5 said:**
> I have been using this method for some months now, and most of the time it has worked well, but recently I've been having no end of problems running the app - I make sure that all the settings are correct, and still I get a load of error warnings telling me that the sample rate is wrong, despite the fact that I've made doubly sure that it's all set up correctly.  I'm now tearing my hair out!  I had a look at the updated sc_trans, and the instructions for use are just gibberish to me.  

Any constructive help would really be appreciated.

(no, I didn't put the smileys in, they appeared when I Cut & Pasted it here!)
Mate, seriously. Put that on a code tag, the things will be more organized. Here is your exmaple:
```
<08/29/10@11:19:36> [TRANSCast] DNAS/posix v0.400-LAME (Mar  4  2003) starting up...
<08/29/10@11:19:36> [MAIN] PID: 7511
<08/29/10@11:19:36> [MAIN] Loaded config from sc_trans.conf
<08/29/10@11:19:36> [MAIN] Loading playlist (Music)
<08/29/10@11:19:36> [MAIN] Found (38) entries in  playlist
<08/29/10@11:19:36> [MAIN] Playlist decoder thread starting
<08/29/10@11:19:36> [MAIN] Streaming thread starting
<08/29/10@11:19:36> [DECODE] Opened 01 - Allsortz - La Bamba -  Radio Edit.mp3
<08/29/10@11:19:36> [CONFIG] WARNING: No InputSamplerate defined,  assuming 44100!
<08/29/10@11:19:36> [CONFIG] WARNING: No InputChannels defined,  assuming 2!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> [STREAM] Creating stream socket
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> Warning: input file samplerate is -1215531338  Hz, must be 44100!
<08/29/10@11:19:36> [DECODE] Opened 01 - Morcheeba - The Sea.mp3
<08/29/10@11:19:36> [STREAM] Connected to host server
<08/29/10@11:19:36> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:19:39> [MAIN] Title Updated
<08/29/10@11:19:43> [MAIN] SIGHUP; Flushing Log File
<08/29/10@11:19:43> [MAIN] SIGHUP handled. lost terminal
<08/29/10@11:19:46> [STREAM] Creating stream socket
<08/29/10@11:19:46> [STREAM] Creating stream socket
<08/29/10@11:19:46> [STREAM] Connected to host server
<08/29/10@11:19:47> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:19:57> [STREAM] Creating stream socket
<08/29/10@11:19:57> [STREAM] Connected to host server
<08/29/10@11:19:57> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:20:07> [STREAM] Creating stream socket
<08/29/10@11:20:10> [STREAM] Connected to host server
<08/29/10@11:20:10> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:20:20> [STREAM] Creating stream socket
<08/29/10@11:20:20> [STREAM] Connected to host server
<08/29/10@11:20:20> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:20:30> [STREAM] Creating stream socket
<08/29/10@11:20:31> [STREAM] Connected to host server
<08/29/10@11:20:31> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:20:41> [STREAM] Creating stream socket
<08/29/10@11:20:41> [STREAM] Connected to host server
<08/29/10@11:20:41> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:20:51> [STREAM] Creating stream socket
<08/29/10@11:20:51> [STREAM] Connected to host server
<08/29/10@11:20:51> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:01> [STREAM] Creating stream socket
<08/29/10@11:21:01> [STREAM] Connected to host server
<08/29/10@11:21:01> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:12> [STREAM] Creating stream socket
<08/29/10@11:21:12> [STREAM] Connected to host server
<08/29/10@11:21:12> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:22> [STREAM] Creating stream socket
<08/29/10@11:21:22> [STREAM] Connected to host server
<08/29/10@11:21:22> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:32> [STREAM] Creating stream socket
<08/29/10@11:21:32> [STREAM] Connected to host server
<08/29/10@11:21:32> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:42> [STREAM] Creating stream socket
<08/29/10@11:21:42> [STREAM] Connected to host server
<08/29/10@11:21:43> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:21:53> [STREAM] Creating stream socket
<08/29/10@11:21:53> [STREAM] Connected to host server
<08/29/10@11:21:53> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:22:03> [STREAM] Creating stream socket
<08/29/10@11:22:03> [STREAM] Connected to host server
<08/29/10@11:22:03> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:22:13> [STREAM] Creating stream socket
<08/29/10@11:22:13> [STREAM] Connected to host server
<08/29/10@11:22:13> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:22:23> [STREAM] Creating stream socket
<08/29/10@11:22:24> [STREAM] Connected to host server
<08/29/10@11:22:24> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:22:34> [STREAM] Creating stream socket
<08/29/10@11:22:34> [STREAM] Connected to host server
<08/29/10@11:22:34> [STREAM] Disconnecting from stream host  [waiting 10s]
<08/29/10@11:22:44> [STREAM] Creating stream socket
<08/29/10@11:22:44> [TRANSCast] DNAS/posix v0.400-LAME (Mar  4  2003) starting up...
<08/29/10@11:22:44> [MAIN] PID: 7575
<08/29/10@11:22:44> [MAIN] Loaded config from sc_trans.conf
<08/29/10@11:22:44> [MAIN] Loading playlist (Music)
<08/29/10@11:22:44> [MAIN] Found (38) entries in  playlist
<08/29/10@11:22:44> [MAIN] Playlist decoder thread starting
<08/29/10@11:22:44> [MAIN] Streaming thread starting
<08/29/10@11:22:44> [DECODE] Opened 01 - Allsortz - La Bamba -  Radio Edit.mp3
<08/29/10@11:22:44> [STREAM] Connected to host server
<08/29/10@11:22:44> [STREAM] Creating stream socket
<08/29/10@11:22:44> [CONFIG] WARNING: No InputSamplerate defined,  assuming 44100!
<08/29/10@11:22:44> [CONFIG] WARNING: No InputChannels defined,  assuming 2!
<08/29/10@11:22:44> Warning: input file samplerate is -1216760138
```
A lot better huh? ;)

---

### Post by SpotHT on 2010-12-07
Nice how-to guide, I am trying it now!

---

### Post by olympus112 on 2011-09-28
Im sorry Im kinda new at this, but nothing is working for me. Yes I realize this information is not up to date as of this day but Im assuming the method is still the same.
I miss being a DJ in Second Life and would like to do so again. Please help.
:(:confused:

---

### Post by charlis jamez on 2011-09-29
its so nice to visit here a nice thread. Am so impressed with your such a good hard work, its definitely a good and diferent idea for others, you guys are doing good work good luck, keep it up..:)
___________
[ search engine optimization ]("http://www.seomaterial.com/") is the way to increase visibility of a website by [ web development ]("http://www.seomaterial.com/").

---

