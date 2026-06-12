---
title: "jack connections window connects wrongly with each restart of play"
date: 2014-11-27
forum: Ubuntu Studio
---

### Post by a-you on 2014-11-27
There must be a simple answer, but I don't know what it is. Searching the interwebs came up empty too.

I'm using jack and qjackctl, but in patchage it was the same.

It's possible to for example play a file in audacity and route the signal to pure data (Pd). But, using that example, each time playback stops the virtual port/connector for audacity dissapears, and when playback is started again it reappears---except that by default it connects to the "system" output! How in the world can I simply have it either preserve the audacity virtual ports or at least remember how I had them connected so that when audacity reappears again the connections are as I had set them??

It seems inconceivable that I have to manually reconnect everything each time I want to restart playback of a file. It's the same whether I'm using audacity or another playback app, I just used that as an example.

Also I get the idea that I can pause the playback instead of stopping it, but this just seems still kind of crazy.

I tried enabling "Activate Patchbay persistence" in qjackctl's "setup" dialog but that doesn't do it.

Thanks in advance! There must be some obvious answer, but what??

[edit] Thanks to this article:

[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

I've learned of a way to... I spoke too soon. That actually doesn't work! That is, when "stop" is clicked instead of pause the ports for (for example) audacity vanish and the patch is not restored.

Anybody know how to do this??

---

### Post by luctor on 2014-11-27
There's an option in jack to NOT autoconnect, maybe this will help you somehow.

I have learned that audacity is horrible with jack and have never got it to work properly. As I use audacity purely as an editor I don't really have the need.

---

### Post by a-you on 2014-11-28
Thanks luctor.

Hmm, I didn't realize there was an option to have it not autoconnect. I'll look into that today.

And yeah, I've never used audacity with jack before, but actually in principle they work together fine it seeems to me. But anyway all I was trying to do (and still am) was to use some simple audio player of wav files that could be routed to a Pd patch and then from that to the outputs. But the autoconnect was driviing me nuts.

I could use ardour, and that'd probably be the real way to do it, but in this simple scenario creating an ardour session seemed like more than necessary.

There are workarounds, to be sure, including using ardour. I do find it strange that simply preserving or rather reconnecting jack in a persistent way seems so awkward, so I thought maybe there was an obvious solution that I was just somehow overlooking.

Today I want to check out [aj-snapshot]("http://aj-snapshot.sourceforge.net/"), which some say is an excellent tool for restoring jack connections. It's in the repositories btw.

---

### Post by a-you on 2014-11-28
Just wanted to post a quick thank you to this person for this article which notes that alsaplayer can play a file and when the playing is stopped the virtual ports remain in the qjackctl connections dialog. Very nice. Perhaps it helps somebody

[http://audio-and-linux.blogspot.de/2011/07/mp3-player-with-jack-output.html](http://audio-and-linux.blogspot.de/2011/07/mp3-player-with-jack-output.html)

---

### Post by jejeman on 2014-11-28
Thats how Audacity works, VLC too.
If I remember correctly Audacious should keep connection through entire session.

---

