---
title: "Remove Wine or Fix IE4 on Wine 1.2 AMD 64 bit?"
date: 2010-05-04
forum: Wine
---

### Post by PeggySue on 2010-05-04
Hi,

I have backed myself into a corner and need help recovering!

I have a 32 bit desktop and a 64 bit laptop and have just done a fresh install of 10.04 with wine 1.2 on both and tried to install a windows only program called Memory Map.  This application will not install without Internet Explorer being present.

First I tried the 64 bit laptop but was thrown by the new Ubuntu feature-bug that doesn't allow you to run programs on a CD.  I thrashed around, copied the installer executable to the desktop and generally made a mess.  When I ran the executable from the desktop it said it needed IE4 or later to install.  I thrashed around some more and tried to install IE5.  Having made a complete mess I used Synaptic to do a complete removal of Wine and Wine-geko and reinstalled 1.2 then 1.0 but still got the "Needs IE4" message.

My second attempt was on the desktop.  I used a terminal and ran "wine path-to-installer-on-CD" and this worked fine.  Memory-Map has loaded and runs fine under wine 1.2.

My question is I have I failed to reinstall wine correctly (is there something more to do than complete removal and delete the .wine folder) or is there a bug in wine with AMD 64 bit?

Any ideas would be appreciated.

---

### Post by cogadh on 2010-05-04
If you uninstalled Wine and deleted the .wine directory, then Wine is totally gone. To be certain you could try running "sudo apt-get purge wine" which will wipe everything, including any downloaded installation files, but generally speaking, a simple uninstall and deletion of the .wine directory is enough.

---

### Post by spaik on 2010-05-04
u might need to install winetricks and that might help you with the problem. never the less, wine sometimes doesnt work as we wish :(

---

### Post by PeggySue on 2010-05-05
Thanks for the help.

"sudo apt-get purge wine" showed the extras that were downloaded as dependencies.  I removed these but no go.

I hadn't heard of winetricks which is why I spent ages trying to download a version of Internet Explorer higher than 4.  I installed IE6 using winetricks but no go.

After much head scratching I wondered if it was a 64 bit processor problem.  I had been running the Memory Map program under the Mint 8 32 bit operating system.  So I tried installing 10.04 32 bit and everything worked well.  Memory Map runs fine under wine and all is now as it should be.  The 32 bit Ubuntu doesn't appear slower than the 64 bit version.  Perhaps it might be noticeable with a heavy processor load.

There appears to be a bug in wine when running in 64 bit mode.  Perhaps its just the Internet Explorer implementation that doesn't work correctly.  I will raise a bug report.

Thanks again for your help.

---

