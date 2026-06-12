---
title: "Which distro is suit for me?"
date: 2019-08-26
forum: Ubuntu, Linux and OS Chat
---

### Post by blacksun1102 on 2019-08-26
Hi guys, 
I have been using Windows since the early 90s and fairly new to Linux. So far I have played around with Ubuntu, Mint, and Debian. I didn't like the side launcher in Ubuntu and prefer a start menu. I also don't care for the GNOME and Unity desktop either. (Sorry to offend anyone.) However, I really liked the Cinnamon environment in Mint. But am currently having trouble deciding on a distro. I am pretty tech savvy and wouldn't mind doing little tweaking. I have an older Gateway computer with an AMD Phenom x4 1.8Ghz, 8GB ram, 640GB hard drive and an AMD Radeon HD 5570 graphic card. Any suggestions? Thanks!
Black!

---

### Post by guiverc on 2019-08-26
Firstly desktops != distro.   I love and use both Ubuntu and debian (okay others too, but primarily those two) and GNOME3/Unity weren't for me so I use other desktops - but to me at least, desktop != distribution.

I'm using LXQt (Lubuntu) currently, but my box also has XFCE (Xubuntu) installed, along with GNOME (Ubuntu) and MATE (Ubuntu-MATE). Partially as I cannot decide on anything (recall I mentioned distros earlier), so I push the decision of which I use to login time. This though does complicate things, so I'd not recommend loading multiple desktops on your machine when you start.

I'd for sure recommend Ubuntu & Debian. Mint is arguably more visually polished, but I prefer the security aspects of Ubuntu myself. Distribution choice though is up to you.  Debian is generally older packages (LXQt is currently pretty similar to this my primary Ubuntu box, but the other desktops are generally behind Ubuntu when comparing my current *Ubuntu 19.10 (2019-October release, ie. development) versus debian testing (bullseye/11). 

On-top of your distribution choice - you can then decide desktop (find your old D&D die/dice sets or you'll end up like me with multiple desktops which does have costs..) If you like XFCE, for Ubuntu use Xubuntu.  If you like GNOME it's main Ubuntu, if you like KDE it's Kubuntu, if you like LXQt it's modern Lubuntu (LXDE for older Lubuntu), if you like MATE it's Ubuntu-MATE, If you like Budgie it's Ubuntu-Budgie etc...  

The right desktop for you is a very personal thing, very much your tastes & experience/background with computers.  Some are lighter & faster (eg. Lubuntu/Xubuntu) when compared with others (GNOME/Ubuntu) but on my ~decade old box I can still use GNOME okay & it's more my personal taste that has me rarely use it.

You don't need to install, but can get a feel by downloading, writing to thumb-drive & "Try Ubuntu", or [https://tutorials.ubuntu.com/tutorial/try-ubuntu-before-you-install#0](https://tutorials.ubuntu.com/tutorial/try-ubuntu-before-you-install#0)  which applies equally well to any Ubuntu flavor (even to debian if you grab the live ISOs). 

If you can't decide, best I can offer is go look for your old D&D die/dice sets..  I never found mine...

ps: *I'd also recommend released or stable releases, not development.  It's do as I say, not as ..*

---

### Post by CatKiller on 2019-08-26
> **blacksun1102 said:**
> So far I have played around with Ubuntu, Mint, and Debian. I didn't like the side launcher in Ubuntu and prefer a start menu. I also don't care for the GNOME and Unity desktop either. However, I really liked the Cinnamon environment in Mint.

You don't appear to have tried KDE, which is the other major desktop environment. Lots of people like Xfce and LXQt, too, which also have the menu-based interface.

If you decide that you like Cinnamon best, I'd recommend using Ubuntu with Cinnamon rather than running Linux Mint.

The desktop environment and the distro are not the same thing, and the default look isn't the only way it can behave. With the exception of Gnome, all the desktop environments are pretty straightforward to customise to your tastes.

You'd pick your distro based on things like release schedule (Ubuntu has a Long Term Support release every two years and interim releases every six months; other distros are rolling-release), packaging structure (apt, or rpm, or compiling everything from source), or how quickly security issues are fixed. Once you've picked your distro, you can use any desktop environment with it.

Ubuntu has the largest userbase, and is the target for non-enterprise software. Enterprise software tends to target Red Hat primarily, and then Ubuntu. Masochists and control freaks tend to go for Arch or Gentoo, where they have to do everything themselves.

For Ubuntu, there are various flavours: those are just Ubuntu with different defaults. Different desktop environments by default, and Ubuntu Studio uses a lowlatency kernel, for example. You can install anything you want whichever flavour you start with: all the flavours use the same repositories.

---

### Post by Artim on 2019-08-26
"Start button?"  A mostly "familiar" interface that's easy to navigate?  Give Xubuntu a try on a LiveUSB.  It seems to suit people coming from Windows.

---

### Post by TheFu on 2019-08-26
That's a long period of learning on Windows. You'll have much to unlearn, grasshopper.  ;)
Distro definitely is NOT the GUI or the OS.  The GUI is just another program, like a different editor. There are probably 50 different GUIs you can run.  

