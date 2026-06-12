---
title: "Are the Firefox Devs lazy for Linux or something...?"
date: 2007-08-29
forum: The Cafe
---

### Post by knopper67 on 2007-08-29
I'm not sure if any of you guys noticed this before but haven't you noticed that the preferences window in firefox can be resized to any Size. But heres the thing...
It Doesn't Happen in windows.

Everytime i report a bug describing this problem...no one ever bothers to read the bug report. It's getting very annoying.

[IMG]http://img110.imageshack.us/img110/2567/screenshotminefieldpreffx7.png[/IMG]

---

### Post by FriedChips on 2007-08-29
okay you are saying that it is a bug that you can resize the window? You can do that with any window it is not a bug.....

---

### Post by knopper67 on 2007-08-29
Thats not what i meant to say...it should resize to the point that it stops so it doesn't overlap the content in the window.

---

### Post by karellen on 2007-08-29
> **FriedChips said:**
> okay you are saying that it is a bug that you can resize the window? You can do that with any window it is not a bug.....

I think he's saying that the resizing of the windows covers the buttons. or that the content of the windows doesn't get resized as well. this doesn't happen in windows, though

---

### Post by knopper67 on 2007-08-29
Yes that is exactly what i meant! Thanks for saying it more clearly so everyone can understand.

---

### Post by happysmileman on 2007-08-29
Firefox for Linux sucks *** compared to Firefox on Windows, the devs seem to assume that they're guaranteed a market shar on Linux and therefore they can afford to **** it up a bit compared to Windows.

EDIT: I use Opera so I'm not a hypocrite or something, I will consider moving to Firefox in future if I think it's improved, will definitely try out 3.0

---

### Post by knopper67 on 2007-08-29
Speaking of Firefox Sucking on linux...anyone here seeing this a linux developer? Maybe we could create a not-crappy fork of firefox...

---

### Post by knopper67 on 2007-08-29
-happysmileman

Not to stunt your luck or anything but this doesn't seem to be fixed yet in the Aug 29 Nightly Build of FF3

---

### Post by karellen on 2007-08-29
yeap, I've noticed myself. firefox for windows looks more polished

---

### Post by ~LoKe on 2007-08-29
Doesn't really bother me...

---

### Post by FuturePilot on 2007-08-29
I thought this happened on Windows too. No? Hmmm. I usually don't resize that window anyway.

---

### Post by ryno519 on 2007-08-29
Patient: Doctor, it hurts when I do this.
Doctor: Then stop doing it.

---

### Post by 23meg on 2007-08-29
The bug affects the Windows and OSX builds as well.

