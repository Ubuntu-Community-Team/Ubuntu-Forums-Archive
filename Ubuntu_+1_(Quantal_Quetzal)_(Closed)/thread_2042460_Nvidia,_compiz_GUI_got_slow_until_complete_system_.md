---
title: "Nvidia, compiz GUI got slow until complete system stall"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-14
I think I stumbled into something unexpected here. I just booted the PC and realized that, after a minute or so into the desktop, moving between viewports (Ctrl+Alt+Arrow) was becoming slow. Top was showing nothing out of the ordinary. I had no browser, no other application besides what runs as a default when we boot current QQ.  

Dragging windows was also very slow. I launched glxgears and verified that instead of 9.5K I was getting about 5K. As a test, I enabled Wobbly Windows and tried to move a window. My mouse pointer was moving instantly from origin to destination, but the window was taking 3 to 5 seconds to go from one position to the other in slow motion. Opening the Dash started taking just about the same time.

I had time to switch to VT and look at the CPU and verified it was a normal, "on demand" 800MHz state, and NVidia was not running in it's highest frequency or hot. Then the PC completely stalled, which is really rare for me, and I had to manually press the reset button. I couldn't even Switch to a VT, Magic SysRq, nothing. Dead.
 
I reboot a couple more times today and saw the same issue 2 more times. But I have failed to find a cause or usable output.

I did try to disable/enable VSync in ccsm and nvidia-settings but it didn't solve it. Same for the force redraw workaround. They speed things up a little in exchange for some tearing (which I could see form and disappear in slow motion), but thing remain totally unusable.

There are no random bugs, of course, I just don't know what triggers it. I'm using the PC with a 4hr uptime now and it's as fast as usual.

Has anyone else seen anything like that today or recently? A complete stall was out of the ordinary for me.

My setup is:
QQ x86_64
X.Org X Server 1.12.1.902 (1.12.2 RC 2)
Compiz 0.9.8
Unity 6.0.0
NVidia 304.32 / 304.37

Regards,
Effenberg

---

