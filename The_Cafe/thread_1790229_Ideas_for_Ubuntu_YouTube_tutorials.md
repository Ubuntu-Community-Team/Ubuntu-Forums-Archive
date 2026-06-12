---
title: "Ideas for Ubuntu YouTube tutorials?"
date: 2011-06-24
forum: The Cafe
---

### Post by de_dust on 2011-06-24
I've been wanting to make videos about Ubuntu but can't for the life of me think of anything to teach.

---

### Post by haqking on 2011-06-24
> **de_dust said:**
> I've been wanting to make videos about Ubuntu but can't for the life of me think of anything to teach.

how to use the forums to search for commonly asked questions.

then make it a sticky LOL ;-)

oh and i mean that for real, not meant at your post being repeated ;-)

---

### Post by cariboo on 2011-06-24
A tutorial on how to create a great video tutorial

---

### Post by drawkcab on 2011-06-24
How to install the codecs for x264 and configure smplayer so that all .mkvs can be played?

---

### Post by trizrK on 2011-06-25
> **de_dust said:**
> I've been wanting to make videos about Ubuntu but can't for the life of me think of anything to teach.
Newbie stuff.
use a screen capturer too.
WITH voice, lol.
Cant tell you how much i hate the slow notepad typing!:-x

---

### Post by MrEgg on 2011-06-25
You may want to check out [Ubuntu Screencasts]("http://screencasts.ubuntu.com") - there's a lot of tutorials over there, which could inspire you for new ones !

---

### Post by coutts99 on 2011-06-25
Youtube tutorials suck.

Write a proper text based howto, much more use to everyone.

---

### Post by slooksterpsv on 2011-06-25
> **coutts99 said:**
> Youtube tutorials suck.

Write a proper text based howto, much more use to everyone.

With screenshots.

Anyways to your original question:

How to get a decent FPS from screen capture (gots a script to do thats for mes =D ), how to use DASH, umm.... Ubuntu umm.... the others are really just app specific; oh how to search effectively in Ubuntu Software Center.

---

### Post by kidknapp on 2011-06-25
Jack and Rosegarden with Hydrogen and realtime kernel. :p

---

### Post by kleovoulinos on 2011-06-25
I would make a tutorial about what extensions to install to run DVD's that are, let's say Windows compatible!

---

### Post by Random_Dude on 2011-06-25
How to do an Ubuntu minimal install.
There are already enough videos about normal installation procedures and newbie stuff IMHO.

Cheers :cool:

---

### Post by ZarathustraDK on 2011-06-25
+1 on the fleshed out guide on how to obtain optimal FPS on screencasts/video-tutorials.

Seems to me that getting a proper FPS on these things is a highly individual thing that depends on hardware, resolution, refresh rate and whatnot. A proper guide that teaches how to produce an optimal, fluid, youtube-ready screencast, 720p/1080p res, would go a long way.

Youtube is one of the few venues where the creative bunch of users can pimp their desktop, so it's one of the few marketing-tools we possess.

Remember back when Compiz first came out? Youtube really served to win over a lot of people back then.

---

### Post by Bart_D on 2011-06-25
> **de_dust said:**
> I've been wanting to make videos about Ubuntu but can't for the life of me think of anything to teach.

How to perform an Ubuntu minimal installation starting from the Minimal CD image installation [B]ALL THE WAY to having a working desktop (preferably Gnome 3 with Gnome Shell) with
- plug-n-play
- audio
- video
drivers installed.[/B]

Note that the part I hilited in **bold** is NOT described on Psychocats. This is very disappointing and so YOU need to step up and produce a YouTube video showing EXACTLY how this is done.

---

### Post by slooksterpsv on 2011-06-25
> **ZarathustraDK said:**
> +1 on the fleshed out guide on how to obtain optimal FPS on screencasts/video-tutorials.

Seems to me that getting a proper FPS on these things is a highly individual thing that depends on hardware, resolution, refresh rate and whatnot. A proper guide that teaches how to produce an optimal, fluid, youtube-ready screencast, 720p/1080p res, would go a long way.

Youtube is one of the few venues where the creative bunch of users can pimp their desktop, so it's one of the few marketing-tools we possess.

Remember back when Compiz first came out? Youtube really served to win over a lot of people back then.

```

echo "Press CTRL+C to stop"
ffmpeg -r 30 -s 1366x768 -f x11grab -i :0.0 -vcodec msmpeg4v2 -qscale 2 ~/RD-$(date +%F_%k-%M-%S).avi
echo "Finished Recording!"

```

That's how I do it =D

EDIT: Weird for LMDE I have to do: $(echo $(date +%F_%k-%M-%S) | sed 's/ //g') for the RD-$... cause otherwise it puts in a space that shouldn't be there.

---

