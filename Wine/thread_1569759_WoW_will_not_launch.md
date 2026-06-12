---
title: "WoW will not launch"
date: 2010-09-07
forum: Wine
---

### Post by Sgt.Schultz on 2010-09-07
I've just built myself a new computer but cannot get World of Warcraft to launch! I'm using Wine 1.2 on Ubuntu 9.10 with nvidia's 256.53 64-bit driver. I have also tried using wine 1.3 beta with no avail. I saw the following error in terminal when executing WoW.exe - "err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7e63d586"

Thanks for reading. ):P

---

### Post by cwwilson721 on 2010-09-07
Did you use Nvidia's own driver? Or the package from Ubuntu?

If you used Nvidia's did you install the 32-bit libraries? If not, that's your problem. wine is 32-bit. It needs them.

Also, make sure WoW is running in OpenGL mode, by either editing the config.wtf, or adding '-opengl' at the end of the launch command

---

### Post by aspiredfang on 2010-09-07
Highly recommend you check out [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421) for any of the odds and sods with regards to getting WoW to work.

As mentioned in the previous post, the biggest thing to consider is starting WoW in openGL mode

*Edit - Make sure you have shadows disabled too! I stopped playing now so the issue might have been resolved but, they weren't supported properly in openGL mode so, would screw up the game

---

### Post by Sgt.Schultz on 2010-09-07
> **cwwilson721 said:**
> Did you use Nvidia's own driver? Or the package from Ubuntu?

If you used Nvidia's did you install the 32-bit libraries? If not, that's your problem. wine is 32-bit. It needs them.

Also, make sure WoW is running in OpenGL mode, by either editing the config.wtf, or adding '-opengl' at the end of the launch command

Are you saying that I need to force an installation of the 32-bit driver in order to get wine working? I've only installed Nvidia's 64-bit driver directly from their website. I've also already tried editing config.wtf and adding '-opengl' without any luck.

Thank for your response.

---

### Post by cwwilson721 on 2010-09-07
> **Sgt.Schultz said:**
> Are you saying that I need to force an installation of the 32-bit driver in order to get wine working? I've only installed Nvidia's 64-bit driver directly from their website. I've also already tried editing config.wtf and adding '-opengl' without any luck.

Thank for your response.
During the install of Nvidia's 64bit script, it asks if you want to install the 32bit libs. Say "Yes".

THAT is why it's not working.

And to add to the other posters comments:

[LIST]
[*]Disable Compiz. Install/use compiz-fusion-icon, and select "Metacity" as desktop (Search Forum)
[*]Use opengl. Either edit config.wtf, or add '-opengl' at end of launch command (Search forum)
[*]Use XP mode, not 'Vista' or 'Windows7' for your wine environment for WoW. Unless you want issues with sound.
[*]No shadows, and watch Anti-aliasing. Both will KILL your FPS
[*]Enable "Reduce Input Lag"
[*]Use lowest video settings at first, and slowly boost them up, until you get a good balance between FPS and quality
[/LIST]
If you need more help, send me a message thru this board. I'll see what we can do, either YIM, AIM or MSN

---

### Post by Sgt.Schultz on 2010-09-07
> **cwwilson721 said:**
> During the install of Nvidia's 64bit script, it asks if you want to install the 32bit libs. Say "Yes".

THAT is why it's not working.

And to add to the other posters comments:

[LIST]
[*]Disable Compiz. Install/use compiz-fusion-icon, and select "Metacity" as desktop (Search Forum)
[*]Use opengl. Either edit config.wtf, or add '-opengl' at end of launch command (Search forum)
[*]Use XP mode, not 'Vista' or 'Windows7' for your wine environment for WoW. Unless you want issues with sound.
[*]No shadows, and watch Anti-aliasing. Both will KILL your FPS
[*]Enable "Reduce Input Lag"
[*]Use lowest video settings at first, and slowly boost them up, until you get a good balance between FPS and quality
[/LIST]
If you need more help, send me a message thru this board. I'll see what we can do, either YIM, AIM or MSN

Thank you for the suggestion cwwilson721! I just reinstalled the driver so that the 32-bit libs are included, which fixed my problem. 

Again thank you for your help and quick replies. ):P

---

### Post by cwwilson721 on 2010-09-07
No problem. Now you just have to wait for the "weekly go outside while WoW is down" time.

Please, if this fixed your issue, mark/change the thread as 'solved'

---

