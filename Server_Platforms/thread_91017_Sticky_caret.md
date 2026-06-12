---
title: "Sticky caret ??"
date: 2005-11-16
forum: Server Platforms
---

### Post by dbee on 2005-11-16
When I type text on my screen, quite often the caret doesn't disappear when I nudge the text along. So I can get a whole row of 'ghost carets'.

I'm running on an idle AMD64 with a reasonable graphics card, no system load and a GB of memory. But the exact same thing happened on my P3 from time to time.:confused: 
Why is this happening ?

---

### Post by LordHunter317 on 2005-11-16
What is your graphics card?  This in X?  If on the console, are you using a framebuffer?

---

### Post by dbee on 2005-11-16
I'm using an nVIDIA geforce series 6 XENON, but like I said - I had the same problem with my P3 which had a Mark Radeon 7200. I'm using gnome ...

What's the easiest way to check if I'm using a framebuffer ? 
There doesn't seem to be a lilo or grub .conf file ...

---

### Post by dbee on 2005-11-27
bump ... same problem ????

---

### Post by hk_2999 on 2006-09-23
I'm having this problem too.

---

### Post by thojoh on 2006-10-14
SOLUTION FOUND!

at least for my computer. I had the same problem: which was that I had those 'ghosts' of the cursor (caret, whatever it is called - the vertical line that shows you where the letters you type will appear). Many of these lines where just staying on the screen when I was moving through text in OpenOffice or Firefox.

I had to change my NVIDIA driver that was installed. If you have a certain graphic card version, you might need a different (older) driver to get rid of this ghosting thing. At least, that was it with me.

Changing it was easy using Synaptic:


1. Search for "Nvidia" in Synaptic

2. Look which NVIDIA driver is installed.

On my computer, "NVIDIA binary XFree86 4.x/X.Org driver" was installed (which probably is the default for computers using NVIDIA)
I had to change it to the "legacy" version:
"NVIDIA binary XFree86 4.x/X.Org 'legacy' driver"

3. Install the "legacy" version of the NVIDIA driver
(uninstalling the current driver will automatically be done by Synaptic)

4. In the terminal, run "sudo nvidia-glx-config enable" to enable the driver. 

5. Restart you computer.

Done!

(of course this solution only applies if you have one of these graphic cards that need the older 'legacy' version. I didn't know for sure about my graphic card, but I just tried it and it seems that that was the case. Now, the problem is solved.) 
The computer makes a backup of the changes to the xorg.conf file and tells you in the terminal which command to use to bring back the old settings. So if you note down that command before restarting you computer, you can always revert your changes if it doesn't solve your problem.

I hope this helps some of you!  (I have seen the problem posted several times, but never seriously addressed with a soution.)

all the best!   :-D 

thomas

---

