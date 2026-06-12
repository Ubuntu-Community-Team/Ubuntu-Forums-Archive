---
title: "Wine with World of Warcraft on a new X server"
date: 2010-06-12
forum: Wine
---

### Post by Mirror Shades on 2010-06-12
Hey guys,

I decided to play World of Warcraft through wine and it runs pretty much fine, but I can't minimize it to the taskbar to view other applications running on my desktop. So I found [[COLOR="Red"]this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=51486") which tells how to make games run on a new X server. I've configured my x.et according to this guide, but when I try to run it in terminal it just starts and shuts down immediately, outputting this last line:

> xinit:  No such file or directory (errno 2):  no program named "/media/MEDIA/Games/WoW 3.3.3a/WoW.exe" in PATH


I filled x.et file like that:

> #!/bin/bash
xinit /media/MEDIA/Games/"WoW 3.3.3a"/WoW.exe $* -- :1

I suppose this is wrong, because it should run through wine and I haven't pointed that out to the X server (because I don't know how), at least I think so. Could you guys lend me a hand in making this to run? Or maybe you know some other ways to minimize full-screen game to desktop, because it really bugs me when I can't browse the internet while playing. Thanks in advance :)

BTW I'm using Ubuntu 10.04 if that is of any help.

---

### Post by jeremyswalker on 2010-06-12
I've never tried what you are attempting. However, when I used to play WoW, I just used virtual consoles to have access to other programs. For example, I would press "Ctrl + Alt + F1" while in-game, login at the prompt, run something like "xinit /usr/bin/fluxbox -- :1", and there you have it. Of course, you could substitute "fluxbox" for "gnome-session", etc.

---

### Post by Mirror Shades on 2010-06-12
I guess I don't get it. When I press "Alt + F1" in-game, game doesn't go down to the tray, but the cursor gets hold of my desktop and programs in the background - I can see the game, but my cursor controls the background programs, and when I move over active objects there, my screen just blinks, giving me a millisecond's view of my background. Same thing happens with "Alt + Tab" and "Ctrl + Alt + D". Maybe there's something with my video card drivers or something? Or is it really like that in all Ubuntu systems?

---

### Post by jeremyswalker on 2010-06-12
Sorry, my mistake. The correct key combo is "Ctrl + Alt + F1". You can use F1 through F6, take your pick.

---

### Post by Mirror Shades on 2010-06-13
Your suggestion really worked, thank you. But now I have some more questions:

1. This "xinit /usr/bin/gnome-session -- :1" means that I'm making a new session called "gnome-session", right? How is my primary session called then?

2. How can I switch between those two sessions back and forth? Because now this new session brings up my desktop, but I have managed to return to my game only by switching from my current user, and couldn't figure out how to return to "gnome-session" once more. Maybe there's a hotkey that can switch between sessions or something?

Oh and I've been having some thoughts on running my background programs (web browser, etc.) and my games in different workspaces. Maybe I could just simply switch between them and this would solve my minimizing problem. Could that be possible or would game still get "stuck" on top of my desktop?

Thank you for your replies

---

### Post by jeremyswalker on 2010-06-13
To get back to the main session that starts when you turn your computer on use "Ctrl + Alt + F7". When I played, I installed fluxbox. That way I had a nice lightweight window manager, instead of running multiple gnome sessions. I'm not sure about your workspaces question.

---

