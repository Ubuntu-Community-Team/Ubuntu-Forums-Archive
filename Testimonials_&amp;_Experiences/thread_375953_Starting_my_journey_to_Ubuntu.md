---
title: "Starting my journey to Ubuntu"
date: 2007-03-04
forum: Testimonials &amp; Experiences
---

### Post by Geert Jan on 2007-03-04
So, I've been messing around with Ubuntu for a while now and I really like where it's going. I'm hoping in the coming months I will be able to slowly start doing more and more in Ubuntu, and finally leaving my Windows XP partition only for World of Warcraft. Of course Windows Vista will never touch any of my hard drives.

Anyway, so I really like Ubuntu so far, I just wanted to mention some things that bother me.

First, the "Keyboard Shortcuts" application, which I find very confusing. Some of the shortcuts are listed as weird hexadecimal codes or something? I tried changing the next- and previous track shortcuts for Rhythmbox, but I couldn't get it to work. Also, I think the window could use a "reset to defaults" button.

Second is the missing support for VobSub subtitles in Totem/gstreamer. I'm talking about the widely used format where an *.idx and *.sub file contain the subtitles. When I try to open an avi with VobSub subtitles Totem just freezes. There is a bug report about it [here]("https://launchpad.net/ubuntu/+source/gstreamer0.10/+bug/49208"), but I think it mistakenly got marked as fixed. You see, halfway down the page somebody started talking about a *different* bug. That bug got fixed and the original bug got marked as fixed it seems, even though it's still not working.

I can get movies with VobSubs to play using VLC, but the subtitles look kind of weird in that program, very jaggy. Also, the reason I like Gnome and Totem is that everything is clean and simple. VLC is definitely not a typical Gnome app.

Ok, so that was my rant. Hope I don't sound too negative, like I said, I really like Ubuntu except for these things. If any of you have tips for me, like where to report things like these, I'd like to hear them. I understand posting in this subforum probably won't help things get changed.

---

### Post by Guus on 2007-03-04
Welcome to Ubuntu :D

try Mplayer if youre not satisfied with VLC; its in the repositories

Also have you tried running WoW with Wine? ive heard some players got it working

(btw are you dutch :D?)

---

### Post by Pikestaff on 2007-03-04
Welcome :)

Once you get more comfortable with Ubuntu you may want to try running WoW with Wine as the above poster mentioned, I know a lot of people have gotten it working because it's a popular game.  Here is a guide you might want to check out:

[http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

### Post by Geert Jan on 2007-03-05
Thanks for the welcome :)

About running WoW on wine, I don't think I'm going to bother trying. I've tried running WoW on Windows using OpenGL instead of the default Direct3D, and it gave me a noticeably lower framerate in game. So I'd rather just stick with Direct3D and thus Windows for WoW. I don't mind taking a minute to startup Windows considering I normally play in sessions of a couple of hours anyway.

I have tried MPlayer. First it wouldn't play anything because of a video output error. So i checked the preferences, which just like VLC's seem rather complex (again, not clean like "real" Gnome apps). I got it to work but MPlayer does sometimes still give weird error messages, even if the movie seems to be playing fine.

I would just really like to be able to simply use Totem.


Some other things I noticed since my last post:

Alacarte, the menu editor, seems a little buggy. Sometimes it doesn't save changes I made, and it crashed a few times.

And some good news: I got my TV-Out working fine using the instructions on the Ubuntu Wiki. :)
I had to look in the readme of the NVidia drivers to find out how to set my monitor on 1280x1024 and my TV on 1024x768 though. But I got that working too, with the screen on the TV automatically panning where my mouse goes. 8)


