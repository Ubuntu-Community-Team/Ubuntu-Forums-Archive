---
title: "Achieving the functionality of Ubuntu 10.04"
date: 2013-11-08
forum: Ubuntu, Linux and OS Chat
---

### Post by mazar83 on 2013-11-08
I have been patiently waiting for Ubuntu to restore the features that made me decide to use it in the first place. These were, among other things, the ability to have a different wallpaper on each of any number of desired workspaces (Compiz Wallpaper Plugin), the ability to save your session (especially terminals and their pwd's) because everyone has to reboot sometimes even if they'd rather not (gnome-session-save), the presence of a workspace switcher that conforms to the dimensions of your workspace setup and even shows an outline of the windows open in each workspace, and the ability for windows to have depth (Compiz 3D Windows Plugin).   ------------------------------------------------- For me, the ability to save sessions is the feature needed most urgently, but lengthy forum conversations indicate a lack of interest by Ubuntu to address this problem because the feature has problems? ------------------------------------------------- Well, at least the Compiz Wallpaper plugin has been restored in Ubuntu 13.04. However, the workspace switcher is buggy (often causing the system to freeze for 5-30 seconds) and the icon is static and uninformative. In Ubuntu 10.04, I had options to install workspace switcher applets all over the place, but in Ubuntu 13.04 I can not figure out how to install the workspace switcher applet from Ubuntu 10.04, a different switcher with similar functionality to that of Ubuntu 10.04, or any other for that matter. ------------------------------------------------- The Compiz 3D Windows plugin does not only make the cube visually appealing. It helps me see all the windows. It improves my ability to multi-task.     ------------------------------------------------- Together these features are the reason why I did not use Windows for years, but they do not seem to work consistently on Ubuntu after the introduction of Unity. I really tried Unity and for the most part it works. I do not accept rejecting a new approach because of having to learn how to use it, but the issues above have nothing to do with how one uses Unity. I need these features and I am tired of waiting. Are these features improved, fixed, or replaced in Ubuntu 13.10? If not, kindly inform me of a distribution where these features are readily available with the default shell interface.  Thank you, Mark Mazar

---

### Post by grahammechanical on 2013-11-08
If the functionality that you want is not in 13.04, then it will not be in 13.10, because 13.10 is not considered to be a major version upgrade. Do you have any reason to suppose that those functions would be put back into Ubuntu?

The Ubuntu developers have their minds on other developments. Such as Ubuntu as a converged OS between Phone, Tablet and PC. Unity is at version 7 and it is not so different from the version that is in 13.04. I do not think that it has the functions that you desire. The next version is Unity 8 and it is more or less complete but it will not come on to the Ubuntu desktop until 14.10 because it is designed to run on Mir. And Mir will not be in Ubuntu until 14.10. Mir is Ubuntu's display manager that will replace the X-server in 14.10 and also Light DM and Compiz. Until Ubuntu is based upon Mir I do not see much work being done to produce special effects. 

As with so much in Ubuntu and in open source in general development depends very much upon community developers who work on projects of their choosing. As someone once said, they have their own itch to scratch. Developers do not take orders from us. Even those developers who are paid to work do not take orders from us.

I think that you will find that every Linux distribution provides a downloadable live session image. You should test out a few. You may find that those developers have different aims to you. But then again you may find a distro that suits your taste exactly, Try live sessions first. do not take other people's recommendations.

Regards.

---

### Post by lykwydchykyn on 2013-11-08
You might try a distro with KDE, such as Kubuntu, OpenSuse or MEPIS.  I know that KDE at least can be configured with a different wallpaper for each desktop.

---

### Post by buzzingrobot on 2013-11-08
The lead Compiz developer put it into maintenance mode late last year, so it's unlikely anything that depends on it will be resurrected.

Saving a session is obviously useful.  KDE has a feature it calls "Activities" which is something like session saving:  Each workspace can be configured independently and persistently. I don't know, though, if it actually preserves state between restarts.  

KDE also has a huge roster of effects, wobbly and otherwise.

On Unity, the Windows + S key combination will show all open windows on all workspaces. Holding down just the Windows key will display a chart of all Unity's keyboard shortcuts.

The Gnome 2 interface used in 10.04 was discontinued by its developers 3 years ago, who moved on to the entirely different approach of Gnome 3.  Rather than rely on Gnome 3,  Ubuntu built its own interface, Unity. 

The XFCE interface might offer some of the functionality you're after.  it's a traditional panel-based interface.  It's offered on many distributions, including Xubuntu, an official member of the Ubuntu ranks.

The MATE desktop is based on the abandoned Gnome 2 code base and, as esssentially a recompilation of that platform with some adjustments so it can work in contemporary systems, is, visually and otherwise, almost identical to the interfce you used in 10.04.  No offical Ubuntu flavor exists but it can be easily installed following the guidance here:  mate-desktop.org. (Worked fine on 13.04 here.  Don't know if any of the old Ubuntu-developed plugins will work of if they are still available.)  Compiz can be installed, although I haven't. There is a Fedora spin that offers MATE with Compiz.

---

### Post by lykwydchykyn on 2013-11-08
> **buzzingrobot said:**
> 
Saving a session is obviously useful.  KDE has a feature it calls "Activities" which is something like session saving:  Each workspace can be configured independently and persistently. I don't know, though, if it actually preserves state between restarts.  


It can.  See settings->system administration->startup and shutdown->session management.

---

