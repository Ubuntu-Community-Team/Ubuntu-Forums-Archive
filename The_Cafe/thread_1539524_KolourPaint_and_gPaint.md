---
title: "KolourPaint and gPaint"
date: 2010-07-26
forum: The Cafe
---

### Post by user1397 on 2010-07-26
I know this has come up before, but I don't see a resolution on this issue anywhere, so I will readdress it here.

Many people like to have/use a simple drawing program such as MS Paint (especially Windows migrants who are used to Paint) for basic editing.  I don't blame them, Paint is very easy to use, and can be used for a plethora of basic tasks that many people require.  Programs like photoshop and GIMP are far too advanced for the kind of tasks I'm talking about here.

So the two programs most similar to MS Paint in my experience are KolourPaint and gPaint.

KolourPaint is by far the more intuitive, less buggy, and prettier of the two.

Just download them and see for yourself.

Now my question is, would it be possible to just take the basic KolourPaint code and use gtk and pygtk maybe instead of qt to code the gui to make a gnome version?

Or should gPaint just be improved?

Does anyone care?

---

### Post by pinguy on 2010-07-26
[http://pinta-project.com/](http://pinta-project.com/)

Is the best simple gtk paint program I have come across.

---

### Post by user1397 on 2010-07-27
bump

---

### Post by Simian Man on 2010-07-27
I am working on a GTK+ paint program.  It is nearing alpha quality, but even then will need a lot of work.

As for Kolourpaint, porting it to GTK would as much as than starting from scratch I think.

---

### Post by user1397 on 2010-07-27
> **Simian Man said:**
> I am working on a GTK+ paint program.  It is nearing alpha quality, but even then will need a lot of work.

As for Kolourpaint, porting it to GTK would as much as than starting from scratch I think.

oh cool. got a link yet?

---

### Post by Simian Man on 2010-07-27
> **ubuntuman001 said:**
> oh cool. got a link yet?

No, it's really unusable at the moment; I haven't had much time for fun programming lately...

---

### Post by ultrageeky on 2010-07-27
Have a look at [MyPaint]("http://www.getdeb.net/software/MyPaint"). You'll need to enable the GetDeb repositories ([Click here, choose option one]("http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install"))

---

### Post by RevengeOfTheToxicRodent on 2010-07-27
KolourPaint is great, but last time I used it (in Kubuntu 9.10), there was an odd bug. When you moved the brush too fast in a circular motion, it would crash x.

---

### Post by user1397 on 2010-07-28
> **RevengeOfTheToxicRodent said:**
> KolourPaint is great, but last time I used it (in Kubuntu 9.10), there was an odd bug. When you moved the brush too fast in a circular motion, it would crash x.
hmm never heard of that bug, wondered if they fixed it or if it was just an isolated bug.

---

### Post by user1397 on 2010-07-28
> **ultrageeky said:**
> Have a look at [MyPaint]("http://www.getdeb.net/software/MyPaint"). You'll need to enable the GetDeb repositories ([Click here, choose option one]("http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install"))
looks cool, but it's still not what I'm talking about.

I'm talking about MS Paint look-alike programs, such as gpaint and kolourpaint

---

### Post by Twitch6000 on 2010-07-28
Well it doesn't hurt to use kde apps in a gnome de.

There is also a way to make it blend in better with gktqt.

---

### Post by Simian Man on 2010-07-29
> **ubuntuman001 said:**
> oh cool. got a link yet?

Actually you prompted me to return to it and get a 0.1 release together.  I posted it [here]("http://ubuntuforums.org/showthread.php?p=9652661") :).

---

### Post by agnes on 2010-07-29
mtPaint can be used as a GTK Paint substitute. It is lightweight, yet alongside the painting tools it includes image editing tools. But it's less intuitive than something like KolourPaint.

---

### Post by user1397 on 2010-07-29
> **Simian Man said:**
> Actually you prompted me to return to it and get a 0.1 release together.  I posted it [here]("http://ubuntuforums.org/showthread.php?p=9652661") :).
awesome! i'll try your app later tonight, and give you some feedback if you want me to.

thanks!

---

### Post by user1397 on 2010-08-04
> **Simian Man said:**
> Actually you prompted me to return to it and get a 0.1 release together.  I posted it [here]("http://ubuntuforums.org/showthread.php?p=9652661") :).

Not too shabby at all Simian Man, I thought Congo Paint was quite simple yet effective.  I'll be watching its progress.

As for any bugs I had, the only thing was I couldn't use the spray nor the bucket filler (don't know what that's called exactly) too much at one time, or else it would freeze or lock up.  Other than that, tried all features and everything worked.  Good job!

---

### Post by chris4585 on 2010-08-04
I think gnome-paint is a pretty good candidate: [http://code.google.com/p/gnome-paint/]("http://code.google.com/p/gnome-paint/")

---

### Post by Legendary_Bibo on 2010-08-04
I use GNUPaint for quick sketches. It seems to be an identical clone to the MS Paint before Windows 7 except with options for effects.

---

### Post by wkhasintha on 2010-08-04
yup gPaint is big time sluggish . Gotta try Kolourpaint out, Thanx for mentioning.

---

### Post by Legendary_Bibo on 2010-08-04
If you really want MS Paint, you could just use it through Wine.

---

### Post by ultrageeky on 2010-08-04
If you really want to use MSPaint (and I don't think the OP does) you can install it with Wine, PlayOnLinux or winetricks. I'm in the middle of writing an installer for all three. You can test it out [here]("http://journalxtra.com/2010/08/how-to-install-windows-games-and-apps-into-linux/"). It was intended to make it easy to group add software from winetricks but I updated it to add the official wine and PlayOnLinux repositories and install them too (along with wisotool).

If you use it, be careful with the Wine and PlayOnLinux remover because it causes left-over and defunct menu items to relocate to "Applications>Other" which is where the re-installed PlayOnLinux is also found. Will get it fixed shortly.

---

### Post by Legendary_Bibo on 2010-08-04
I can't seem to find the Windows 7 Paint though. It seems MS hasn't put it on their site. So how would I go about copying it off my dad's Win7 computer?

---

### Post by ultrageeky on 2010-08-04
Right click it's icon, select properties, look for it's file location or file name, move it over to you Linux OS and install it with Wine. You'll need a Windows 7 license to use it (I think).

---

### Post by nerdy_kid on 2010-08-04
> **ubuntuman001 said:**
> I know this has come up before, but I don't see a resolution on this issue anywhere, so I will readdress it here.

Many people like to have/use a simple drawing program such as MS Paint (especially Windows migrants who are used to Paint) for basic editing.  I don't blame them, Paint is very easy to use, and can be used for a plethora of basic tasks that many people require.  Programs like photoshop and GIMP are far too advanced for the kind of tasks I'm talking about here.

So the two programs most similar to MS Paint in my experience are KolourPaint and gPaint.

KolourPaint is by far the more intuitive, less buggy, and prettier of the two.

Just download them and see for yourself.

Now my question is, would it be possible to just take the basic KolourPaint code and use gtk and pygtk maybe instead of qt to code the gui to make a gnome version?

Or should gPaint just be improved?

Does anyone care?

actually, if you install systemsettings you can set the qt theme to gtk (which actually works, unlike the qt engine for gtk).

---

### Post by ubunterooster on 2010-08-04
*spam post so I can check something*

---

### Post by Spice Weasel on 2010-08-05
[http://canvaspaint.org/](http://canvaspaint.org/)

Problem solved.

---

