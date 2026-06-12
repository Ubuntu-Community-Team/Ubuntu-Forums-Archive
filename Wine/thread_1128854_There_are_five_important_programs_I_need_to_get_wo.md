---
title: "There are five important programs I need to get working on Ubuntu.."
date: 2009-04-18
forum: Wine
---

### Post by Prog4E on 2009-04-18
I'm currently in transition phase between Windows Vista and Linux Ubuntu.
Anyway, if there's anyone who could send me a solution for these five software, I'd really appreciate it because they are the only obstacle between me and a fully Ubuntu'd computer:

- Adobe Audition
- Adobe Photoshop
- Adobe Premiere Pro
- Guitar Pro 5.2
- iTunes

They did not work in Wine with me, but I'm sure there must be some  way to get them to work. Already found a solution for iTunes and I'll be working on it next week.

Thanks
Fabio K.

---

### Post by Yashiro on 2009-04-18
- Adobe Audition
- Adobe Photoshop
- Adobe Premiere Pro
No. Very old versions sort of work via Wine. But at the end of the day if you are remotely competent with these tools you'll have to use them on Windows.

- Guitar Pro 5.2
Never heard of it.

- iTunes
Maybe via Wine but it's flaky.

---

### Post by Prog4E on 2009-04-18
> **Yashiro said:**
> - Adobe Audition
- Adobe Photoshop
- Adobe Premiere Pro
No. Very old versions sort of work via Wine. But at the end of the day if you are remotely competent with these tools you'll have to use them on Windows.

- Guitar Pro 5.2
Never heard of it.

- iTunes
Maybe via Wine but it's flaky.


If I may rectify what I have said at first: 
I am not very experienced with Premiere and Photoshop, and if I could find a near-perfect equivalent to these two then I'm fine.

I use Guitar Pro to write music by typing the notes, thus creating MIDI files out of it.

And I have tried iTunes with Wine... Didn't work at all, but I believe I found something on this forum that shows me how to get it fully working with some Debian package I have to download first, so I'm fine with that.. I'll try it next week.

As for Adobe Audition: there is no way I can live without it because I record music all the time and I've been using it for 4 years, so it'll be hard to say goodbye just like that  :P

---

### Post by zoldiel on 2009-04-18
Photoshop CS2 works pretty well with wine with minimal issues, last I checked anything newer will not work. 

I have not tried the others, however if it does not work with wine you may want to give Crossover Office a try, its a commercial product based on wine, it isn't free but you can download a 30 day demo at codeweavers.com.

---

### Post by Mike_IronFist on 2009-04-18
> **Prog4E said:**
> I'm currently in transition phase between Windows Vista and Linux Ubuntu.
Anyway, if there's anyone who could send me a solution for these five software, I'd really appreciate it because they are the only obstacle between me and a fully Ubuntu'd computer:

- Adobe Audition
- Adobe Photoshop
- Adobe Premiere Pro
- Guitar Pro 5.2
- iTunes

They did not work in Wine with me, but I'm sure there must be some  way to get them to work. Already found a solution for iTunes and I'll be working on it next week.

Thanks
Fabio K.

Interesting that you bring these things up. As part of the mission of Ubuntu is to free us from the "shackles" of commercial software, there are free alternatives that may or may not meet or even exceed the expectations you have set by these programs. Your first three (adobe) programs are hard to replace, but I have some viable options for you to try. Try to forgive some gaps in my knowledge here though - my Ubuntu machine is currently under maitenance so I'm typing from Windows.

Most of what you want can likely be provided by the programs offered by Ubuntu Studio. Ubuntu Studio by itself is a version of Ubuntu packed with all sorts of media-creation and editing programs for music, graphics and video. I wouldn't recommend installing Ubuntu Studio itself, but installing its four important program packages, ubuntustudio-audio, ubuntustudio-audioplugins, ubuntustudio-video and ubuntustudio-graphics will provide you with lots of stuff for media production.

If you don't feel Ubuntu can provide worthy substitutes, you might want to keep Windows around for dual booting.
[B]
- Adobe Audition Alternative: ubuntustudioaudio package[/B]
 The music side of Ubuntu Studio is the biggest. It takes serious getting used to with learning how to use Ubuntu for music creation after so much time on Windows, but if you're dedicated, you'll find that the programs in this package contain some pretty amazing stuff:
Ardour: Literally about as close you can get to Pro Tools without copyright infringement. It's the best if you work with professional music programs and know how those kinds of programs work.
Audacity: The best audio-editing program you could get. If you need to master a song or edit a sound, Audacity is flawless for it.

