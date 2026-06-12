---
title: "[SOLVED] GUI without desktop?"
date: 2008-05-19
forum: Server Platforms
---

### Post by kshane on 2008-05-19
Hi all...

I "miss" DOS, believe it or not...  So,I am "playing" with the server edition of 8.04.  I set aside a 9 gig partition and have it running fairly well, including a static ip set up.  

I was wondering if it is possible to use a graphical program without installing a desktop?  In other words, I want to keep the command line environment, but be able to use programs such as Firefox and Gedit.

I installed firefox from the repositories, but I get an error on the display when I try to invoke the program.

I know these are probably pretty basic questions, so I appreciate your patience.  Just trying to learn.  :grin: 

Kevin

---

### Post by 505 on 2008-05-19
No, not possible, but have you tried Ctrl+Alt+F1 on any graphical linux. Will get you straight to a terminal (DOS-like) environment. Ctrl+Alt+F7 will get you back to the GUI. On F1 to F6 there are 6 distinct terminals present, for all your command line needs.

---

### Post by kshane on 2008-05-19
Thanks for the answer!  

Yes, I knew about the terminal.  Was just hoping!  :)

Kevin

---

### Post by kshane on 2008-05-19
Um..  Actually, how about just running some kind of basic browser without a desktop environment?

Thanks in advance!

Kevin

---

### Post by ginjabunny on 2008-05-19
as far as I know browsers like Firefox need some sort of window manager, maybe something like fluxbox or icewm would fit the bill, if not then maybe xfce.

I think you can fiddle with the initial runlevel to stop the window manager from starting by default and use startx but I think you have to move startup services into that runlevel aswell, I am not sure about this in Ubuntu but I used to do it in Fedora. There maybe an easier way of doing it.

---

### Post by NateMan on 2008-05-19
To browse the web without a gui, try install lynx (sudo apt-get install lynx) Its a non-graphical web browser that works quite well.

---

### Post by kshane on 2008-05-19
Appreciate the response!

I was basically thinking along the lines of a DOS type environment.  Being able to run an editor that was graphical, but ANSI-based, etc...

I suppose if I want to run a DOS-like environment, I'll have to run DOS!  :lolflag:

Again, thanks...

Kevin

---

### Post by NateMan on 2008-05-19
What do you mean by running a graphical editor that is ansi based? There are plenty of ansi based IDEs available, vim, emacs, etc... Let me know a little more about what your trying to do and maybe you can be helped.

---

### Post by kshane on 2008-05-19
> **NateMan said:**
> What do you mean by running a graphical editor that is ansi based? There are plenty of ansi based IDEs available, vim, emacs, etc... Let me know a little more about what your trying to do and maybe you can be helped.

I would like to maintain a non-gui environment, while having some basic type of graphical interface, i.e., nano, vim, etc...  For example, a similar type interface for web browsing, music player, video player, etc., with keyboard-based interface and a basic, graphic (ANSI?) output to the screen (except video replay, of course).

Kevin

---

### Post by NateMan on 2008-05-19
I do believe that all of the above except for video can be done. I know there are music players, ides, web browsers, and almost any sort of thing that can be done without graphics. Video playback may not be possible, at least as far as I can tell. The nix terminal is quite well developed, far beyond what dos can do. You can use Lynx for webbrowsing, the named programs for editing, and mplayer or mp3blaster for audio. Any other programs you need a terminal equivalent for? Almost anything can be found for the cli by searching.

---

### Post by kshane on 2008-05-19
> **NateMan said:**
> I do believe that all of the above except for video can be done. I know there are music players, ides, web browsers, and almost any sort of thing that can be done without graphics. Video playback may not be possible, at least as far as I can tell. The nix terminal is quite well developed, far beyond what dos can do. You can use Lynx for webbrowsing, the named programs for editing, and mplayer or mp3blaster for audio. Any other programs you need a terminal equivalent for? Almost anything can be found for the cli by searching.

Thanks for the enlightenment!  I'll give those programs a shot and keep experimenting around...

Kevin

---

### Post by NateMan on 2008-05-19
Your welcome, it was no problem. I'm glad I could help. We run numerous cli only boxes at work and well we've figured out ways around most stuff. Happy serving!

---

