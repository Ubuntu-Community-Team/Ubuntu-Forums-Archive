---
title: "What Is The Best Media Server"
date: 2010-09-19
forum: Server Platforms
---

### Post by NoSalt on 2010-09-19
Hello All

    I have an Ubuntu desktop running Lucid 10.04, and a large NAS on my local network. What I am wanting to do is to rip all of my DVDs onto the NAS so I can stream them to my television in the other room. I am trying to find the best media server software but I am not having much luck. I have tried "Mediatomb", but it isn't very "friendly" (IMHO). Does anybody else have any suggestions for media server software that I can use?

Thanks for taking the time to read.  :)

---

### Post by CharlesA on 2010-09-19
Depends on what you want to stream it to. PS3MediaServer is pretty good if you've got the horsepower.

---

### Post by SquALeD on 2010-09-19
Yep, depends what you want to stream to as Charles said. I run a Lucid server that streams all my media to my TVs via samba. The TVs are connected with WDTV live boxes that see samba as another device on the network - no config needed apartf rom adding my 3 1TB media drives as 'guest' shares.

1080p files streams 100% perfect, no stuttering at all on 10/100/cat 5 etc. 

Used to run PS3MS and it was the bomb on the PS3 (!) but since going toWDTV Live have no need for it..

---

### Post by CharlesA on 2010-09-19
> **SquALeD said:**
> Yep, depends what you want to stream to as Charles said. I run a Lucid server that streams all my media to my TVs via samba. The TVs are connected with WDTV live boxes that see samba as another device on the network - no config needed, 1080 mkvs stream perfectly over my network.

I wonder if those WDTV boxes will play VOB files directly... Hmm..

The reason I have to use PS3MediaServer is because it can do transcoding on the fly, which takes a ton of horsepower.

---

### Post by SquALeD on 2010-09-19
Yep they do play vobs without trans Charles, kust seems a bit neater doing things with .mkv :)

Used to trans with PS3MS but I had a situation here where I had a WDTV in one room and a PS3 in another and niether would play the same formats if you know what I mean. Something had to go and it was the PS3.

WDTV just works..

---

### Post by CharlesA on 2010-09-19
> **SquALeD said:**
> Yep they do play vobs without trans Charles, kust seems a bit neater doing things with .mkv :)

Thanks. I've got a ton of dvds ripped to straight off the disk (VOB, IFO, etc) and have been having a hard time finding something to play them that has a decent interface. VLC will play them as will Windows Media Center, but I haven't yet figured out how to get a nice "10-foot display" for VLC.

---

### Post by SquALeD on 2010-09-19
Why no convert to .mkv and have a format thets being pretty much adopted by all..?

Maybe this is getting slightly OT. OP if you rip to .mkv most media streamers willplay this format APART from the PS3

---

### Post by CharlesA on 2010-09-19
> **SquALeD said:**
> Why no convert to .mkv and have a format thets being pretty much adopted by all..?

Maybe this is getting slightly OT. OP if you rip to .mkv most media streamers willplay this format APART from the PS3
Er yeah.. kinda detailed the thread a bit.

Anyway, I'm currently using a Windows 7 based HTPC, since it can play VOB files and has a decent interface. I was going to replace it with a PS3, but it's hard to find anything that'll work for what I want to do, since I wanted to keep an exact copy of the dvd, in case I somehow lose it (fire, flood, etc). If I transcode it, that wouldn't happen. :P

@OP: There are a few media servers out there, but it really depends on what you are serving to.

---

### Post by LightningCrash on 2010-09-19
OP I have tried uShare and was not very impressed. It was also not very secure.

I would just share out the relevant directories with Samba.

---

### Post by Cowboybebop79 on 2010-09-19
Personally I would combine turnkey linux file server (very easy to setup) which is based on Ubuntu but has been stripped down to exactly what you need for that purpose. At the other end XBMC or Boxee first choice being boxee as the interface is a bit easier to understand and you can get going pretty quickly. The only system that would need particularly more horse power 64 horses to be exact would be the one you use to rip from. I use Handbrake to rip to mkv which will give you a full film with subtitles and alternate audio for a gig or under depending on your quality settings. Enjoy

---

### Post by kgatan on 2010-09-20
Hope its ok if i highjack your thread a little :)

Im trying to do the same thing as you, currently just using ubuntu as NAS with XMBC installed on a win7 at the primary tv.

What format will you use when ripping your dvds to the NAS?
I wanna do it right from the start since it be a pain to ripp 300 dvds twice.
I dont mind if each rip is 2gb but theres a jungle of video and audio formats out there and i havnt found a good guide through them yet.

Is it possible to automate ripping so you just have to switch dvds without any configuring?

---

### Post by Cowboybebop79 on 2010-09-20
At the moment the choice will be between mp4, mkv, webm. I don't know of any ripper/encoders for webm but it is prity new technically it is a stripped down version of mp4 to make it easier to stream over the Internet. I originally started using a program called thoggen which ripped to ogv. But I have started using handbrake recently to rip to MKV as it is a light year ahead in compression and quality multiple audio tracks and subtitle tracks blah blah....... the good thing I found about handbrake is that it gives tool tip advice for each setting giving you the ability to make some educated adjustments instead of expecting you to know everything like some muxing fu. As far as automation is concerned I would imagine you could whip up a bash script to run the cli version of handbrake.

---

### Post by NoSalt on 2010-09-21
I've been ripping them all into .m4v (HandbBrake's default) and I was hoping to stream them from my Lucid box in my office to, say, an Apple TV in the living room. The new Apple TV is very small and unobtrusive and perfect for my needs. I believe it will recognize UPnP, so that is what I have been looking for in a media server software. Maybe I should try to decrypt Mediatombs instructions again. I was just hoping there would be a simpler option out there.

---

