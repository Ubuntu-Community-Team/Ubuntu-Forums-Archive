---
title: "How to construct &quot;music htpc&quot;?"
date: 2009-04-25
forum: The Cafe
---

### Post by bogoliubov on 2009-04-25
Hello. I have some 350 CDs and lots of mp3s, flacs and oggs in my music collection. The CDs do take up some space and I'd like to be able to able to listen to all my music from one place.

So I want to rip my CDs to flacs and build a small, cheap, quiet and energy efficient htpc-like computer. Either it should have a large HD or use my LAN to access music on my main computer. This in itself is not very difficult, but I have some more wishes that I don't know how to solve:

I want to be able to browse and play music without having to have a monitor/TV connected. So this means having buttons on the case (or next to it) and a very small screen. The screen could be a monochrome text display (cheap), but I don't know how to choose one that works and how to connect it. 
Changing settings on the machine can be done using ssh from another machine, so the buttons only need to control the music browsing/playing. Also a remote control would be nice, but not that crucial. On the other hand, a remote control may be easier to fix than the buttons on the machine?

Any suggestions on hardware and software solutions to this is very much appreciated!

---

### Post by zmjjmz on 2009-04-25
It would be easier to use a remote with LiRC. I would google for some monochrome displays, but you might have to settle for a small (USB maybe) 7" display.

---

### Post by DMcA on 2009-04-25
I've been thinking about doing something like this too. My idea is to use a minimal terminal to control the music, which is being streamed from a server running mpd (music player daemon) somewhere else (to cut down on noise/space etc).

I've had a brief look for monitors and it shouldn't be too difficult to get hold of one for under £40, although this is still a bit too pricey. There's a lot of small car monitors available although it's actually quite difficult to find anything monochrome - or at least I found it difficult I don't exactly know what I'm looking for. Let me know if you do find or know of something, I'd be very interested. My plan for control keys was to use a USB numeric keypad and then remap the buttons for the necessary functions, which should be straightforward I think.

If you do get hold of a small monochrome display capable of displaying a terminal then an ncurses music player such ncmpc/mpd would be an ideal solution and mpd could run on the same or another machine. If you only have a single line display mpd/mpc could work too. For remote control anyremote running on a mobile phone works well, although something like LiRC would be optimal (I have no experience with IR control though).

---

### Post by bogoliubov on 2009-04-26
I was also thinking about using a numeric keypad as base for the buttons.

A "terminal screen" (is that the right name?) is what I'd like to have. How do I know that it will work with Linux/Ubuntu? And how do I choose and setup music software for this? Any links to guides about it would be nice! 

I think I'd like the music library to reside on my other computer, so that the music htpc will mount the right drives upon startup/login. Usually I use ssh for this.


So far I've planned on getting a cheap mini-itx board with Atom cpu and a digital sound output.

---

### Post by gn2 on 2009-04-26
Just buy an [Acer Revo]("http://gizmodo.com/5204432/acer-revo-and-nvidia-ion-hands-on-flawless-blu+ray-playback-changes-cheap-computers-forever").
[URL="http://www.play.com/PC/PCs/4-/9606798/Acer-Aspire-Revo-Intel-Atom-N230-1-6GHz-1GB-8GB-SSD-Linux-Desktop-PC/Product.html?source=5066&engine=froogle_pc&keyword=Acer+Aspire+Revo+%2F+Intel+Atom+N230+1.6GHz+%2F+1GB+%2F+8GB+SSD+%2F+Linux+%2F+Desktop+PC+(92.G1DYZ.UF0)"]
Currently at pre-order stage in the UK for £179[/URL].

---

### Post by billgoldberg on 2009-04-26
Have you considered buying a wireless network stereo?

Those kind of things can access your music on your server (that you would run on your desktop) and will play it.

This one for example seems like something that would fit your needs:

