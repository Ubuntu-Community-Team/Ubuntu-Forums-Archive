---
title: "GNOME 2.16 released--eyecandy implications?"
date: 2006-09-07
forum: The Cafe
---

### Post by Brunellus on 2006-09-07
[http://www.gnome.org/start/2.16/](http://www.gnome.org/start/2.16/)

everybody's favorite desktop environment, GNOME, released v. 2.16 today.  

My eyebrows went up as I read this in the release announcement regarding the window manager everybody loves to hate (Metacity):

> 
Advanced 3D effects

Metacity, GNOME's default window manager, makes its first steps into the world of 3D accelerated desktop computing. Many extensions to its compositor engine let your windows wobble, shrink, explode, fade in and out, bounce on window focus, and show other interesting, unusual or funny effects such as having different transparency for different window types like menus, dialogs, and main windows.

Not yet enabled by default, new compositing affects are only available when Metacity is compiled with the special --enable-compositor option. The new compositing features also depend on support for the GLX_texture_from_pixmap extension, which is only available to owners of Intel i830 to i945, and ATI Radeon 7000 to 9250 chips at the present time.

“It's important to note,” says Vincent Untz, member of the GNOME release team, “that it's an ongoing work, and that more will come in 2.18”.

Once Metacity is compiled with the correct option, the effects can be turned on and off without a restart or new login, and applications can take advantage of this. For example, the GNOME terminal can now offer real transparency.

What, no love for nvidia users?   I wonder when laptops with puny Intel integrated graphics will be able to kick out the eyecandy. I am already dreaming of a System76 Gazelle...with GNOME 2.16 eyecandy.

---

### Post by Lord Illidan on 2006-09-07
So this can work on v. old graphics cards but not the new ones? I'll stick with compiz and XGL, thanks...

---

### Post by frodon on 2006-09-07
No nvidia support, it's a shame, i wonder how metacity can chalenge xfwm4, compiz and kwin if they offer the small eyecandy improvements only to a part of the community.
nvidia is the first constructor and the only one to provide good linux drivers, hope this will be fixed in gnome 2.18

---

### Post by Brunellus on 2006-09-07
i'm guessing that the GNOME team is doing a bit of discrimination in favor of open-source drivers.

---

### Post by Virogenesis on 2006-09-07
I'm seriously going off of gnome, they did this on purpose it really stinks.
GNOME will lose users if keep on forcing their religion down the throat of people.

---

### Post by frodon on 2006-09-07
> **Virogenesis said:**
> I'm seriously going off of gnome, they did this on purpose it really stinks.
GNOME will lose users if keep on forcing their religion down the throat of people.It's not needed, just use xfwm4 (the XFCE wm), it's also GTK, it's faster than metacity and have more eyecandy.
Just do : ```
sudo apt-get install xfwm4 xfce4-mcs-manager
killall metacity & xfwm4
```And you're ready to go, i use it for 2 years now ;)

---

### Post by Virogenesis on 2006-09-07
frodon, done exactly that before you suggested I'm annoyed by this hopefully they will get alot of compliants from users.
Only prob with xfce is it lacks a decent filemanger IMO.

---

### Post by llonesmiz on 2006-09-07
The important part is:
> The new compositing features also depend on support for the GLX_texture_from_pixmap extension, which is only available to owners of Intel i830 to i945, and ATI Radeon 7000 to 9250 chips **at the present time.**


In theory nVidia and ATI will support that extension in their next binary drivers. That is the same extension needed for AIGLX, so there is no conspiracy, it's just that right know only the open source drivers support that.

---

### Post by atrus123 on 2006-09-07
> **llonesmiz said:**
> The important part is:


In theory nVidia and ATI will support that extension in their next binary drivers. That is the same extension needed for AIGLX, so there is no conspiracy, it's just that right know only the open source drivers support that.

Yep, no conspiracy here; it all comes down to what the closed source drivers support.  If you want to shout at someone, shout at your card manufacturer.

---

### Post by TravisNewman on 2006-09-07
> **Brunellus said:**
> [http://www.gnome.org/start/2.16/](http://www.gnome.org/start/2.16/)

everybody's favorite desktop environment, GNOME, released v. 2.16 today.  

My eyebrows went up as I read this in the release announcement regarding the window manager everybody loves to hate (Metacity):



What, no love for nvidia users?   I wonder when laptops with puny Intel integrated graphics will be able to kick out the eyecandy. I am already dreaming of a System76 Gazelle...with GNOME 2.16 eyecandy.
Well, granted, the integrated intel chips suck hard. I can't play doom3 with them. However, XGL/Compiz runs like a dream! No joke.

But no, I don't think it's a conspiracy, however, I don't understand why compiz, kwin, and xfwm4 can support the intels and new radeons but aiglx and metacity can't.

---

### Post by GazaM on 2006-09-07
> **panickedthumb said:**
> Well, granted, the integrated intel chips suck hard. I can't play doom3 with them. However, XGL/Compiz runs like a dream! No joke.

But no, I don't think it's a conspiracy, however, I don't understand why compiz, kwin, and xfwm4 can support the intels and new radeons but aiglx and metacity can't.

I'll try to explain this as best I can, in a nutshell. Compiz, kwin, xfwm4, metacity etc. don't have to support any graphics drivers. This isn't a problem with metacity.

All of these compositing Window Managers need an Xserver with appropriate features to actually work, currently the two options are XGL and AIGLX. There are various threads on this very forum which contain discussion on the merits of both and why you should use one over the other. Put shortly, XGL currently works as a 'hack' (not necessarily in a bad sense) on top of the normal Xserver, whereas AIGLX is now built in and included in Xorg 7.1 and the general opinion is that AIGLX is the better option for various reasons. Compiz can currently work with either XGL or AIGLX.

Because of the way XGL works though, it can run on top of even proprietary drivers. AIGLX however, is going to need support for the mentioned GLX extension in the drivers themselves to work with them (the support should be coming soon apparently).

So again... this isn't a problem with Gnome or metacity.

---