If you like Cinnamon, why not just load that?  The packages are cinnamon-desktop-environment if you want everything, including all the applications you don't want or **cinnamon-desktop** if you just want the main GUI/DE.  There's little need to install a whole new OS.  However, when searching for a new desktop, it is prudent to use a new userid since some of the DEs are built using the same underlying libraries which can conflict in their settings.  Once you decide on the GUI you want, if you even want a GUI at all, then simply **mv ~/.config ~/.config-old** and logout, pick the new DE/WM from the menu BEFORE you login, login and all will be fine. You'll have a 100% fresh setup from the GUI settings without impacting any of your other data.  Set a reminder to delete ~/.config-old in a month (or use an **at** command to do it automatically), and be happy.

BTW, there's no need to have a DE at all.  GUIs are layered on Unix systems. 
```
X11 (this could be Wayland, but I don't think Wayland is read for normal use yet)
&#9492;&#9472;&#9472; Window_Manager (openbox, twm, mwm, fvwm, fluxbox, and 50 more)
    &#9492;&#9472;&#9472; Desktop_Environment (Gnome3, Gnome2, KDE, Mate, and 30 more)
        &#9492;&#9472;&#9472; DE_Shell
```
DEs seem to add hundreds of MBs of bloat for very little additional capabilities. A WM is the minimum required to have a "desktop" that lets us control where different X11 client programs are run.  It is responsible for the Window title, scroll bar, handles, and 6 controls in the upper left and upper right of the window.  It is also responsible for launching other programs, keyboard shortcuts, lots of things.

---

### Post by Frogs Hair on 2019-08-26
There is some good info [here]("https://ubuntuforums.org/showthread.php?t=2415676").

---

### Post by cruzer001 on 2019-08-26
That's one fine sticky DuckHook put together.

My words of wisdom is don't overthink it and just do it.  Your new and will be changing your mind on what to run at least half a dozen times.

---

### Post by lammert-nijhof on 2019-08-26
There is no best desktop, they all have different shades of grey. There is nothing wrong with a choice for Mint. You could also look at Peppermint, its look and feel is the same as Linux Mint, but it is more efficient with its resource usage.

---

### Post by deadflowr on 2019-08-26
What was wrong with Mint?
If you liked it, why not keep using it?

---

### Post by coffeecat on 2019-08-27
Sorry folks, but the OP is a copy-paste spammer. Compare with this: [https://ubuntuforums.org/showthread.php?t=2281804](https://ubuntuforums.org/showthread.php?t=2281804)

For those who have not seen this before, a copy paste spammer is one who copy-pastes a post from an earlier thread or from elsewhere, in order to simulate an innocent enquiry. They then come back later to add their spam links. That is, if they remember to come back at all. Spammers are notoriously and unbelievably stupid.

Thanks to all who contributed. I've closed the thread to new posts, but will leave it in situ as the discussion might be useful to those surfing the forum.

---

