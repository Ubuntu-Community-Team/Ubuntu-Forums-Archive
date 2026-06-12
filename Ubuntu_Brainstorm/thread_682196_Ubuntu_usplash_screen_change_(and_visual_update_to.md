---
title: "Ubuntu usplash screen change (and visual update to livecd?)"
date: 2008-01-29
forum: Ubuntu Brainstorm
---

### Post by gavintlgold on 2008-01-29
I started up the SUSE livecd to try out kde4, and I was stunned by the beauty and elegance of the startup sequence.

First there was about a half-second of text, but a green screen immediately started up to select the type of startup (like ubuntu's). The difference was it said "welcome" in many languages, with a little wipe-fade effect. This animation impressed me, because I assumed that it would not be possible to do that kind of thing before hardware initialization.

Then, while it started, it said "openSUSE" in the side, very small, with a nice green screen, and very lightly "esc for details"... when I clicked that the resolution was much higher than ubuntu's and the layout of the terminal was much neater than ubuntu's.

When I started without the verbose mode, the progressbar slid across smoothly and then kde4 started.

Now, compared to Gutsy Gibbon, that was amazing (even if kde4 itself is quite buggy). I think that since Ubuntu is having a visual refresh, it should attempt something similar.

I suppose I should take a picture of the startup, or try it in a virtual machine... Anyway, I was wondering if it would be possible to implement something (which goes with the ubuntu theme) that looked up to par with this standard.

here are some screenshots:

[[img]http://picpaste.com/extpics/welcome.png[/img]](http://picpaste.com/welcome.png)  [[img]http://picpaste.com/extpics/kde4live.png[/img]](http://picpaste.com/kde4live.png)  [[img]http://picpaste.com/extpics/loading.png[/img]](http://picpaste.com/loading.png)  [[img]http://picpaste.com/extpics/terminal_1.png[/img]](http://picpaste.com/terminal_1.png)

---

### Post by zombiepig on 2008-01-30
I'll second most of that - I was very impressed by the bootup process when I checked out OpenSuse. (But then again, i love green :))

---

### Post by mattismyname on 2008-01-30
I third that.  I would especially appreciate a higher text-mode resolution by default to make reading the kernel messages easier as they scroll by.

Years ago I configured my box to up the text-mode resolution so I know it's possible.  Of course, there may be reasons (backward compatability) for having a low default resolution.

---

### Post by Gina on 2008-01-30
I agree too.  The Ubuntu startup is incredibly boring - not even any colour on the grub menu by default (it's there, it only needs turning on by default).  I really hate white text on black background - remiscent of DOS of the 80s and early 90s!!

---

### Post by MacUntu on 2008-01-30
There is only one OS with a worse graphical boot process than Ubuntu:

[IMG]http://www.johntp.com/wp-content/uploads/vista-default-boot-screen.jpg[/IMG]

---

### Post by xsnslaine on 2008-01-30
> **MacUntu said:**
> There is only one OS with a worse graphical boot process than Ubuntu:

[IMG]http://www.johntp.com/wp-content/uploads/vista-default-boot-screen.jpg[/IMG]

=D> couldn't of said it better myself

---

### Post by amano on 2008-01-30
A bootup like SuSe is not possible for the moment. I think that usplash is limited to 256 colours and I agree with the developers that those are better spent on the logo than on shaded backgrounds or whatever.

But a first step in the right direction would be to make at least the bootsplash and GDM visually coherent. 

Same background, same logo placement etc, etc. It should look like one thing, not like 2 different things  (though technically they are of course).

---

### Post by smartboyathome on 2008-01-30
I am pretty sure SUSE uses Splashy or a varient from splashy, and for GRUB it uses GFXBoot, which gives you the ability to use graphics with GRUB. At the moment, Ubuntu doesn't want to use either of these (due to reasons such as it may break suspendability and such, at least for splashy), so it probably won't be able to "update" it as much.

---

### Post by mattismyname on 2008-01-30
Thanks for the input amano and smartboy.  I'm curious, are there any impediments to using a higher text-mode resolution for the kernel boot messages?

---

### Post by DizzyTech on 2008-01-30
I know this is not true for all, but openSUSE had both suspend and hibernate work on my laptop while Ubuntu did neither.  Same for Fedora.

---

### Post by gavintlgold on 2008-01-31
> **amano said:**
> 
...a first step in the right direction would be to make at least the bootsplash and GDM visually coherent. 

Same background, same logo placement etc, etc. It should look like one thing, not like 2 different things  (though technically they are of course).

I definitely agree about the coherence. Would it also be possible to get rid of the black screens during boot/login? When I start up, there are 3 times it switches to black:

[LIST=1]
[*]After GRUB
[*]After ubuntu starts up
[*]after i log in
[/LIST]

Now, I know it has to start up x and stuff like that, but is there any way to make it seem like the startup and gdm are THE SAME app? Would one have to start X up before the login screen comes on? (I suppose so :( ) I suppose before GDM's ok, since that's the start of X. But why does it go black when I log in? It flickers to brown and then black, then loads.

While I'm at it, wouldn't it be cool if, after login, the screen remained blank until the stuff like the panel was already loaded and everything, then it faded into your complete desktop (with compiz)? Right now, there's a mess of little white rectangles while the panel loads, and lots of color switches (brown, black, wallpaper)...

In terms of starting up elegantly, I think Ubuntu has a while to go. But then of course, the important part is that it works, which I can't say for the kde cd when I tried to install it with VirtualBox onto an image (boot failed... then again maybe it's virtualbox).

---

### Post by smartboyathome on 2008-01-31
That could be possible (E17, XFCE, and KDE all already do it), but Ubuntu took out GNOME's splash screen because it delayed the startup, so it needs to be replaced anyway.

---

