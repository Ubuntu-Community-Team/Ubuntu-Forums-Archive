---
title: "Media Player Suggestions"
date: 2016-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Iflana on 2016-01-16
Does anyone have suggestions for media players for use with Ubuntu 14.04 x64?

I am relatively unhappy with Rhythm Box, as it's completely text based & doesn't appear to be reading MP3 tags properly.  I prefer something that is more graphical as well, so that my young children can assist in picking out music with me at the computer.  I have tried Music and it won't even load my music library.  On my Windows 7 installation I use the Zune player for music, and I really like it.  For DVDs and Bluray I've tried VLC, but I have yet to try a disc that it will recognize and play.  The video playback is of lesser concern, but would be nice to have.  It doesn't matter to me if the music and video are in the same or separate applications.  The music player is really essential for me though as we have it running for about 8 hours a day every day!

---

### Post by ajgreeny on 2016-01-16
> I am relatively unhappy with Rhythm Box, as it's completely text basedWhat does that mean exactly?  RB has a full GUI with a lot of plugins as well so I'm not sure quite what your problem is.  There are many players available so do a search and see if you can find anything else that fits the bill for you.

VLC would normally be my application of choice for video files and DVDs, though for a simple audio player I also like audacious.
For VLC to find a disk and play it you may need to point it to the disk drive first, though once done that should be remembered, so open VLC ->Media ->Open Disk and make sure it points to whatever your DVD drive device name is; mine is /dev/sr0.

You will also have to make sure you have followed all the info on DVD playing in the restricted formats info at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Iflana on 2016-01-16
I have searched, and am not sure what to try - hence the request for personal suggestions.  Reviews led me to VLC, which won't play anything.  I've tried open disk repeatedly from within the program by path, from the program by browsing, as well as using the prompts when a disc is inserted.  I still have yet to see anything play.  I'll check out the link on restricted formats, though I'm not sure why a disc legally purchased from a retail store would be restricted in any way for private home viewing.

As far as Rhythm Box goes, all I see is text & a few small buttons for play, stop, pause, shuffle & repeat.  There's really nothing graphical unless you count being able to click on text.  Text is useless to a two year old child that can't read.  A picture can be used to identify and explore music.  They can recognise an album cover for example.  Yes, I've got the cover art plugin enabled.  All that's given me is an itty bitty picture in the now playing of the status bar.  Trying to engage them with text isn't going to happen and they lose patience quickly, as do I, searching through over 5000 tracks.  To make it more difficult the tags aren't reading what I'd like them to be reading.  I don't know if that's because I'm unfamiliar with customizing the program, or because it doesn't do what I'd like it to do.  For example, I get composing song artist instead of album artist.  That results in me seeing a choice selection of several artists bogged together instead of one.  So I have to search through, memorize the composing artists for each song, and end up selecting a bunch of them instead of just being able to select Ozzy & have all his albums play.  Here's an example of what the Zune player looks like that I found online, so you can maybe see more of what I'm hoping to find.

[IMG]http://microsoft-news.com/wp-content/uploads/2014/01/Zune-Desktop-VLC-UI.jpg[/IMG]

[IMG]http://cnet4.cbsistatic.com/hub/i/r/2009/09/14/6f7da3f0-f8e2-11e2-8c7c-d4ae52e62bcc/resize/570xauto/19c86c0f6d1018fcb152397763471276/quickplay.png[/IMG]

Now contrast that with what I'm getting with Rhythm Box.

[IMG]http://ubuntuhandbook.org/wp-content/uploads/2015/02/rhythmbox-csd.jpg[/IMG]

I'm not expecting a mirror image, but I really want that album art, as well as to be able to actually find my music a lot easier!  You said there are a lot of plugins, but I counted less than 20.  Maybe I'm not configuring it right.  I'm definitely not seeing a lot of options.

> **ajgreeny said:**
> What does that mean exactly?  RB has a full GUI with a lot of plugins as well so I'm not sure quite what your problem is.  There are many players available so do a search and see if you can find anything else that fits the bill for you.

VLC would normally be my application of choice for video files and DVDs, though for a simple audio player I also like audacious.
For VLC to find a disk and play it you may need to point it to the disk drive first, though once done that should be remembered, so open VLC ->Media ->Open Disk and make sure it points to whatever your DVD drive device name is; mine is /dev/sr0.

You will also have to make sure you have followed all the info on DVD playing in the restricted formats info at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Bucky Ball on 2016-01-17
Thread moved to ***Ubuntu, Linux and OS Chat***.

Please attach large pics using 'Go Advanced' or 'Adv Reply' and using the paperclip icon. Bear a thought for those with slow connections or vision issues (or both), some of whom may be able to input. Thanks.

Try them all! What's stopping you? This is not Windows. Just install from Software Centre. Try it out. If you don't like, uninstall. 'Completely remove' is available in Synaptic (I don't use SCentre) or once you've removed you can open a terminal and 'sudo apt-get autoremove' to exterminate any of its diaspora. Simple. :)

VLC for me, Audacious is lightweight and efficient, Clementine is bulky but has lots of features. Do a search, make a list, try them all.

Best to stick with stuff from the official repos in my opinion (although up to you, of course). That way you know it will be regularly updated and has been tested with your current release. Good luck.

---

