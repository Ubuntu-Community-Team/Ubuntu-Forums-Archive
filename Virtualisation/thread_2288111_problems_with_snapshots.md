---
title: "problems with snapshots"
date: 2015-07-24
forum: Virtualisation
---

### Post by pedrwilliams on 2015-07-24
I used Oracle VM virtual box to create a virtual machine running Windows Xp.(host Ubuntu 14 LTS).  I would like to create a number of snapshots with the machine in various different states but when I make a snapshot it simply replaces the already existing machine with the machine in its current state, so I only have a single machine state preserved. I am able to make a clone .
The manual says "select a machine in the virtual box manager and then click on the Snapshots button on the right". But there is NO Snapshots button on the right.
Virtual box 4,3,30 Host Ubuntu 14.04 LTS Guest Windows Xp

---

### Post by v3.xx on 2015-07-25
> when I make a snapshot it simply replaces the already existing machine with the machine in its current state
Could you explain this a bit more.

When a snapshot is created its auto-assigned a number.  Snapshot #1; #2 and so on.  It should not replace an existing snapshot.

---

### Post by pedrwilliams on 2015-07-25
The current machine is replaced by the last numbered snapshot eg "win Xp " machine is replaced by "win Xp snapshot 4" and I can't find "win Xp snapshot 3"(nor snapshot 2 nor snapshot 1 nor "win Xp"
I hope this is clear. Thanks for interest!

---

### Post by v3.xx on 2015-07-25
You have me at a slight disadvantage.  I run a Ubuntu host and our screens are a bit different.   But you should have something like this.

[ATTACH=CONFIG]263378[/ATTACH]

Is yours empty?

---

### Post by howefield on 2015-07-25
Hello pedrwilliams, I have removed your last post. Please use the paperclip icon from the posting window to attach an image to your post.

Presumably you triggered a Firefox bug by dropping an image into Firefox converting it into a huge amount of base64 code.

---

### Post by pedrwilliams on 2015-07-25
> **howefield said:**
> Hello pedrwilliams, I have removed your last post. Please use the paperclip icon from the posting window to attach an image to your post.

Presumably you triggered a Firefox bug by dropping an image into Firefox converting it into a huge amount of base64 code.

Sorry! Pardon my stupidity!
P.W.

---

### Post by pedrwilliams on 2015-07-25
> **v3.xx said:**
> You have me at a slight disadvantage.  I run a Ubuntu host and our screens are a bit different.   But you should have something like this.

[ATTACH=CONFIG]263378[/ATTACH]

Is yours empty?

I am probably being stupid and looking at the wrong file. Screenshot is [ATTACH=CONFIG]263380[/ATTACH]attached

---

### Post by v3.xx on 2015-07-25
No nothing stupid about this so far.  Your screen is very different from mine. So I went here to take a look at others
[https://www.google.com/search?q=windows+virtualbox+manager+pics&client=ubuntu&hs=F54&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ved=0CCEQsARqFQoTCIKNiIzk9sYCFRAsiAodkioLZA&biw=1440&bih=665#imgrc=3dA5ybTLfV4sjM%3A](https://www.google.com/search?q=windows+virtualbox+manager+pics&client=ubuntu&hs=F54&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ved=0CCEQsARqFQoTCIKNiIzk9sYCFRAsiAodkioLZA&biw=1440&bih=665#imgrc=3dA5ybTLfV4sjM%3A)
I am unsure, but it looks like yours should be more like mine.  As in missing.

Brain fart..the top of the screen is cut off, out of view.

Press Alt and r-click on the window and try to drag it down.

Edit
Also how did you install vBox?

---

### Post by pedrwilliams on 2015-07-25
I obtained Vbox from Ubuntu software centre and installed using synaptic package

I tried your suggestions ie Alt + Rclick - no help

Since your last post I have updated Vbox (from the website) from 4.3...  to 5.0. There is still no "details" button and no "snapshots " button . 
There seems some slight problem with ubuntu in my PC . Clicking on the waste bin brings up a small window headed "help" . Could this be related?
I don't know what to do now
Thanks
P.W.

---

### Post by v3.xx on 2015-07-25
Are you able to go fullscreen and seamless mode?

Look in vBox tool bar, click on "View"

---

### Post by pedrwilliams on 2015-07-26
There is no problem doing either . Full screen,scaled mode and seamless mode , all work properly.

---

### Post by ajgreeny on 2015-07-26
It's Alt+**left** click to move a window, not right click.

Try that and you should then see two buttons or tabs top right of the VBox window that are labelled **Details** and **Snapshots** just like v3.xx shows.

---