[https://bugzilla.mozilla.org/show_bug.cgi?id=283697](https://bugzilla.mozilla.org/show_bug.cgi?id=283697)

---

### Post by blithen on 2007-08-29
Not to be mean, but why care?
Why resize it in the first place?

---

### Post by 23meg on 2007-08-29
The problem doesn't just occur upon resizing; it occurs as soon as the the Preferences window is opened. It opens cropped, and you have to resize it to see all the elements.

---

### Post by ryno519 on 2007-08-29
> **23meg said:**
> The problem doesn't just occur upon resizing; it occurs as soon as the the Preferences window is opened. It opens cropped, and you have to resize it to see all the elements.

I don't.

---

### Post by ~LoKe on 2007-08-29
> **23meg said:**
> The problem doesn't just occur upon resizing; it occurs as soon as the the Preferences window is opened. It opens cropped, and you have to resize it to see all the elements.

Mine opens up fine.

---

### Post by 23meg on 2007-08-29
[QUOTE=knopper67]Everytime i report a bug describing this problem...no one ever bothers to read the bug report.[/QUOTE]

See the link above; it seems it's a widely acknowledged bug, with lots of duplicates as well. Maybe you should get better at reporting bugs.

---

### Post by 23meg on 2007-08-29
> **~LoKe said:**
> Mine opens up fine.

Mine too. It doesn't apply to all configurations. I haven't read all the comments, so don't know what exactly the cause is here, but this kind of thing generally happens when there's no reliable measurement to base the window size upon. If you set a fixed window size, it may work with the default or assumed font and widget sizes and resolutions, but once the user changes them, things may go awry.

---

### Post by ajgreeny on 2007-08-29
This all seems like a very large thread about something that is in my opinion of very small importance.  So what if you have to resize the Preferences window?  How often do you open that window anyway?

A storm in a teacup!

---

### Post by blithen on 2007-08-29
> **ajgreeny said:**
> This all seems like a very large thread about something that is in my opinion of very small importance.  So what if you have to resize the Preferences window?  How often do you open that window anyway?

A storm in a teacup!

Thank you!

---

### Post by starcraft.man on 2007-08-29
That's it? Your making a big deal out of nothing. Resize it so it fits all the buttons and move on. How often do you change options anyway? Twice a year? Less?

Man that was a disappointing rant.

---

### Post by happysmileman on 2007-08-29
> **knopper67 said:**
> -happysmileman

Not to stunt your luck or anything but this doesn't seem to be fixed yet in the Aug 29 Nightly Build of FF3

It's fixed in Opera 9.23 so that's the end of that.

firefoxUsers--;

---

### Post by ~LoKe on 2007-08-29
> **happysmileman said:**
> It's fixed in Opera 9.23 so that's the end of that.

firefoxUsers--;

Elitists--;

---

### Post by Dimitriid on 2007-08-29
There's bigger issues with Firefox Linux to worry about resize. Try Epiphany if you want better gnome integration ( Konqueror for KDE )

---

### Post by happysmileman on 2007-08-29
> **~LoKe said:**
> Elitists--;

Calling me an elitist? I use whatever works and looks good on my Desktop, I'd be an elitist if I went around claiming my choices were better, I'm just saying Firefox need to actually get off their asses and wade through their source code until they actually find and fix things on Linux, right now they take it for granted that people will use it no matter how bad it is on Linux, this needs to change and the only way it will is if people actually switch and point out their mistakes.

---

### Post by Interestedinthepenguin on 2007-08-29
This fixed the issue for me; add it to your userChrome.css file (located in /home/username/.mozilla/firefox/profile.default/chrome/):

```
#BrowserPreferences {min-width: 450px !important; min-height: 430px !important;}
```

---

### Post by 23meg on 2007-08-29
[QUOTE=happysmileman]I'm just saying Firefox need to actually get off their asses and wade through their source code until they actually find and fix things on Linux, right now they take it for granted that people will use it no matter how bad it is on Linux[/QUOTE]

The bug isn't specific to Linux.

---

### Post by karellen on 2007-08-29
> The bug isn't specific to Linux.
well in windows that windows cannot be resized. so...it can't overlap the content

---

### Post by 23meg on 2007-08-29
It can. 

[https://bugzilla.mozilla.org/attachment.cgi?id=184483](https://bugzilla.mozilla.org/attachment.cgi?id=184483)

---

### Post by spier on 2007-08-29
Maybe I'm missing something, but my firefox Preferences window look nice, even before any window resize...

---

### Post by 23meg on 2007-08-29
> **spier said:**
> Maybe I'm missing something, but my firefox Preferences window look nice, even before any window resize...

Now try one or more of the following:

- Choose a different GTK theme
- Make your fonts 3px smaller/larger
- Change your display DPI

Still? If so, you're either lucky, or not pushing things far enough.

---

### Post by Ozor Mox on 2007-08-29
I can resize my Firefox preferences window too but it looks fine when I first open it so I just...don't. What exactly is the problem again?

---

### Post by spier on 2007-08-29
> **23meg said:**
> Now try one or more of the following:

- Choose a different GTK theme
- Make your fonts 3px smaller/larger
- Change your display DPI

Still? If so, you're either lucky, or not pushing things far enough.
The latter, probably. Tried  some of the standard themes and bigger system fonts with no avail -window size just increased.

---

