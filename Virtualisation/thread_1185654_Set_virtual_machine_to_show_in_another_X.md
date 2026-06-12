---
title: "Set virtual machine to show in another X?"
date: 2009-06-12
forum: Virtualisation
---

### Post by kloplop321 on 2009-06-12
Well, I was reading somewhere that some people have done things like make a windows game, like Age of Wonders work well in full screen by moving it to another X Session.
this is what I saw in the winedb in one of the comments 
```
# Launches a new X session on display 3. If you don't have an Nvidia
# card take out the "& nvidia-settings --load-config-only" part
xinit -- :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "/home/user/.wine/drive_c/Program Files/Age of Wonders/"

# Forces the system to have a break for 2 seconds, X doesn't launch
# instantly
sleep 2

# hide the X cursor
xsetroot -display :3 -cursor /home/user/empty.xbm /home/user/empty.xbm

# Launches game (modify as needed)
DISPLAY=:3 env WINEPREFIX="/home/user/.wine" WINEDEBUG=-all wine "C:\Program Files\Age of Wonders\AoW.exe" 
```

Is there a way that I can make VirtualBox OSE to go full screen in another X session?
I am not very experienced with the terminal, so I am not exactly sure how to construct this. Also, is there a way I can make it so that after linux boots and logs in that the virtual machine starts up in another session and I can press like Ctrl+Alt+F6 and be in say Windows XP?

---

### Post by bodhi.zazen on 2009-06-12
Yes but you will need to do some reading and configuration.

Start with these two threads (I am suggesting you ssh into the guest)

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Those links are not exact, you will have to adapt (learn to start a new X session with the first, forward X with the second).

Once configured, start the guest on the command line without X and ssh in.

If you have a Windows guest it will be harder. Probably best ot start a minimal X session and then VNC in or go with seamless integration.

---

### Post by kloplop321 on 2009-06-12
I have managed to be able to make it run in a different X, I seem to have gotten it to work. Though it really makes my laptop slow.
Thank you for the links

---

