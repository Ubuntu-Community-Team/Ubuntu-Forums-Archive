---
title: "Tilda problems: Launching, estability."
date: 2011-12-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-22
Tilda is broken for a week or so here. I have an icon for it in the launcher. I normally click on it once to start the process and use a shortcut (Ctrl+F12) to reveal/hide the terminal Window. Or I click the Launcher icon again to reveal it. That's the normal behaviour.

Now I have to click the launcher repeatedly (4, 5 times) until it loads for the first time. The number of times is random. Eventually, it will start a new instance that doesn't fit the saved configuration and use defaults (wrong size, font, placement, etc). Then I have to exit this instance and continue to click the launcher icon until I see it is running correctly.

From that point on it seems to run ok, but crashes eventually after a couple hours of work.

---

### Post by mc4man on 2011-12-22
The only thing I see is that once hidden that instance, (tilda 0), 'leaves' the launcher so re-clicking the icon opens a new  instance, (tilda 1, ect.). Each instance seems to use it's own config settings.
(And at least here the Icon= in the .desktop needed to be full path or it wouldn't use tilda.png, would use  utilities-terminal (gnome-terminal's icon

---

### Post by effenberg0x0 on 2011-12-22
> **mc4man said:**
> The only thing I see is that once hidden that instance, (tilda 0), 'leaves' the launcher so re-clicking the icon opens a new  instance, (tilda 1, ect.). Each instance seems to use it's own config settings.
(And at least here the Icon= in the .desktop needed to be full path or it wouldn't use tilda.png, would use  utilities-terminal (gnome-terminal's icon

Yes, I did set the .desktop to use a custom icon with a full path back when I installed it. 
Not sure why it would be spawning new instances for you. 
AFAIK, Tilda used to work like this to me (which I always thought to be the default behaviour, but not sure any more, I'm using it for a couple months only):

- 1 click on launcher: Start Tilda minimised/hidden
- Further clicks on launcher: Show previously opened instance. Same effect as using a keyboard shortcut to reveal it.
- Middle click on launcher: Start new instance. If a previous instance was running, the second one would not load the program settings and would be using ugly defaults.

---

