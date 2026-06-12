---
title: "I want to record my C64 games to a video file!"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by Rytron on 2010-01-25
Hi.
I have the C64 emulator 'Vice'. I own many C64 games on cassette tapes so everything is legal.

I use esound at present and not pulse. I want to record C64 games in Vice with audio. What method is best? Keep in mind that I cannot get internal audio to be recorded with GTK-recordmydesktop. Is another recording program worthwhile?

---

### Post by Lars Noodén on 2010-01-27
ffmpeg is one tool that can record the X11 session

---

### Post by Rytron on 2010-01-27
> **Lars Noodén said:**
> ffmpeg is one tool that can record the X11 session

How? Do you know the code to use?

---

### Post by Lars Noodén on 2010-01-27
No code (despite the tags below, it's about the only way to get fixed spacing).  

But the program to use would be FFMPEG and the settings will go something like this:

```

ffmpeg -v 2 -y -s *1600x1050* -r 9 -f x11grab -i *:0.0* \
-g 300 -threads 0 -vcodec libtheora -sc_threshold -1 \
-cqp 22 -b 1200k /tmp/screenCapture1.ogv

```

You'll have to choose the settings that meet your needs.  Screen resolution, is one that might be different for you.

---

### Post by Rytron on 2010-01-27
Thank you Lars Noodén. I will give it a try. :)

....I am confused!

---

### Post by Rytron on 2010-01-29
> **Coerver126 said:**
> yeah
thanks for the sharing

_______________

[fast cash](http://americanfinancesolutions.com)
[business cash advances](http://americanfinancesolutions.com)
[business loans for bad credit](http://americanfinancesolutions.com)

How did you get it to work?

---

### Post by AutoStatic on 2010-01-29
He/she didn't, it's a spambot.

---

### Post by Rytron on 2010-01-29
> **AutoStatic said:**
> He/she didn't, it's a spambot.

Thanks for the info AutoStatic.

---

### Post by AutoStatic on 2010-01-29
You're welcome. Wish I could help you but it's just that I'm not using Esound.

---

### Post by Rytron on 2010-02-07
I can record games such as Nexuix and Open Arena with no problems using glc. Also I can record a game running in wine (example: glc-capture wine /path/to/game.exe
Why can I not record a C64 game running in x64? I tried glc-capture x64 5thGear.t64 but as yet have had no success. Has anyone managed to do this?

---

### Post by Rytron on 2010-02-09
Has anyone managed to capture a game using glc and a wine run emulator such as vice or similar?

---

### Post by qubodup on 2010-04-06
> **Rytron said:**
> Has anyone managed to capture a game using glc and a wine run emulator such as vice or similar?
It [appears so]("http://www.youtube.com/watch?v=lJph0HceV0o"). Found via [google?search=glc+wine]("http://www.google.com/search?hl=en&q=glc+wine")

> ```
ffmpeg -v 2 -y -s 1600x1050 -r 9 -f x11grab -i :0.0 \
-g 300 -threads 0 -vcodec libtheora -sc_threshold -1 \
-cqp 22 -b 1200k /tmp/screenCapture1.ogv
```
Thanks Lars, hopefully this will allow me to dig deep enough to be able to replace my current lack of audio recording ability in xvidcap.

---

### Post by Rytron on 2010-04-06
Thank you qubodup. ):P

---

