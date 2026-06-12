---
title: "Here is some help for the somewhat common blank desktop"
date: 2014-03-05
forum: Ubuntu Studio
---

### Post by psionprime on 2014-03-05
There is an ongoing problem with no mouse, no desktop. Sometimes you have wallpaper, other times just a blank screen. The following are a few tips and not a solution as I don't know what is causing it for sure. Another common point is another account such as "guest" is usually fine.

I have had a stable UbuntuStudio 13.10 system for a while. When I updated AMD drivers to the latest betas (13.5, 14.1, 14.2 as of this writing) I had this issue every time. This last one I put more effort into it as the time before I did spend a lot but finally wound up backing up my home directory and reinstalling as my XOrg system was so hosed.

The initial install (all the betas) worked fine for a few boots, then something happened and I lost my desktop or it went blank. I searched the web and found tips on how to reconfigure the XOrg desktop, advice on how to reinstall yadda yadda yadda. All good advice and for the most part didn't work. I'm not a newb but it was taking a while. This last time, and I've been able to repeat it, something has happened to change /home/$USER/.config, .dbus and .gvfs to be owned by root:root. The xfce section inside .config had a display that was also causing issue.

So some points:

- while other accounts appear fine, the one you 'sudo' for the driver install may have chown some folders. change those back and preferable when everything is stable back up the .config file to restore it if you have issues

- if you are locking up before you get a chance to login you can try to boot into 'advanced' rescue mode. Start networking so everything is mounted then enter a root shell. Inside the shell you can try to remove the packages you installed, force reinstall the x system etc.

- if you are at the point where you log in but get the blank screen or just wall paper you probably need to ctrl-alt-f1 to a text terminal, log in, and sudo service lightdm stop to kill the xserver. You can then do ls -a -l and see if the above mentioned folders have been changed to root ownership. You can manually try starting the desktop with startxfce4. If you get just the desktop wall paper (ctrl-alt-f7) go back to the text terminal and check the diagnostic messages. Use ctrl-c to stop that session. If X appears to be working, just xfce4 appears glitched, you can carefully choose to delete .cache .config .Xauthority .dbus Just make sure you have saved any data incase things go wrong. Watching the debug messages is what clued me in .dbus was not creating a session and saw it had root ownership. I changed it to my user with sudo chown -r user:user .dbus After deleting those try startxfce4 again. If your screen is blank just wait a few minutes for things to time out. If X and xfce4 are working you will eventually get a default screen. It took my machine a little over a minute so am guessing there is a 60 second timeout in there somewhere.

I am extremely pleased most linux software I have is designed to use default values so you can get rid of potential corrupt config files.

I'm sharing this as not a solution but just tips as I haven't nailed down what is happening. Something is going on with the AMD drivers, Xorg or in the glue scripts for when video drivers are changed. I had to remove all referenced to multiple monitors as well. I also see a lot of people have these symptoms with nVidia so there is a common pattern with how the system reacts to driver changes.

Thanks to the Ubuntu Studio team who put this distribution together !

---

### Post by i-nimene on 2014-03-20
Thank you so much!!! You finally helped me... actually resolved my problem!! Thank you so much.

---

