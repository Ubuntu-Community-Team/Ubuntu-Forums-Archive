---
title: "virtualbox gutsy seamless taskbar covers kde taskbar"
date: 2007-10-21
forum: Virtualisation
---

### Post by frankeleone on 2007-10-21
Hello,
     I have searched various forums (Virtualbox, Ubuntu, Linuxquestions) for this problem I am having. I have seen it addressed in only one thread in Ubuntu without solution here in a closed development forum:
[http://ubuntuforums.org/showthread.php?t=568710]("http://ubuntuforums.org/showthread.php?t=568710")

and once in a virtualbox forum without solution. My problem is that under seamless mode, my windows xp guest taskbar covers my Kubuntu 7.10 KDE taskbar at the bottom as if it does not "see" the KDE desktop. I have attached a screenshot.

How I arrived at this problem: When I had Kubuntu 7.06 (host) with Virtualbox 1.5 (not the ose) and 1.4 guest additions, I had no problem with the windows xp guest taskbar fitting nicely atop the host KDE taskbar in seamless mode. I then upgraded from 7.06 to 7.10 Kubuntu, got Virtualbox to use the latest kernel, and the problem started. At the time of upgrade, I selected the Nvidia restricted driver, but thinking that this may be the problem, I have since uninstalled it. I'm sure the Compiz desktop effects are not going, as it is an older computer, and I looked to see that nothing has been installed on the Adept manager that has anything with Compiz in the name. I have made sure that the screen resolution of 7.10 is the same as the resolution in the guest windows xp. Continuing to look for a solution, I next upgraded the guest additions to 1.5, then Virtualbox to 1.52, then the guest additions to 1.52. None of these efforts changed anything. The virtual machine itself actually works fine; it's just the annoying, and unmoveable,  location of the windows xp guest taskbar that has been the issue since I upgraded from Kubuntu 7.06 to Kubuntu 7.10. I guess I should be thankful, actually. Any help would be greatly appreciated. Thanks, Frank

---

### Post by jsully1 on 2007-10-22
When you go into seamless mode, go to display properties on the Windows machine - what's the resolution set at?  Mine adjusts (in gnome) to 1400x1000, indicating that it's subtracting the 25 pixels for each of my Gnome panels (top and bottom).

---

### Post by n3tfury on 2007-10-22
or you can move your kde bar up top.  that's what i do in gnome.

---

### Post by Jimlas53 on 2007-10-23
I have the same (annoying!) issue on two different machines, and I also see unpredictable switching of the background.  It looks like the guest background is basically black, sometimes this shows instead of the Ubuntu desktop.  Going out of seamless mode everything is fine.
The guest uses the classic XP blue background.

---

### Post by frankeleone on 2007-11-02
OK....so, I was thinking of doing a clean install of Gutsy to see if that would fix the problem. I'm not really interested in the workaround type solutions, but thanks for the input. Before I do this, has anyone had this problem with a clean instal, or just an upgrade from Feisty to Gutsy? Thanks, Frank

---

### Post by antraxx2k4 on 2007-11-02
Another "workaround solution"... (how I accomplish this)

I moved the XP taskbar to the right and set it to auto-hide, because I don't need it much.
But the solution with the reduced resolution sounds good too.

Anyway, I love the seamless mode and how easy it was to set up. :-)

---

### Post by Ponhovo on 2008-05-14
how i resize the windows desktop to "1400x1000", so the taskbars don1t hide one another?

---

### Post by ethanep on 2008-06-05
I found a workaround that takes 3 seconds and works. Make a new pannle that is the same height as the windows taskbar at the bottom of the screen. If there is nothing on it, it won't get selected and come to the top from anything you do. The windows bar sits on the bottom of the screen with the empty panel behind it and the panel for ubuntu its directly above it. I have had no disadvantages to this except that you lose a little screen when the VM is not running.

Hope this works for you.

---