[http://reviews.cnet.com/digital-audio-receivers-dars/logitech-squeezebox-boom/4505-6470_7-33232996.html](http://reviews.cnet.com/digital-audio-receivers-dars/logitech-squeezebox-boom/4505-6470_7-33232996.html)

---

### Post by bogoliubov on 2009-04-26
> **gn2 said:**
> Just buy an [Acer Revo]("http://gizmodo.com/5204432/acer-revo-and-nvidia-ion-hands-on-flawless-blu+ray-playback-changes-cheap-computers-forever").
[URL="http://www.play.com/PC/PCs/4-/9606798/Acer-Aspire-Revo-Intel-Atom-N230-1-6GHz-1GB-8GB-SSD-Linux-Desktop-PC/Product.html?source=5066&engine=froogle_pc&keyword=Acer+Aspire+Revo+%2F+Intel+Atom+N230+1.6GHz+%2F+1GB+%2F+8GB+SSD+%2F+Linux+%2F+Desktop+PC+(92.G1DYZ.UF0)"]
Currently at pre-order stage in the UK for £165[/URL].

That is a nice machine and I may be interested in it. But I still would have to have the TV on in order to play music.

---

### Post by bogoliubov on 2009-04-26
> **billgoldberg said:**
> Have you considered buying a wireless network stereo?

Those kind of things can access your music on your server (that you would run on your desktop) and will play it.

This one for example seems like something that would fit your needs:

[http://reviews.cnet.com/digital-audio-receivers-dars/logitech-squeezebox-boom/4505-6470_7-33232996.html](http://reviews.cnet.com/digital-audio-receivers-dars/logitech-squeezebox-boom/4505-6470_7-33232996.html)

That is a good idea. But it has to work with linux computers and should not have any speakers. I want a unit for my stereo setup and with a digital output (spdif preferrably)

---

### Post by gn2 on 2009-04-26
> **bogoliubov said:**
> That is a nice machine and I may be interested in it. But I still would have to have the TV on in order to play music.

Once you've selected the tracks you want to hear, just switch the TV (or monitor) off.

EDIT: Or just use a netbook.....?

---

### Post by pwnst*r on 2009-04-26
> **bogoliubov said:**
> Hello. I have some 350 CDs and lots of mp3s, flacs and oggs in my music collection. The CDs do take up some space and I'd like to be able to able to listen to all my music from one place.

So I want to rip my CDs to flacs and build a small, cheap, quiet and energy efficient htpc-like computer. Either it should have a large HD or use my LAN to access music on my main computer. This in itself is not very difficult, but I have some more wishes that I don't know how to solve:

I want to be able to browse and play music without having to have a monitor/TV connected. So this means having buttons on the case (or next to it) and a very small screen. The screen could be a monochrome text display (cheap), but I don't know how to choose one that works and how to connect it. 
Changing settings on the machine can be done using ssh from another machine, so the buttons only need to control the music browsing/playing. Also a remote control would be nice, but not that crucial. On the other hand, a remote control may be easier to fix than the buttons on the machine?

Any suggestions on hardware and software solutions to this is very much appreciated!

here you go:

[http://www.avsforum.com/avs-vb/forumdisplay.php?f=76](http://www.avsforum.com/avs-vb/forumdisplay.php?f=76)

enjoy.

---

### Post by billgoldberg on 2009-04-26
> **bogoliubov said:**
> That is a good idea. But it has to work with linux computers and should not have any speakers. I want a unit for my stereo setup and with a digital output (spdif preferrably)

There are things like that without speakers, that you just have to hook into your speakers.

Most are compatible with Linux.

I'm trying to do the same as you, and am going to buy this one:

[http://www.trustedreviews.com/multimedia/review/2008/09/18/Philips-NP1100-Streamium-Network-Music-Player/p1](http://www.trustedreviews.com/multimedia/review/2008/09/18/Philips-NP1100-Streamium-Network-Music-Player/p1)

or this one:
[http://www.trustedreviews.com/multimedia/review/2008/04/10/Logitech-Squeezebox-Duet-Network-Music-System/p1](http://www.trustedreviews.com/multimedia/review/2008/04/10/Logitech-Squeezebox-Duet-Network-Music-System/p1)

The second one is better, but the first one is cheaper.

---

### Post by pwnst*r on 2009-04-26
> **billgoldberg said:**
> There are things like that without speakers, that you just have to hook into your speakers.

Most are compatible with Linux.

I'm trying to do the same as you, and am going to buy this one:

[http://www.trustedreviews.com/multimedia/review/2008/09/18/Philips-NP1100-Streamium-Network-Music-Player/p1](http://www.trustedreviews.com/multimedia/review/2008/09/18/Philips-NP1100-Streamium-Network-Music-Player/p1)

or this one:
[http://www.trustedreviews.com/multimedia/review/2008/04/10/Logitech-Squeezebox-Duet-Network-Music-System/p1](http://www.trustedreviews.com/multimedia/review/2008/04/10/Logitech-Squeezebox-Duet-Network-Music-System/p1)

The second one is better, but the first one is cheaper.

i've got two of these and couldn't be happier.

[http://www.slimdevices.com/pi_squeezebox.html](http://www.slimdevices.com/pi_squeezebox.html)

---

### Post by bogoliubov on 2009-04-27
> **pwnst*r said:**
> i've got two of these and couldn't be happier.

[http://www.slimdevices.com/pi_squeezebox.html](http://www.slimdevices.com/pi_squeezebox.html)

Yeah, that looks very nice! And if I understood correctly they even support linux! Not bad. 

I guess one installs some server software to stream the files. Any issues with this? 

I'm seriously considering this machine. Thanks for the help!

---

### Post by pwnst*r on 2009-04-27
> **bogoliubov said:**
> Yeah, that looks very nice! And if I understood correctly they even support linux! Not bad. 

I guess one installs some server software to stream the files. Any issues with this? 

I'm seriously considering this machine. Thanks for the help!

no issues for me.  i use the slimserver on both an ubuntu box and a windows box.  they have VERY friendly and helpful forums too.

*edit*  they also have a wireless version that costs a little more, but obviously worth it if you don't have/want to run CAT5/6.  my friend has the wireless version and listens to FLAC exclusively (we both do) and it performs no different than mine.

---

### Post by bogoliubov on 2009-04-30
By the way. The squeezebox seems nice, but is there anyone that also shows video? I'd still want the feature of playing music without have the TV on, and decent linux compatibility.

Any suggestions?

---

### Post by PurposeOfReason on 2009-04-30
Easiest way? Build a computer. Any computer will do, if it can play a flac and connect to the network, you're good. Then mount the networked drives with samba and you're set. Doing it right now. Build you're own is better than those pre builts because you're going to need HDD space, and a lot of it. 350CDs in flac is quite a bit of space and it would be silly to have a small box for media with a bunch of external HDDs.

---

### Post by pwnst*r on 2009-04-30
> **PurposeOfReason said:**
> Build you're own is better than those pre builts because you're going to need HDD space, and a lot of it. 350CDs in flac is quite a bit of space and it would be silly to have a small box for media with a bunch of external HDDs.

you don't understand how the squeezebox works.

---

### Post by pwnst*r on 2009-04-30
> **bogoliubov said:**
> By the way. The squeezebox seems nice, but is there anyone that also shows video? I'd still want the feature of playing music without have the TV on, and decent linux compatibility.

Any suggestions?

um. laptop.

---

### Post by PurposeOfReason on 2009-04-30
> **pwnst*r said:**
> you don't understand how the squeezebox works.
Yes I do, and for $300, it isn't worth if considering he could build a media center for less than $250. Which is cheaper and way more fun. :popcorn:

My solution is fully linux compatible, allows for endless choices, and can have more than one task. All for less.

Edit - Reading, the squeebox compresses audio. Because that is just what you want when it isn't necessary. :roll:

---

### Post by yoasif on 2009-04-30
[mpd]("http://wiki.archlinux.org/index.php/Mpd") is probably the easiest way to do this. basically, set up a mpd machine, and connect to it from some other machine on your network. you can set up playlists, etc.

---

### Post by pwnst*r on 2009-05-01
> **PurposeOfReason said:**
> Yes I do, and for $300, it isn't worth if considering he could build a media center for less than $250. Which is cheaper and way more fun. :popcorn:

My solution is fully linux compatible, allows for endless choices, and can have more than one task. All for less.

Edit - Reading, the squeebox compresses audio. Because that is just what you want when it isn't necessary. :roll:

compresses audio?  where'd you read that.  also, what are you using for the DAC on that nix box?  the squeezebox classic has the Burr-Brown PCM1748.

---

### Post by PurposeOfReason on 2009-05-01
> **pwnst*r said:**
> compresses audio?  where'd you read that.  also, what are you using for the DAC on that nix box?  the squeezebox classic has the Burr-Brown PCM1748.
                           **Audio formats**

             
[LIST]
[*]                     Lossless Formats (Apple Lossless, FLAC, WMA Lossless)
[LIST]
[*]"Bit-perfect" CD audio streaming, with reduced storage and bandwidth usage
[*]Approximately 2:1 compression ratio
[/LIST]
                 
[/LIST]



Right there. They use it as a perk to reduce bandwidth usage. So that right there negates anything a DAC would do. If he really needed a DAC, he'd get one. How you ask? They call it a decent sound card which will blow away whatever integrated POS that box has.

I'm not trying to insult the squeebox. Just saying, there is much better out there. If you want one, fine, I really couldn't care. But as he asked a forum a question, I'm answering with what I believe is best. However, in contrast to all this, it is made by logitech. They make a few good keyboards, that's about it.

---

### Post by DMcA on 2009-05-01
> **PurposeOfReason said:**
> **Audio formats**

             
[LIST]
[*]                     Lossless Formats (Apple Lossless, FLAC, WMA Lossless)
[LIST]
[*]"Bit-perfect" CD audio streaming, with reduced storage and bandwidth usage
[*]Approximately 2:1 compression ratio
[/LIST]
                 
[/LIST]



Right there. They use it as a perk to reduce bandwidth usage. So that right there negates anything a DAC would do. If he really needed a DAC, he'd get one. How you ask? They call it a decent sound card which will blow away whatever integrated POS that box has.

I'm not trying to insult the squeebox. Just saying, there is much better out there. If you want one, fine, I really couldn't care. But as he asked a forum a question, I'm answering with what I believe is best. However, in contrast to all this, it is made by logitech. They make a few good keyboards, that's about it.

I'm not entirely sure what you're saying here. They support FLAC, that's a good thing. It's not doing on-the-fly lossy compression to your music, the information you get out is exactly the same as what's on the original CD. 

Personally I agree that building your own system would be more fun, potentially cheaper, and certainly give you more control, however.

---

### Post by cariboo on 2009-05-01
I do something similar, this is in my shop, so sound quality isn't that important. You can use any computer, install using the minimal iso, and just install a command line system. 

All my mp3's are on my sever, so just mount the share and play your tunes. I use a combination of mpg123 and randomplay. I have about 12,000 mp3's, and I really hate hearing the same song over and over agian, so I edit .randomplayrc so that there won't be any repeats for 7 days. 

Randomplay and mpg123 are in the repositories.

---

### Post by bogoliubov on 2009-05-01
Thanks for all the suggestions. But still what is important for me is to be able to browse and play music without having the TV on! So buttons and a small alfanumeric screen is a must! Also storage is not needed since I'll store the music on my main computer...

---

### Post by simtaalo on 2009-05-01
> **DMcA said:**
>  It's not doing on-the-fly lossy compression to your music,

from the info posted above it seems it is doing exactly that.

---

### Post by Sceiron on 2009-05-01
> **bogoliubov said:**
> Thanks for all the suggestions. But still what is important for me is to be able to browse and play music without having the TV on! So buttons and a small alfanumeric screen is a must! Also storage is not needed since I'll store the music on my main computer...

I have the Squeezebox myself and It is the best way to enjoy/browse your music in Stereo. To me it sounds like its exactly what you are looking for. This is the best technical gadget i have ever bought!

It has spdif, optical and analog output, a nice remote control.
Is supports lossless audio (and more). It is very easy to install in linux (from my experience). I just installed jaunty, no configuration needed except that you need to specify your music directory :)
If you buy the Squeezebox v.3 you will come out a bit cheaper then buying the new version(remote with display) i think.

Im currently running it on wireless, and have never had any problems with buffering or anything else :)

---

### Post by pwnst*r on 2009-05-01
> **PurposeOfReason said:**
> **Audio formats**

             
[LIST]
[*]                     Lossless Formats (Apple Lossless, FLAC, WMA Lossless)
[LIST]
[*]"Bit-perfect" CD audio streaming, with reduced storage and bandwidth usage
[*]Approximately 2:1 compression ratio
[/LIST]
                 
[/LIST]



Right there. They use it as a perk to reduce bandwidth usage. So that right there negates anything a DAC would do. If he really needed a DAC, he'd get one. How you ask? They call it a decent sound card which will blow away whatever integrated POS that box has.

I'm not trying to insult the squeebox. Just saying, there is much better out there. If you want one, fine, I really couldn't care. But as he asked a forum a question, I'm answering with what I believe is best. However, in contrast to all this, it is made by logitech. They make a few good keyboards, that's about it.

interesting, i'll have to dig into that further.  and lol, a good sound card is 1/3 of the cost of the squeezebox and if you don't know what Burr-Brown is, forget it.  i'm talking to a brick wall.  

it's obvious your'e biased against logitech, and that's cool, your choice.

---

### Post by bogoliubov on 2009-05-01
The squeezebox is probably what I'm going for. But in case there is something similar but that also can play video, that'd be perfect! Otherwise I'll need two different machines, which is a bit expensive. 

The DAC is not very important since my stereo amp has a decent built-in (Advance MAP305 DA)...

---

### Post by bigm141414 on 2009-05-01
Try building a computer based on the Atom mobo combos from intel. Stick in a picoPSU and a $5 silent chipset fan and the thing will make no noise and uses very little power. I have a similar setup I use for messing around with Ubuntu and it works well for music and movies. You could always connect a USB remote to it and config linux shortcut keys to work with it.

---

### Post by bogoliubov on 2009-05-01
> **bigm141414 said:**
> Try building a computer based on the Atom mobo combos from intel. Stick in a picoPSU and a $5 silent chipset fan and the thing will make no noise and uses very little power. I have a similar setup I use for messing around with Ubuntu and it works well for music and movies. You could always connect a USB remote to it and config linux shortcut keys to work with it.

Yeah, that was my original idea. But I still don't know how to build it with a alfanumeric display so that I don't need to have the TV on just to play music...?

---

### Post by PurposeOfReason on 2009-05-01
> **pwnst*r said:**
> interesting, i'll have to dig into that further.  and lol, a good sound card is 1/3 of the cost of the squeezebox and if you don't know what Burr-Brown is, forget it.  i'm talking to a brick wall.  

it's obvious your'e biased against logitech, and that's cool, your choice.
Not to get this thread too off topic, but biased and first hand knowledge are two different things. I have dissambled more logitech speakers than you have probably owned. They are decent quality for simple daily tasks, just not for the price. I fail to see what BB Co. has to do with any of this. Really, I think you're trying to hide under various rocks and not look at reason, tests, and facts.

---

### Post by pwnst*r on 2009-05-01
> **PurposeOfReason said:**
> Not to get this thread too off topic, but biased and first hand knowledge are two different things. I have dissambled more logitech speakers than you have probably owned. They are decent quality for simple daily tasks, just not for the price. I fail to see what BB Co. has to do with any of this. Really, I think you're trying to hide under various rocks and not look at reason, tests, and facts.

lol logitech speakers.  nothing to do with the fact that Slimserver devices was bought by logitech.  so they just brand them, not build them.  

fact is, you've never heard or used one.  next.

---

### Post by thisllub on 2009-05-01
> **yoasif said:**
> [mpd]("http://wiki.archlinux.org/index.php/Mpd") is probably the easiest way to do this. basically, set up a mpd machine, and connect to it from some other machine on your network. you can set up playlists, etc.

I use mpd, icecast and the browser on my WiFi phone with the Relaxx interface.

I can stream music to phones and computers all over the house.

It took all of half an hour to download and set everything up.
I wrote a script to create a playlist with all my music in it then I broke it up into smaller playlists.

---

### Post by PurposeOfReason on 2009-05-01
> **pwnst*r said:**
> lol logitech speakers.  nothing to do with the fact that Slimserver devices was bought by logitech.  so they just brand them, not build them.  

fact is, you've never heard or used one.  next.
Right, I've never used them, I just take them apart. :roll: Stop deflecting.

---

### Post by pwnst*r on 2009-05-01
you take apart squeezeboxes?  lol.  ok, champ.

---

### Post by PurposeOfReason on 2009-05-02
> **pwnst*r said:**
> you take apart squeezeboxes?  lol.  ok, champ.
I don't think I ever said that. Just logitech speakers, which the squeezebox will have. Same company, same results. That's all I'm saying, no more. You're in love with yours and that's okay. If you like them, that is all that matters.

---

### Post by ssam on 2009-05-02
i have a headless mini-itx system for music (and a few other things like backup).

i used to have rhythmbox on it, and use
```
ssh -CX miniitx rhythmbox
```
from my main machine, so that the rhythmbox window is drawn on my main computer, and the music come out of the big speaks on the little computer.

now i have switched to mpd. so mpd runs on the little computer with the speakers still. in i can run the an mpd client on my main computer, or a laptop, or a nokia internet tablet.

you could get an n770 pretty cheap and use that as the remote control.

if you really need physical buttons on the music server, then maybe you could get a USB gamepad, and setup the buttons to call commands.

i recommend gmpc as a mpd client. the ubuntu package does not have any plugins, but there is a PPA that has a new version and the plugins.

also look at the xmms2 software. it is similar to mpd.

another option would be to use pulseaudio to stream over the network.

---

### Post by niko7865 on 2009-05-02
If you don't mind using another computer to control the music htpc, you could install mpd + pitchfork, which is what I do.

[http://lukemcreynolds.com/content/pitchfork_mpd_client_mirror/](http://lukemcreynolds.com/content/pitchfork_mpd_client_mirror/)

---

### Post by DMcA on 2009-05-02
> **simtaalo said:**
> from the info posted above it seems it is doing exactly that.

How so? The post states that the device handles lossless formats, e.g. FLAC and as such gives a 2:1 compression ratio. this is normal for FLAC. If you stream FLAC you get the same bits out as on the original CD, which is good.

Even if it is doing on the fly compression to FLAC (which is not clear or, I think, correct) it doesn't matter. The process would be lossless.

---

### Post by DMcA on 2009-05-02
I believe the key, difficult to acquire, piece of hardware for actually building a system that the OP (or at least myself) would be interested in is a small, cheap, monochrome monitor capable of displaying a terminal.  

Does this exist? If so any suggestions about where to get one?

---

### Post by pwnst*r on 2009-05-02
> **PurposeOfReason said:**
> I don't think I ever said that. Just logitech speakers, which the squeezebox will have. Same company, same results. That's all I'm saying, no more. You're in love with yours and that's okay. If you like them, that is all that matters.

again, you don't know what the squeezebox even is.  there are no speakers.  you connect the squeezebox to your existing HT or audio system.

lol like i'd use logitech speakers.  i use M-Audio for my workstation and my home theater cost a ridiculous amount of money, but that's one of my hobbies.

---

### Post by PurposeOfReason on 2009-05-02
> **pwnst*r said:**
> again, you don't know what the squeezebox even is.  there are no speakers.  you connect the squeezebox to your existing HT or audio system.

lol like i'd use logitech speakers.  i use M-Audio for my workstation and my home theater cost a ridiculous amount of money, but that's one of my hobbies.
Well now I feel foolish. But even then, it is even worse because for 300, you're just getting a wireless antenna which compresses audio. Yes, you and your large sums of money spent on your system aren't even playing 320 kbps quailty.

My statement still stands. He'd be much better off building a computer.

---

### Post by pwnst*r on 2009-05-02
actually the 2:1 compression is talking about the lossless codecs.  the squeezebox compresses nothing.

what else you got.

---

### Post by gn2 on 2009-05-02
Perhaps the OP just needs a small screen like [the ones used in car PCs]("http://www.carcomputer.co.uk/component/option,com_virtuemart/page,shop.browse/category_id,46/Itemid,26/").

No way will it be under the budget though, I still reckon the best option is a netbook.

---

### Post by PurposeOfReason on 2009-05-02
> **pwnst*r said:**
> actually the 2:1 compression is talking about the lossless codecs.  the squeezebox compresses nothing.

what else you got.
Ha, don't try to pull that one. I read up on that and went to the hi-fi forums. There is no question that the aqueezebox compresses audio. I'm almost tempted to demo one to prove it seeing as I scorred 19/25 when comparing 320kbps to flac blind and 24/25 at 198. That using just a pair of Ad-700s. Not your "high end" setup.

It does play flac though. It gets the origional file, compresses it over the network, and unfolds it at the box. But any self respection audio lover knows that you will loose qualith that way.

---

### Post by pwnst*r on 2009-05-02
> **PurposeOfReason said:**
> Ha, don't try to pull that one. I read up on that and went to the hi-fi forums. There is no question that the aqueezebox compresses audio. I'm almost tempted to demo one to prove it seeing as I scorred 19/25 when comparing 320kbps to flac blind and 24/25 at 198. That using just a pair of Ad-700s. Not your "high end" setup.

It does play flac though. It gets the origional file, compresses it over the network, and unfolds it at the box. But any self respection audio lover knows that you will loose qualith that way.

no question eh?  proof would be nice.

"respecting"
"lose"
"quality"

lol, next.

---

### Post by PurposeOfReason on 2009-05-02
> **pwnst*r said:**
> no question eh?  proof would be nice.

"respecting"
"lose"
"quality"

lol, next.
Coming from the guy who has a broken shift key. When you feel the need to attack me instead of my argument, I know I have won.

---

### Post by pwnst*r on 2009-05-02
> **PurposeOfReason said:**
> Coming from the guy who has a broken shift key. When you feel the need to attack me instead of my argument, I know I have won.

well i can see one spelling error, but you were rampant in that post. 

your argument is flawed.  there is nothing in the specs that point to the device compressing files.  since it's doing the receiving why would it need to compress?  


again, proof please.

---

### Post by DMcA on 2009-05-03
> **PurposeOfReason said:**
> 
It does play flac though. It gets the origional file, compresses it over the network, and unfolds it at the box. But any self respection audio lover knows that you will loose qualith that way.


Unfortunately, there is so much misinformation out there about digital music. If you stream a losslessly compressed file over a network you should be able to reconstruct the original source perfectly. It is exactly the same as streaming any other compressed file format such as  gzip, compare the checksums if you like. 

If you cannot do this, there is something wrong with your setup. Double blind testing is irrelevant here since you are comparing a process that ought to be lossless.

---

### Post by DMcA on 2009-05-03
> **gn2 said:**
> Perhaps the OP just needs a small screen like [the ones used in car PCs]("http://www.carcomputer.co.uk/component/option,com_virtuemart/page,shop.browse/category_id,46/Itemid,26/").

No way will it be under the budget though, I still reckon the best option is a netbook.

was thinking of something like that and indeed you can get the a lot cheaper than those, for example at amazon:

[http://www.amazon.co.uk/monitor-In-Car-Technology/s/qid=1241343347/ref=sr_nr_n_8?ie=UTF8&rs=560798&keywords=monitor&bbn=560800&rnid=560800&rh=n%3A560798%2Cn%3A!560800%2Ck%3Amonitor%2Cn%3A3030781](http://www.amazon.co.uk/monitor-In-Car-Technology/s/qid=1241343347/ref=sr_nr_n_8?ie=UTF8&rs=560798&keywords=monitor&bbn=560800&rnid=560800&rh=n%3A560798%2Cn%3A!560800%2Ck%3Amonitor%2Cn%3A3030781)

Still not ideal though. I'm sure there's got to be a way to buy ultra-cheap terminal displays, I just don't know where. 

Any yeah a netbook certainly does have all the hardware at a decent price. I'd get one of the really cheap ones for the parts and then dissemble if I thought it were possible and I had the skills. Seems a shame though, when it ought to be cheaper to only buy only the bits you need.

---

### Post by pwnst*r on 2009-05-03
> **DMcA said:**
> Unfortunately, there is so much misinformation out there about digital music. If you stream a losslessly compressed file over a network you should be able to reconstruct the original source perfectly. It is exactly the same as streaming any other compressed file format such as  gzip, compare the checksums if you like. 

If you cannot do this, there is something wrong with your setup. Double blind testing is irrelevant here since you are comparing a process that ought to be lossless.

he's misinformed about the product, period.

---

### Post by bogoliubov on 2009-05-04
Ok, while I greatly appreciate all help on this subject, I feel that the discussion has changed a bit.

Anyhow, most likely I'll buy a squeezebox, but I'll look for something similar (=> alfanumeric screen, linux support, digital stereo out, flac and ogg support) that also plays video. 

Thanks for the help.

---