There's a lot more, and I recommend you download the whole package, in addition to the free plugins. To get this package, open Synaptic Package Manager and click the search button, then in the window that pops up type "ubuntustudio" (without the quotes) and you should easily be able to find the packages ubuntustudio-audio and ubuntustudio-audioplugins . Download both for a full Ubuntu music production experience.
**Additional Recommendations:** Jokosher, Rosegarden, and Linux Multimedia Studio are all good choices for less in-depth musical sequencing. You can get them from Add/Remove under the Applications menu.

**-Adobe Photoshop Alternative: GIMP, and maybe the ubuntustudio-graphics package.**
GIMP is pretty much a no-brainer. It already comes on Ubuntu and it does just about everything that Photoshop does, but it's free. But if GIMP does not do enough, you can get a ridiculous amount of graphical editing programs by downloading the ubuntustudio-graphics package. It has 3-D editing program Blender and tons of other stuff for whatever you could possibly want to do with a picture. This one is definitely a high recommendation, as the Ubuntu Studio graphics package is way bigger than just Photoshop in terms of both capabilities and content. Get it by using the search button in Synaptic to search for "ubuntustudio" (without quotes) and picking the graphics package.

**-Adobe Premier Alternative: ubuntustudio-video package**
I think you will not have a hard time finding an awesome video program made for Ubuntu using Add/Remove or Synaptic, but you might want to try downloading and installing ubuntustudio-video from Synaptic, which has a great video editor and a stop-motion capture program. It's by far the lightest of the packages, but there are lots of video editors for Ubuntu - even SUBTITLE editors! Search for video editors on add/remove and give all sorts of ones a try to decide which ones are right for you. Get this video package by using the search button in Synaptic to search for "ubuntustudio" (without quotes) and picking the video package.

**Guitar Pro Alternative: Tux Guitar or Dguitar**
Tux Guitar: Now this one sounds really good. It has a lot of features and appears to have all the good features of Guitar Pro. I have not tried it yet so I do not know, but from the looks of it, it's an absolute recommend. Get it with Add/Remove.

