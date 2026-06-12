---
title: "Rockbox should I do it"
date: 2007-07-01
forum: The Cafe
---

### Post by LostArt on 2007-07-01
Hey everyone, I recentely restored my ipod, and now I was wondering if I should convert the firmware to Rockbox, Has anyone done it here, I know I can always change it back, but I' a bit timid about the whole thing. I'd love to change how my ipod looks, does rockbox look pretty, what kind of video files does it support, is it recomended, IfI skrew up does it void out my warrenty, can I downlaod themes for it, Is it difficult to install, I just want to make sure before doing simething kind of huge like this. Oh yeah, can I look at my files in a windows explorer kind of way.

Thanks for the help,

Chip,chip :popcorn:
Justin

---

### Post by stmiller on 2007-07-01
Yes try it. It doesn't format or alter your ipod in anyway. You simply unpack a directory onto the ipod, and it then boots into Rockbox. All of your iTunes library music is there.

If you want to revert back to the standard ipod, you simply hook the ipod up in disk mode and delete that rockbox directory from the ipod.

---

### Post by Celegorm on 2007-07-01
I've got rockbox on my ipod, and I highly recommend it. It won't replace the original firmware, but rather set it up as a dual boot. I don't remember all of the details, but it was fairly easy to go through the directions and get it working. I like how I can now just copy files onto my ipod rather than having some program convert them into some weird scheme that makes it unreadable if you treat it like a removable hard drive and browse through the files. It should also be able to play all the files you have on your ipod already.

---

### Post by SoulinEther on 2007-07-01
At the moment rockbox does not support video playback as you know it; the iPod Video uses a hardware chip to decompress movies, and Rockbox currently has no support for it whatsoever. It has to use the main processor to decompress and display video (mpg format, not sure 2 or 4). And in fact, i think it uses the main cpu for everything (audio too).

Its not bad. It adds support for several formats, most of them open like ogg and flac. The themes are kinda nifty, and it can work with the Apple iTunes database just fine (gotta tweak one piece of settings though).

Two display modes: File browser, and Database. Database is more like your old iPod style where you go by album artist etc, the file browser is ... a file browser.

And there is no anti-aliasing support yet for fonts because rockbox is still running like 2-bit fonts with no alpha layer support... so... everything but your fonts will look cool, except... if you go for a nice font that has no rounded edges, then you'll not notice any problems whatsoever.

I even got a friend to convert his iPod to Rockbox. He likes it. A lot.

---

### Post by qamelian on 2007-07-01
Be sure to check out the bug reports on the Rockbox site before you decide. Unfortunately, I failed to do so and fell victim to a bug that prevents the iPod from recharging while running the Rockbox firmware. By the time I discovered the problem, my iPod could not hold enough of a charge to reboot into the original iPod firmware to allow me to recharge. This turned my iPod into a paperweight until I could purchase the AC charger which allowed me to run the iPod using AC power until I could reboot into Apple's firmware. Another side effect is that this issue screwed up the sensor that the iPod uses to determine how much charge is left. It took me several attempts at charging and running it down to recalibrate the sensor. 

Despite these issues, the second of which is a known Apple problem and not Rockbox's fault, Rockbox adds some additional functionality that I was missing from the original firmware. The recharge issue, if I remember correctly, affects only the 5G iPods, but you should check the bug reports anyway to be sure.

---

### Post by LostArt on 2007-07-01
Thanks, I will check the bugs, I'm pretty sure my ipod is fifth generation so I'm gonna have the charging bug to I guess, How can I fix that. My ipod is not the newest video, It's the one just before the brand new one. Also, I didn't fully understand you SoulinEther, will it still play movies? dies that mean it has lesser quality? or use more battery??? Lastly can I do Drag and Drop, and does it support MP4, or AVI video files, thanks for all of your help by the way

---

### Post by reacocard on 2007-07-01
I did it for my brother's iPod (30GB Video (5.5 gen?)), it works beautifully. Also, rockbox doesn't destroy the default iPod firmware, it just dual-boots with it, like Ubuntu and Windows do. Turn on the iPod with the hold switch off, you get rockbox. With hold switch on, you get the iPod firmware. You can remove rockbox at any time too, you just remove the .rockbox directory and run the install tool with a different option. There are only two thing the Apple firmware has over rockbox at this point: it plays DRMed stuff bought from itunes, and it plays video well. Rockbox has basic support for MPEG 1/2 video, but it's not very good yet as it lacks support for the iPod's hardware decoder. Rockbox is definitely worth a try though, since you can always just boot into the Apple frimware for videos, and use rockbox for everything else.

---

### Post by SoulinEther on 2007-07-01
No, the video decompression plugin is not at 100%; it looks pretty bad and I think it doesn't support sound..

So if you want to watch movies, just boot into the regular Apple firmware.

---

### Post by a12ctic on 2007-07-01
I love Rockbox on my E260 Sansa player but it was nothing but trouble on my friends nano. You could try it and see how it works out, you can always replace it. On my player, it adds support to mpeg which is much better than the format supported by the default (its some odd formatt in a .mov container),  ogg/flac support, added formats for the recorder, better sound quality, more sound features (i love the gapeless + crossfeed/dithering/a more advanced eq), far better play lsit support. I just love it. Also, it takes advantage of both the cores in my mp3 player.

---

### Post by yatt on 2007-07-02
Rockbox has weird problems with being connected with your computer. When you unmount it, it will just remount itself, and if you shut your computer off with it unplugged it will remain running and completely drain your battery.

---

### Post by hanzomon4 on 2007-07-02
My only major complaint is the database, I have duplicate entries and sometimes the track order is all messed up. Try it out and grab a kickass theme

---

### Post by Incense on 2007-07-03
I tried it for a while on my 5G. The games and themes are pretty awesome. I had a hard time getting use to the device not powering down when I paused it for a while, and my batteries took a big hit, even when I did power it off. I was also very used to the iPod way of doing podcasts, and didn't like how I couldn't tell what I hadn't listened to. It's just really getting used to change though. Like the others said, give it a shot, and if you don't like it, you can just delete it.

---

### Post by LostArt on 2007-07-06
So I did install Rockbox, and I like it so far, I just have one Problem, how do I make it go to sleep like an ipod, I don't like how it constantly shuts itself down, Is there some way it'll just go to sleep?? Also where can I find some awesome themes

---

### Post by Strider42 on 2007-07-14
> **hanzomon4 said:**
> My only major complaint is the database, I have duplicate entries and sometimes the track order is all messed up. Try it out and grab a kickass theme


Make sure you have Auto Update set to 'yes' and then Initialize the DB again, that should resolve the problem.  Well it did for me.  I'm running an 80Gb 5th gen pod.

Blows Apple iTunes out of the water.  Drag and drop, what a joy.  And the themes are great.

---

### Post by Strider42 on 2007-07-14
> **LostArt said:**
> So I did install Rockbox, and I like it so far, I just have one Problem, how do I make it go to sleep like an ipod, I don't like how it constantly shuts itself down, Is there some way it'll just go to sleep?? Also where can I find some awesome themes

[Themes - click here]("http://www.rockbox.org/twiki/bin/view/Main/WpsGallery")

[Wiki - click here for other questions you have]("http://www.rockbox.org/twiki/bin/view/Main/WebHome")

[Support Forums - click here]("http://forums.rockbox.org/")

Playlist creation is a little cumbersome in machine, but I use Exaile to create my playlists and then export them to a .m3u file.  Works a treat.

Have fun it's great firmware.

---

