---
title: "Music Player with multiple Libraries/Profiles"
date: 2010-03-18
forum: The Cafe
---

### Post by Crowchild on 2010-03-18
I've got most of 30,000+ mp3s stored on a external hard drive and when I open up rhythm box it takes quite a while to add or remove these depending on whether or not the drive is mounted.

Is there a way to set up multiple libraries for my various drives? If this can't be done is there a player that does do this?

Thanks.

---

### Post by Crowchild on 2010-03-18
This worked for me: [http://brainstorm.ubuntu.com/idea/8311/](http://brainstorm.ubuntu.com/idea/8311/)

There is support for this both in HAL and Rhythmbox. Create a file in the root of the external harddisk or usb drive with the name ".is_audio_player". Put the following content in the file: 

audio_folders=MUSIC/,RECORDINGS/ 
folder_depth=3 
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg 

Your machine now knows how to handle your music on the external harddisk or usb drive.

---

### Post by nothingspecial on 2010-03-18
Have a look at guayadeque music player.

It is insanely fast for large music collections.

Although I don`t understand exactly what you want it to do, I think it might.

It certainly supports multiple libraries.

It is under active development and feature requests are implemented, aslong as they don`t intefere with the prime objective - a full featured music player for very large collections with an emphasis on speed.

Install instructions and discussion [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1398128").

Bug reports and support [[COLOR="Lime"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

Feature requests [[COLOR="DeepSkyBlue"]here[/COLOR]]("http://sourceforge.net/apps/ideatorrent/guayadeque/")

---

### Post by koleoptero on 2010-03-18
Decibel Audio Player keeps seperate libraries and doesn't refresh without you asking it to, so it loads in a snap. I've had the same problem a while ago and it worked perfectly for me. It's also much faster than any other player you might find (besides mpd or cmus). Give it a try but use the latest version that's available at [their homepage.]("http://decibel.silent-blade.org/")

---

### Post by Crowchild on 2010-03-18
Thanks for the tips guys. The work around I mentioned earlier just doesn't cut it as rhythmbox treats the drive like a mp3 player and refreshes the library every time it's plugged in.

In case I didn't explain what I was looking for in my first post.

My problem is that I have a massive music collection on an external harddrive. I don't want to have my music program have to refresh the library everytime I mount my drive. I'd like to have one library for my local music (that refresh often) and one library for me external hdd (that refreshs only when I want it to).

I'll give guayadeque & Decibel a try.

---

### Post by nothingspecial on 2010-03-18
If guayadeque doesn`t do what you want it to......just ask ;)

---

### Post by Crowchild on 2010-03-18
I can't seem to see a way to set up multiple libraries on Guayadeque.  I see that this is a suggestion on [http://sourceforge.net/apps/ideatorrent/guayadeque/ideatorrent/idea/11/](http://sourceforge.net/apps/ideatorrent/guayadeque/ideatorrent/idea/11/)

I am going to create an account so I can vote for this idea. In the mean time Decibel seem to do this just fine.

---

### Post by nothingspecial on 2010-03-18
I understand what you mean now.

We`ll see.

---

