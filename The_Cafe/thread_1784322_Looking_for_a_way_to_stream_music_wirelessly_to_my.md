---
title: "Looking for a way to stream music wirelessly to my speakers"
date: 2011-06-16
forum: The Cafe
---

### Post by rodamu on 2011-06-16
Hi!

The title describes prety much everything. I have 2 aiwa's speakers pluged to a amplifier, which then plugs into my notebook via mini plug.

The problem is that in my notebook, the mini plug input is located in the front, so it's a pain in the neck to conect the cable, not to mention that my portability is greatly reduced.

Recently I found in banshee's options, that it can connect to a DAAP server. What I was thinking was: Is there a way to connect the speakers to a "device" which setups a DAAP server and then I could play music through wifi into my speakers?

PD: If this is wrongly posted, please delete it.

---

### Post by LowSky on 2011-06-16
No idea about DAAP, I never played with it.

there are several other options I can think about.. I know they make bluetooth adapters and other type of wirelss connectors for transmitting music wirelessly to a stereo.

---

### Post by rodamu on 2011-06-16
Yes I heard about bluetooth wireless streaming, but they say the quality is not that good. Also I recently tested my notebook with my friend's car stereo with bluetooth and the quality was terrible! I think that there is a alsa issue, so i better play safe with wifi streaming.

 I heard about Linksys Music Bridge. What about that? Anyone knows if it works with DAAP or at least with Banshee or Linux?

---

### Post by AeroZak on 2011-06-16
There are definitely many ways to do what you're asking, but what type of "device" were you hoping to use?  Did you want to connect a computer to your speakers and run music off of there, or were you hoping to go buy a device like a roku and stream music to that?

---

### Post by AeroZak on 2011-06-16
By computer, I meant something like an older computer that you don't use any more, or a specific computer that could be purchased specifically for a home media center.

---

### Post by rodamu on 2011-06-16
I didn't explain well. What I want is a device which plugs via RCA to the amplifier, and then recives the wifi stream from my notebook. As I said before I think that the Wireless-G Music Bridge does this, but I don't know if it uses DAAP or if it uses some strange protocol. The reason why I want to use DAAP is because i'm sure it will work with Banshee media player.

Also there is a device from logitech that i think does this, I need to investigate further. It's called Squeezebox and works for sure with Linux.

---

### Post by collisionystm on 2011-06-16
An fm transmitter and an old radio with a headphone jack lol.

---

### Post by 73ckn797 on 2011-06-16
There are surround sound speaker kits that have wireless connectivity to rear speakers but the connection would have to be at the laptop/computer then broadcast to the speaker receiver. It is more than you would want based on your comment about portability.

---

### Post by rodamu on 2011-06-16
The FM transmitter is not an option due to the location of the mini plug device.

The whole idea of this "project" is to recycle my speakers,which by the way sound very well. If I'd want a full hifi system I'd probably get Creative Inspire S2 wirelles BT system.

I'm going to look into Lynksys Music Bridge and Logitech Squeezebox, thanks for the replys!

---

### Post by rodamu on 2011-06-16
Hi, I'm back!

After investigating DAAP, I found out that that is not what I want to do.

What I want to do is to create with Banshee a DAAP server. Then I would connect this server to a client "device" which then would bridge all the way down to the speakers. Do you think that this can be achived? Specially creating a DAAP server with banshee

---

### Post by AeroZak on 2011-06-17
What you're asking for is definitely possible.  I've done it many different times with many different devices and services.

What I generally use for my DAAP device is my PS3, however since you probably don't want to go out and buy a $300 system, it's best to look into other options.

But what I don't quite see is why you need to use a DAAP server, there are many different types of music servers out there.

Another device I have is called a Roku Soundbridge, which I believe is similar to the Linksys Music Bridge you mentioned earlier, and while it doesn't seem to be compatible with DAAP, I use a server running from my computer called FireFly with it, along with a few other different servers.

Another thing I've done is just used an older computer, and connected it to my amp via RCA.  The computer would run as the server, and my laptop (or any other computer on my LAN) could control what song it played.

Or, you could do the same thing except run the server from your computer, and just stream the music through something like VLC media player.

Like I said in my first post, you have plenty of different options, all compatible with your server idea and the RCA connections, all that's left to do is pick one.  Older computers can be found on Craigslist for cheap (but then you need either a cord to convert it to RCA, or install an RCA card), Rokus and similar devices can be found for a fairly good price, and PS3s are expensive but fun.

---

### Post by dmizer on 2011-06-17
> **rodamu said:**
> Also I recently tested my notebook with my friend's car stereo with bluetooth and the quality was terrible!

There are two different sound profiles for bluetooth. One is mono (HSP) for voice headsets where high quality is not necessary. This is usually the default setting. What you need to do is change your profile to A2DP.

I use bluetooth to stream music over multiple devices with very little perceptible loss in quality.

---

### Post by rodamu on 2011-06-17
@AeroZak I want to use DAAP, because I want to use Banshee to play my music, not other player. But if you say that with Roku Soundbridge you can have the server running in the background, and then when you play a song throungh Banshee this server would transfer it to Roku, then it's perfect.

@dmizer Yes, I know that is also one of my possibilites, the thing is that online, at least all the bluetooth music receivers I saw there is not a clear view about their sound quality. Some people say it's awful, some others say its very good... Anyway, a bluetooth receiver is yet a posibility, but If i can have a "looseless" wireless system then i would go for it instead of BT.

---

### Post by AeroZak on 2011-06-18
> **rodamu said:**
> @AeroZak I want to use DAAP, because I want to use Banshee to play my music, not other player. But if you say that with Roku Soundbridge you can have the server running in the background, and then when you play a song throungh Banshee this server would transfer it to Roku, then it's perfect.

Sorry, I should be more specific.  FireFly runs on my laptop which servers out the music, but Banshee isn't used to pick the song being played.

However, the Roku Soundbridge can also stream internet radio, so what you can do is buy a Roku Soundbridge, then set up a streaming server on your computer and configure it so when you pick a song on Banshee, it'll stream it online.  After this, you could just connect your Roku to your stream!

This way, the server runs in the background, you can use Banshee to pick your music, and it'll play through your TV via RCA with the Roku.

While I have never done anything this elaborate as far as streaming goes, you should just be able to configure vlc to pick up whatever song you are playing on a specific sound card, then have it stream.

If that is not possible on linux (I'm pretty sure you can do it on windows), then a really quick and dirty way to do it without any research would be to open two vlcs.  One vlc would record what you are playing from one soundcard, and save it as a file.  Simultaneously, the second vlc would stream the file being saved.

However, this quick and dirty way would take much space and system resources, probably to the point where you would not like this idea.

If I was in your position, the best thing to do would either be to research how streaming works on VLC and how to configure it with your soundcard, or just get use to another GUI for streaming your music.  Banshee is not the only music player out there.  When I use FireFly, the method of picking a song is actually a remote that the Roku Soundbridge has.  FireFly tells the soundbridge which songs can be played, and you pick it via the remote.

---

### Post by rodamu on 2011-06-18
mmm sounds intresting, I will consider it. Otherwise I think I will buy a bluetooth music receiver. It cheaper than roku, and i think its better to save the money, so that in the future i could buy those big pioneer stereo systems which have bluetooth, radio streaming, etc.

Anyway, thank you so much for yur help guys! I will mark this thread as sloved.

---