(And yeah, I'm Dutch Guus :))

---

### Post by Geert Jan on 2007-03-06
I'm starting to have second thoughts about whether Ubuntu is ready to become my main OS right now. :(

I updated to Feisty, but none of the things I posted about have been fixed yet. I also found more things I'm not happy with:

- Resizing columns (in most/all Gnome/GTK(?) apps) is still (has always been as far as I know) non-intuitive and confusing. When I grab a separator between two columns with my mouse, you'd think the separator moves to where I move my mouse. Instead it moves all over the place. Makes the entire OS seem very unpolished.

- When I set my screen to 1024x768 so my TV-out can play movies at full screen, Totem changes it back to 1280x1024 the moment I make Totem play full screen. I found this bug on launchpad.net and I reported that I encountered it too. But it's still an "unconfirmed" bug so I doubt it'll be fixed anytime soon.

- Tag support on audio files. For example, some media players/taggers use ID3v2.3 tags on MP3s, others use ID3v2.4, causing a lot of compatibility problems. Some programs don't recognize tags on FLAC files. And I haven't found a program yet that supports some kind (any kind) of "Album Artist" tag. I really like to sort my music album-wise, and I have a lot of songs that don't have the same artist as album artist. Also, why do albums always get sorted alphabetically? Wouldn't sorting by year be much more logical?

*takes a deep breath*

Ok, sorry for again a negative post. I'm only doing this because I would SO love to switch to Ubuntu, but right now it feels like I will have to make sacrifices if I do. Don't get me wrong, I'm willing to do that and take some bad things with the many good things it has to offer over Windows, but I guess I just set my hopes of how perfect Ubuntu would be right now a little too high.

---

### Post by Geert Jan on 2007-03-09
> **Geert Jan said:**
> - When I set my screen to 1024x768 so my TV-out can play movies at full screen, Totem changes it back to 1280x1024 the moment I make Totem play full screen. I found this bug on launchpad.net and I reported that I encountered it too. But it's still an "unconfirmed" bug so I doubt it'll be fixed anytime soon.

Well, I stand corrected on this one. I posted on Launchpad about that bug a couple of days ago and it has been fixed already. Nice.

So anyway, the "Ubuntu Testimonials" part of the forum seems to have disappeared, so I'm not even sure anybody can still read this, but I just wanted to make a final post saying that I'm going to keep my Ubuntu partition and I'm going to keep track of its development. I wasn't lying about never getting Windows Vista, so I'm still planning on switching to Ubuntu in the future, at least before Windows XP becomes really outdated.

So I guess I'll see you then. :)

---

### Post by jocheem67 on 2007-03-12
Hey fellow-dutchman:

I've been struggling with multimedia in ubuntu:

about tagging, that's a tricky thing in every Os. You're right about the diff. tagging versions and that they're not well picked up by the vatious players. You should try to find a combination of proggies that do the trick for you. What works for me is using these programs: cowbell for tagging albums, playing with rhythmbox works flawlessly. Sometimes I switch to foobar2000 in xp for tagging by hand, it&#347; a very sophisticated progam. It works in wine by the way too or with vmware...
Amarok is another player I use. It has lots of option but it doesn't read tags that well, probably another version - thingie. It&#347; about trial and error and some persistance, but that counts for windows too.

subtitles are read by totem as long as they are text-based. Rip a dvd with for example dvd::rip, rip the subs, resulting in an .idx and a.sub file and convert them with ksubtitleripper ( by the way the fastest ocr-program around ) to .srt...Then with subtitle-editor I convert those to .ssa to make them readable with my stand-alone. It only takes minutes. The last step is only obligatory for me I guess.

Switching Os'ses is a long road, but well worth trying. Ubuntu is remarkable initiative.

Good luck!

---

### Post by Geert Jan on 2007-03-28
Hmm... I'm a bit more enthusiastic about Ubuntu again. 8)

First off, thanks for the reply jocheem67. Yeah I currently use foobar2000 on Windows too, it's excellent and I configured it exactly to my liking. It now looks like no other music player, which is why I have so much trouble finding a suitable Linux player.

But... I have a plan!

Recently I've been brushing up on my C++ skills, and also learning some Python and GTK programming with the help of Glade. So right now I think that with some more practice and learning about GStreamer I might be able to program my own simple music player. Just need to find the time to do it. :)

So anyway, at the moment I'm using my Ubuntu partition for most of my university work already (including programming), and I'm feeling up to slowly making the switch from Windows again. I switched back to Edgy, but I can't wait to try out the final version of Feisty!

---

### Post by Geert Jan on 2007-06-20
Just wanted to bump this old thread one final time to mention that I have now fully switched to Ubuntu!

My Windows XP partition is now only used for World of Warcraft.

About some of the hurdles I complained about earlier: I decided upon using VLC for video. I still think it has too many options for a GNOME app, but since the default options are fine and it has a big "reset to defaults" button I can live with it. :)
I also followed through with my plan to write my own music player, it's already working. I wrote it using Python, GTK and GStreamer. Three great pieces of software if you ask me. If I ever feel it's really finished I might even try releasing it to the public. :)

So, this was my story. It took me some time, but now I'm really one of you. :D

---

