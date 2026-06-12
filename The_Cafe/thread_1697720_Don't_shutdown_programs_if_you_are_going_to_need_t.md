---
title: "Don't shutdown programs if you are going to need them again"
date: 2011-03-01
forum: The Cafe
---

### Post by TheDudeAlex on 2011-03-01
(didn't really know where to post this, it's an idea I have... It might already exist, I don't know.)

Problem/Idea/...: 

When you close a window firefox shuts down if there aren't any other FF windows left.
But the user is not paying attention to that. He's browsing, emailing, chatting, ... Maybe for 1 minute he doesn't need firefox, but when he does need it again firefox will have to restart all over. Maybe that only takes 4 seconds, but I'm looking for a way to save those seconds :-)

So I started searching:

    - Firefox open-new-tab-when-last-tab-is-closed-option: 
Opens a new tab when the last tab is closed. Still shuts down firefox when (X) is pressed and doesn't hide FF in any way.

    - Ubuntu brainstorm Idea #24255: 
This idea is about making a difference between closing and minimizing (to system tray). Because now, programs do it 'as they please'. Emesene, mail apps or torrent programs minimize to system tray while others shut down when (X) is pressed. 

    - "Alltray": can minimize programs to the system tray, doesn't close the window (the webpage(s) in that window), and really old ubuntu package (2006);

This is kind of what I'm looking for but the main difference is that I don't want the program to just minimize to another place (system tray instead of window navigation area, which is the normal minimize option). I want it to close the window (a group of tabs for example) when I press (X) BUT keep firefox running.

    -"MinimizeToTray Plus" firefox add-on: it works really nice in Ubuntu 10.04. But again: it only minimizes the window and when I open FF from tray, I get my webpages back. I can shut the window from File > Quit, but then it closes ALL firefox windows...

    -I looked into running Firefox as a background process, but I'm starting to think that this isn't possible. It would have to switch to foreground and back again when firefox is started and closed.

    -My last idea was that maybe firefox can just keep an open/empty tab hidden somewhere. 

I'm hoping someone here has some creative input :p cause I'm running out of thoughts.
I feel like this can be useful in more than just browsers. For example: word processors, media players... Anything you want to access fast and multiple times in one 'session'.

I got this idea partly from mac os x where this is already implemented... When you close chrome window, chrome itself doesn't shutdown. Anyway,
 Grtz
Alex

---

### Post by cchhrriiss121212 on 2011-03-01
> Maybe that only takes 4 seconds, but I'm looking for a way to save those seconds
Try using preload form the repos, it will load your most used apps into RAM.

TBH I'm not really sure how your idea is an improvement or whether it solves a problem people actually have. If you want to keep something running, just minimize the program. I'm pretty sure minimize itself was developed as a way to close something, but keep it running.

Personally I want my OS to do what I tell it, when I ask something to close, that is what I want. Hidden tabs and background processes will leave less resources for competing apps.

---

### Post by s.fox on 2011-03-01
Not a support thread. Moved to  [The Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")

---

### Post by 3Miro on 2011-03-01
Linux is smart to cache things into RAM. If you open a program, then close it, then open it again, it would take only a fraction of the time (unless you have waited a long time to open it again and long time depends on how much RAM you have and what else you are doing). This is not exactly what you are suggesting, but it is close. What I do often, is that I just keep a Chromium windows open with Gmail on one of my workspaces.

You suggestion in particular is somewhat Mac-ish. While not necessarily bad, the problem is that some people would be confused on what is opened and what is closed (why is my computer getting slower, I don't have any windows opened, what do you mean "running in the background").

Something that people are using to speedup Firefox (I have not done any of this):

[http://www.webupd8.org/2009/05/speed-up-firefox-by-mounting-profile-in.html](http://www.webupd8.org/2009/05/speed-up-firefox-by-mounting-profile-in.html)

[http://lifehacker.com/#!5687850/speed-up-firefox-by-moving-your-cache-to-ram-no-ram-disk-required](http://lifehacker.com/#!5687850/speed-up-firefox-by-moving-your-cache-to-ram-no-ram-disk-required)

---

### Post by BrokenKingpin on 2011-03-01
> **cchhrriiss121212 said:**
> 
TBH I'm not really sure how your idea is an improvement or whether it solves a problem people actually have. If you want to keep something running, just minimize the program. I'm pretty sure minimize itself was developed as a way to close something, but keep it running.

Personally I want my OS to do what I tell it, when I ask something to close, that is what I want. Hidden tabs and background processes will leave less resources for competing apps.
> **3Miro said:**
> Linux is smart to cache things into RAM. 
This. If I close something it better actually close and not just hide itself, unless it is to the tray and clearly visible. Also, if you are finding applications talking to long to load even after the OS has cached them, then that is just bad application design (I am looking at you Firefox) and you should look to switch to an alternative (Chromium).

---

### Post by NMFTM on 2011-03-01
> **cchhrriiss121212 said:**
> Try using preload form the repos, it will load your most used apps into RAM.
Noted.

---

### Post by TheDudeAlex on 2011-03-10
Thx guys!

I've made firefox run in ram and it works a bit faster ( I thinks )

---