Dguitar: Its goal is to be identical to Guitar Pro and compatible with its files. It's probably exactly what you want but I don't know if you can install it via Add/Remove, Synaptic, or if your only option is to download a binary that you have to compile. Because I don't know where you can get it, I'm recommending Tux Guitar over it. However I think you should try both. If you can't find it in Add/Remove or Synaptic, try the official website:
[COLOR="Blue"][Dguitar on Source Forge]("http://dguitar.sourceforge.net/en/index.html)[/COLOR]

**iTunes alternative: Rhythmbox Music Player**
This one is another one pre-installed on Ubuntu, but usually when you open an MP3, it opens with the other media player by default. You can change this easily by right-clicking an Mp3, clicking properties, and changing what program the file opens with under the "open with" tab. Like iTunes, you can import music folders, use it with your iPod, downoad podcasts, make playlists, and more. It's excellent and a near-perfect iTunes substitute.


I know it's not all the same as your original programs, but please give all these a try. You may find some you love, and others that don't do what you need. Either way it's good to try the best that free software has to offer. I guarantee you will find lots of programs to love.

---

### Post by blazemore on 2009-04-18
Songbird is a good alternative to iTunes.
It has a good music library and can sync with your ipod.

I also recommend Banshee for good ipod support.

---

### Post by Prog4E on 2009-04-18
> **Mike_IronFist said:**
> Interesting that you bring these things up. As part of the mission of Ubuntu is to free us from the "shackles" of commercial software, there are free alternatives that may or may not meet or even exceed the expectations you have set by these programs. Your first three (adobe) programs are hard to replace, but I have some viable options for you to try. Try to forgive some gaps in my knowledge here though - my Ubuntu machine is currently under maitenance so I'm typing from Windows.

Most of what you want can likely be provided by the programs offered by Ubuntu Studio. Ubuntu Studio by itself is a version of Ubuntu packed with all sorts of media-creation and editing programs for music, graphics and video. I wouldn't recommend installing Ubuntu Studio itself, but installing its four important program packages, ubuntustudio-audio, ubuntustudio-audioplugins, ubuntustudio-video and ubuntustudio-graphics will provide you with lots of stuff for media production.

If you don't feel Ubuntu can provide worthy substitutes, you might want to keep Windows around for dual booting.
[B]
- Adobe Audition Alternative: ubuntustudioaudio package[/B]
 The music side of Ubuntu Studio is the biggest. It takes serious getting used to with learning how to use Ubuntu for music creation after so much time on Windows, but if you're dedicated, you'll find that the programs in this package contain some pretty amazing stuff:
Ardour: Literally about as close you can get to Pro Tools without copyright infringement. It's the best if you work with professional music programs and know how those kinds of programs work.
Audacity: The best audio-editing program you could get. If you need to master a song or edit a sound, Audacity is flawless for it.

There's a lot more, and I recommend you download the whole package, in addition to the free plugins. To get this package, open Synaptic Package Manager and click the search button, then in the window that pops up type "ubuntustudio" (without the quotes) and you should easily be able to find the packages ubuntustudio-audio and ubuntustudio-audioplugins . Download both for a full Ubuntu music production experience.
**Additional Recommendations:** Jokosher, Rosegarden, and Linux Multimedia Studio are all good choices for less in-depth musical sequencing. You can get them from Add/Remove under the Applications menu.

**-Adobe Photoshop Alternative: GIMP, and maybe the ubuntustudio-graphics package.**
GIMP is pretty much a no-brainer. It already comes on Ubuntu and it does just about everything that Photoshop does, but it's free. But if GIMP does not do enough, you can get a ridiculous amount of graphical editing programs by downloading the ubuntustudio-graphics package. It has 3-D editing program Blender and tons of other stuff for whatever you could possibly want to do with a picture. This one is definitely a high recommendation, as the Ubuntu Studio graphics package is way bigger than just Photoshop in terms of both capabilities and content. Get it by using the search button in Synaptic to search for "ubuntustudio" (without quotes) and picking the graphics package.

**-Adobe Premier Alternative: ubuntustudio-video package**
I think you will not have a hard time finding an awesome video program made for Ubuntu using Add/Remove or Synaptic, but you might want to try downloading and installing ubuntustudio-video from Synaptic, which has a great video editor and a stop-motion capture program. It's by far the lightest of the packages, but there are lots of video editors for Ubuntu - even SUBTITLE editors! Search for video editors on add/remove and give all sorts of ones a try to decide which ones are right for you. Get this video package by using the search button in Synaptic to search for "ubuntustudio" (without quotes) and picking the video package.

**Guitar Pro Alternative: Tux Guitar or Dguitar**
Tux Guitar: Now this one sounds really good. It has a lot of features and appears to have all the good features of Guitar Pro. I have not tried it yet so I do not know, but from the looks of it, it's an absolute recommend. Get it with Add/Remove.

Dguitar: Its goal is to be identical to Guitar Pro and compatible with its files. It's probably exactly what you want but I don't know if you can install it via Add/Remove, Synaptic, or if your only option is to download a binary that you have to compile. Because I don't know where you can get it, I'm recommending Tux Guitar over it. However I think you should try both. If you can't find it in Add/Remove or Synaptic, try the official website:
[COLOR="Blue"][Dguitar on Source Forge]("http://dguitar.sourceforge.net/en/index.html)[/COLOR]

**iTunes alternative: Rhythmbox Music Player**
This one is another one pre-installed on Ubuntu, but usually when you open an MP3, it opens with the other media player by default. You can change this easily by right-clicking an Mp3, clicking properties, and changing what program the file opens with under the "open with" tab. Like iTunes, you can import music folders, use it with your iPod, downoad podcasts, make playlists, and more. It's excellent and a near-perfect iTunes substitute.


I know it's not all the same as your original programs, but please give all these a try. You may find some you love, and others that don't do what you need. Either way it's good to try the best that free software has to offer. I guarantee you will find lots of programs to love.


Thanks man! Great info you gave me here. 
- So basically if you say DGuitar is compatible with GP files and works just like it, that's one down :D

- I'll try the Ubuntu Studio you're talking about as well.. From what you say, it seems quite interesting/attractive. I guess it'll take me some time to get used to it, but of course it would: I've been using Windows since I was 3, and there is still a lot about it that I do not understand. But Ubuntu? I feel that we bonded from the first couple of uses. So I believe it'd be fine with me.

- For Photoshop and Premiere, I guess they're not really an issue for me because I haven't been using them for too long.

These are four solved in just one thread :D Never worked that way before with me!

And there remains iTunes. I checked Wikipedia for all Linux-iPod software and found that none of them works with iPod Touch/iPhone for syncing applications so I'll just stick to iTunes.. it shouldn't be too hard getting it to work on Ubuntu.

Again, I really appreciate all you gave me. So most probably, starting next week, I'll have my Ubuntu HDD permanently (Yeah, Dual-boot once made a big mess with my Acer Aspire so I used an old 80 GB HDD that I had in one of those drawers instead of removing Vista, so I have to replace HDD's every time I need to change OS...thats's why I'm sticking to Ubuntu for good this time!.

---

### Post by frodon on 2009-04-18
Moved to Wine forum

---

### Post by glotz on 2009-04-18
Yeah, the question you need to ask is "I want to do this and this, what program should I use?".

Welcome to freedom.

---

