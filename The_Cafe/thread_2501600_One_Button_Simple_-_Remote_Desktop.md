---
title: "One Button Simple - Remote Desktop"
date: 2024-10-14
forum: The Cafe
---

### Post by Shibblet on 2024-10-14
I have two computers.  One is for data processing.  I basically don't need to access but for a few minutes at a time to start some processes, and then log-out.  When the processes are done, the computer turns itself off, and I can start it again whenever I need to.  These processes use at least 90% of the CPU, so when it's working, I can use my "main" computer at full capacity.

So, I need a headless PC with a remote desktop.

I have just spent the better part of a week [COLOR="#FF0000"][SIZE=3]**TRYING**[/SIZE][/COLOR] to get a remote desktop server to work on various Linux distributions.  The only "server" side OS I could get working was Ubuntu, and then it had some caveats.

I've tried x2go, TigerVNC, RDP, etc.  All of the above.  The only success I had, was turning on Remote Desktop on Ubuntu 24.10... and even that was a bit of a frustration.  You go to click the button to turn on Remote Desktop, and the settings menu freezes.  I found out you have to ```
sudo apt-get reinstall remote-desktop
```, then restart the computer, just to turn it on.  Not sure what the problem was there, but at least I found a solution.

[https://ubuntuforums.org/showthread.php?t=2501123]("https://ubuntuforums.org/showthread.php?t=2501123")
BTW, TheFu... thank you for all the help... even though I couldn't get it to work.

Anyway.  It kinda worked.  After I was able to remote into Ubuntu, I found that it wouldn't shut-down appropriately, not would it boot up without a monitor attached.  Ugh.

Then I heard that KDE Plasma 6 has included a remote desktop application.  Did not work [COLOR="#FF0000"][SIZE=3]**AT ALL.**[/SIZE][/COLOR]  After a week of fussing, fighting, researching, reading, and a significant amount of frustration... I called a friend to see if he could help.

Unfortunately, his response was "Dude... just use Windows on the server PC.  All you have to do is turn on RDP.  Then it's open to use."

I saw no recourse at this point, so I gave it a shot... sure enough, it worked [COLOR="#0000FF"][SIZE=3]**flawlessly, and effortlessly.**[/SIZE][/COLOR]

This took me back in my head to a previous post about "When the year of the Linux desktop will be a real thing..." [https://ubuntuforums.org/showthread.php?t=2500707]("https://ubuntuforums.org/showthread.php?t=2500707")

And this little remote deskop thing answered my question.  Simplicity.

Ubuntu has attemtped to do this, by having features that people want, and making them readily usable, at the flip of a switch.  Like Remote-Desktop.  And it's frustrating to not have another working option available.  I mean, I can understand Linux not having support for proprietary software... but [COLOR="#FF0000"][SIZE=3]**no easy way**[/SIZE][/COLOR] to set-up a remote desktop?  Seems absurd to me.

I mean, is it just me?  Am I the only one seems to run into these problems?  Has anyone else strugged with remote-desktops, and their configuration?  I feel like I'm building a house of cards in front of a fan.

---

### Post by TheFu on 2024-10-14
Yes, it is just you. ;)

OTOH, I don't install a new OSes more than every 2-4 yrs, so when I get something working, I'll have 2-4 yrs that it "just works".  I ensure most of my OSes are on the same release version for greater compatibility.  Trying to get GUI things to work between 20.04 and 24.04 can be a challenge.  I avoid that.  Both my physical "servers" run 20.04.  This is so maintaining them both is easier.  I installed and used 1 of them for about 6 months before moving the other one from 18.04 to 20.04.  A cautious time.

Since 20.04, Canonical has been pushing Wayland. That makes all sorts of desktop-things a challenge that wouldn't be if we all stayed on Xorg - X/11.  For my part, I've only played with Wayland long enough to see that it doesn't meet my needs, then I moved back to Xorg for all GUI stuff, which actually works.

Remote desktops are tightly coupled to the display server.  So, rather than blaming those RDP/VNC/NX programs, blame Wayland for preventing them from all working.  

With 24.04, Wayland became the default display server for everyone, so that means you need to only use wayland-aware remote desktop tools, which are still very limited in the number available.  Last time I checked a few years ago, I think only the Gnome Remote Desktop supported Wayland. Perhaps that has changed. IDK.

Linux doesn't care about remote desktops.  Don't confuse the OS with applications.  The different GUIs don't care about remote desktops either.  Don't confuse 1 application from another.  The "desktop" most people thing of as "the OS" isn't and it never has been.  The "desktop" runs on a display server and the display server runs on the OS. At least 3 different layers.  And since the 1990s, we haven't been worried much about the display server (X/Server), because it almost always "just worked" for everyone.  Prior to that point, getting the X/Server to run with the settings we wanted could be a big challenge.  When it was first available on Linux, it was possible to override our CRTs with incorrect settings in our xorg.conf file and burn out monitors.  Compared to those days, things really are much better.   

Until Wayland came along.  Eventually, Wayland will work for everyone. It isn't there yet.  There are many capabilities in X/11 that Wayland just doesn't provide and for varying reasons, they aren't prioritized in the way each of us would prefer.  Seems that game performance always get prioritized higher than automation or remote desktop support.

Sigh.

BTW, I loaded up Kubuntu 24.10 yesterday into a VM for a LUG show and tell.  Allowing all default install choices.  For the most part, it was a nice experience, though I was unhappy that the partition table was MBR.  There's no good reason for any Linux-only system to use MBR partition tables in 2024. There just isn't.  Also, the swap file was about 500MB.  That's not enough for a system with just 4GB of RAM.  Bad installer choices.  But I guess that will depend on the installer team and their decisions to correct.

Anyway, if you use wayland and want remote desktop to just work, then you'll need the gnome remote desktop program - perhaps on both sides. IDK.  [https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop) appears to say that Gnome Remote Desktop is tied to mutter and the same version of Gnome DE, which is probably too heavy for your old laptop.

KDE Plasma with Wayland has this [https://planet.kde.org/arjen-hiemstra-2023-08-08-remote-desktop-using-the-rdp-protocol-for-plasma-wayland/](https://planet.kde.org/arjen-hiemstra-2023-08-08-remote-desktop-using-the-rdp-protocol-for-plasma-wayland/) ... they suggest using a flatpak to try it out.

---

### Post by ryderbell on 2024-10-21
Thank you so much for sharing the link.

---

